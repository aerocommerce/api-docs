# Collection Index

## Overview

This endpoint retrieves a paginated list of all collections

## Structure

See [View Collection](VIEW.md) for the structure of the collection payloads inside the `data` array

## Example Response

```http request
GET /api/collections?per_page=2
```

```json lines
{
    "current_page": 1,
    "data": [
      //...
    ],
    "first_page_url": "http://aero.test/api/collections?page=1",
    "from": 1,
    "last_page": 3,
    "last_page_url": "http://aero.test/api/collections?page=3",
    "next_page_url": "http://aero.test/api/collections?page=2",
    "path": "http://aero.test/api/collections",
    "per_page": 2,
    "prev_page_url": null,
    "to": 2,
    "total": 5
}
```

[Back to contents](../../README.md#table-of-contents)
