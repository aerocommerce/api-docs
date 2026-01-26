# Update Attribute

## Overview

This endpoint updates an existing attribute in a specific group by its `id` or `name`. Only the fields provided in the request will be updated; unspecified fields remain unchanged.

## Structure

### Attribute

| Name           | Type   | Description                                    | Required? |
|----------------|--------|------------------------------------------------|-----------|
| `name`         | string | The name of the attribute (e.g., Small or Red) | No        |
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
PUT /api/attribute-groups/{id|name}/attributes/{id|name}
```

```json lines
{
    "name": "Updated Small",
    "display_name": "Updated Small"
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
