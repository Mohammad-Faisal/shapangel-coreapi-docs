---
sidebar_position: 12
---

# Send Rate Sheet File via E-mail

You can send a rate sheet file via e-mail using the `PUT /send_ratesheet/{filename}` endpoint. Attach the rate sheet as binary in the request.

## Request Example

### cURL Example

```bash
curl --location --request PUT 'http://localhost:8000/send_ratesheet/Ship_Angel_-_Ocean_Rate_Template.xlsx' \
--header 'Content-Type: application/vnd.openxmlformats-officedocument.spreadsheetml.sheet' \
--header 'Authorization: Basic c2hpcGFuZ2VsOlVoaGIzODgyXzgua2xrMQ==' \
--data '@/C:/Users/ze-notebook/Downloads/Ship_Angel_-_Ocean_Rate_Template.xlsx'
```

### Python Example

```python
import requests

# Define the endpoint URL
url = "https://coreapi.shipangel.ai/send_ratesheet/Ship_Angel_-_Ocean_Rate_Template.xlsx"

# Define the request headers
headers = {
    "Authorization":"HEADER_TOKEN",
    "Content-Type": "application/vnd.openxmlformats-officedocument.spreadsheetml.sheet"
}

# Define the request data
data = open("C:/Users/ze-notebook/Downloads/Ship_Angel_-_Ocean_Rate_Template.xlsx", "rb")

# Make the API request
response = requests.put(url, headers=headers, data=data)

# Print the JSON response
print(response.json())
```

### Nodejs Example

```javascript

const axios = require("axios");
const fs = require("fs");

// Define the endpoint URL

const url = "https://coreapi.shipangel.ai/send_ratesheet/Ship_Angel_-_Ocean_Rate_Template.xlsx";

// Define the request headers
const headers

{
  "Authorization":"HEADER_TOKEN",
    "Content-Type": "application/vnd.openxmlformats-officedocument.spreadsheetml.sheet"
}

// Define the request data
const data = fs.createReadStream("C:/Users/ze-notebook/Downloads/Ship_Angel_-_Ocean_Rate_Template.xlsx");

// Make the API request
axios
  .put(url, data, { headers })
  .then((response) => {
    // Print the JSON response
    console.log(response.data);
  })
  .catch((error) => {
    console.error(error);
  });
```

## Response

If the file is not added to the request, the response will be a status 400 (Bad Request) with the following body:

```json
{
  "success": false,
  "message": "Missing file"
}
```

If the message was sent with the file successfully, the response will be a status 200 (Success) with the following body:

```json
{
  "success": true,
  "message": "Message sent successfully"
}
```
