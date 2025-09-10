# Update Tag

## Attributes:

### Tag

| Name        | Type    | Description                               | Required? |
|-------------|---------|-------------------------------------------|-----------|
| `name`      | string  | The name of the tag                       | No        |
| `slug`      | string  | The slug of the tag                       | No        |
| `reference` | string  | The reference of the tag                  | No        |
| `image`     | object  | The image of the tag, see [Image](#image) | No        |
| `has_slug`  | boolean | Whether the tag has a slug or not         | No        |

### Image

| Name  | Type   | Description             | Required? |
|-------|--------|-------------------------|-----------|
| `src` | string | The source of the image | Yes       |

## Example Request

```http request
PUT /api/tag-groups/{tagGroupId}/tags/{tagId}
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

