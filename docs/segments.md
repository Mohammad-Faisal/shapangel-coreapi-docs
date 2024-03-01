---
sidebar_position: 7
---

# Schedule Segments

You can retrieve schedule segments by using the `GET /segments` endpoint.

## Request

### To get schedule segments

```http
GET /segments
```

To get details of a particular segment by its ID

```http
GET /segments/{id}
```

## Query Parameters

| Parameter             | Type   | Description                                                                                                                 |
| :-------------------- | :----- | :-------------------------------------------------------------------------------------------------------------------------- |
| `port_origin`         | `text` | Locode or IATA code of the origin port (required).                                                                          |
| `port_destination`    | `text` | Locode or IATA code of the destination port (required).                                                                     |
| `origin_destinations` | `text` | Optional: a list of origin-destination locodes or IATA codes, comma-separated with origin and destination separated by '-'. |
| `date_from`           | `text` | Starting date to search. Format: YYYYMMDD. If not provided, current date is used.                                           |

## Response

| Field                 | Type   | Description                                                                                             |
| :-------------------- | :----- | :------------------------------------------------------------------------------------------------------ |
| `id`                  | `int`  | Unique identifier of the segment.                                                                       |
| `url`                 | `text` | URL of the segment.                                                                                     |
| `segment_order`       | `int`  | Order of the segment.                                                                                   |
| `scac_code`           | `text` | SCAC code of the carrier.                                                                               |
| `carrier_alias`       | `text` | Alias of the carrier.                                                                                   |
| `carrier_service_des` | `text` | Description of the carrier service.                                                                     |
| `vessel_imo`          | `text` | IMO number of the vessel.                                                                               |
| `vessel_name`         | `text` | Name of the vessel.                                                                                     |
| `origin_date`         | `text` | Date of origin. Format: YYYY-MM-DDTHH:MM:SSZ.                                                           |
| `destination_date`    | `text` | Date of destination. Format: YYYY-MM-DDTHH:MM:SSZ.                                                      |
| `dwell_time`          | `int`  | Dwell time in days.                                                                                     |
| `date_created`        | `text` | Date and time of creation. Format: YYYY-MM-DDTHH:MM:SSZ.                                                |
| `ship_schedule`       | `text` | Origin and destination locodes or IATA codes separated by '-'.                                          |
| `from_locode`         | `text` | Origin port locode or IATA code.                                                                        |
| `to_locode`           | `text` | Destination port locode or IATA code.                                                                   |
| `origin_destinations` | `text` | Origin-destination locodes or IATA codes, comma-separated with origin and destination separated by '-'. |

## Python code example

```python
import requests

# Define the endpoint URL
url = "https://coreapi.shipangel.ai/schedulesegments"

# Define the request parameters
params = {
    "port_origin": "USNYC",           # Required: origin port locode
    "port_destination": "HKHKG",      # Required: destination port locode
    "date_from": "20230201"           # Optional: filter results starting from date
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
const url = "https://coreapi.shipangel.ai/schedulesegments";

// Define the request parameters
const params = {
  port_origin: "USNYC", // Required: origin port locode
  port_destination: "HKHKG", // Required: destination port locode
  date_from: "20230201", // Optional: filter results starting from date
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
    "id": 123,
    "url": "https://coreapi.shipangel.ai/schedulesegments/123",
    "segment_order": 1,
    "scac_code": "XYZ",
    "carrier_alias": "CarrierXYZ",
    "carrier_service_des": "ServiceXYZ",
    "vessel_imo": "1234567",
    "vessel_name": "VesselXYZ",
    "origin_date": "2023-12-18T03:18:01Z",
    "destination_date": "2023-12-25T03:18:01Z",
    "dwell_time": 3,
    "date_created": "2023-12-18T03:18:01Z",
    "ship_schedule": "USNYC-HKHKG",
    "from_locode": "USNYC",
    "to_locode": "HKHKG",
    "origin_destinations": "USNYC-HKHKG"
  }
]
```
