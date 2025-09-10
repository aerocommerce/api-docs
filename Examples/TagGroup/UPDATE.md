# Update Tag Group

## Attributes:

### Tag Group

| Name              | Type    | Description                                                                  | Required? |
|-------------------|---------|------------------------------------------------------------------------------|-----------|
| `name`            | string  | The name of the tag group                                                    | No        |
| `reference`       | string  | The reference of the tag group                                               | No        |
| `show_in_filters` | boolean | Whether the tag group shows in filters on listings page (defaults to `true`) | No        |

## Example Request

```http request
PUT /api/tag-groups/
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

