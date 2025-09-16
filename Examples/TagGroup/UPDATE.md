# Update Tag Group

## Overview

This endpoint updates an existing tag group by its `id` or `name`. Only the fields provided in the request will be updated; unspecified fields remain unchanged.

## Structure

### Tag Group

| Name              | Type    | Description                                             | Required? |
|-------------------|---------|---------------------------------------------------------|-----------|
| `name`            | string  | The name of the tag group (e.g., Size or Colour)        | No        |
| `reference`       | string  | The reference of the tag group                          | No        |
| `show_in_filters` | boolean | Whether the tag group shows in filters on listings page | No        |

## Example Request

```http request
PUT /api/tag-groups/{id|name}
```

```json lines
{
    "name": "Updated Size",
    "show_in_filters": false
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
