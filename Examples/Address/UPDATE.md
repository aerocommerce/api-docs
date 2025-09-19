# Update Address

## Overview

This endpoint updates an existing customer address by its `id`. Only the fields provided in the request will be updated; unspecified fields remain unchanged.

## Structure

| Name          | Type    | Description                                                                            | Required? |
|---------------|---------|----------------------------------------------------------------------------------------|-----------|
| `name`        | string  | The name of the address                                                                | No        |
| `first_name`  | string  | The first name for the address                                                         | No        |
| `last_name`   | string  | The last name for the address                                                          | No        |
| `company`     | string  | The company for the address                                                            | No        |
| `mobile`      | string  | The mobile number for the address                                                      | No        |
| `phone`       | string  | The phone number for the address                                                       | No        |
| `line_1`      | string  | The first line for the address                                                         | No        |
| `line_2`      | string  | The second line for the address                                                        | No        |
| `city`        | string  | The city for the address                                                               | No        |
| `county`      | string  | The county for the address                                                             | No        |
| `zone`        | string  | The zone code for the address, only applicable for some countries (e.g., US, AU, etc)  | No        |
| `postcode`    | string  | The postcode for the address, only applicable for some countries (e.g., GB, US, etc)   | No        |
| `country`     | string  | The country code for the address                                                       | No        |
| `reference`   | string  | The **unique** reference for the address                                               | No        |
| `eori_number` | string  | The EORI number for the address                                                        | No        |
| `is_default`  | boolean | Whether the address is default                                                         | No        |

## Example Request

```http request
PUT /api/customers/{id}/addresses/{id}
```

```json lines
{
    "name": "API Address Updated",
    "first_name": "test2",
    "county": "Test 2"
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
