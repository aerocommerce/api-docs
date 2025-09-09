# View Attribute Group

## Attributes:

### Attribute Group

| Name         | Type   | Description                                                                                     |
|--------------|--------|-------------------------------------------------------------------------------------------------|
| `name`       | string | The name of the attribute group                                                                 |
| `display_as` | string | The display as of the attribute group, e.g.: dropdown, color_swatches, image_swatches, swatches |
| `reference`  | string | The reference of the attribute group                                                            |

### Tag

| Name    | Type     | Description                                |
|---------|----------|--------------------------------------------|
| `name`  | string   | The name of the tag                        |
| `group` | object   | The tag group, see [Tag Group](#tag-group) |

### Tag Group

| Name    | Type    | Description               |
|---------|---------|---------------------------|
| `name`  | string  | The name of the tag group |

### Image

| Name  | Type   | Description             |
|-------|--------|-------------------------|
| `url` | string | The source of the image |

## Example Response

```http request
GET /api/attribute-groups/{id}
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
