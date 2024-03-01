---
sidebar_position: 11
---

# Get RateSheetAttribute Items

You can retrieve RateSheetAttribute items using the `GET /ratesheet_attributes` endpoint.

## Query Parameters

| Parameter         | Type | Description                                      |
| :---------------- | :--- | :----------------------------------------------- |
| `name__icontains` | Text | Filter by case-insensitive text within the name. |
| `text__icontains` | Text | Filter by case-insensitive text within the text. |
| `attribute_type`  | Text | Filter by the type of the attribute.             |

## Response Fields

| Field            | Description                                             |
| :--------------- | :------------------------------------------------------ |
| `id`             | The unique identifier of the ratesheet attribute.       |
| `url`            | The URL of the ratesheet attribute.                     |
| `name`           | The name of the ratesheet attribute.                    |
| `attribute_type` | The type of the ratesheet attribute.                    |
| `text`           | The description of the ratesheet attribute.             |
| `internal_id`    | The internal identifier of the ratesheet attribute.     |
| `commodity`      | The commodity of the ratesheet attribute.               |
| `container_type` | The type of container of the ratesheet attribute.       |
| `rate_sheet`     | The rate sheet of the ratesheet attribute.              |
| `from_locode`    | The origin port locode of the ratesheet attribute.      |
| `to_locode`      | The destination port locode of the ratesheet attribute. |

## Python Code Example

```python
import requests

# Define the endpoint URL
url = "https://api.example.com/ratesheetattributes"

# Define the request parameters
params = {
    "name__icontains": "Attribute A",
    "attribute_type": "Type A"
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
const url = "https://api.example.com/ratesheetattributes";

// Define the request parameters
const params = {
  name__icontains: "Attribute A",
  attribute_type: "Type A",
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

```json
[
  {
    "id": 1,
    "url": "https://api.example.com/ratesheetattributes/1",
    "name": "Attribute A",
    "attribute_type": "Type A",
    "text": "Description of Attribute A",
    "internal_id": "ATTR001",
    "commodity": "General Cargo",
    "container_type": "40HC",
    "rate_sheet": "Example Rate Sheet",
    "from_locode": "USNYC",
    "to_locode": "HKHKG"
  }
]
```
