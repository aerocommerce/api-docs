# Store Tag Group

## Overview

This endpoint creates a new tag group using the provided json data

## Structure

### Tag Group

| Name              | Type    | Description                                                                  | Required? |
|-------------------|---------|------------------------------------------------------------------------------|-----------|
| `id`              | int     | The id for the tag group                                                     | No        |
| `name`            | string  | The name of the tag group (e.g., Size or Colour)                             | Yes       |
| `reference`       | string  | The reference of the tag group                                               | No        |
| `show_in_filters` | boolean | Whether the tag group shows in filters on listings page (defaults to `true`) | No        |
| `tags`            | array   | An array of [Tag](#tag) objects                                              | No        |

### Tag

| Name        | Type    | Description                                                                                       | Required?   |
|-------------|---------|---------------------------------------------------------------------------------------------------|-------------|
| `id`        | int     | The id for the tag                                                                                | No          |
| `name`      | string  | The name of the tag (e.g., Small or Red)                                                          | Yes         |
| `slug`      | string  | The slug of the tag, if not present it is auto-generated from name (unless `has_slug` is `false`) | Conditional |
| `reference` | string  | The reference of the tag                                                                          | No          |
| `image`     | object  | The [Image](#image) of the tag                                                                    | No          |
| `has_slug`  | boolean | Whether the tag has a slug or not (defaults to `false`, unless `slug` is provided)                | No          |

### Image

| Name  | Type   | Description                 | Required? |
|-------|--------|-----------------------------|-----------|
| `src` | string | The source url of the image | Yes       |

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

[Back to contents](../../README.md#table-of-contents)
