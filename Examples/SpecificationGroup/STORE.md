# Store Specification Group

## Overview

This endpoint creates a new specification group using the provided json data

## Structure

### Specification Group

| Name     | Type   | Description                          | Required? |
|----------|--------|--------------------------------------|-----------|
| `id`     | int    | The id of the specification group    | No        |
| `name`   | string | The name for the specification group | Yes       |
| `fields` | array  | An array of [Field](#field) objects  | No        |

### Field

| Name      | Type   | Description                                                        | Required? |
|-----------|--------|--------------------------------------------------------------------|-----------|
| `name`    | string | The name of the field                                              | Yes       |
| `presets` | array  | An array of strings to use as preset options                       | No        |
| `default` | string | The default value for the field, note: _p:0 means the first preset | Yes       |
| `prefix`  | string | The prefix for the field                                           | No        |
| `suffix`  | string | The suffix for the field                                           | No        |


## Example Request

```http request
POST /api/specification-groups/
```

```json lines
{
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

## Example Response

```json
{
    "specificationGroup": {
        "id": 1
    }
}
```

[Back to contents](../../README.md#table-of-contents)
