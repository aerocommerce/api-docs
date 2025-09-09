# Store Tag

## Attributes:

### Tag

| Name        | Type    | Description                                                        | Required?   |
|-------------|---------|--------------------------------------------------------------------|-------------|
| `name`      | string  | The name of the tag                                                | Yes         |
| `slug`      | string  | The slug of the tag, if not present it is auto-generated from name | Conditional |
| `reference` | string  | The reference of the tag                                           | No          |
| `image`     | object  | The image of the tag, see [Image](#image)                          | No          |
| `has_slug`  | boolean | Whether the tag has a slug or not (defaults to `false`)            | No          |

### Image

| Name  | Type   | Description             | Required? |
|-------|--------|-------------------------|-----------|
| `src` | string | The source of the image | Yes       |

## Example Request

```http request
POST /api/tag-groups/{id}/tags
```

```json lines
{
    "name": "Medium",
    "slug": "med-ium"
}
```

## Example Response

```json
{
    "tag": {
        "id": 1
    }
}
```

