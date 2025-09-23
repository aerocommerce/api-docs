# Store Attribute Group

## Overview

This endpoint creates a new attribute group using the provided json data

## Structure

### Attribute Group

| Name              | Type   | Description                                                                                      | Required? |
|-------------------|--------|--------------------------------------------------------------------------------------------------|-----------|
| `id`              | int    | The id for the attribute group                                                                   | No        |
| `name`            | string | The name of the attribute group (e.g., Size or Colour)                                           | Yes       |
| `display_as`      | string | The display as of the attribute group (e.g.: dropdown, color_swatches, image_swatches, swatches) | No        |
| `reference`       | string | The reference of the attribute group                                                             | No        |
| `attributes`      | array  | The attributes of the attribute group, see [Attribute](#attribute)                               | No        |

### Attribute

| Name           | Type   | Description                                    | Required? |
|----------------|--------|------------------------------------------------|-----------|
| `id`           | int    | The id for the attribute                       | No        |
| `name`         | string | The name of the attribute (e.g., Small or Red) | Yes       |
| `display_name` | string | The display name of the attribute              | No        |
| `reference`    | string | The reference of the attribute                 | No        |
| `image`        | object | The [Image](#image) of the attribute           | No        |
| `tags`         | array  | An array of [Tag](#tag) objects                | No        |

### Image

| Name  | Type   | Description                 | Required? |
|-------|--------|-----------------------------|-----------|
| `src` | string | The source url of the image | Yes       |

### Tag

| Name       | Type   | Description                                | Required? |
|------------|--------|--------------------------------------------|-----------|
| `name`     | string | The name of the tag (e.g., Small or Red)   | Yes       |
| `group`    | object | The tag group, see [Tag Group](#tag-group) | Yes       |

### Tag Group

| Name      | Type   | Description                                      | Required? |
|-----------|--------|--------------------------------------------------|-----------|
| `name`    | string | The name of the tag group (e.g., Size or Colour) | Yes       |

## Example Request

```http request
POST /api/attribute-groups/
```

```json lines
{
    "name": "Colour",
    "attributes": [
        {
            "name": "Blue",
            "reference": "blue"
        },
        {
            "name": "red"
        }
    ]
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
