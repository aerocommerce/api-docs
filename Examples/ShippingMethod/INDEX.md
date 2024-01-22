# Payment Method Index

## Attributes:

See [View Shipping Method](VIEW.md)

## Remarks

This is a paginated route (see [Pagination Conventions](../../CONVENTIONS.md#pagination-conventions))

In addition to the standard parameters accepted for a paginated route, this route also accepts:

| Parameter        | Description                                | Example                                 |
|------------------|--------------------------------------------|-----------------------------------------|
| `min_updated_at` | The min updated at for a shipping method   | ?min_updated_at=2023-08-30%2010:35:05   |
| `max_updated_at` | The max updated at for a shipping method   | ?max_updated_at=2023-08-30%2010:35:05   |

see [Date Conventions](../../CONVENTIONS.md#date-conventions) for more info on acceptable values for these parameters

## Example Response

```http request
GET /api/shipping-methods?per_page=2
```

```json lines
{
    "current_page": 1,
    "data": [
        {
            "id": 2,
            "name": "123",
            "available": true,
            "rates": [
                {
                    "id": 2,
                    "currency": "GBP",
                    "min_price": 1000,
                    "max_price": null,
                    "min_weight": 0,
                    "max_weight": null,
                    "min_volume": 0,
                    "max_volume": null,
                    "price": 12300
                }
            ]
        },
        {
            "id": 3,
            "name": "123123",
            "available": true,
            "rates": [
                {
                    "id": 3,
                    "currency": "GBP",
                    "min_price": 0,
                    "max_price": null,
                    "min_weight": 0,
                    "max_weight": null,
                    "min_volume": 0,
                    "max_volume": null,
                    "price": 12300
                }
            ]
        }
    ],
    "first_page_url": "http://l9.test/api/shipping-methods?page=1",
    "from": 1,
    "last_page": 2,
    "last_page_url": "http://l9.test/api/shipping-methods?page=2",
    "links": [
        {
            "url": null,
            "label": "&laquo; Previous",
            "active": false
        },
        {
            "url": "http://l9.test/api/shipping-methods?page=1",
            "label": "1",
            "active": true
        },
        {
            "url": "http://l9.test/api/shipping-methods?page=2",
            "label": "2",
            "active": false
        },
        {
            "url": "http://l9.test/api/shipping-methods?page=2",
            "label": "Next &raquo;",
            "active": false
        }
    ],
    "next_page_url": "http://l9.test/api/shipping-methods?page=2",
    "path": "http://l9.test/api/shipping-methods",
    "per_page": 2,
    "prev_page_url": null,
    "to": 2,
    "total": 4
}
```
