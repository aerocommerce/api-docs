# Attribute Group Index

## Overview

This endpoint retrieves a paginated list of all attribute groups

## Structure

See [View Attribute Group](VIEW.md) for the structure of the attribute group payloads inside the `data` array

## Example Response

```http request
GET /api/attribute-groups?per_page=2
```

```json lines
{
    "current_page": 1,
    "data": [
      //...
    ],
    "first_page_url": "http://aero.test/api/attribute-groups?page=1",
    "from": 1,
    "last_page": 3,
    "last_page_url": "http://aero.test/api/attribute-groups?page=3",
    "next_page_url": "http://aero.test/api/attribute-groups?page=2",
    "path": "http://aero.test/api/attribute-groups",
    "per_page": 2,
    "prev_page_url": null,
    "to": 2,
    "total": 5
}
```

[Back to contents](../../README.md#table-of-contents)
