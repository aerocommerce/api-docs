# Update Attribute

## Attributes:

### Attribute

| Name           | Type   | Description                                     | Required? |
|----------------|--------|-------------------------------------------------|-----------|
| `name`         | string | The name of the attribute                       | No        |
| `display_name` | string | The display name of the attribute               | No        |
| `reference`    | string | The reference of the attribute                  | No        |
| `image`        | object | The image of the attribute, see [Image](#image) | No        |
| `tags`         | array  | The tags of the attribute, see [Tag](#tag)      | No        |

### Image

| Name  | Type   | Description             | Required? |
|-------|--------|-------------------------|-----------|
| `src` | string | The source of the image | Yes       |

### Tag

| Name       | Type   | Description                                | Required? |
|------------|--------|--------------------------------------------|-----------|
| `name`     | string | The name of the tag                        | Yes       |
| `group`    | object | The tag group, see [Tag Group](#tag-group) | Yes       |

### Tag Group

| Name      | Type   | Description               | Required? |
|-----------|--------|---------------------------|-----------|
| `name`    | string | The name of the tag group | Yes       |

## Example Request

```http request
POST /api/attribute-groups/{attributeGroupId}/attributes/{attributeId}
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

