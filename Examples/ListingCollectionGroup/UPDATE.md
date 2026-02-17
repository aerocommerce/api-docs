# Update Listing Collection Group

## Overview

This endpoint updates an existing listing collection group by its `key`. Only the fields provided in the request will be updated; unspecified fields remain unchanged.

## Structure

### Listing Collection Group

| Name       | Type   | Description                               | Required? |
|------------|--------|-------------------------------------------|-----------|
| `name`     | string | The name for the listing collection group | No        |
| `listings` | array  | An array of [Listing](#listing) objects   | No        |

### Listing

| Name         | Type   | Description                               | Required?         |
|--------------|--------|-------------------------------------------|-------------------|
| `id`         | int    | The id of the listing                     | Conditional `*`   |
| `variant_id` | int    | The id of the variant (of the listing)    | Conditional `*`   |
| `sku`        | string | The SKU of the variant (of the listing)   | Conditional `*`   |
| `product_id` | int    | The id of the product (of the listing)    | Conditional `*`   |
| `model`      | string | The model of the product (of the listing) | Conditional `*`   |

`*` At least one must be present, resolved in the order they are listed top-down

## Example Request

```http request
PUT /api/listing-collection-groups/{key}
```

```json lines
{
    "name": "API Test 2",
    "listings": [
        {
            "id": 2
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
