---
sidebar_position: 4
---

# Ship Schedules

# Ship Schedules

You can retrieve ship schedules by using the `GET /ship-schedules` endpoint.

## Request

### To get all ship schedules

```http
GET /ship-schedules
```

### Query Parameters

| Parameter             | Type      | Description                                                                                                                 |
| :-------------------- | :-------- | :-------------------------------------------------------------------------------------------------------------------------- |
| `port_origin`         | `text`    | Locode or IATA code of the origin port (required).                                                                          |
| `port_destination`    | `text`    | Locode or IATA code of the destination port (required).                                                                     |
| `origin_destinations` | `text`    | Optional: a list of origin-destination locodes or IATA codes, comma-separated with origin and destination separated by '-'. |
| `num_results`         | `Number`  | Max number of results to retrieve. If empty, all results are returned.                                                      |
| `date_from`           | `text`    | Starting date to search. Format: YYYYMMDD. If not provided, current date is used.                                           |
| `limit`               | `integer` | The number of records to return.                                                                                            |
| `offset`              | `integer` | The number of records to skip.                                                                                              |

## Response fields

| Field                 | Type      | Description                                                                                             |
| :-------------------- | :-------- | :------------------------------------------------------------------------------------------------------ |
| `id`                  | `integer` | Unique identifier for the ship schedule.                                                                |
| `duration_days`       | `integer` | Duration of the voyage in days.                                                                         |
| `url`                 | `text`    | URL to retrieve the details of the ship schedule.                                                       |
| `voyage_id`           | `text`    | Unique identifier for the voyage.                                                                       |
| `scac_code`           | `text`    | Standard Carrier Alpha Code (SCAC) of the carrier.                                                      |
| `carrier_alias`       | `text`    | Alias of the carrier.                                                                                   |
| `carrier_service_des` | `text`    | Description of the carrier service.                                                                     |
| `vessel_name`         | `text`    | Name of the vessel.                                                                                     |
| `vessel_imo`          | `text`    | IMO number of the vessel.                                                                               |
| `origin_date`         | `text`    | Date of departure from the origin port.                                                                 |
| `destination_date`    | `text`    | Date of arrival at the destination port.                                                                |
| `routing`             | `text`    | Routing of the voyage.                                                                                  |
| `date_created`        | `text`    | Date the record was created.                                                                            |
| `from_locode`         | `text`    | Origin port locode or IATA code.                                                                        |
| `to_locode`           | `text`    | Destination port locode or IATA code.                                                                   |
| `origin_destinations` | `text`    | Origin-destination locodes or IATA codes, comma-separated with origin and destination separated by '-'. |

## Python code example

```python
import requests

# Define the endpoint URL
url = "https://coreapi.shipangel.ai/shipschedules"

# Define the request parameters
params = {
    "port_origin": "USNYC",  # Required: origin port locode or IATA code
    "port_destination": "HKHKG",  # Required: destination port locode or IATA code
    "num_results": 10,  # Optional: max number of results
    "date_from": "20230201",  # Optional: starting date to search
    "limit": 5,  # Optional: max number of records to return
    "offset": 0  # Optional: number of records to skip
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
const url = "https://coreapi.shipangel.ai/shipschedules";

// Define the request parameters
const params = {
  port_origin: "USNYC", // Required: origin port locode or IATA code
  port_destination: "HKHKG", // Required: destination port locode or IATA code
  num_results: 10, // Optional: max number of results
  date_from: "20230201", // Optional: starting date to search
  limit: 5, // Optional: max number of records to return
  offset: 0, // Optional: number of records to skip
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
    "duration_days": 7,
    "url": "https://coreapi.shipangel.ai/shipschedules/123",
    "voyage_id": "ABC123",
    "scac_code": "XYZ",
    "carrier_alias": "CarrierXYZ",
    "carrier_service_des": "ServiceXYZ",
    "vessel_name": "VesselXYZ",
    "vessel_imo": "1234567",
    "origin_date": "2023-12-18T03:18:01Z",
    "destination_date": "2023-12-25T03:18:01Z",
    "routing": "USNYC-HKHKG",
    "date_created": "2023-12-18T03:18:01Z",
    "from_locode": "USNYC",
    "to_locode": "HKHKG",
    "origin_destinations": "USNYC-HKHKG"
  }
]
```
