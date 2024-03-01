---
sidebar_position: 8
---

# Ratesheets

You can retrieve ratesheets by using the `GET /ratesheets` endpoint.

## Request

### To get ratesheets

```http
GET /ratesheets
```

To get details of a particular ratesheet by its ID

```http
GET /ratesheets/{id}
```

markdown
Copy code

# Ratesheets

You can retrieve ratesheets by using the `GET /ratesheets` endpoint.

## Request

### To get ratesheets

```http
GET /ratesheets
```

To get details of a particular ratesheet by its ID

```http
GET /ratesheets/{id}
```

## Query Parameters

| Parameter                        | Type       | Description                                                                                               |
| :------------------------------- | :--------- | :-------------------------------------------------------------------------------------------------------- |
| `client__client_name__icontains` | `text`     | Case-insensitive text within the client_name of the Company that uploaded the rate sheet (partial match). |
| `file_name__icontains`           | `text`     | Case-insensitive text within the file_name (partial match).                                               |
| `valid_from__gte`                | `DateTime` | Date greater than the "from" validity date.                                                               |
| `valid_from__lte`                | `DateTime` | Date less than the "from" validity date.                                                                  |
| `valid_to__gte`                  | `DateTime` | Date greater than the "to" validity date.                                                                 |
| `valid_to__lte`                  | `DateTime` | Date less than the "to" validity date.                                                                    |
| `app_id`                         | `text`     | Id of the rate sheet in the app.                                                                          |
| `full_data`                      | `Boolean`  | Whether the user wants the full data or not (true or false).                                              |
| `limit`                          | `integer`  | The number of records to return.                                                                          |
| `offset`                         | `integer`  | The number of records to skip.                                                                            |

## Response Fields

The response will contain the following fields:

| Field                  | Type      | Description                             |
| :--------------------- | :-------- | :-------------------------------------- |
| `id`                   | `integer` | The unique identifier of the ratesheet. |
| `ratesheet_header`     | `object`  | The ratesheet header details.           |
| `ratesheet_rates`      | `array`   | The list of rate details.               |
| `ratesheet_surcharges` | `array`   | The list of surcharge details.          |
| `ratesheet_notes`      | `array`   | The list of notes.                      |

## Python code example

```python
import requests

# Define the endpoint URL
url = "https://coreapi.shipangel.ai/ratesheets"

# Define the request parameters
params = {
    "client__client_name__icontains": "example_company",  # Optional: case-insensitive text within the client_name
    "valid_from__gte": "2023-01-01",                      # Optional: date greater than or equal to the "from" validity date
    "full_data": True                                     # Optional: whether to get full data or not
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
const url = "https://coreapi.shipangel.ai/ratesheets";

// Define the request parameters
const params = {
  client__client_name__icontains: "example_company", // Optional: case-insensitive text within the client_name
  valid_from__gte: "2023-01-01", // Optional: date greater than or equal to the "from" validity date
  full_data: true, // Optional: whether to get full data or not
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
    "ratesheet_header": {
      // Ratesheet header details
    },
    "ratesheet_rates": [
      // List of rate details
    ],
    "ratesheet_surcharges": [
      // List of surcharge details
    ],
    "ratesheet_notes": [
      // List of notes
    ]
  }
]
```

If `full_data` is false, the response is as follows:

```json
[
  {
    "id": 123,
    "client_name": "Example Company",
    "url": "https://coreapi.shipangel.ai/ratesheets/123",
    "file_name": "example_ratesheet.xlsx",
    "file_location": "/path/to/example_ratesheet.xlsx",
    "date_created": "2023-01-01T00:00:00Z",
    "date_updated": "2023-01-01T00:00:00Z",
    "valid_from": "2023-01-01T00:00:00Z",
    "valid_to": "2023-12-31T00:00:00Z",
    "note": "Example ratesheet for testing",
    "app_id": "APP123",
    "client": "Example Company"
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
  "error": "No rate sheets in the current user's company"
}
```
