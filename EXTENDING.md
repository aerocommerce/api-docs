## Extending the API

### Queries

To extend any queries used in the view/index endpoints you can extend the relevant pipeline, e.g.:

```php
\Aero\Api\Pipelines\Query\OrderQuery::extend(function (\Illuminate\Database\Eloquent\Builder $query, $next) {
    $query->with('customRelationship');
    
    return $next($query);
});
```

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


