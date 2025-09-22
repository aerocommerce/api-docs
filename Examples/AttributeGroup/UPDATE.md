# Update Attribute Group

## Overview

This endpoint updates an existing attribute group by its `id` or `name`. Only the fields provided in the request will be updated; unspecified fields remain unchanged.

## Structure

### Attribute Group

| Name         | Type    | Description                                                                                      | Required? |
|--------------|---------|--------------------------------------------------------------------------------------------------|-----------|
| `name`       | string  | The name of the attribute group (e.g., Size or Colour)                                           | No        |
| `display_as` | string  | The display as of the attribute group (e.g.: dropdown, color_swatches, image_swatches, swatches) | No        |
| `reference`  | string  | The reference of the attribute group                                                             | No        |

## Example Request

```http request
PUT /api/attribute-groups/
```

```json lines
{
    "name": "Updated Size",
    "display_as": "swatches"
}
```

## Example Response

```json
{
    "attributeGroup": {
        "id": 1
    }
}
```

[Back to contents](../../README.md#table-of-contents)
