# Update Address

## Attributes:

| Name           | Type    | Description                              | Required?                |
|----------------|---------|------------------------------------------|--------------------------|
| `name`         | string  | The name of the address                  | No                       |
| `first_name`   | string  | The first name for the address           | Yes                      |
| `last_name`    | string  | The last name for the address            | Yes                      |
| `company`      | string  | The company for the address              | No                       |
| `mobile`       | string  | The mobile number for the address        | No                       |
| `phone`        | string  | The phone number for the address         | No                       |
| `line_1`       | string  | The first line for the address           | Yes                      |
| `line_2`       | string  | The second line for the address          | No                       |
| `city`         | string  | The city for the address                 | Yes                      |
| `zone`         | string  | The zone code for the address            | No (depends on country)  |
| `postcode`     | string  | The postcode for the address             | Yes (depends on country) |
| `country`      | string  | The country code for the address         | No                       |
| `reference`    | string  | The **unique** reference for the address | No                       |
| `eori_number`  | string  | The EORI number for the address          | No                       |
| `is_default`   | boolean | Whether the address is default           | No                       |

## Example Request

```http request
PUT /api/customers/{customerId}/addresses/{addressId}
```

```json lines
{
    "name": "API Address Updated",
    "first_name": "test2"
}
```

## Example Response

```json
{
    "address": {
        "id": 1
    }
}
```

