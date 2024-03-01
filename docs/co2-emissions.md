---
sidebar_position: 2
---

# CO2 emissions

You can calculate the CO2 emissions for a shipment by using the `GET /co2emissions` endpoint.

## Request

### To get all entries

```http
GET /co2emissions
```

To get a particular entry by its ID

```http
GET /co2emissions/{id}
```

## Query Parameters

| Parameter | Type      | Description                      |
| :-------- | :-------- | :------------------------------- |
| `limit`   | `integer` | The number of records to return. |
| `offset`  | `integer` | The number of records to skip.   |

## Response Fields

| Field                  | Description                                            |
| :--------------------- | :----------------------------------------------------- |
| `url`                  | The URL of the CO2 emissions entry.                    |
| `co2`                  | The total CO2 emissions in kilograms.                  |
| `co2_wtt`              | The CO2 emissions from well to tank in kilograms.      |
| `co2_ttw`              | The CO2 emissions from tank to well in kilograms.      |
| `co2_intensity`        | The CO2 intensity in kilograms per tonne-kilometer.    |
| `scac_code`            | The Standard Carrier Alpha Code (SCAC) of the carrier. |
| `ship_type`            | The type of the ship.                                  |
| `ship_fuel_type`       | The fuel type of the ship.                             |
| `container_type`       | The type of the container.                             |
| `number_of_containers` | The number of containers.                              |
| `weight`               | The weight of the shipment in kilograms.               |
| `trade_line`           | The trade line of the shipment.                        |
| `date_created`         | The date and time when the entry was created.          |
| `from_locode`          | The origin port locode.                                |
| `to_locode`            | The destination port locode.                           |

## Python code example

```python
import requests

# Define the endpoint URL
url = "https://coreapi.shipangel.ai/co2"

# Define the request parameters
params = {
    "container_type": ["20GP", "40GP"],  # Optional: filter by container type
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
const url = "https://coreapi.shipangel.ai/co2";

// Define the request parameters
const params = {
  container_type: ["20GP", "40GP"], // Optional: filter by container type
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

## Example JSON response

```json
{
  "CO2Emissions": {
    "url": "https://coreapi.shipangel.ai/co2",
    "co2": 1000,
    "co2_wtt": 900,
    "co2_ttw": 1100,
    "co2_intensity": 0.5,
    "scac_code": "ABC123",
    "ship_type": null,
    "ship_fuel_type": "LNG",
    "container_type": "40GP",
    "number_of_containers": 5,
    "weight": 25000,
    "trade_line": "Transpacific",
    "date_created": "2023-12-18T03:18:01Z",
    "from_locode": "USNYC",
    "to_locode": "HKHKG"
  }
}
```
