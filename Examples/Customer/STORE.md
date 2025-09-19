# Store Customer

## Attributes:

### Customer
| Name                    | Type      | Description                                                                                  | Required?      |
|-------------------------|-----------|----------------------------------------------------------------------------------------------|----------------|
| `name`                  | string    | The name of the customer                                                                     | No             |
| `email`                 | string    | The email of the customer                                                                    | No             |
| `password`              | string    | The plain-text password of the customer                                                      | See note below |
| `password_hash`         | string    | The hashed password of the customer                                                          | See note below |
| `group`                 | string    | The group name of the customer                                                               | No             |
| `tax_group`             | string    | The tax group name of the customer                                                           | No             |
| `addresses`             | array     | The addresses of the customer, see [Address](#address)                                       | No             |
| `additional_attributes` | array     | The additional attributes of the customer, see [Additional Attribute](#additional-attribute) | No             |

**NOTE:** One of either `password` or `password_hash` must be present, using `password_hash` is advised - the hashing algorithm must match the store's (normally `bcrypt` by default)

### Address

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
| `county`       | string  | The county for the address               | No                       |
| `zone`         | string  | The zone code for the address            | No (depends on country)  |
| `postcode`     | string  | The postcode for the address             | Yes (depends on country) |
| `country`      | string  | The country code for the address         | No                       |
| `reference`    | string  | The **unique** reference for the address | No                       |
| `eori_number`  | string  | The EORI number for the address          | No                       |
| `is_default`   | boolean | Whether the address is default           | No                       |

### Additional Attribute

| Name    | Type    | Description                           | Required? |
|---------|---------|---------------------------------------|-----------|
| `key`   | string  | The key of the additional attribute   | Yes       |
| `value` | string  | The value of the additional attribute | Yes       |

## Example Request

```http request
POST /api/customers
```

```json lines
{
    "name": "Test",
    "email": "test@gmail.com",
    "password_hash": "$2y$10$0QFHb4QU0wAsaskZPQv0Re72Xa2KXrWt5YR32O5aBxIwc0c41bbwm",
    "group": "Group Name",
    "addresses": [
        {
            "name": "API Address",
            "first_name": "test",
            "last_name": "test",
            "company": "test",
            "mobile": null,
            "phone": null,
            "line_1": "test",
            "line_2": null,
            "city": "test",
            "county" : "Test",
            "zone": null,
            "postcode": "te57 10l",
            "country": "GB",
            "reference": null,
            "eori_number": null,
            "is_default": true
        }
    ],
    "additional_attributes": [
        {
            "key": "api",
            "value": "true"
        }
    ]
}
```

## Example Response

```json
{
    "customer": {
        "id": 1
    }
}
```
