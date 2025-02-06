---
icon: webhook
---

# Queries

Verida offers a suite of **Query APIs** that enable you to store, query, and manage user data across decentralized databases and datastores, as well as perform advanced searches. This page covers the **Databases** and **Datastores** sections of the Verida User API Reference.

For full technical details, consult the [Verida API Reference Documentation](https://user-apis.verida.network/).

### Table of Contents

1. **Datastores**
   * Get a Record by ID (`api:ds-get-by-id`)
   * Create a Record (`api:ds-create`)
   * Update a Record (`api:ds-update`)
   * Query a Datastore (`api:ds-query`)
   * Watch a Datastore (`api:ds-query`)
   * Delete a Record (`api:ds-delete`)
2. **Databases**
   * Get a Record by ID (`api:db-get-by-id`)
   * Create a Record (`api:db-create`)
   * Update a Record (`api:db-update`)
   * Query a Database (`api:db-query`)

***

### Datastores

Datastores are **schema-based collections** of structured data. Endpoints for datastores operate similarly to databases but typically refer to a **base64-encoded schema URL** or a well-known **shortcut**. Each datastore endpoint requires the relevant **API scope** (e.g., `api:ds-get-by-id`) and uses **1 credit** per request unless otherwise noted.

#### 1. Get a Record by ID

* **HTTP Method & Endpoint**: `GET /ds/{dsUrlEncoded}/{id}`
* **Summary**: Retrieve a specific record by its `id` from a datastore.
* **Credit Usage**: **1 credit**
* **Scope:** `api:ds-get-by-id`
*   **Example**:

    ```bash
    # dsUrlEncoded is typically the base64-encoded schema URL or a known shortcut
    curl -X GET "https://user-apis.verida.network/ds/aHR0cHM6Ly9....json/456" \
         -H "Authorization: Bearer YOUR_AUTH_TOKEN"
    ```
* **Full Documentation**:\
  [Datastore: Get Record by ID](https://user-apis.verida.network/#1664829f-ca3a-4b06-ad0a-bafff48b9495)

***

#### 2. Create a Record

* **HTTP Method & Endpoint**: `POST /ds/{dsUrlEncoded}`
* **Summary**: Insert a new record into the specified datastore.
* **Credit Usage**: **1 credit**
* **Scope:** `api:ds-create`
*   **Example**:

    ```bash
    curl -X POST "https://user-apis.verida.network/ds/aHR0cHM6Ly9.../" \
         -H "Authorization: Bearer YOUR_AUTH_TOKEN" \
         -H "Content-Type: application/json" \
         -d '{
           "key": "value",
           "createdAt": "2025-02-03T12:00:00Z"
         }'
    ```
* **Full Documentation**:\
  [Datastore: Create Record](https://user-apis.verida.network/#7b5b2ebf-6270-4807-8c37-fb9cfe31b946)

***

#### 3. Update a Record

* **HTTP Method & Endpoint**: `PUT /ds/{dsUrlEncoded}/{id}`
* **Summary**: Update an existing datastore record identified by `id`.
* **Credit Usage**: **1 credit**
* **Scope:** `api:ds-update`
*   **Example**:

    ```bash
    curl -X PUT "https://user-apis.verida.network/ds/aHR0cHM6Ly9.../456" \
         -H "Authorization: Bearer YOUR_AUTH_TOKEN" \
         -H "Content-Type: application/json" \
         -d '{
           "updatedKey": "newValue"
         }'
    ```
* **Full Documentation**:\
  [Datastore: Update Record](https://user-apis.verida.network/#847bdc5f-0009-4848-a4df-b91da8d97726)

***

#### 4. Query a Datastore

* **HTTP Method & Endpoint**: `POST /ds/query/{dsUrlEncoded}`
* **Summary**: Run queries (similar to databases) from a datastore.
* **Credit Usage**: **1 credit**
* **Scope:** `api:ds-query`
*   **Example** (Query):

    ```bash
    curl -X POST "https://user-apis.verida.network/ds/query/aHR0cHM6Ly9..." \
         -H "Authorization: Bearer YOUR_AUTH_TOKEN" \
         -H "Content-Type: application/json" \
         -d '{
           "filters": { "key": "value" }
         }'
    ```
* **Full Documentation**:\
  [Datastore: Query](https://user-apis.verida.network/#499008b7-333a-4e61-bb86-1f96e6eda966)

***

#### 5. Query a Datastore

* **HTTP Method & Endpoint**: `GET /ds/watch/{dsUrlEncoded}`
* **Summary**: Subscribe to **real-time updates** from a datastore. This is not a typical HTTP request, it uses _EventSource_ to stream the database changes.
* **Credit Usage**: **1 credit**
* **Scope:** `api:ds-query`
* **Full Documentation**:\
  [Datastore: Watch](https://user-apis.verida.network/#801cdf87-30f2-4dbb-ac84-e18d9d1ab3df)

***

#### 6. Delete a Record

* **HTTP Method & Endpoint**: `DELETE /ds/{dsUrlEncoded}/{id}`
* **Summary**: Remove a record permanently from a datastore.
* **Credit Usage**: **1 credit**
* **Scope:** `api:ds-delete`
*   **Example**:

    ```bash
    curl -X DELETE "https://user-apis.verida.network/ds/aHR0cHM6Ly9.../456" \
         -H "Authorization: Bearer YOUR_AUTH_TOKEN"
    ```

***

### Databases

Database endpoints allow you to work with **traditional, table-like data**. Each endpoint requires an `auth_token` with the relevant **API scope** (e.g., `api:db-get-by-id`) and consumes **1 credit** per request unless otherwise noted.

#### 1. Get a Record by ID

* **HTTP Method & Endpoint**: `GET /db/{dbName}/{id}`
* **Summary**: Fetch a single record from a specific database using its unique `id`.
* **Credit Usage**: **1 credit**
* **Scope:** `api:db-get-by-id`
*   **Example**:

    ```bash
    curl -X GET "https://user-apis.verida.network/db/myDatabase/123" \
         -H "Authorization: Bearer YOUR_AUTH_TOKEN"
    ```
* **Full Documentation**:\
  [Database: Get Record by ID](https://user-apis.verida.network/#e4408ed9-1e13-495b-810b-4b4ded8f3eb0)

***

#### 2. Create a Record

* **HTTP Method & Endpoint**: `POST /db/{dbName}`
* **Summary**: Insert a new record into the specified database.
* **Credit Usage**: **1 credit**
* **Scope:** `api:db-create`
*   **Example**:

    ```bash
    curl -X POST "https://user-apis.verida.network/db/myDatabase" \
         -H "Authorization: Bearer YOUR_AUTH_TOKEN" \
         -H "Content-Type: application/json" \
         -d '{
           "title": "First Entry",
           "content": "Hello World!"
         }'
    ```

***

#### 3. Update a Record

* **HTTP Method & Endpoint**: `PUT /db/{dbName}/{id}`
* **Summary**: Modify an existing record identified by `id` in a specific database.
* **Credit Usage**: **1 credit**
* **Scope:** `api:db-update`
*   **Example**:

    ```bash
    curl -X PUT "https://user-apis.verida.network/db/myDatabase/123" \
         -H "Authorization: Bearer YOUR_AUTH_TOKEN" \
         -H "Content-Type: application/json" \
         -d '{
           "title": "Updated Title",
           "content": "Revised Content"
         }'
    ```

***

#### 4. Query a Database

* **HTTP Method & Endpoint**: `POST /db/query/{dbName}`
* **Summary**: Run queries to filter and retrieve multiple records from the specified database.
* **Credit Usage**: **1 credit**
* **Scope:** `api:db-query`
*   **Example**:

    ```bash
    curl -X POST "https://user-apis.verida.network/db/query/myDatabase" \
         -H "Authorization: Bearer YOUR_AUTH_TOKEN" \
         -H "Content-Type: application/json" \
         -d '{
           "filters": { "status": "active" },
           "limit": 10
         }'
    ```
* **Full Documentation**:\
  [Database: Query](https://user-apis.verida.network/#934196b1-7136-4f27-a593-0750bcfe6fa9)

***

### Best Practices

1. **Secure Your Requests**: Always include the `Authorization: Bearer YOUR_AUTH_TOKEN` header and ensure your application only requests the necessary scopes.
2. **Understand Credit Costs**: Each API call draws from your available credits. Optimize your queries and reduce unnecessary calls.
3. **Use the Right Endpoint**: Databases vs. Datastores have subtle differences. Identify which storage mechanism and endpoint best suit your application.
4. **Leverage Real-Time Updates**: Where possible, use datastore watching (`GET /ds/watch`) to keep application data in sync without continuous polling.
5. **Respect Scope Requirements**: For instance, if you need `api:ds-delete`, your user must grant a scope that allows **delete** access (e.g., `ds:rwd:file`).
