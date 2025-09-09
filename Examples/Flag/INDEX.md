# Flag Index

## Attributes:

See [View Flag](VIEW.md)

## Remarks

This is a paginated route (see [Pagination Conventions](../../CONVENTIONS.md#pagination-conventions))

In addition to the standard parameters accepted for a paginated route, this route also accepts:

| Parameter        | Description                     | Example                                 |
|------------------|---------------------------------|-----------------------------------------|
| `min_updated_at` | The min updated at for a flag   | ?min_updated_at=2023-08-30%2010:35:05   |
| `max_updated_at` | The max updated at for a flag   | ?max_updated_at=2023-08-30%2010:35:05   |

see [Date Conventions](../../CONVENTIONS.md#date-conventions) for more info on acceptable values for these parameters

This is also a scoped route (see [Scoped Conventions](../../CONVENTIONS.md#scoped-conventions))

## Example Response

```http request
GET /api/flags?per_page=2
```

```json lines
{
    "current_page": 1,
    "data": [
      //...
    ],
    "first_page_url": "http:\/\/seg.test\/api\/flags?page=1",
    "from": 1,
    "last_page": 3,
    "last_page_url": "http:\/\/seg.test\/api\/flags?page=3",
    "next_page_url": "http:\/\/seg.test\/api\/flags?page=2",
    "path": "http:\/\/seg.test\/api\/orders",
    "per_page": 2,
    "prev_page_url": null,
    "to": 2,
    "total": 5
}
```

See [Flag View Example Response](./VIEW.md#example-response) for the structure of the flags data


