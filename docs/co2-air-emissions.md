---
sidebar_position: 3
---

# CO2 Air Emissions

You can calculate the CO2 emissions for air shipments by using the `GET /co2airemissions` endpoint.

## Request

### To get all entries

```http
GET /co2airemissions
```

### To get a particular entry by its ID

```http
GET /co2airemissions/{id}
```

## Query Parameters

| Parameter | Type      | Description                      |
| :-------- | :-------- | :------------------------------- |
| `limit`   | `integer` | The number of records to return. |
| `offset`  | `integer` | The number of records to skip.   |

## Response Fields

The response will contain the following fields:

| Field           | Description                          |
| :-------------- | :----------------------------------- |
| `url`           | The URL of the API endpoint.         |
| `co2`           | The total CO2 emissions.             |
| `co2_wtt`       | The CO2 emissions from well to tank. |
| `co2_ttw`       | The CO2 emissions from tank to well. |
| `co2_intensity` | The CO2 intensity.                   |
| `scac_code`     | The Standard Carrier Alpha Code.     |
| `weight`        | The weight of the shipment.          |
| `trade_line`    | The trade line of the shipment.      |
| `date_created`  | The date the record was created.     |
| `from_locode`   | The origin port locode.              |
| `to_locode`     | The destination port locode.         |

## Python code example

```python
import requests

# Define the endpoint URL
url = "https://coreapi.shipangel.ai/co2airemissions"

# Define the request parameters
params = {
    "port_origin": "USNYC",  # Required: origin port locode
    "port_destination": "HKHKG"  # Required: destination port locode
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
const url = "https://coreapi.shipangel.ai/co2airemissions";

// Define the request parameters
const params = {
  port_origin: "USNYC", // Required: origin port locode
  port_destination: "HKHKG", // Required: destination port locode
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
{
  "CO2AirEmissions": {
    "url": "https://coreapi.shipangel.ai/co2airemissions",
    "co2": 1000,
    "co2_wtt": 900,
    "co2_ttw": 1100,
    "co2_intensity": 0.5,
    "scac_code": "ABC123",
    "weight": 25000,
    "trade_line": "Transpacific",
    "date_created": "2023-12-18T03:18:01Z",
    "from_locode": "USNYC",
    "to_locode": "HKHKG"
  }
}
```
