# Store Upsell Group

## Overview

This endpoint creates a new upsell group using the provided json data

## Structure

| Name     | Type   | Description                     | Required? |
|----------|--------|---------------------------------|-----------|
| `key`    | int    | The key of the upsell group     | Yes       |
| `name`   | string | The name for the upsell group   | Yes       |

## Example Request

```http request
POST /api/upsell-groups/
```

```json lines
{
    "key": "api-test",
    "name": "API Test",
}
```

## Example Response

```json
{
    "upsellGroup": {
        "key": "api-test"
    }
}
```

[Back to contents](../../README.md#table-of-contents)
