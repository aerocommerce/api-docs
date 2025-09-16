# Order Flags

## Overview

These endpoints allow flags (by `id` or `name`) to be added to orders (by `id` or `reference`)

## Attach Flag

### Example Request

```http request
POST /api/orders/{id|reference}/flags/{id|name}
```

### Example Response

```json lines
{
    "order": {
        "id": 1
    },
    "flag": {
        "id": 1
    }
}
```

## Detach Flag

### Example Request

```http request
DELETE /api/orders/{id|reference}/flags/{id|name}
```

### Example Response

```http request
204 No Content
```

[Back to contents](../../README.md#table-of-contents)
