# View Tag Group

## Overview

This endpoint retrieves a single tag group by `id` or `model`

## Structure

### Tag Group

| Name              | Type    | Description                                             |
|-------------------|---------|---------------------------------------------------------|
| `name`            | string  | The name of the tag group (e.g., Size or Colour)        |
| `reference`       | string  | The reference of the tag group                          |
| `show_in_filters` | boolean | Whether the tag group shows in filters on listings page |
| `tags`            | array   | An array of [Tag](#tag) objects                         |

### Tag


| Name        | Type    | Description                                                        |
|-------------|---------|--------------------------------------------------------------------|
| `name`      | string  | The name of the tag (e.g., Small or Red)                           |
| `slug`      | string  | The slug of the tag, if not present it is auto-generated from name |
| `reference` | string  | The reference of the tag                                           |
| `image`     | object  | The image of the tag, see [Image](#image)                          |
| `has_slug`  | boolean | Whether the tag has a slug or not                                  |

### Image

| Name  | Type   | Description          |
|-------|--------|----------------------|
| `url` | string | The url of the image |

## Example Request

```http request
GET /api/tag-groups/{id|name}
```

## Example Response

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
