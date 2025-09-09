# Update Attribute Group

## Attributes:

### Attribute Group

| Name         | Type    | Description                                                                                     | Required? |
|--------------|---------|-------------------------------------------------------------------------------------------------|-----------|
| `name`       | string  | The name of the attribute group                                                                 | No        |
| `display_as` | string  | The display as of the attribute group, e.g.: dropdown, color_swatches, image_swatches, swatches | No        |
| `reference`  | string  | The reference of the attribute group                                                            | No        |

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

