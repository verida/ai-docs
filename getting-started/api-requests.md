---
description: Learn how to make an API request
icon: magnifying-glass-chart
---

# API Requests

### Make an API Request

You will need an `auth_token` from a user (see [Authentication](authentication.md)) to make requests to Verida endpoints.

API requests must include the `auth_token`in the `Authorization` header as a **Bearer** token.

```js
const API_ENDPOINT = "https://api.verida.ai/api/rest/v1/auth";
// Obtain token from localstorage (or your own database)
const authToken = localStorage.getItem("veridaAuthToken") || "";

// Example: search/universal endpoint
$.get({
    url: `${API_ENDPOINT}/search/universal?keywords=meeting+agenda`,
    headers: {
        "Authorization": `Bearer ${authToken}`,
        "Content-Type": "application/json"
    },
    success: (response) => {
        console.log(response);
        // Handle the response data
    }
});
```

> **Important:** Ensure you store and handle the `auth_token` securely. Unauthorized access to this token could compromise your application and user data.

{% hint style="info" %}
See the [Broken link](broken-reference "mention") or [API Reference](https://user-apis.verida.network/) to learn more about all the available endpoints
{% endhint %}
