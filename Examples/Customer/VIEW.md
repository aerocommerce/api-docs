# View Customer

## Overview

This endpoint retrieves a single customer by `id`

## Structure

### Product

| Name                    | Type      | Description                                                       |
|-------------------------|-----------|-------------------------------------------------------------------|
| `id`                    | int       | The id of the customer                                            |
| `name`                  | string    | The name of the customer                                          |
| `email`                 | string    | The email of the customer                                         |
| `created_at`            | timestamp | The date that the customer was created at                         |
| `group`                 | object    | The group the customer belongs to, see [Group](#group)            |
| `addresses`             | array     | An array of [Address](#addresses) objects                         |
| `tax_group`             | object    | The [Tax Group](#tax-group) of the customer                       |
| `additional_attributes` | object    | An array of [Additional Attribute](#additional-attribute) objects |

### Group

A customer can belong to a group, if it doesn't then `group` will be `null`, see attributes below:

| Name        | Type   | Description                                                      |
|-------------|--------|------------------------------------------------------------------|
| `id`        | int    | The id of the customer group                                     |
| `name`      | string | The name of the customer group                                   |
| `tax_group` | object | The tax group of the customer group, see [Tax Group](#tax-group) |

### Tax Group

A customer & customer group can have a tax group, if they don't then `tax_group` will be `null`, see attributes below:

| Name   | Type   | Description                        |
|--------|--------|------------------------------------|
| `id`   | int    | The id of the customer tax group   |
| `name` | string | The name of the customer tax group |

### Addresses

A customer can have addresses, see attributes below:

| Name          | Type    | Description                              |
|---------------|---------|------------------------------------------|
| `name`        | string  | The name of the address                  |
| `first_name`  | string  | The first name for the address           |
| `last_name`   | string  | The last name for the address            |
| `company`     | string  | The company for the address              |
| `mobile`      | string  | The mobile number for the address        |
| `phone`       | string  | The phone number for the address         |
| `line_1`      | string  | The first line for the address           |
| `line_2`      | string  | The second line for the address          |
| `city`        | string  | The city for the address                 |
| `zone`        | string  | The zone code for the address            |
| `postcode`    | string  | The postcode for the address             |
| `country`     | string  | The country code for the address         |
| `reference`   | string  | The **unique** reference for the address |
| `eori_number` | string  | The EORI number for the address          |
| `is_default`  | boolean | Whether the address is default           |

### Additional Attribute

| Name    | Type    | Description                           |
|---------|---------|---------------------------------------|
| `key`   | string  | The key of the additional attribute   | 
| `value` | string  | The value of the additional attribute |

## Example Response

```http request
GET /api/customers/{id}
```

```json lines
{
    "id": 1,
    "name": "test test",
    "email": "test@gmail.com",
    "created_at": "2025-06-27T13:00:47.000000Z",
    "group": {
        "id": 1,
        "name": "test",
        "tax_group": {
            "id": 1,
            "name": "Retail Customer"
        }
    },
    "addresses": [
        {
            "id": 1,
            "name": null,
            "first_name": "test",
            "last_name": "test",
            "company": "test",
            "mobile": null,
            "phone": null,
            "line_1": "test",
            "line_2": null,
            "city": "test",
            "zone": null,
            "postcode": "te57 10l",
            "country": "GB",
            "reference": null,
            "eori_number": null,
            "is_default": 0
        },
        {
            "id": 2,
            "name": null,
            "first_name": "test",
            "last_name": "test",
            "company": "test",
            "mobile": null,
            "phone": null,
            "line_1": "test",
            "line_2": null,
            "city": "test",
            "zone": null,
            "postcode": "te57 10l",
            "country": "GB",
            "reference": null,
            "eori_number": null,
            "is_default": 1
        }
    ],
    "tax_group": null,
    "additional_attributes": []
}
```

[Back to contents](../../README.md#table-of-contents)
