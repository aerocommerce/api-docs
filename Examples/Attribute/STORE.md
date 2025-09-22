# Store Attribute

## Overview

This endpoint creates a new attribute using the provided json data

## Structure

### Attribute

| Name           | Type   | Description                                    | Required? |
|----------------|--------|------------------------------------------------|-----------|
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
POST /api/attribute-groups/{id|name}/attributes
```

```json lines
{
    "name": "Medium",
    "display_name": "Medium"
}
```

## Example Response

```json
{
    "attribute": {
        "id": 1
    }
}
```

[Back to contents](../../README.md#table-of-contents)
