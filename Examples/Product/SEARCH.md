# Product Search

## Required

This route performs product search queries using elasticsearch, as such you should reindex your product documents, e.g.:

```
php artisan aero:search:reindex --type=product
```

## Attributes:

See [View Product](VIEW.md)

## Remarks

This is a paginated route (see [Pagination Conventions](../../CONVENTIONS.md#pagination-conventions))

In addition to the standard parameters accepted for a paginated route, this route also accepts:

| Parameter        | Description                        | Example                                 |
|------------------|------------------------------------|-----------------------------------------|
| `min_updated_at` | The min updated at for a product   | ?min_updated_at=2023-08-30%2010:35:05   |
| `max_updated_at` | The max updated at for a product   | ?max_updated_at=2023-08-30%2010:35:05   |

see [Date Conventions](../../CONVENTIONS.md#date-conventions) for more info on acceptable values for these parameters

This is also a scoped route (see [Scoped Conventions](../../CONVENTIONS.md#scoped-conventions))

This route also has some specific scopes:

| Name                 | Description                                     | Example                   |
|----------------------|-------------------------------------------------|---------------------------|
| `active`             | Only return active products                     | ?scope=active             |
| `inactive`           | Only return inactive products                   | ?scope=inactive           |
| `visible`            | Only return visible products                    | ?scope=visible            |
| `hidden`             | Only return hidden products                     | ?scope=hidden             |
| `categorised`        | Only return products that are in a category     | ?scope=categorised        |
| `un-categorised`     | Only return products that aren't in a category  | ?scope=un-categorised     |
| `published`          | Only return published products                  | ?scope=published          |
| `unpublished`        | Only return unpublished products                | ?scope=unpublished        |
| `scheduled`          | Only return scheduled to be published products  | ?scope=scheduled          |
| `has-stock`          | Only return products that have stock            | ?scope=has-stock          |
| `out-of-stock`       | Only return products that don't have stock      | ?scope=out-of-stock       |
| `not-tracking-stock` | Only return products that aren't tracking stock | ?scope=not-tracking-stock |
| `reduced`            | Only return reduced products                    | ?scope=reduced            |
| `not-reduced`        | Only return non-reduced products                | ?scope=not-reduced        |
| `has-images`         | Only return products that have images           | ?scope=has-images         |
| `no-images`          | Only return products that don't have images     | ?scope=no-images          |

This route also has some specific filters:

| Name              | Description                                                                             | Example                                                        |
|-------------------|-----------------------------------------------------------------------------------------|----------------------------------------------------------------|
| `manufacturers`   | Only return products with specific manufacturer ids (or names)                          | <span style="white-space: nowrap;">?manufacturers=1,2,3</span> |
| `price`           | Only return products with specific price in whole units (e.g. pounds, not pence)        | ?price=123                                                     |
| `min_price`       | Only return products with price above min price in whole units (e.g. pounds, not pence) | ?min_price=123                                                 |
| `max_price`       | Only return products with price below max price in whole units (e.g. pounds, not pence) | ?max_price=123                                                 |
| `stock_level`     | Only return products with specific stock level                                          | ?stock_level=1                                                 |
| `min_stock_level` | Only return products with stock above specific stock level                              | ?min_stock_level=1                                             |
| `max_stock_level` | Only return products with stock below specific stock level                              | ?max_stock_level=10                                            |
| `type`            | Only return products of a certain type (e.g. simple or variant)                         | ?type=variant                                                  |

## Example Response

```http request
GET /api/products/search?per_page=2&min_updated_at=2023-08-30%2010:36:23&min_stock_level=1&max_stock_level=10
```

```json lines
{
    "current_page": 1,
    "data": [
      //...
    ],
    "first_page_url": "http://seg.test/api/products/search?per_page=2&min_updated_at=2023-08-30%2010%3A36%3A23&min_stock_level=1&max_stock_level=10&page=1",
    "from": 1,
    "last_page": 3,
    "last_page_url": "http://seg.test/api/products/search?per_page=2&min_updated_at=2023-08-30%2010%3A36%3A23&min_stock_level=1&max_stock_level=10&page=3",
    "next_page_url": "http://seg.test/api/products/search?per_page=2&min_updated_at=2023-08-30%2010%3A36%3A23&min_stock_level=1&max_stock_level=10&page=2",
    "path": "http:\/\/seg.test\/api\/products\/search",
    "per_page": 2,
    "prev_page_url": null,
    "to": 2,
    "total": 5
}
```

See [Product View Example Response](./VIEW.md#example-response) for the structure of the products data


