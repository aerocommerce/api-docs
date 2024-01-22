# Order Status Index

## Attributes:

See [View Order Status](VIEW.md)

## Remarks

This is a paginated route (see [Pagination Conventions](../../CONVENTIONS.md#pagination-conventions))

In addition to the standard parameters accepted for a paginated route, this route also accepts:

| Parameter        | Description                            | Example                                 |
|------------------|----------------------------------------|-----------------------------------------|
| `min_updated_at` | The min updated at for an order status | ?min_updated_at=2023-08-30%2010:35:05   |
| `max_updated_at` | The max updated at for an order status | ?max_updated_at=2023-08-30%2010:35:05   |

see [Date Conventions](../../CONVENTIONS.md#date-conventions) for more info on acceptable values for these parameters

## Example Response

```http request
GET /api/order-statuses?per_page=2
```

```json lines
{
    "current_page": 1,
    "data": [
        {
            "id": 1,
            "name": "Cancelled",
            "state": "canceled",
            "group": null
        },
        {
            "id": 2,
            "name": "On Hold",
            "state": "on_hold",
            "group": {
                "id": 1,
                "name": "test"
            }
        }
    ],
    "first_page_url": "http://l9.test/api/order-statuses?page=1",
    "from": 1,
    "last_page": 5,
    "last_page_url": "http://l9.test/api/order-statuses?page=5",
    "links": [
        {
            "url": null,
            "label": "&laquo; Previous",
            "active": false
        },
        {
            "url": "http://l9.test/api/order-statuses?page=1",
            "label": "1",
            "active": true
        },
        {
            "url": "http://l9.test/api/order-statuses?page=2",
            "label": "2",
            "active": false
        },
        {
            "url": "http://l9.test/api/order-statuses?page=3",
            "label": "3",
            "active": false
        },
        {
            "url": "http://l9.test/api/order-statuses?page=4",
            "label": "4",
            "active": false
        },
        {
            "url": "http://l9.test/api/order-statuses?page=5",
            "label": "5",
            "active": false
        },
        {
            "url": "http://l9.test/api/order-statuses?page=2",
            "label": "Next &raquo;",
            "active": false
        }
    ],
    "next_page_url": "http://l9.test/api/order-statuses?page=2",
    "path": "http://l9.test/api/order-statuses",
    "per_page": 2,
    "prev_page_url": null,
    "to": 2,
    "total": 9
}
```
