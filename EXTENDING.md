## Extending the API

### Routes

To add some API routes you can use the `addApiRoutes` method on the Router, e.g.:

```php
\Illuminate\Routing\Router::addApiRoutes(__DIR__.'/../routes/api.php');
```

This prefixes the routes with `api` and also attaches the `aero.api` middleware group which has the following middleware:

```php
'middleware' => [
    \Aero\Api\Http\Middleware\ForceJsonResponse::class, //Forces Response to be JSON instead of HTML
    \Aero\Api\Http\Middleware\LogApiUsage::class, //Logs API Usage so it can be viewed in Admin
    \Aero\Api\Http\Middleware\CheckApiToken::class, //Validates API Token 
    \Aero\Api\Http\Middleware\SetLanguageHeader::class, //Sets "Language" Header used for Translations
],
```

Can modify the middleware in this group via the `api` config file

### Queries

To extend any queries used in the view/index endpoints you can extend the relevant pipeline, e.g.:

```php
\Aero\Api\Pipelines\Query\OrderQuery::extend(function (\Illuminate\Database\Eloquent\Builder $query, $next) {
    $query->with('customRelationship');
    
    return $next($query);
});
```

#### Adding custom scope

Create a scope class (can also just pass a closure):

```php
class ProductScheduledScope extends \Aero\Api\Scopes\ElasticApiScope
{
    public function __invoke(\Aero\Search\Elastic\Query\Builder $query): void
    {
        $query->publishedAfter(Carbon::now());
    }
}
```

```php
\Aero\Api\Pipelines\Query\ElasticProductQuery::addScope('scheduled', \Aero\Api\Scopes\Products\Elastic\ProductScheduledScope::class)
```

For eloquent queries it is the same procedure but you receive an eloquent query builder instead of an elastic query (and extend EloquentApiScope instead)

#### Adding custom filter

Create a filter class (can also just pass a closure):

```php
class ProductManufacturersFilter extends \Aero\Api\Filters\ElasticApiFilter
{
    public function __invoke(\Aero\Search\Elastic\Query\Builder $query): void
    {
        $rawManufacturers = $this->request->get('manufacturers');

        if (! $rawManufacturers) {
            return;
        }

        $manufacturers = explode(\Aero\Api\Http\Requests\ApiIndexRequest::IDS_SEPARATOR, $rawManufacturers);

        $query->withFacets([
            'm' => $manufacturers,
        ]);
    }
}
```

For eloquent queries it is the same procedure but you receive an eloquent query builder instead of an elastic query (and extend EloquentApiFilter instead)

**NOTE:** The difference between scopes and queries are that scopes don't receive parameters and are called via `?scope=scope1,scope2` while filters can accept parameters e.g. `?manufacturers=1,2,3`

### Validation

To extend any validation used for endpoints you can extend the relevant request, e.g.:

```php
\Aero\Api\Http\Requests\CreateOrderRequest::expects('custom_field', 'required|string', [
    'custom_field.required' => 'The custom field is required'
]);
```

You can also extend the `prepareForValidation` method of the request by extending the relevant pipeline, e.g.:

```php
\Aero\Api\Pipelines\Prepare\PrepareCreateOrder::extend(function (\Aero\Api\Helpers\Data $data, $next) {
    // Transform payload before validation runs
    
    return $next($data);
});
```

You can also extend the `validated` method of the request by extending the relevant pipeline, e.g.:

```php
\Aero\Api\Pipelines\Validated\CreateOrderValidated::extend(function (\Aero\Api\Helpers\Data $data, $next) {
    // Transform payload after validation has succeeded
    
    return $next($data);
});
```

See [Helpers > Data](#data) for information about the `Data` helper class

### Helpers

#### Data

This class is essentially a wrapper for an array that forwards calls to `data_get` & `data_set` it also implements `ArrayAccess` see below recommended usage

Getting values:

```php
// Use get method (recommended)
$data->get('key', 'default value');

// Or use array syntax
$data['key'] ?? 'default value';

// Or use data_get
data_get($data, 'key', 'default value');
```

Setting values:

```php
// Use set method (recommended)
$data->set('key', 'value');

// Or use fill method (only sets value if it doesn't exist)
$data->fill('key', 'value');

// Or use array syntax
$data['key'] = 'value';

// Or use data_set (not recommended - will throw an error if using nested keys, e.g. 'key.child')
data_set($data, 'key', 'value');
```

Checking values exist:

```php
// Use exists method (recommended)
$data->exists('key');

// Or use isset
isset($data['key']);
```

Forgetting values:

```php
// Use forget method (recommended)
$data->forget('key');

// Or use unset
unset($data['key']);
```


