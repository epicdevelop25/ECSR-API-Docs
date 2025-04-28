# Fixing "Token Validation Failed" in ECSR API Requests

Some endpoints require valid CSRF tokens or your request will be rejected with a `Token Validation Failed` error. 

ECSR uses two CSRF values:
- **`X-Csrf-Token` header**
- **`rbxcsrf4` cookie**

This guide walks you through retrieving both values using Python, then demonstrates how to use them in subsequent API calls.

---

## 1. Retrieve CSRF Tokens

To get the CSRF values, make an initial request to any endpoint that returns them, like ``/v2/logout`` or if you prefer, simply call your target endpoint twice. Then extract the values from the first response.

```python
import requests

cookies = {".ROBLOSECURITY": "<YOUR_COOKIE_VALUE>"}

response = requests.post("https://ecsr.io/apisite/v2/logout", cookies=cookies)

csrf_token = response.headers.get("X-Csrf-Token")
csrf_cookie = response.cookies.get("rbxcsrf4")

print(f"X-Csrf-Token: {csrf_token}\nrbxcsrf4 cookie: {csrf_cookie}")
```

**What this does:**
- Sends a POST to `/v2/logout`
- Captures `X-Csrf-Token` from response headers
- Captures `rbxcsrf4` from response cookies

---

## 2. Make Authenticated Requests

Now that you have both CSRF values, include them in your headers and cookies when calling endpoints that require CSRF validation.

```python
import requests

cookies={".ROBLOSECURITY": "<YOUR_COOKIE_VALUE>"}

initial = requests.post("https://ecsr.io/apisite/v2/logout", cookies=cookies)

csrf_token = initial.headers["X-Csrf-Token"]
csrf_cookie = initial.cookies.get("rbxcsrf4")

headers = {"X-Csrf-Token": csrf_token}
cookies = {
    ".ROBLOSECURITY": "<YOUR_COOKIE_VALUE>",
    "rbxcsrf4": csrf_cookie
}
payload = {"usernames": ["Sow"]}

response = requests.post("https://ecsr.io/apisite/users/v1/usernames/users", json=payload, headers=headers, cookies=cookies)

print(response.json())
```

**Expected output:**

```json
{
  "data": [
    {
      "id": 985,
      "name": "Sow",
      "requestedName": "Sow",
      "displayName": null
    }
  ]
}
```
