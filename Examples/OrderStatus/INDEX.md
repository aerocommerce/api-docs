# Order Status Index

## Overview

This endpoint retrieves a paginated list of all order statuses

## Structure

See [View Order Status](VIEW.md) for the structure of the order status payloads inside the `data` array

## Example Response

```http request
GET /api/order-statuses?per_page=2
```

```json lines
{
    "current_page": 1,
    "data": [
        //
    ],
    "first_page_url": "http://aero.test/api/order-statuses?page=1",
    "from": 1,
    "last_page": 5,
    "last_page_url": "http://aero.test/api/order-statuses?page=5",
    "next_page_url": "http://aero.test/api/order-statuses?page=2",
    "path": "http://aero.test/api/order-statuses",
    "per_page": 2,
    "prev_page_url": null,
    "to": 2,
    "total": 9
}
```

[Back to contents](../../README.md#table-of-contents)
