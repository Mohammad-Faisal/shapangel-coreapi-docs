---
sidebar_position: 9
---

# Rates

You can retrieve rates by using the `GET /rates` endpoint.

## Request

### To get rates

```http
GET /rates
```

To get details of a particular rate by its ID

```http
GET /rates/{id}
```

## Query Parameters

| Parameter                                    | Type       | Description                                                                                               |
| :------------------------------------------- | :--------- | :-------------------------------------------------------------------------------------------------------- |
| `rate_sheet__client__client_name__icontains` | `text`     | Case-insensitive text within the client_name of the Company that uploaded the rate sheet (partial match). |
| `container_type`                             | `text`     | Type of the container. Options: 20DC, 40DC, and 40HC.                                                     |
| `rate_sheet__valid_from__gte`                | `DateTime` | Ratesheet validity_from date is greater than or equal to the parameter.                                   |
| `rate_sheet__valid_from__lte`                | `DateTime` | Ratesheet validity_from date is less than or equal to the parameter.                                      |
| `rate_sheet__valid_to__gte`                  | `DateTime` | Ratesheet validity_to date is greater than or equal to the parameter.                                     |
| `rate_sheet__valid_to__lte`                  | `DateTime` | Ratesheet validity_to date is less than or equal to the parameter.                                        |
| `valid_from__gte`                            | `DateTime` | Rate validity_from date is greater than or equal to the parameter.                                        |
| `valid_from__lte`                            | `DateTime` | Rate validity_from date is less than or equal to the parameter.                                           |
| `valid_to__gte`                              | `DateTime` | Rate validity_to date is greater than or equal to the parameter.                                          |
| `valid_to__lte`                              | `DateTime` | Rate validity_to date is less than or equal to the parameter.                                             |
| `shipper`                                    | `text`     | Name of the shipper company.                                                                              |
| `forwarder`                                  | `text`     | Name of the forwarder company.                                                                            |
| `carrier`                                    | `text`     | SCAC code of the Carrier Company.                                                                         |
| `service`                                    | `text`     | Name of the service. Examples: AW, SR, FT, ST, N.                                                         |
| `commodity`                                  | `text`     | Name of the Commodity.                                                                                    |
| `booking_url`                                | `text`     | URL to the booking page.                                                                                  |
| `limit`                                      | `integer`  | The number of records to return.                                                                          |
| `offset`                                     | `integer`  | The number of records to skip.                                                                            |

## Response Fields

| Field                     | Description                                               |
| :------------------------ | :-------------------------------------------------------- |
| `id`                      | The ID of the rate.                                       |
| `client_name`             | The name of the Company that uploaded the rate sheet.     |
| `client_id`               | The ID of the Company that uploaded the rate sheet.       |
| `rate_sheet_file_name`    | The name of the rate sheet file.                          |
| `from_locode_locode`      | The origin port locode.                                   |
| `from_locode_name`        | The origin port name.                                     |
| `to_locode_locode`        | The destination port locode.                              |
| `to_locode_name`          | The destination port name.                                |
| `origin_city_name`        | The origin city name.                                     |
| `origin_city_locode`      | The origin city locode.                                   |
| `destination_city_name`   | The destination city name.                                |
| `destination_city_locode` | The destination city locode.                              |
| `url`                     | The URL of the rate details.                              |
| `shipper`                 | The name of the shipper company.                          |
| `forwarder`               | The name of the forwarder company.                        |
| `carrier`                 | The SCAC code of the Carrier Company.                     |
| `service`                 | The name of the service. Examples: AW, SR, FT, ST, N.     |
| `commodity`               | The name of the Commodity.                                |
| `booking_url`             | The URL to the booking page.                              |
| `valid_from`              | The rate validity_from date.                              |
| `valid_to`                | The rate validity_to date.                                |
| `container_type`          | The type of the container. Options: 20DC, 40DC, and 40HC. |
| `freight_rate`            | The freight rate.                                         |
| `contract_rate`           | The contract rate.                                        |
| `spot_rate`               | The spot rate.                                            |
| `usa_rate_filed`          | The USA rate filed.                                       |
| `space_guarantee`         | The space guarantee.                                      |
| `note`                    | The note.                                                 |
| `internal_id`             | The internal ID.                                          |
| `rate_sheet`              | The rate sheet.                                           |
| `from_locode`             | The origin port locode.                                   |
| `to_locode`               | The destination port locode.                              |
| `origin_city`             | The origin city.                                          |
| `destination_city`        | The destination city.                                     |

## Python code example

```python
import requests

# Define the endpoint URL
url = "https://coreapi.shipangel.ai/rates"

# Define the request parameters
params = {
    "rate_sheet__client__client_name__icontains": "example_company",  # Optional: case-insensitive text within the client_name
    "container_type": "40DC",                                         # Optional: type of the container
    "rate_sheet__valid_from__gte": "2023-01-01",                      # Optional: ratesheet validity_from date greater than or equal to
    "valid_from__lte": "2024-01-01"                                   # Optional: rate validity_from date less than or equal to
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
const url = "https://coreapi.shipangel.ai/rates";

// Define the request parameters
const params = {
  rate_sheet__client__client_name__icontains: "example_company", // Optional: case-insensitive text within the client_name
  container_type: "40DC", // Optional: type of the container
  rate_sheet__valid_from__gte: "2023-01-01", // Optional: ratesheet validity_from date greater than or equal to
  valid_from__lte: "2024-01-01", // Optional: rate validity_from date less than or equal to
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
    "client_name": "Example Company",
    "client_id": 456,
    "rate_sheet_file_name": "example_ratesheet.xlsx",
    "from_locode_locode": "USNYC",
    "from_locode_name": "New York",
    "to_locode_locode": "HKHKG",
    "to_locode_name": "Hong Kong",
    "origin_city_name": "New York",
    "origin_city_locode": "USNYC",
    "destination_city_name": "Hong Kong",
    "destination_city_locode": "HKHKG",
    "url": "https://coreapi.shipangel.ai/rates/123",
    "shipper": "Example Shipper",
    "forwarder": "Example Forwarder",
    "carrier": "ABC",
    "service": "AW",
    "commodity": "Electronics",
    "booking_url": "https://example.com/booking",
    "valid_from": "2023-01-01",
    "valid_to": "2023-12-31",
    "container_type": "40DC",
    "freight_rate": 1500,
    "contract_rate": true,
    "spot_rate": false,
    "usa_rate_filed": true,
    "space_guarantee": 10,
    "note": "Example note",
    "internal_id": "ID123",
    "rate_sheet": "Ratesheet 123",
    "from_locode": "USNYC",
    "to_locode": "HKHKG",
    "origin_city": "New York",
    "destination_city": "Hong Kong"
  }
]
```

## Error Response

If the user is not present in the database, the response is as follows:

```json
{
  "error": "Unknown User"
}
```

If no ratesheet is found, the response is as follows:

```json
{
  "error": "No rates in the current user's company"
}
```
