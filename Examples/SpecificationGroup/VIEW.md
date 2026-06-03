# View Specification Group

## Overview

This endpoint retrieves a single specification group by `id`

## Structure

### Specification Group

| Name       | Type    | Description                                                 | Version   |
|------------|---------|-------------------------------------------------------------|-----------|
| `id`       | int     | The id of the specification group                           | `>=0.1.0` |
| `name`     | string  | The name for the specification group                        | `>=0.1.0` |
| `sort`     | int     | The sort for the specification group                        | `>=1.0.0` |
| `fields`   | array   | An array of [Field](#field) objects                         | `>=0.1.0` |
| `media`    | array   | An array of [Media](#media) objects                         | `>=0.3.2` |
| `settings` | object  | A [Settings](#settings) object with grouped key-value pairs | `>=1.0.0` |

### Field

| Name       | Type   | Description                                                          | Version   |
|------------|--------|----------------------------------------------------------------------|-----------|
| `name`     | string | The name of the field                                                | `>=0.1.0` |
| `presets`  | array  | An array of strings to use as preset options                         | `>=0.1.0` |
| `default`  | string | The default value for the field, note: `_p:0` means the first preset | `>=0.1.0` |
| `prefix`   | string | The prefix for the field                                             | `>=0.1.0` |
| `suffix`   | string | The suffix for the field                                             | `>=0.1.0` |
| `sort`     | int    | The sort for the field                                               | `>=1.0.0` |
| `media`    | array  | An array of [Media](#media) objects                                  | `>=1.0.0` |
| `settings` | object | A [Settings](#settings) object with grouped key-value pairs          | `>=1.0.0` |

### Media

| Name           | Type   | Description                         |
|----------------|--------|-------------------------------------|
| `id`           | int    | The id of the media                 |
| `slug`         | string | The slug of the media               |
| `disk`         | string | The disk used to store the media    |
| `path`         | string | The path of the media on the disk   |
| `title`        | string | The title of the media              |
| `type`         | string | The mimetype of the media           |
| `extension`    | string | The file extension of the media     |
| `size`         | int    | The file size of the media in bytes |
| `meta`         | object | The meta data of the media          |
| `source`       | string | The source file name of the media   |
| `is_protected` | bool   | Whether the media is protected      |

### Settings

Settings are grouped as key-value pairs.
- Use "_" for ungrouped settings.
- Each group contains its own object of key-value pairs.

```json
{
    "settings": {
        "_": {
            "no_group": "value"
        },
        "group": {
            "key": "value"
        }
    }
}
```

## Example Response

```http request
GET /api/specification-groups/{id}
```

```json
{
    "id": 1,
    "name": "API Test",
    "fields": [
        {
            "name": "Field 1",
            "presets": ["A", "B", "C"],
            "default": "D",
            "prefix": "prefix",
            "suffix": "suffix",
            "media": [],
            "settings": {
                "test": {
                    "test": 123
                }
            }
        }
    ],
    "media": [],
    "settings": {
        "test": {
            "test": 456
        }
    }
}
```

[Back to contents](../../README.md#table-of-contents)
