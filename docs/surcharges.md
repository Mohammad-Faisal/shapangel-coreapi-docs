---
sidebar_position: 10
---

# Get Surcharges

You can retrieve surcharges using the `GET /surcharges` endpoint.

## Request

### To get surcharges

```http
GET /surcharges
```

To get details of a particular surcharge by its ID

```http
GET /surcharges/{id}
```

## Query Parameters

| Parameter                                    | Type    | Description                                             |
| :------------------------------------------- | :------ | :------------------------------------------------------ |
| `rate_sheet__client__client_name__icontains` | Text    | Filter by case-insensitive text within the client name. |
| `container_type`                             | Text    | Filter by type of container.                            |
| `remarks__icontains`                         | Text    | Filter by case-insensitive text within the remarks.     |
| `name__icontains`                            | Text    | Filter by case-insensitive text within the name.        |
| `conditional`                                | Boolean | Filter by whether the surcharge is conditional.         |

## Response Fields

| Field              | Description                               |
| :----------------- | :---------------------------------------- |
| `id`               | The unique identifier of the surcharge.   |
| `url`              | The URL of the surcharge.                 |
| `shipper`          | The shipper of the surcharge.             |
| `internal_id`      | The internal identifier of the surcharge. |
| `name`             | The name of the surcharge.                |
| `container_type`   | The type of container.                    |
| `per_shipment`     | The surcharge amount per shipment.        |
| `per_container`    | The surcharge amount per container.       |
| `conditional`      | Whether the surcharge is conditional.     |
| `category`         | The category of the surcharge.            |
| `commodity`        | The commodity of the surcharge.           |
| `remarks`          | The remarks of the surcharge.             |
| `rate_sheet`       | The rate sheet of the surcharge.          |
| `from_locode`      | The origin port locode.                   |
| `to_locode`        | The destination port locode.              |
| `origin_city`      | The origin city.                          |
| `destination_city` | The destination city.                     |

## Python Code Example

```python
import requests

# Define the endpoint URL
url = "https://api.example.com/surcharges"

# Define the request parameters
params = {
    "rate_sheet__client__client_name__icontains": "Example Company",
    "container_type": "40HC",
    "conditional": True
}

# Make the API request
response = requests.get(url, params=params)

# Print the JSON response
print(response.json())
```

## Nodejs Code Example

```javascript
const axios = require("axios");

// Define the endpoint URL
const url = "https://api.example.com/surcharges";

// Define the request parameters
const params = {
  rate_sheet__client__client_name__icontains: "Example Company",
  container_type: "40HC",
  conditional: true,
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
    "id": 1,
    "url": "https://api.example.com/surcharges/1",
    "shipper": "Example Shipper",
    "internal_id": "SUR001",
    "name": "Surcharge A",
    "container_type": "40HC",
    "per_shipment": 50.0,
    "per_container": 25.0,
    "conditional": true,
    "category": "Handling",
    "commodity": "General Cargo",
    "remarks": "Applicable for high-density cargo",
    "rate_sheet": "Example Rate Sheet",
    "from_locode": "USNYC",
    "to_locode": "HKHKG",
    "origin_city": "New York",
    "destination_city": "Hong Kong"
  }
]
```
