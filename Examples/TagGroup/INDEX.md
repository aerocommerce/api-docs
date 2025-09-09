# Tag Group Index

## Attributes:

See [View Tag Group](VIEW.md)

## Remarks

This is a paginated route (see [Pagination Conventions](../../CONVENTIONS.md#pagination-conventions))

In addition to the standard parameters accepted for a paginated route, this route also accepts:

| Parameter        | Description                        | Example                                 |
|------------------|------------------------------------|-----------------------------------------|
| `min_updated_at` | The min updated at for a tag group | ?min_updated_at=2023-08-30%2010:35:05   |
| `max_updated_at` | The max updated at for a tag group | ?max_updated_at=2023-08-30%2010:35:05   |

see [Date Conventions](../../CONVENTIONS.md#date-conventions) for more info on acceptable values for these parameters

This is also a scoped route (see [Scoped Conventions](../../CONVENTIONS.md#scoped-conventions))

## Example Response

```http request
GET /api/tag-groups?per_page=2
```

```json lines
{
    "current_page": 1,
    "data": [
      //...
    ],
    "first_page_url": "http:\/\/seg.test\/api\/tag-groups?page=1",
    "from": 1,
    "last_page": 3,
    "last_page_url": "http:\/\/seg.test\/api\/tag-groups?page=3",
    "next_page_url": "http:\/\/seg.test\/api\/tag-groups?page=2",
    "path": "http:\/\/seg.test\/api\/orders",
    "per_page": 2,
    "prev_page_url": null,
    "to": 2,
    "total": 5
}
```

See [Tag Group View Example Response](./VIEW.md#example-response) for the structure of the tag-groups data


