# Product Index

## Overview

This endpoint retrieves a paginated list of all products

## Structure

See [View Product](VIEW.md) for the structure of the product payloads inside the `data` array

## Scopes

| Name                 | Description                                     | Example                   |
|----------------------|-------------------------------------------------|---------------------------|
| `active`             | Only return active products                     | ?scope=active             |
| `inactive`           | Only return inactive products                   | ?scope=inactive           |
| `visible`            | Only return visible products                    | ?scope=visible            |
| `hidden`             | Only return hidden products                     | ?scope=hidden             |
| `published`          | Only return published products                  | ?scope=published          |
| `unpublished`        | Only return unpublished products                | ?scope=unpublished        |
| `scheduled`          | Only return scheduled to be published products  | ?scope=scheduled          |

**NOTE:** These scopes are applied at the database level and may not always reflect real-time search index data. For precise filtering, use the [Search Product](SEARCH.md) endpoint.

## Example Response

```http request
GET /api/products?per_page=2&min_updated_at=2023-08-30%2010:36:23
```

```json lines
{
    "current_page": 1,
    "data": [
      //...
    ],
    "first_page_url": "http://aero.test/api/products?page=1",
    "from": 1,
    "last_page": 16,
    "last_page_url": "http://aero.test/api/products?page=16",
    "next_page_url": "http://aero.test/api/products?page=2",
    "path": "http://aero.test/api/products",
    "per_page": 2,
    "prev_page_url": null,
    "to": 2,
    "total": 32
}
```

[Back to contents](../../README.md#table-of-contents)
