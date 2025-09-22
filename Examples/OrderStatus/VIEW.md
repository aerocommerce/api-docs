# View Order Status

## Overview

This endpoint retrieves a single order status by `id`

### Order Status

| Name    | Type   | Description                             |
|---------|--------|-----------------------------------------|
| `id`    | int    | The id of the order status              |
| `name`  | string | The name of the order status            |
| `state` | string | The state of the order status           |
| `group` | object | The [Group](#group) of the order status |

### Group

| Name   | Type   | Description                        |
|--------|--------|------------------------------------|
| `id`   | int    | The id of the order status group   |
| `name` | string | The name of the order status group |

## Example Response

```http request
GET /api/order-statuses/{id}
```

```json lines
{
    "id": 2,
    "name": "On Hold",
    "state": "on_hold",
    "group": {
        "id": 1,
        "name": "test"
    }
}
```

[Back to contents](../../README.md#table-of-contents)
