# Store Attribute Group

## Attributes:

### Attribute Group

| Name         | Type    | Description                                                                                     | Required? |
|--------------|---------|-------------------------------------------------------------------------------------------------|-----------|
| `name`       | string  | The name of the attribute group                                                                 | Yes       |
| `display_as` | string  | The display as of the attribute group, e.g.: dropdown, color_swatches, image_swatches, swatches | No        |
| `reference`  | string  | The reference of the attribute group                                                            | No        |
| `attributes` | array   | The attributes of the attribute group, see [Attribute](#attribute)                              | No        |

### Attribute

| Name           | Type   | Description                                     | Required? |
|----------------|--------|-------------------------------------------------|-----------|
| `name`         | string | The name of the attribute                       | Yes       |
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

