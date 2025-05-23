---
description: Learn how to generate an authentication token to access user data
icon: lock-keyhole
---

# Authentication

This guide explains how to authenticate users in your application to obtain an `auth_token`, and make API requests to Verida’s services.

## Overview

To access user data via Verida APIs, you must include a valid `auth_token` in every request. This token can be generated using Verida's authorization endpoints and stored securely by your application for future requests.

### Quick Start Examples

1. **Run the Verida App Connect Example:**
   * You can clone and run the [Verida App Connect Example](https://github.com/verida/app-connect-example) locally to test the authentication flow.
   * Inspect the source code to understand how authorization is integrated and how the `auth_token` is handled.
2. **Generate an Auth Token from the** [**Developer Console**](https://admin.verida.ai/)**:**
   * Sign in to the Verida AI Developer Console and open the [Sandbox](https://admin.verida.ai/sandbox).
   * [Generate an Auth Token](https://admin.verida.ai/sandbox/generate-token) in the Sandbox for quick testing and to explore scopes.

***

### Connection Flow

Below is a typical flow when integrating your application with Verida AI:

1. **Generate an authentication request URL**
   * Include the scopes you require as well as the `redirectUrl` for successful authentication.
   * The easiest way to generate an authentication URL is via the [#developer-sandbox](developer-console.md#developer-sandbox "mention") and then edit the `redirectUrl`
2. **Redirect the user to the authentication request URL**
   * The user is prompted to grant or deny your application access.
3. **User grants access and is redirected back**
   * If the user grants access, they are redirected to your specified `redirectUrl` with an `auth_token` in the query parameters.
4. **Store the `auth_token`**
   * Your application should save the token securely, either linked to the user’s account in your database or in the user’s local browser storage.
5. **Make requests to Verida APIs**
   * Include the token in the `Authorization` header for all subsequent calls to Verida’s APIs.

***

### Display the Verida Connect Button

You can embed a **Connect** button in your UI with the authentication URL as the link. When clicked, it sends users to the Verida authentication flow.

<figure><img src="https://assets.verida.io/auth/Connect-Verida.png" alt=""><figcaption></figcaption></figure>

```html
<a href="${authenticationURL}" id="connectButton" class="verida-connect">
  <img src="https://assets.verida.io/auth/Connect-Verida.png" />
</a>
```

Replace `${`authenticationURL`}` with the URL generated in the previous step.

***

### Handle an Authentication Response

Once the user grants your application access, they will be redirected to the `redirectUrl` you specified with an `auth_token` query parameter.

Example of how to capture the `auth_token` in TypeScript:

```ts
const currentUrl = new URL(window.location.href);
const authToken = currentUrl.searchParams.get("auth_token");

if (authToken) {
    // Save the token, e.g. in localStorage or your application database
    localStorage.setItem("veridaAuthToken", authToken);
    
    // You can now use this token to make requests to Verida APIs
}
```

***

***

### Next Steps

* **Explore Additional Scopes**: Visit [Verida’s Scopes API](https://api.verida.ai/api/rest/v1/auth/scopes) for a comprehensive list of available scopes.
* **Advanced Use Cases**: Consider reading more about Verida’s data storage, encryption, and decentralized identity solutions to fully leverage the ecosystem.
* **Production Deployment**: If you’re planning a production rollout, ensure you use secure storage for the `auth_token`.
