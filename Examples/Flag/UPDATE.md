# Update Flag

## Overview

This endpoint updates an existing flag by its `id` or `name`. Only the fields provided in the request will be updated; unspecified fields remain unchanged.

## Structure

| Name          | Type    | Description                             | Required? |
|---------------|---------|-----------------------------------------|-----------|
| `name`        | string  | The name of the flag                    | No        |
| `color`       | hexcode | The color of the flag (format ##RRGGBB) | No        |

## Example Request

```http request
PUT /api/flags/{id|name}
```

```json lines
{
    "name": "API Flag Updated",
    "color": "#A1B2C3",
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
