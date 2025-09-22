# Update Tag

## Overview

This endpoint updates an existing tag by its `id` or `name`. Only the fields provided in the request will be updated; unspecified fields remain unchanged.

## Structure

### Tag

| Name        | Type    | Description                       | Required? |
|-------------|---------|-----------------------------------|-----------|
| `name`      | string  | The name of the tag               | No        |
| `slug`      | string  | The slug of the tag               | No        |
| `reference` | string  | The reference of the tag          | No        |
| `image`     | object  | The [Image](#image) of the tag    | No        |
| `has_slug`  | boolean | Whether the tag has a slug or not | No        |

### Image

| Name  | Type   | Description                 | Required? |
|-------|--------|-----------------------------|-----------|
| `src` | string | The source url of the image | Yes       |

## Example Request

```http request
PUT /api/tag-groups/{id|name}/tags/{id|name}
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

[Back to contents](../../README.md#table-of-contents)
