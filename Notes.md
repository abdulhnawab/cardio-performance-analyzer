

# Key Terms:
**Category:** The category you chose for your application
**Club:** Will show if you have a club associated with your application
**Client ID:** Your application ID
**Client Secret:** Your client secret (please keep this confidential)
**Access token:** Your access token, which will change every six hours (please keep this confidential)
**Your Refresh token:** The token you will use to get a new access token (please keep this confidential)
**Rate limits:** Your current rate limit
**Authorization Callback Domain:** When building your app, change “Authorization Callback Domain” to localhost or any domain. When taking your app live, change “Authorization Callback Domain” to a real domain.

It's been a while since I've programmed, so I needed a refresher on how APIs worked, here are some notes
# Making Requests Against an API

## Definition
- **Making a request against an API**: your program sends a structured message to another piece of software (usually a server), asking it to do something or return data.
- The server sends back a **response**.
- **"Against"** is developer slang for "directed at" or "targeting." People also say "hitting" or "calling" an API.

## Analogy: a restaurant
| Restaurant | API |
|---|---|
| Menu | API documentation (what you can ask for, and how) |
| Your order | Request |
| Kitchen | Server (its inner workings stay hidden) |
| Dish served | Response |

> You don't need to know how the kitchen cooks. You only need to order in a form the waiter understands.

## Parts of a request (HTTP/REST APIs)
- **Method**: the kind of action
  - `GET`: read data
  - `POST`: create something
  - `PUT` / `PATCH`: update something
  - `DELETE`: remove something
- **URL / endpoint**: where to send it and which resource you want
  - e.g. `https://api.github.com/users/octocat`
- **Headers**: extra details, often authentication and data format
  - e.g. `Authorization: Bearer <token>`, `Content-Type: application/json`
- **Query parameters**: options added to the end of the URL
  - e.g. `?page=2&limit=10`
- **Body**: the data you're sending (mostly for `POST` / `PUT`)
  - e.g. `{"name": "New repo"}`

## Parts of a response
- **Status code**: a number saying how it went
  - `200` OK
  - `201` Created
  - `400` Bad request (your mistake)
  - `401` Unauthorized (not authenticated)
  - `404` Not found
  - `500` Server error
- **Headers**: details about the response
- **Body**: the data itself, usually JSON

## Example

### Terminal (curl)
```bash
curl https://api.github.com/users/octocat
```

### Response (excerpt)
```json
{ "login": "octocat", "name": "The Octocat", "public_repos": 8 }
```

### Python
```python
import requests

r = requests.get("https://api.github.com/users/octocat")
print(r.status_code, r.json()["name"])
```

## Side note
- "API" also covers libraries and operating-system interfaces, where a "request" is just a function call.
- In everyday use, "making a request against an API" almost always means an **HTTP request to a web API**.

# OAuth Tokens
- To be continued...