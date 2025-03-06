---
icon: rectangles-mixed
---

# Other Endpoints

### Connection Profiles

* **HTTP Method & Endpoint**: `GET /connections/profiles`
* **Summary**: Fetch the profile of a connection (ie: "google" or "telegram").
* **Credit Usage**: **1 credit**
* **Scope:** `api:connections-profiles`
*   **Example**:

    ```bash
    # dsUrlEncoded is typically the base64-encoded schema URL or a known shortcut
    curl -X GET "https://api.verida.ai/api/rest/v1/connections/profiles" \
         -H "Authorization: Bearer YOUR_AUTH_TOKEN"
    ```
* **Full Documentation**: [Connections / Profiles](https://user-apis.verida.network/#b6da5446-11cd-4ba5-9652-ba2d646ece1b)
