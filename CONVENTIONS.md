# API Conventions

## Payload Conventions

Here are the main conventions & exceptions to those conventions that our payloads abide by, any more specific exceptions will be addressed in the relevant section in `Examples`

### Attribute Conventions

When passing attribute data to the API the key will typically match the attribute name on the respective model, the one main exception to this are any attribute ending with '_code' will lose its suffix (e.g.: 'currency_code' => 'currency')

### Relationship Conventions

When passing nested (related) data to the API the key should be a snake case representation of the relationship method between the model and related model, e.g.: `shippingMethod` => `shipping_method`

### Price Conventions

All requests expect amounts to be provided in the currency's smallest unit. For example, to charge 10 GBP, provide an amount value of 1000 (that is, 1000 pence).

When passing a price it should be formatted as a nested json object with `amount` & `tax` keys where the `amount` is the price **excluding tax**, e.g.:

```json lines
{
    "price": {
        "amount": 40000, // Excluding tax
        "tax": 8000
    }
}
```

**Some** prices (will be mentioned in the relevant examples section) support passing an unnested value which includes tax, e.g.:

```json lines
{
    "price": 48000 // Including tax
}
```

### Date Conventions

When passing a date it must be Carbon parseable date, e.g.: `"2023-09-01T09:29:41.000000Z"` or `"2023-09-01 09:29:41"` or `"2023-09-01"`, if no time is provided midnight will be used as the date's time

### Pagination Conventions

Any paginated endpoint accepts the following parameters

| Parameter   | Description                                                    | Example      |
|-------------|----------------------------------------------------------------|--------------|
| `page`      | The page number, defaults to 1                                 | ?page=2      |
| `per_page`  | The number of results per page, defaults to 24, max allowed 96 | ?per_page=48 |
| `ids`       | The ids (comma seperated) of models to be fetched              | ?ids=1,2,5   |

Any paginated endpoint will return a response inline with the Laravel pagination system, e.g.:

### Scoped Conventions

Any scoped endpoint (typically an index endpoint) supports a `scope` parameter which should be a comma seperated string of the scopes you wish to use (the supported scopes are endpoint specific and as such will be outlined in the relevant section)

```json lines
{
    "current_page": 1,
    "data": [
        //...
    ],
    "first_page_url": "http://l9.test/api/products?page=1",
    "from": 1,
    "last_page": 2,
    "last_page_url": "http://l9.test/api/products?page=2",
    "next_page_url": "http://l9.test/api/products?page=2",
    "path": "http://l9.test/api/products",
    "per_page": 24,
    "prev_page_url": null,
    "to": 24,
    "total": 29
}
```

### Image Factory Conventions

The following query parameters can be passed in order to use Image Factory for generating the image urls

| Parameter               | Description             | Example                               |
|-------------------------|-------------------------|---------------------------------------|
| `image_factory_width`   | The width               | ?image_factory_width=200              |
| `image_factory_height`  | The height              | ?image_factory_height=200             |
| `image_factory_options` | Comma seperated options | ?image_factory_options=flip,greyscale |

If any of these query parameters are present in the GET requests then the Image Factory will be used

[Back to contents](README.md#table-of-contents)
