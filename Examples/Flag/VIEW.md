# View Flag

## Attributes:

| Name         | Type   | Description                          |
|--------------|--------|--------------------------------------|
| `id`         | int    | The id of the flag                   |
| `name`       | string | The **unique** name for the flag     |
| `color`      | string | The colour of the flag (hexadecimal) |
| `created_at` | date   | The date the flag was created        |

## Example Response

```http request
GET /api/flags/{id}
```

```json
{
    "id": 1,
    "name": "Flag",
    "color": "#7f3434",
    "created_at": "2025-06-30T08:14:27.000000Z"
}
```

[Back to contents](../../README.md#table-of-contents)
