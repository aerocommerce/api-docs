# Store Address

## Overview

This endpoint creates a new customer address using the provided json data

## Structure

| Name           | Type    | Description                                                                    | Required?   |
|----------------|---------|--------------------------------------------------------------------------------|-------------|
| `id`           | int     | The id for the address                                                         | No          |
| `name`         | string  | The name of the address                                                        | No          |
| `first_name`   | string  | The first name for the address                                                 | Yes         |
| `last_name`    | string  | The last name for the address                                                  | Yes         |
| `company`      | string  | The company for the address                                                    | No          |
| `mobile`       | string  | The mobile number for the address                                              | No          |
| `phone`        | string  | The phone number for the address                                               | No          |
| `line_1`       | string  | The first line for the address                                                 | Yes         |
| `line_2`       | string  | The second line for the address                                                | No          |
| `city`         | string  | The city for the address                                                       | Yes         |
| `county`       | string  | The county for the address                                                     | No          |
| `zone`         | string  | The zone code for the address, required for some countries (e.g., US, AU, etc) | Conditional |
| `postcode`     | string  | The postcode for the address, required for some countries (e.g., GB, US, etc)  | Conditional |
| `country`      | string  | The country code for the address                                               | Yes         |
| `reference`    | string  | The **unique** reference for the address                                       | No          |
| `eori_number`  | string  | The EORI number for the address                                                | No          |
| `is_default`   | boolean | Whether the address is default                                                 | No          |

## Example Request

```http request
POST /api/customers/{id}/addresses
```

```json lines
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
    "county": "Test",
    "zone": null,
    "postcode": "te57 10l",
    "country": "GB",
    "reference": null,
    "eori_number": null,
    "is_default": true
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

[Back to contents](../../README.md#table-of-contents)
