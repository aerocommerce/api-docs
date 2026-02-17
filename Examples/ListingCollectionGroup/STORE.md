# Store Listing Collection Group

## Overview

This endpoint creates a new listing collection group using the provided json data

## Structure

### Listing Collection Group

| Name       | Type   | Description                               | Required? |
|------------|--------|-------------------------------------------|-----------|
| `key`      | string | The key of the listing collection group   | Yes       |
| `name`     | string | The name for the listing collection group | Yes       |
| `listings` | array  | An array of [Listing](#listing) objects   | No        |

### Listing

| Name         | Type   | Description                               | Required?          |
|--------------|--------|-------------------------------------------|--------------------|
| `id`         | int    | The id of the listing                     | Conditional `*`    |
| `variant_id` | int    | The id of the variant (of the listing)    | Conditional `*`    |
| `sku`        | string | The SKU of the variant (of the listing)   | Conditional `*`    |
| `product_id` | int    | The id of the product (of the listing)    | Conditional `*`    |
| `model`      | string | The model of the product (of the listing) | Conditional `*`    |

`*` At least one must be present, resolved in the order they are listed top-down

## Example Request

```http request
POST /api/listing-collection-groups/
```

```json lines
{
    "key": "api",
    "name": "API Test",
    "listings": [
        {
          "id": 1
        }
    ]
}
```

## Example Response

```json
{
    "listingCollectionGroup": {
        "key": "api"
    }
}
```

[Back to contents](../../README.md#table-of-contents)
