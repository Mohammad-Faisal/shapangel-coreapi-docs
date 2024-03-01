---
sidebar_position: 1
---

# Getting Started

To Get started by you need to get your credentials.
Get your username and password from `admin@shipangel.com`

## Authentication

We use `Basic Auth` for authentication.

For creating a token you have to encode `username:password` in base64. To do that, go to your terminal encode your username and password like the following

```bash
echo -n "username:password" | base64
```

You will get a token in response. Use this token in the header with `Authorization: Bearer <token>`

An example of a request with a token in the header

```bash
curl -X GET "https://coreapi.shipangel.ai/rates" -H "Authorization: Bearer <token>"
```

Also you can try out teh API in our [Swagger](https://coreapi.shipangel.ai/swagger-ui/) documentation.
