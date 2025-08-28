# Customer Index

## Attributes:

See [View Customer](VIEW.md)

## Remarks

This is a paginated route (see [Pagination Conventions](../../CONVENTIONS.md#pagination-conventions))

This is also a scoped route (see [Scoped Conventions](../../CONVENTIONS.md#scoped-conventions))

## Example Response

```http request
GET /api/customers?per_page=2
```

```json lines
{
    "current_page": 1,
    "data": [
        //...
    ],
    "first_page_url": "http://l11.test/api/customers?page=1",
    "from": 1,
    "last_page": 1,
    "last_page_url": "http://l11.test/api/customers?page=1",
    "links": [
        {
            "url": null,
            "label": "&laquo; Previous",
            "active": false
        },
        {
            "url": "http://l11.test/api/customers?page=1",
            "label": "1",
            "active": true
        },
        {
            "url": null,
            "label": "Next &raquo;",
            "active": false
        }
    ],
    "next_page_url": null,
    "path": "http://l11.test/api/customers",
    "per_page": 2,
    "prev_page_url": null,
    "to": 1,
    "total": 1
}
```

See [Customer View Example Response](./VIEW.md#example-response) for the structure of the customers data


