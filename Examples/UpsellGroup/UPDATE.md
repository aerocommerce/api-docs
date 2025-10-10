# Update Upsell Group

## Overview

This endpoint updates an existing upsell group by its `key`. Only the fields provided in the request will be updated; unspecified fields remain unchanged.

## Structure

| Name     | Type   | Description                     | Required? |
|----------|--------|---------------------------------|-----------|
| `name`   | string | The name for the upsell group   | Yes       |

## Example Request

```http request
PUT /api/upsell-groups/{key}
```

```json lines
{
    "name": "API Test Updated",
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
