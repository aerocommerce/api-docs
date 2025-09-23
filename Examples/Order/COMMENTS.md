# Order Comments

## Overview

This endpoint allows a comment to be added to an order (by `id` or `reference`)

## Structure

| Name              | Type        | Description                                               | Required? |
|-------------------|-------------|-----------------------------------------------------------|-----------|
| `admin`           | int\|string | The id or email of the admin                              | No        |
| `message`         | string      | The comment message                                       | Yes       |
| `customer_facing` | boolean     | Whether the comment is customer facing (default: `false`) | No        |
| `created_at`      | timestamp   | The date the comment was created (defaults to now)        | No        |

**NOTE:** If no `admin` is supplied then the API Token name will be displayed for the comment in the admin

## Example Request

```http request
POST /api/orders/{id|reference}/comments
```

```json lines
{
    "admin": "admin@example.com",
    "message": "This is an API message",
    "customer_facing": true,
    "created_at": "2025-09-01 09:29:41"
}
```

## Example Response

```json lines
{
    "order": {
        "id": 1
    },
    "comment": {
        "id": 1
    }
}
```
