# Responses

## Codes

| Code | Scenario                                     | Responses                                                             |
|------|----------------------------------------------|-----------------------------------------------------------------------|
| 200  | Request was successful                       | [Responses > 200 (Success)](#200-success)                             | 
| 201  | One (or multiple) resources were created     | [Responses > 201 (Created)](#201-created)                             | 
| 400  | Cannot process request due to client error   | [Responses > 400 (Bad request)](#400-bad-request)                     | 
| 401  | Invalid / Unauthorized bearer token provided | [Responses > 401 (Unauthorized)](#401-unauthorized)                   |
| 404  | Resource not found                           | [Responses > 404 (Not found)](#404-not-found)                         |
| 422  | Payload failed validation                    | [Responses > 422 (Unprocessable entity)](#422-unprocessable-entity)   | 
| 500  | Internal server error                        | [Responses > 500 (Internal Server Error)](#500-internal-server-error) |

## Examples

### 200 (Success)

Example below illustrates the response received when making a `GET` request to `/api/orders/{id}`

```json
{
    "reference": "LTS123456",
    "email": "testing@gmail.com",
    "subtotal": {
        "amount": 84166.67,
        "tax": 16833.33
    },
    "shipping": {
        "amount": 83.33,
        "tax": 16.67
    },
    "discount": {
        "amount": 8416.67,
        "tax": 1683.33
    },
    "surcharge": {
        "amount": 0,
        "tax": 0
    },
    "ordered_at": "2023-09-01T09:29:41.000000Z",
    "deliver_on": null,
    "currency": {
        "code": "GBP",
        "symbol": "£"
    },
    "status": {
        "id": 3,
        "name": "Successful",
        "state": "successful"
    },
    "customer": {
        "id": 1,
        "name": "1",
        "email": "1@gmail.com"
    },
    "shipping_method": {
        "id": 1,
        "name": "Standard"
    },
    "billing_address": {
        "id": 331,
        "first_name": "Aero",
        "last_name": "Commerce",
        "company": "Aero Commerce",
        "mobile": null,
        "phone": null,
        "line_1": "28-32 Albert Rd",
        "line_2": null,
        "city": "Middlesbrough",
        "zone": null,
        "postcode": "TS1 1QD",
        "reference": null,
        "country": "GB",
        "eori_number": null
    },
    "shipping_address": {
        "id": 331,
        "first_name": "Aero",
        "last_name": "Commerce",
        "company": "Aero Commerce",
        "mobile": null,
        "phone": null,
        "line_1": "28-32 Albert Rd",
        "line_2": null,
        "city": "Middlesbrough",
        "zone": null,
        "postcode": "TS1 1QD",
        "reference": null,
        "country": "GB",
        "eori_number": null
    },
    "items": [
        {
            "id": 148,
            "name": "Sandro Paris Checked Trench Coat",
            "sku": "SHPMA00148-M",
            "product_id": 4,
            "variant_id": 14,
            "shippable": true,
            "quantity": 2,
            "price": {
                "amount": 42083.33,
                "tax": 8416.67
            },
            "discount": {
                "amount": 8416.67,
                "tax": 1683.33
            },
            "full_price": {
                "amount": 42083.33,
                "tax": 8416.67
            },
            "weight": 0,
            "volume": 0
        }
    ]
}
```

### 201 (Created)

Example below illustrates the response received when making a `POST` request to `/api/orders`

```json
{
    "order": {
        "id": 15
    }
}
```

### 400 (Bad Request)

Example below illustrates the response received making a `GET` request to `/api/orders/{id}` without supplying an id

```json
{
    "message": "Missing order ID"
}
```

### 401 (Unauthorized)

Example below illustrates the response received when a bearer token isn't supplied

```json
{
    "message": "Unauthorized: Bearer token missing."
}
```

### 404 (Not found)

Example below illustrates the response received making a `GET` request to `/api/orders/{id}` using an id that doesn't exist

```json
{
    "message": "The requested order with ID {id} could not be found."
}
```

### 422 (Unprocessable entity)

Example below illustrates the response received when making a `POST` request to `/api/orders` that fails validation

```json
{
    "message": "The given data was invalid.",
    "errors": {
        "currency_code": ["The currency code field is required."]
    }
}
```

### 500 (Internal server error)

Example below illustrates the response received when an Exception is thrown

```json
{
    "message": "Exception message..."
}
```

[Back to contents](README.md#table-of-contents)
