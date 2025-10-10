# Update Specification Group

## Overview

This endpoint updates an existing specification group by its `id`. Only the fields provided in the request will be updated; unspecified fields remain unchanged.

## Structure

### Specification Group

| Name     | Type   | Description                          | Required? |
|----------|--------|--------------------------------------|-----------|
| `id`     | int    | The id of the specification group    | No        |
| `name`   | string | The name for the specification group | No        |
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
PUT /api/specification-groups/{id}
```

```json lines
{
    "name": "API Test",
    "fields": [
        {
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
