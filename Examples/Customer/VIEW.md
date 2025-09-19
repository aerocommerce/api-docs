# View Customer

## Attributes:

### Product

| Name                    | Type    | Description                                                                                  |
|-------------------------|---------|----------------------------------------------------------------------------------------------|
| `id`                    | int     | The id of the customer                                                                       |
| `name`                  | string  | The name of the customer                                                                     |
| `email`                 | string  | The email of the customer                                                                    |
| `created_at`            | date    | The date that the customer was created at                                                    |
| `group`                 | object  | The group the customer belongs to, see [Group](#group)                                       |
| `addresses`             | array   | The address of the customer, see [Address](#addresses)                                       |
| `tax_group`             | object  | The tax group of the customer, see [Tax Group](#tax-group)                                   |
| `additional_attributes` | object  | The additional attributes of the customer, see [Additional Attribute](#additional-attribute) |

### Group

A customer can belong to a group, if it doesn't then `group` will be `null`, see attributes below:

| Name              | Type   | Description                                                      |
|-------------------|--------|------------------------------------------------------------------|
| `group.id`        | string | The id of the customer group                                     |
| `group.name`      | string | The name of the customer group                                   |
| `group.tax_group` | object | The tax group of the customer group, see [Tax Group](#tax-group) |

### Tax Group

A customer & customer group can have a tax group, if they don't then `tax_group` will be `null`, see attributes below:

| Name              | Type   | Description                        |
|-------------------|--------|------------------------------------|
| `tax_group.id`    | string | The id of the customer tax group   |
| `tax_group.name`  | string | The name of the customer tax group |

### Addresses

A customer can have addresses, see attributes below:

| Name                      | Type    | Description                              |
|---------------------------|---------|------------------------------------------|
| `addresses.*.name`        | string  | The name of the address                  |
| `addresses.*.first_name`  | string  | The first name for the address           |
| `addresses.*.last_name`   | string  | The last name for the address            |
| `addresses.*.company`     | string  | The company for the address              |
| `addresses.*.mobile`      | string  | The mobile number for the address        |
| `addresses.*.phone`       | string  | The phone number for the address         |
| `addresses.*.line_1`      | string  | The first line for the address           |
| `addresses.*.line_2`      | string  | The second line for the address          |
| `addresses.*.city`        | string  | The city for the address                 |
| `addresses.*.county`      | string  | The county for the address               |
| `addresses.*.zone`        | string  | The zone code for the address            |
| `addresses.*.postcode`    | string  | The postcode for the address             |
| `addresses.*.country`     | string  | The country code for the address         |
| `addresses.*.reference`   | string  | The **unique** reference for the address |
| `addresses.*.eori_number` | string  | The EORI number for the address          |
| `addresses.*.is_default`  | boolean | Whether the address is default           |

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
            "county": "Test",
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
            "county": null,
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
