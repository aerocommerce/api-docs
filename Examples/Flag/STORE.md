# Store Flag

## Attributes:

| Name          | Type    | Description                         | Required? |
|---------------|---------|-------------------------------------|-----------|
| `name`        | string  | The name of the flag                | Yes       |
| `color`       | string  | The color of the flag (hexadecimal) | Yes       |

## Example Request

```http request
POST /api/flags/
```

```json lines
{
    "name": "API Flag",
    "color": "#000000",
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

