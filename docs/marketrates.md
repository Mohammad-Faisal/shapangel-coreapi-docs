---
sidebar_position: 5
---

# Market Rates

You can retrieve market rates for sea transportation by using the `GET /marketrates` endpoint.

## Request

### To get the average daily market rates

```http
GET /marketrates
```

### To get the average daily market rate details

```http
GET /marketrates/{id}
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

## Response Fields

| Field                     | Type       | Description                                      |
| :------------------------ | :--------- | :----------------------------------------------- |
| `url`                     | `text`     | The URL of the market rate details.              |
| `port_origin_actual`      | `text`     | The actual origin port locode or IATA code.      |
| `port_destination_actual` | `text`     | The actual destination port locode or IATA code. |
| `contract_length`         | `text`     | The contracted length of the container.          |
| `container_type`          | `text`     | The weight category.                             |
| `quality`                 | `text`     | The quality of the market rate.                  |
| `date`                    | `DateTime` | The date of the market rate.                     |
| `rate_average`            | `float`    | The average daily market rate.                   |
| `date_created`            | `DateTime` | The date the market rate was created.            |
| `port_origin`             | `text`     | The origin port locode or IATA code.             |
| `port_destination`        | `text`     | The destination port locode or IATA code.        |

## Python code example

```python
import requests

# Define the endpoint URL
url = "https://coreapi.shipangel.ai/marketrates"

# Define the request parameters
params = {
    "port_origin": "USNYC",            # Required: origin port locode or IATA code
    "port_destination": "HKHKG",       # Required: destination port locode or IATA code
    "date_to": "20230228",             # Optional: the first date to match
    "contract_length": "long",         # Optional: contracted length of the container
    "container_type": "40DC",          # Optional: weight category
    "date_from": "20230201",           # Optional: the last date to match
    "months": 12,                      # Optional: number of months to count before the date_to
    "output": "long"                   # Optional: output format
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
const url = "https://coreapi.shipangel.ai/marketrates";

// Define the request parameters
const params = {
  port_origin: "USNYC", // Required: origin port locode or IATA code
  port_destination: "HKHKG", // Required: destination port locode or IATA code
  date_to: "20230228", // Optional: the first date to match
  contract_length: "long", // Optional: contracted length of the container
  container_type: "40DC", // Optional: weight category
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
    "url": "https://coreapi.shipangel.ai/marketrates/123",
    "port_origin_actual": "USNYC",
    "port_destination_actual": "HKHKG",
    "contract_length": "long",
    "container_type": "40DC",
    "quality": "good",
    "date": "2023-12-18",
    "rate_average": 1500,
    "date_created": "2023-12-18T03:18:01Z",
    "port_origin": "USNYC",
    "port_destination": "HKHKG"
  }
]
```
