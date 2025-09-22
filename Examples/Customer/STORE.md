# Store Customer

## Overview

This endpoint creates a new customer using the provided json data

## Structure

### Customer

| Name                    | Type      | Description                                                                                  | Required?       |
|-------------------------|-----------|----------------------------------------------------------------------------------------------|-----------------|
| `id`                    | integer   | The id for the customer                                                                      | No              |
| `name`                  | string    | The name of the customer                                                                     | Yes             |
| `email`                 | string    | The email of the customer                                                                    | Yes             |
| `password`              | string    | The plain-text password of the customer                                                      | Conditional `*` |
| `password_hash`         | string    | The hashed password of the customer                                                          | Conditional `*` |
| `group`                 | string    | The group name of the customer                                                               | No              |
| `tax_group`             | string    | The tax group name of the customer                                                           | No              |
| `addresses`             | array     | The addresses of the customer, see [Address](#address)                                       | No              |
| `additional_attributes` | array     | The additional attributes of the customer, see [Additional Attribute](#additional-attribute) | No              |

`*` **Note:** One of password or password_hash must be provided. Using password_hash is recommended. Ensure the hashing algorithm matches the store’s configuration (usually bcrypt)

### Address

| Name          | Type    | Description                                                                    | Required?   |
|---------------|---------|--------------------------------------------------------------------------------|-------------|
| `name`        | string  | The name of the address                                                        | No          |
| `first_name`  | string  | The first name for the address                                                 | Yes         |
| `last_name`   | string  | The last name for the address                                                  | Yes         |
| `company`     | string  | The company for the address                                                    | No          |
| `mobile`      | string  | The mobile number for the address                                              | No          |
| `phone`       | string  | The phone number for the address                                               | No          |
| `line_1`      | string  | The first line for the address                                                 | Yes         |
| `line_2`      | string  | The second line for the address                                                | No          |
| `city`        | string  | The city for the address                                                       | Yes         |
| `county`      | string  | The county for the address                                                     | No          |
| `zone`        | string  | The zone code for the address, required for some countries (e.g., US, AU, etc) | Conditional |
| `postcode`    | string  | The postcode for the address, required for some countries (e.g., GB, US, etc)  | Conditional |
| `country`     | string  | The country code for the address                                               | Yes         |
| `reference`   | string  | The **unique** reference for the address                                       | No          |
| `eori_number` | string  | The EORI number for the address                                                | No          |
| `is_default`  | boolean | Whether the address is default                                                 | No          |

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

[Back to contents](../../README.md#table-of-contents)
