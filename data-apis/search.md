---
icon: magnifying-glass-waveform
---

# Search

Verida’s **Search** APIs let you perform powerful keyword-based searches across multiple data sources. Each search endpoint uses the specified **credit** amount per call.

***

#### 1. Chat Thread Search

* **HTTP Method & Endpoint**: `GET /search/chat-threads`
* **Summary**: Search through **all chat threads** for matching keywords.
* **Credit Usage**: **2 credits**
* **Scope:** `api:search-chat-threads`
*   **Example**:

    ```bash
    bashCopycurl -X GET "https://user-apis.verida.network/search/chat-threads?keywords=urgent" \
         -H "Authorization: Bearer YOUR_AUTH_TOKEN"
    ```
* **Full Documentation**:\
  Search: Chat Threads

***

#### 2. Datastore Search

* **HTTP Method & Endpoint**: `GET /search/ds` or `POST /search/ds`
* **Summary**: Perform a keyword search across **a specific datastore**.
* **Credit Usage**: **1 credit**
* **Scope:** `api:search-ds`
*   **Example**:

    ```bash
    bashCopy# Using GET
    curl -X GET "https://user-apis.verida.network/search/ds?keywords=invoice&datastore=social-email" \
         -H "Authorization: Bearer YOUR_AUTH_TOKEN"
    ```
* **Full Documentation**:\
  Search: Datastore

***

#### 3. Universal Search

* **HTTP Method & Endpoint**: `GET /search/universal`
* **Summary**: Perform a keyword search **across all user data** (datastores, databases, etc.) the user has granted access to.
* **Credit Usage**: **2 credits**
* **Scope:** `api:search-universal`
*   **Example**:

    ```bash
    bashCopycurl -X GET "https://user-apis.verida.network/search/universal?keywords=meeting+agenda" \
         -H "Authorization: Bearer YOUR_AUTH_TOKEN"
    ```
* **Full Documentation**:\
  Search: Universal

## Vector database?

As an AI developer you may be asking, does Verida offer a Vector Database over user data?

We currently don't, because from our testing Vector Databases require more resources to create than a traditional high performance keyword index and produces sub-par results when working with user data.

We are happy to re-assess this if there's a use case that specifically requires a Vector Database.

