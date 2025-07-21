# Order Index

## Attributes:

See [View Order](VIEW.md)

## Remarks

This is a paginated route (see [Pagination Conventions](../../CONVENTIONS.md#pagination-conventions))

In addition to the standard parameters accepted for a paginated route, this route also accepts:

| Parameter        | Description                     | Example                                 |
|------------------|---------------------------------|-----------------------------------------|
| `min_updated_at` | The min updated at for an order | ?min_updated_at=2023-08-30%2010:35:05   |
| `max_updated_at` | The max updated at for an order | ?max_updated_at=2023-08-30%2010:35:05   |
| `min_ordered_at` | The min ordered at for an order | ?min_ordered_at=2023-08-30%2010:35:05   |
| `max_ordered_at` | The max ordered at for an order | ?max_ordered_at=2023-08-30%2010:35:05   |

see [Date Conventions](../../CONVENTIONS.md#date-conventions) for more info on acceptable values for these parameters

This is also a scoped route (see [Scoped Conventions](../../CONVENTIONS.md#scoped-conventions))

This route also has some specific scopes:

| Name      | Description                                                | Example        |
|-----------|------------------------------------------------------------|----------------|
| `visible` | Only return visible orders (those which have been ordered) | ?scope=visible |

## Example Response

```http request
GET /api/orders?per_page=2&min_ordered_at=2023-08-30%2010:36:23
```

```json lines
{
    "current_page": 1,
    "data": [
      //...
    ],
    "first_page_url": "http:\/\/seg.test\/api\/orders?page=1",
    "from": 1,
    "last_page": 3,
    "last_page_url": "http:\/\/seg.test\/api\/orders?page=3",
    "next_page_url": "http:\/\/seg.test\/api\/orders?page=2",
    "path": "http:\/\/seg.test\/api\/orders",
    "per_page": 2,
    "prev_page_url": null,
    "to": 2,
    "total": 5
}
```

See [Order View Example Response](./VIEW.md#example-response) for the structure of the orders data


