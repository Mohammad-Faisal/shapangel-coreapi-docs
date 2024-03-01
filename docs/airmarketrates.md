---
sidebar_position: 6
---

# Air Market Rates

You can retrieve market rates for air transportation by using the `GET /airmarketrates` endpoint.

## Request

### To get the average air market rates

```http
GET /airmarketrates
```

### To get the average air market rate details

```http
GET /airmarketrates/{id}
```

## Query Parameters

| Parameter          | Type       | Description                                                                                                      |
| :----------------- | :--------- | :--------------------------------------------------------------------------------------------------------------- |
| `port_origin`      | `text`     | Locode or IATA code of the origin port (required).                                                               |
| `port_destination` | `text`     | Locode or IATA code of the destination port (required).                                                          |
| `date_to`          | `DateTime` | The first date to match (YYYYMMDD). The default is today.                                                        |
| `contract_length`  | `text`     | Contracted length of the container. Options: long and short. The default is long.                                |
| `container_type`   | `text`     | Weight category. Options: 20DC, 40DC, and 40HC.                                                                  |
| `date_from`        | `DateTime` | The last date to match (YYYYMMDD).                                                                               |
| `months`           | `int`      | Number of months to count before the date_to. This parameter is used when date_from is empty. The default is 12. |
| `output`           | `text`     | Default: long. Options: short and long.                                                                          |
| `limit`            | `integer`  | The number of records to return.                                                                                 |
| `offset`           | `integer`  | The number of records to skip.                                                                                   |

## Python code example

```python
import requests

# Define the endpoint URL
url = "https://coreapi.shipangel.ai/airmarketrates"

# Define the request parameters
params = {
    "port_origin": "USNYC",                # Required: origin port locode or IATA code
    "port_destination": "HKHKG",           # Required: destination port locode or IATA code
    "date_to": "20230228",                 # Optional: the first date to match
    "contract_length": "all",              # Optional: contracted length of the container
    "weight_bracket": "less_than_45kg",    # Optional: weight category
    "date_from": "20230201",               # Optional: the last date to match
    "months": 12,                          # Optional: number of months to count before the date_to
    "output": "long"                       # Optional: output format
}

# Make the API request
response = requests.get(url, params=params)

# Print the JSON response
print(response.json())
```

## Nodejs code example

```javascript
const axios = require("axios");

// Define the endpoint URL
const url = "https://coreapi.shipangel.ai/airmarketrates";

// Define the request parameters
const params = {
  port_origin: "USNYC", // Required: origin port locode or IATA code
  port_destination: "HKHKG", // Required: destination port locode or IATA code
  date_to: "20230228", // Optional: the first date to match
  contract_length: "all", // Optional: contracted length of the container
  weight_bracket: "less_than_45kg", // Optional: weight category
  date_from: "20230201", // Optional: the last date to match
  months: 12, // Optional: number of months to count before the date_to
  output: "long", // Optional: output format
};

// Make the API request
axios
  .get(url, { params })
  .then((response) => {
    // Print the JSON response
    console.log(response.data);
  })
  .catch((error) => {
    console.error(error);
  });
```

## Response

The response will be a JSON object with the following fields:

```json
[
  {
    "url": "https://coreapi.shipangel.ai/airmarketrates/123",
    "port_origin_actual": "USNYC",
    "port_destination_actual": "HKHKG",
    "contract_length": "long",
    "contracted_within": "mid-tier",
    "weight_bracket": "less_than_45kg",
    "service_level": "standard",
    "quality": "good",
    "date": "2023-12-18",
    "rate_average": 1500,
    "date_created": "2023-12-18T03:18:01Z",
    "port_origin": "USNYC",
    "port_destination": "HKHKG"
  }
]
```

If the output parameter is `short`, the response is as follows:

```json
[
  {
    "weight_bracket": "less_than_45kg",
    "date": "2023-12-18",
    "rate_average": 1500
  }
]
```

The table representation of the fields are as follows:

| Field                     | Description                                      |
| :------------------------ | :----------------------------------------------- |
| `url`                     | The URL of the market rate details.              |
| `port_origin_actual`      | The actual origin port locode or IATA code.      |
| `port_destination_actual` | The actual destination port locode or IATA code. |
| `contract_length`         | The contracted length of the container.          |
| `contracted_within`       | The contracted tier.                             |
| `weight_bracket`          | The weight category.                             |
| `service_level`           | The service level.                               |
| `quality`                 | The quality of the market rate.                  |
| `date`                    | The date of the market rate.                     |
| `rate_average`            | The average rate.                                |
| `date_created`            | The date the record was created.                 |
| `port_origin`             | The origin port locode or IATA code.             |
| `port_destination`        | The destination port locode or IATA code.        |
