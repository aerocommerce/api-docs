# Update Flag

## Attributes:

| Name          | Type    | Description                         | Required? |
|---------------|---------|-------------------------------------|-----------|
| `name`        | string  | The name of the flag                | No        |
| `color`       | string  | The color of the flag (hexadecimal) | No        |

## Example Request

```http request
PUT /api/flags/{id}
```

```json lines
{
    "name": "API Flag Updated",
    "color": "#F1F2F3",
}
```

## Example Response

```json
{
    "flag": {
        "id": 1
    }
}
```

