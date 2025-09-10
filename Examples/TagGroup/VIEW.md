# View Tag Group

## Attributes:

### Tag Group

| Name              | Type    | Description                                                                  |
|-------------------|---------|------------------------------------------------------------------------------|
| `name`            | string  | The name of the tag group                                                    |
| `reference`       | string  | The reference of the tag group                                               |
| `show_in_filters` | boolean | Whether the tag group shows in filters on listings page (defaults to `true`) |
| `tags`            | array   | The tags of the tag group, see [Tag](#tag)                                   |

### Tag

| Name       | Type   | Description                                |
|------------|--------|--------------------------------------------|
| `name`     | string | The name of the tag                        |
| `group`    | object | The tag group, see [Tag Group](#tag-group) |

### Tag Group

| Name        | Type    | Description                                                        |
|-------------|---------|--------------------------------------------------------------------|
| `name`      | string  | The name of the tag                                                |
| `slug`      | string  | The slug of the tag, if not present it is auto-generated from name |
| `reference` | string  | The reference of the tag                                           |
| `image`     | object  | The image of the tag, see [Image](#image)                          |
| `has_slug`  | boolean | Whether the tag has a slug or not (defaults to `false`)            |

### Image

| Name  | Type   | Description          |
|-------|--------|----------------------|
| `url` | string | The url of the image |

## Example Response

```http request
GET /api/tag-groups/{id}
```

```json
{
    "id": 1,
    "name": "Size",
    "reference": null,
    "show_in_filters": true,
    "tags": [
        {
            "id": 1,
            "name": "Small",
            "reference": null,
            "slug": "small",
            "image": {
                "url": null
            },
            "has_slug": true
        }
    ]
}
```

[Back to contents](../../README.md#table-of-contents)
