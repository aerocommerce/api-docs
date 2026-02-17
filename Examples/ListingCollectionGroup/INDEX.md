# Listing Collection Group Index

## Overview

This endpoint retrieves a paginated list of all listing collection groups

## Structure

See [View Listing Collection Group](VIEW.md) for the structure of the listing collection group payloads inside the `data` array

## Example Response

```http request
GET /api/listing-collection-groups?per_page=2
```

```json lines
{
    "current_page": 1,
    "data": [
      //...
    ],
    "first_page_url": "http://aero.test/api/listing-collection-groups?page=1",
    "from": 1,
    "last_page": 3,
    "last_page_url": "http://aero.test/api/listing-collection-groups?page=3",
    "next_page_url": "http://aero.test/api/listing-collection-groups?page=2",
    "path": "http://aero.test/api/listing-collection-groups",
    "per_page": 2,
    "prev_page_url": null,
    "to": 2,
    "total": 5
}
```

[Back to contents](../../README.md#table-of-contents)
