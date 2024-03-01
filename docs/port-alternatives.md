---
sidebar_position: 8
---

# Port Alternatives

You can retrieve port alternatives by using the `GET /port_alternatives` endpoint.

## Request

### To get port alternatives

```http
GET /port_alternatives
```

To get details of a particular port alternative by its ID

```http
GET /port_alternatives/{id}
```

## Query Parameters

| Parameter | Type      | Description                                                               |
| :-------- | :-------- | :------------------------------------------------------------------------ |
| `name`    | `text`    | Optional: Exact name or locode of the port alternative or the main port.  |
| `locodes` | `text`    | Optional: A comma-separated list of locodes to find canonical values for. |
| `output`  | `text`    | Default: long. Options: short and long.                                   |
| `limit`   | `integer` | The number of records to return.                                          |
| `offset`  | `integer` | The number of records to skip.                                            |

## Response

The response will be a JSON object with the following fields:

| Field                 | Type      | Description                                    |
| :-------------------- | :-------- | :--------------------------------------------- |
| `id`                  | `integer` | The unique identifier of the port alternative. |
| `alternative_name`    | `text`    | The name of the port alternative.              |
| `alternative_locode`  | `text`    | The locode of the port alternative.            |
| `seaport_locode`      | `text`    | The locode of the main seaport.                |
| `airport_locode`      | `text`    | The locode of the main airport.                |
| `url`                 | `text`    | The URL of the port alternative.               |
| `port_main`           | `text`    | The name of the main port.                     |
| `airport_main`        | `text`    | The name of the main airport.                  |
| `port_alternative`    | `text`    | The name of the port alternative.              |
| `airport_alternative` | `text`    | The name of the airport alternative.           |

## Python code example

```python
import requests

# Define the endpoint URL
url = "https://coreapi.shipangel.ai/portalternatives"

# Define the request parameters
params = {
    "name": "Los Angeles",  # Optional: Exact name or locode of the port alternative or the main port
    "output": "long"        # Optional: output format
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
const url = "https://coreapi.shipangel.ai/portalternatives";

// Define the request parameters
const params = {
  name: "Los Angeles", // Optional: Exact name or locode of the port alternative or the main port
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

## Example JSON response

```json
[
  {
    "id": 123,
    "alternative_name": "Long Beach",
    "alternative_locode": "USLGB",
    "seaport_locode": "USLAX",
    "airport_locode": "LAX",
    "url": "https://coreapi.shipangel.ai/portalternatives/123",
    "port_main": "Los Angeles",
    "airport_main": "Los Angeles",
    "port_alternative": "Long Beach"
  }
]
```
