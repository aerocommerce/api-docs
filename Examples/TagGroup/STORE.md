# Store Tag Group

## Attributes:

### Tag Group

| Name              | Type    | Description                                                                  | Required? |
|-------------------|---------|------------------------------------------------------------------------------|-----------|
| `name`            | string  | The name of the tag group                                                    | Yes       |
| `reference`       | string  | The reference of the tag group                                               | No        |
| `show_in_filters` | boolean | Whether the tag group shows in filters on listings page (defaults to `true`) | No        |
| `tags`            | array   | The tags of the tag group, see [Tag](#tag)                                   | No        |

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
POST /api/tag-groups/
```

```json lines
{
    "name": "Colour",
    "show_in_filters": false,
    "tags": [
        {
            "name": "Blue",
            "slug": "blueeee",
            "reference": "blue"
        },
        {
            "name": "red",
            "has_slug": false
        }
    ]
}
```

## Example Response

```json
{
    "tagGroup": {
        "id": 1
    }
}
```

