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
   * Include the `scopes` you require as well as the `redirectUrl` for authentication output.
2. **Redirect the user to the authentication request URL**
   * The user is prompted to grant or deny your application access via the Verida Vault web application.
3. **User grants access and is redirected back**
   * If the user grants access, they are redirected to your specified `redirectUrl` with an `auth_token` in the query parameters.
4. **Store the `auth_token`**
   * Your application should save the token securely, either linked to the user’s account in your database or via other usual ways handling auth tokens.
5. **Make requests to Verida APIs**
   * Include the token in the `Authorization` header for all subsequent calls to Verida’s APIs.

***

### Generate an Authentication Request URL

To start the authentication process, build a URL that directs users to Verida’s authentication page on the Verida Vault web app `https://app.verida.ai/auth`. This URL must include several query parameters:

* **`scopes`**: An array of scopes that your application requires. The latest valid scopes can be listed via the [Scopes API](https://api.verida.ai/api/rest/v1/auth/scopes).
* **`payer`**: Specifies who will pay for the API requests made with this auth token. Set this to either `user` or `app`.
* **`appDID`**: Your application Verida DID is required to identify your application. 
* **`redirectUrl`**: The URL in your application that handles a successful user authentication.
* **`state`**: Optionally a state object (stringified) for your own reference (User ID, etc.). The state will not be altered and will be returned to the `redirectUrl` as part of the response.

Below is an example authentication request URL (URL-encoded) that includes three scopes:

```
https://app.verida.ai/auth?scopes=api%3Ads-query&scopes=api%3Allm-agent-prompt&scopes=api%3Allm-profile-prompt&redirectUrl=http%3A%2F%2Flocalhost%3A8080%2F&appDID=did%3Avda%3Amainnet%3A0x8013f9A...086
```

#### TypeScript Example

```ts
// Build authentication URL
const authLink = new URL("https://app.verida.ai/auth");

// Add scopes
authLink.searchParams.append("scopes", "api:ds-query");
authLink.searchParams.append("scopes", "api:llm-agent-prompt");

// Application will pay for API requests
authLink.searchParams.append("payer", "app");

// Your Verida DID identifying your application
authLink.searchParams.append("appDID", "did:vda:mainnet:0x8013f9A...086");

// Add your application URL to handle the response
authLink.searchParams.append("redirectUrl", "https://yourapplication.com/auth-callback");

// An optional state object
authLink.searchParams.append("state", JSON.stringify({ userId: "123" }));

// Redirect user to start the authorization process
window.location.href = authLink.toString();
```

***

### Guidelines on displaying Verida Connect to your users

Similar to a standard OAuth mechanism, provide users with a button to explicitly click to intiate the authentication with Verida. The button would direct the user to the Authentication Request URL generated in the previous step.

The button should include a [Verida logo](https://community.verida.network/verida-overview/brand-assets#download-the-brand-asset-pack) and the label "Connect Verida". The logo, label and color scheme must follow Verida's [branding guidelines](https://community.verida.network/verida-overview/brand-assets).

<figure><img src="https://assets.verida.io/auth/Connect-Verida.png" alt=""><figcaption></figcaption></figure>

In addition to the button, consider explaining to your users the reasons your application needs Verida and how their personal data will be used.

***

### Handle an Authentication Response

Once the user grants your application access, they will be redirected to the `redirectUrl` you specified with an `auth_token` query parameter.

If you passed a `state` in the request, it will be returned with response (successfull or not).

In the case of a non-successful authentication, the redirect URL will contains an `error` and `error_description` query parameters. The values for the `error` parameter are: `access_denied`, `invalid_request` and `server_error`.

TypeScript example of how to capture the `auth_token` and other response elements:

```ts
const currentUrl = new URL(window.location.href);

const authToken = currentUrl.searchParams.get("auth_token");
const state = currentUrl.searchParams.get("state");
const error = currentUrl.searchParams.get("error");

if (authToken) {
  // Save the token securely
  // ...  
  // You can now use this token to make requests to Verida APIs
}

if (error) {
  // Handle the failure of the authentication
}
```

***

### Next Steps

* **Explore Additional Scopes**: Visit [Verida’s Scopes API](https://api.verida.ai/api/rest/v1/auth/scopes) for a comprehensive list of available scopes.
* **Advanced Use Cases**: Consider reading more about Verida’s data storage, encryption, and decentralized identity solutions to fully leverage the ecosystem.
* **Production Deployment**: If you’re planning a production rollout, ensure you use secure storage for the `auth_token` (https-only cookie, your backend database, etc.).
