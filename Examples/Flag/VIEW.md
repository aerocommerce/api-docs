# View Flag

## Overview

This endpoint retrieves a single flag by `id` or `name`

## Structure

| Name         | Type      | Description                              |
|--------------|-----------|------------------------------------------|
| `id`         | int       | The id of the flag                       |
| `name`       | string    | The **unique** name for the flag         |
| `color`      | hexcode   | The colour of the flag (format ##RRGGBB) |
| `created_at` | timestamp | The date the flag was created            |

## Example Response

```http request
GET /api/flags/{id|name}
```

```json
{
    "id": 1,
    "name": "Flag",
    "color": "#7f3434",
    "created_at": "2025-06-30T08:14:27.000000Z"
}
```

[Back to contents](../../README.md#table-of-contents)
