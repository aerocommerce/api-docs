# Customer Index

## Overview

This endpoint retrieves a paginated list of all customers

## Structure

See [View Customer](VIEW.md) for the structure of the customer payloads inside the `data` array

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
    "first_page_url": "http://aero.test/api/customers?page=1",
    "from": 1,
    "last_page": 1,
    "last_page_url": "http://aero.test/api/customers?page=1",
    "next_page_url": null,
    "path": "http://aero.test/api/customers",
    "per_page": 2,
    "prev_page_url": null,
    "to": 1,
    "total": 1
}
```

[Back to contents](../../README.md#table-of-contents)
