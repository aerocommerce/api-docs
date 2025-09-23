# Store Flag

## Overview

This endpoint creates a new flag using the provided json data

## Structure

| Name    | Type    | Description                             | Required? |
|---------|---------|-----------------------------------------|-----------|
| `id`    | int     | The id for the flag                     | No        |
| `name`  | string  | The name of the flag                    | Yes       |
| `color` | hexcode | The color of the flag (format ##RRGGBB) | Yes       |

## Example Request

```http request
POST /api/flags/
```

```json lines
{
    "name": "API Flag",
    "color": "#000000",
}
```

## Example Response

```json
{
    "flag": {
        "id": 1
    }
}
```

[Back to contents](../../README.md#table-of-contents)
