# View Attribute Group

## Overview

This endpoint retrieves a single attribute group by `id` or `name`

## Structure

### Attribute Group

| Name         | Type   | Description                                                                                      |
|--------------|--------|--------------------------------------------------------------------------------------------------|
| `name`       | string | The name of the attribute group (e.g., Size or Colour)                                           |
| `display_as` | string | The display as of the attribute group (e.g.: dropdown, color_swatches, image_swatches, swatches) |
| `reference`  | string | The reference of the attribute group                                                             |

### Tag

| Name    | Type     | Description                              |
|---------|----------|------------------------------------------|
| `name`  | string   | The name of the tag (e.g., Small or Red) |
| `group` | object   | The [Tag Group](#tag-group) of the tag   |

### Tag Group

| Name    | Type    | Description                                      |
|---------|---------|--------------------------------------------------|
| `name`  | string  | The name of the tag group (e.g., Size or Colour) |

### Image

| Name  | Type   | Description          |
|-------|--------|----------------------|
| `url` | string | The url of the image |

## Example Response

```http request
GET /api/attribute-groups/{id|name}
```

```json
{
    "id": 1,
    "name": "Size",
    "display_as": "dropdown",
    "reference": null,
    "attributes": [
        {
            "id": 1,
            "name": "Small",
            "display_name": "",
            "reference": null,
            "image": {
                "url": null
            },
            "attributes": []
        }
    ]
}
```

[Back to contents](../../README.md#table-of-contents)
