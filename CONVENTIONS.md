# API Conventions

## Payload Conventions

This section outlines the conventions the payloads follow. Any endpoint-specific exceptions will be documented in the relevant Examples section.

### Attribute Conventions

- Keys generally match the attribute name on their respective models.
- **Exception:** Attributes ending in "_code" should omit the suffix when passed to the API, e.g. `currency_code` => `currency`

### Relationship Conventions

- Nested data should use a **snake_case** version of the relationship method name where present, e.g.: `shippingMethod` => `shipping_method`

### Price Conventions

- Prices retrieved from the API are mostly in the currency's smallest unit, e.g. `1000` = `10 GBP`
- Prices should generally be provided in the currency’s standard unit, e.g. `10` = `10 GBP` (unless otherwise stated)
- Prices should generally be passed as an object, e.g.:

```json lines
{
    "price": {
        "amount": 400, // Excluding tax
        "tax": 80
    }
}
```

- **Exception:** Some endpoints support passing a single tax-inclusive value (noted in examples):

```json lines
{
    "price": 480 // Including tax
}
```

### Date Conventions

- Dates must be **Carbon-parseable**, support formats include:
  - 2023-09-01T09:29:41.000000Z
  - 2023-09-01 09:29:41
  - 2023-09-01 (defaults to midnight if no time is provided)

### Pagination Conventions

All paginated endpoint accepts the following parameters

| Parameter        | Description                                            | Example                                 |
|------------------|--------------------------------------------------------|-----------------------------------------|
| `page`           | The page number (default: 1)                           | ?page=2                                 |
| `per_page`       | The number of results per page (default: 24, max: 96)  | ?per_page=48                            |
| `ids`            | Comma-separated list of IDs to fetch                   | ?ids=1,2,5                              |
| `min_updated_at` | The min updated at for a product                       | ?min_updated_at=2023-08-30%2010:35:05   |
| `max_updated_at` | The max updated at for a product                       | ?max_updated_at=2023-08-30%2010:35:05   |

**Note:** The `min_updated_at` and `max_updated_at` filters are only available on index endpoints for models that have an updated_at timestamp.

Responses follow Laravel’s pagination format, e.g.:

```json lines
{
    "current_page": 1,
    "data": [
        //...
    ],
    "first_page_url": "http://aero.test/api/products?page=1",
    "from": 1,
    "last_page": 2,
    "last_page_url": "http://aero.test/api/products?page=2",
    "next_page_url": "http://aero.test/api/products?page=2",
    "path": "http://aero.test/api/products",
    "per_page": 24,
    "prev_page_url": null,
    "to": 24,
    "total": 29
}
```

### Scoped Conventions

- Index endpoints support a scope parameter, which is a comma-separated list of scopes.
- Supported scopes are endpoint-specific and documented in the corresponding `Examples` section

### Image Factory Conventions

The following query parameters can be added to use Image Factory for generating image URLs:

| Parameter               | Description             | Example                               |
|-------------------------|-------------------------|---------------------------------------|
| `image_factory_width`   | Output image width      | ?image_factory_width=200              |
| `image_factory_height`  | Output image height     | ?image_factory_height=200             |
| `image_factory_options` | Comma-seperated options | ?image_factory_options=flip,greyscale |

If any of these query parameters are present in the GET requests, Image Factory will be applied

[Back to contents](README.md#table-of-contents)
