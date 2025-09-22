# Price List Index

## Overview

This endpoint retrieves a paginated list of all price lists

## Structure

See [View Price List](VIEW.md) for the structure of the price list payloads inside the `data` array

## Example Response

```http request
GET /api/price-lists?per_page=2
```

```json lines
{
    "current_page": 1,
    "data": [
      //...
    ],
    "first_page_url": "http://aero.test/api/price-lists?page=1",
    "from": 1,
    "last_page": 3,
    "last_page_url": "http://aero.test/api/price-lists?page=3",
    "next_page_url": "http://aero.test/api/price-lists?page=2",
    "path": "http://aero.test/api/price-lists",
    "per_page": 2,
    "prev_page_url": null,
    "to": 2,
    "total": 5
}
```

[Back to contents](../../README.md#table-of-contents)
