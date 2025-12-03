# Update Stock

## Overview

This endpoint dispatches a job to bulk update stock for variants (queue subject to `bulk_queue` setting)

## Structure

| Name             | Type   | Description                                                           | Required? |
|------------------|--------|-----------------------------------------------------------------------|-----------|
| `*.sku`          | string | The SKU of the variant                                                | Yes       |
| `*.stock_level`  | int    | The new stock_level of the variant                                    | Yes       |
| `*.stock_action` | string | The stock action (e.g., set, add, remove & multiply). Defaults to set | No        |

## Example Request

```http request
PUT /api/stock
```

```json lines
[
    {
        "sku": "ABC123",
        "stock_level": 23
    },
    {
        "sku": "DEF456",
        "stock_level": 3,
        "stock_action": "add"
    },
    {
        "sku": "GHI789",
        "stock_level": 1,
        "stock_action": "remove"
    },
    {
        "sku": "JKL101",
        "stock_level": 2,
        "stock_action": "multiply"
    }
]
```

## Example Response

```json
[]
```

[Back to contents](../../README.md#table-of-contents)
