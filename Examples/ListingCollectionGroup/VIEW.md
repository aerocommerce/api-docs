# View Listing Collection Group

## Overview

This endpoint retrieves a single listing collection group by `key`

## Structure

### Listing Collection Group

| Name       | Type   | Description                               |
|------------|--------|-------------------------------------------|
| `key`      | string | The key of the listing collection group   |
| `name`     | string | The name for the listing collection group |
| `listings` | array  | An array of [Listing](#listing) objects   |

### Listing

| Name         | Type   | Description                                  |
|--------------|--------|----------------------------------------------|
| `id`         | int    | The id of the listing                        |
| `product_id` | int    | The id of the product linked to the listing  |
| `sort`       | int    | The sort of the listing within the group     |

## Example Response

```http request
GET /api/listing-collection-groups/{key}
```

```json
{
    "key": "api",
    "name": "API Test",
    "listings": [
        {
            "id": 1,
            "product_id": 1
        }
    ]
}
```

[Back to contents](../../README.md#table-of-contents)
