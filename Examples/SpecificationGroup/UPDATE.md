# Update Specification Group

## Overview

This endpoint updates an existing specification group by its `id`. Only the fields provided in the request will be updated; unspecified fields remain unchanged.

## Structure

### Specification Group

| Name       | Type   | Description                                                 | Required? | Version   |
|------------|--------|-------------------------------------------------------------|-----------|-----------|
| `id`       | int    | The id of the specification group                           | No        | `>=0.1.0` |
| `name`     | string | The name for the specification group                        | No        | `>=0.1.0` |
| `sort`     | int    | The sort for the specification group                        | No        | `>=1.0.0` |
| `fields`   | array  | An array of [Field](#field) objects                         | No        | `>=0.1.0` |
| `media`    | array  | An array of [Media](#media) objects                         | No        | `>=0.3.2` |
| `settings` | object | A [Settings](#settings) object with grouped key-value pairs | No        | `>=1.0.0` |

### Field

| Name       | Type   | Description                                                        | Required? | Version   |
|------------|--------|--------------------------------------------------------------------|-----------|-----------|
| `name`     | string | The name of the field                                              | Yes       | `>=0.1.0` |
| `presets`  | array  | An array of strings to use as preset options                       | No        | `>=0.1.0` |
| `default`  | string | The default value for the field, note: _p:0 means the first preset | Yes       | `>=0.1.0` |
| `prefix`   | string | The prefix for the field                                           | No        | `>=0.1.0` |
| `suffix`   | string | The suffix for the field                                           | No        | `>=0.1.0` |
| `sort`     | int    | The sort for the field                                             | No        | `>=1.0.0` |
| `media`    | array  | An array of [Media](#media) objects                                | No        | `>=1.0.0` |
| `settings` | object | A [Settings](#settings) object with grouped key-value pairs        | No        | `>=1.0.0` |

### Media

| Name     | Type   | Description                            | Required? |
|----------|--------|----------------------------------------|-----------|
| `id`     | int    | The id of the media                    | `*`       |
| `source` | string | The source of the media, e.g. test.png | `*`       |

`*` At least one must be present

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

## Example Request

```http request
PUT /api/specification-groups/{id}
```

```json lines
{
    "name": "API Test",
    "fields": [
        {
            "id": 1,
            "name": "Field 1 Updated",
            "presets": ["D", "E", "F"],
            "default": "G"
        }
    ]
}
```

## Example Response

```json
{
    "specificationGroup": {
        "id": 1
    }
}
```

[Back to contents](../../README.md#table-of-contents)
