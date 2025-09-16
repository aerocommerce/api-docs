# Payment Method Index

## Overview

This endpoint retrieves a paginated list of all payment methods

## Structure

See [View Payment Method](VIEW.md) for the structure of the payment method payloads inside the `data` array

## Example Response

```http request
GET /api/payment-methods?per_page=2
```

```json lines
{
    "current_page": 1,
    "data": [
      //
    ],
    "first_page_url": "http://aero.test/api/payment-methods?page=1",
    "from": 1,
    "last_page": 1,
    "last_page_url": "http://aero.test/api/payment-methods?page=1",
    "next_page_url": null,
    "path": "http://aero.test/api/payment-methods",
    "per_page": 2,
    "prev_page_url": null,
    "to": 2,
    "total": 2
}
```

[Back to contents](../../README.md#table-of-contents)
