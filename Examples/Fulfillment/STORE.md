# Store Fulfillment

## Overview

This endpoint creates a new fulfillment for an order (by `id` or `reference`) using the provided json data

## Structure

### Fulfillment

| Name            | Type         | Description                                                                             | Required? |
|-----------------|--------------|-----------------------------------------------------------------------------------------|-----------|
| `id`            | int          | The id for the fulfillment                                                              | No        |
| `reference`     | string       | The reference for the fulfillment                                                       | No        |
| `state`         | string       | The state of the fulfillment (defaults to method's default if not passed)               | No        |
| `method`        | int\| string | The fulfillment method's id, name or driver (defaults to orders' default if not passed) | No        |
| `tracking_code` | string       | The tracking code for the fulfillment                                                   | No        |
| `tracking_url`  | url          | The tracking url for the fulfillment                                                    | No        |
| `weight`        | float        | The total weight of the fulfillment (calculated from items if not passed)               | No        |
| `weight_unit`   | string       | The weight unit (defaults to store's default if not provided)                           | No        |
| `volume`        | float        | The total volume of the fulfillment (calculated from items if not passed)               | No        |
| `volume_unit`   | string       | The volume unit (defaults to store's default if not provided)                           | No        |
| `delivery_note` | string       | The delivery note for the fulfillment                                                   | No        |
| `notify`        | boolean      | Whether the fulfillment notifications are activated (defaults to `true`)                | No        |
| `dispatched_at` | timestamp    | The dispatched at of the fulfillment                                                    | No        |
| `items`         | array        | An array of [Item](#item) objects (if not passed every fulfillable item is fulfilled)   | No        |

**Valid fulfillment states:** `failed`, `pending`, `open`, `successful`, `canceled`, `errored`

### Item

| Name          | Type   | Description                                                            | Required?       |
|---------------|--------|------------------------------------------------------------------------|-----------------|
| `id`          | int    | The id of the order item to be fulfilled                               | Conditional `*` |
| `sku`         | string | The sku of the order item to be fulfilled                              | Conditional `*` |
| `quantity`    | int    | The quantity to be fulfilled (defaults to max possible)                | No              |
| `weight`      | float  | The weight of the item (uses order item's weight if not passed)        | No              |
| `weight_unit` | string | The weight unit (defaults to store's default if not provided)          | No              |
| `volume`      | float  | The volume of the fulfillment (uses order item's volume if not passed) | No              |
| `volume_unit` | string | The volume unit (defaults to store's default if not provided)          | No              |

`*` **Note:** One of id or sku must be provided.

## Example Request

### 1. Fulfill Specific Items

```http request
POST /api/orders/{id|reference}/fulfillments
```

```json lines
{
    "reference": "F1-API",
    "tracking_code": "Test tracking code",
    "tracking_url": "http://aero.test",
    "delivery_note": "Test delivery note",
    "items": [
        {
            "sku": "ABC-123",
            "quantity": 1,
            "weight": 10,
            "weight_unit": "oz",
            "volume": 0.5,
            "volume_unit": "m^3"
        },
        {
            "sku": "DEF-456"
        }
    ]
}
```

### 2. Fulfill All Items

```http request
POST /api/orders/{id|reference}/fulfillments
```

```json lines
{
    "reference": "F2-API",
    "tracking_code": "Test tracking code",
    "tracking_url": "http://aero.test",
    "delivery_note": "Test delivery note",
}
```

## Example Response

```json
{
    "fulfillment": {
        "id": 1
    }
}
```

[Back to contents](../../README.md#table-of-contents)
