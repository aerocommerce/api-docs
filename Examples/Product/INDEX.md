# Product Index

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

| Name      | Description                  | Example        |
|-----------|------------------------------|----------------|
| `visible` | Only return visible products | ?scope=visible |
| `active`  | Only return active products  | ?scope=active  |

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
    "first_page_url": "http:\/\/seg.test\/api\/products?page=1",
    "from": 1,
    "last_page": 3,
    "last_page_url": "http:\/\/seg.test\/api\/products?page=3",
    "next_page_url": "http:\/\/seg.test\/api\/products?page=2",
    "path": "http:\/\/seg.test\/api\/products",
    "per_page": 2,
    "prev_page_url": null,
    "to": 2,
    "total": 5
}
```

See [Product View Example Response](./VIEW.md#example-response) for the structure of the products data


