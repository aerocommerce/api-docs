# View Upsell Group

## Overview

This endpoint retrieves a single upsell group by `key`

## Structure

| Name     | Type   | Description                         |
|----------|--------|-------------------------------------|
| `key`    | string | The key of the upsell group         |
| `name`   | string | The name for the upsell group       |

## Example Response

```http request
GET /api/upsell-groups/{key}
```

```json
{
    "key": "api-test",
    "name": "API Test"
}
```

[Back to contents](../../README.md#table-of-contents)
