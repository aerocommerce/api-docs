# Payment Method Index

## Attributes:

See [View Payment Method](VIEW.md)

## Remarks

This is a paginated route (see [Pagination Conventions](../../CONVENTIONS.md#pagination-conventions))

In addition to the standard parameters accepted for a paginated route, this route also accepts:

| Parameter        | Description                             | Example                                 |
|------------------|-----------------------------------------|-----------------------------------------|
| `min_updated_at` | The min updated at for a payment method | ?min_updated_at=2023-08-30%2010:35:05   |
| `max_updated_at` | The max updated at for a payment method | ?max_updated_at=2023-08-30%2010:35:05   |

see [Date Conventions](../../CONVENTIONS.md#date-conventions) for more info on acceptable values for these parameters

## Example Response

```http request
GET /api/payment-methods?per_page=2
```

```json lines
{
    "current_page": 1,
    "data": [
        {
            "id": 1,
            "name": "Cash",
            "driver": "cash",
            "available": true
        },
        {
            "id": 2,
            "name": "Gift Voucher",
            "driver": "gift_voucher",
            "available": false
        }
    ],
    "first_page_url": "http://l9.test/api/payment-methods?page=1",
    "from": 1,
    "last_page": 1,
    "last_page_url": "http://l9.test/api/payment-methods?page=1",
    "links": [
        {
            "url": null,
            "label": "&laquo; Previous",
            "active": false
        },
        {
            "url": "http://l9.test/api/payment-methods?page=1",
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
    "path": "http://l9.test/api/payment-methods",
    "per_page": 2,
    "prev_page_url": null,
    "to": 2,
    "total": 2
}
```
