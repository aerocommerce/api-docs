# Shipping Method Index

## Overview

This endpoint retrieves a paginated list of all shipping methods

## Structure

See [View Shipping Method](VIEW.md) for the structure of the shipping method payloads inside the `data` array

## Example Response

```http request
GET /api/shipping-methods?per_page=2
```

```json lines
{
    "current_page": 1,
    "data": [
        //
    ],
    "first_page_url": "http://aero.test/api/shipping-methods?page=1",
    "from": 1,
    "last_page": 2,
    "last_page_url": "http://aero.test/api/shipping-methods?page=2",
    "next_page_url": "http://aero.test/api/shipping-methods?page=2",
    "path": "http://aero.test/api/shipping-methods",
    "per_page": 2,
    "prev_page_url": null,
    "to": 2,
    "total": 4
}
```

[Back to contents](../../README.md#table-of-contents)
