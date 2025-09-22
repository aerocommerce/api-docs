# Store Tag

## Overview

This endpoint creates a new tag using the provided json data

## Structure

### Tag

| Name        | Type    | Description                                                                       | Required?   |
|-------------|---------|-----------------------------------------------------------------------------------|-------------|
| `name`      | string  | The name of the tag                                                               | Yes         |
| `slug`      | string  | The slug of the tag, if not present it is auto-generated from name                | Conditional |
| `reference` | string  | The reference of the tag                                                          | No          |
| `image`     | object  | The [Image](#image) of the tag                                                    | No          |
| `has_slug`  | boolean | Whether the tag has a slug or not (defaults to `false` unless `slug` is provided) | No          |

### Image

| Name  | Type   | Description                 | Required? |
|-------|--------|-----------------------------|-----------|
| `src` | string | The source url of the image | Yes       |

## Example Request

```http request
POST /api/tag-groups/{id|name}/tags
```

```json lines
{
    "name": "Medium",
    "slug": "med-ium"
}
```

### Response

```json
{
    "tag": {
        "id": 1
    }
}
```

[Back to contents](../../README.md#table-of-contents)
