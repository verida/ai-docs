---
icon: rectangles-mixed
---

# Other Endpoints

### Connection Profiles

* **HTTP Method & Endpoint**: `GET /connections/profiles`
* **Summary**: Fetch the profile of a connection (ie: "google" or "telegram").
* **Credit Usage**: **0 credits**
* **Scope:** `api:connections-profiles`
*   **Example**:

    ```bash
    # dsUrlEncoded is typically the base64-encoded schema URL or a known shortcut
    curl -X GET "https://api.verida.ai/api/rest/v1/connections/profiles" \
         -H "Authorization: Bearer YOUR_AUTH_TOKEN"
    ```
* **Full Documentation**: [Connections / Profiles](https://user-apis.verida.network/#b6da5446-11cd-4ba5-9652-ba2d646ece1b)

### Connection Status

* **HTTP Method & Endpoint**: `GET /connections/status`
* **Summary**: Access status information on connected third party accounts (ie: Google, Telegram).
* **Credit Usage**: **0 credits**
* **Scope:** `api:connections-status`
*   **Example**:

    ```bash
    # dsUrlEncoded is typically the base64-encoded schema URL or a known shortcut
    curl -X GET "https://api.verida.ai/api/rest/v1/connections/status" \
         -H "Authorization: Bearer YOUR_AUTH_TOKEN"
    ```
* **Full Documentation**: [Connections / Status](https://user-apis.verida.network/#7eb54a98-e90a-4169-ba17-937a4f05eea1)
