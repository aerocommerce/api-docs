# View Specification Group

## Overview

This endpoint retrieves a single specification group by `id`

## Structure

### Specification Group

| Name     | Type      | Description                          |
|----------|-----------|--------------------------------------|
| `id`     | int       | The id of the specification group    |
| `name`   | string    | The name for the specification group |
| `fields` | array     | An array of [Field](#field) objects  |

### Field

| Name      | Type   | Description                                                        |
|-----------|--------|--------------------------------------------------------------------|
| `name`    | string | The name of the field                                              |
| `presets` | array  | An array of strings to use as preset options                       |
| `default` | string | The default value for the field, note: _p:0 means the first preset |
| `prefix`  | string | The prefix for the field                                           |
| `suffix`  | string | The suffix for the field                                           |

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
            "suffix": "suffix"
        }
    ]
}
```

[Back to contents](../../README.md#table-of-contents)
