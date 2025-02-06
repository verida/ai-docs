---
description: Learn about all the available scopes for accessing user data
icon: shield-check
coverY: 0
layout:
  cover:
    visible: false
    size: full
  title:
    visible: true
  description:
    visible: true
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
---

# Scopes

Verida provides a robust and granular permission model to control access to user data and APIs. This document summarizes **all available scopes**, how they are organized, and how to use them in your application.

### Scope Types

There are three main categories of scopes:

1. **API Scopes** (`api:`)
   * Provide access to specific Verida API endpoints (e.g., LLM prompts, universal search).
2. **Database Scopes** (`db:`)
   * Grant read, write, and delete access to a **specific database** within Verida.
3. **Datastore Scopes** (`ds:`)
   * Grant read, write, and delete access to a **specific datastore** (structured data) within Verida.

***

### 1. API Scopes

**API scopes** provide access to particular operations or specialized APIs within the Verida ecosystem. These scopes have a number of **credits** that are consumed when these API endpoints are invoked.

Below is a breakdown by functionality:

#### 1.1 AI Scopes

* **`api:llm-prompt`**\
  Allows running a Large Language Model (LLM) prompt **without** access to user data.
* **`api:llm-agent-prompt`**\
  Allows running a Large Language Model **agent** prompt **with** access to user data.
* **`api:llm-profile-prompt`**\
  Allows running an LLM prompt to generate a profile **based on user data**.

#### 1.2 Search Scopes

* **`api:search-universal`**\
  Perform a keyword-based search **across all user data**.
* **`api:search-ds`**\
  Perform a keyword-based search **across a specific datastore**.
* **`api:search-chat-threads`**\
  Perform a keyword-based search **across all chat threads**.

#### 1.3 Database Operations (API Endpoint)

* **`api:db-get-by-id`**
  * **Endpoint:** `GET /db/$dbName/$id`
  * Allows retrieving a record by ID from a **specific database**.
* **`api:db-create`**
  * **Endpoint:** `POST /db/$dbName`
  * Allows creating a new record in a **specific database**.
* **`api:db-update`**
  * **Endpoint:** `PUT /db/$dbName/$id`
  * Allows updating an existing record in a **specific database**.
* **`api:db-query`**
  * **Endpoint:** `POST /db/query/$dbName`
  * Allows querying a **specific database**.

#### 1.4 Datastore Operations (API Endpoint)

* **`api:ds-get-by-id`**
  * **Endpoint:** `GET /ds/$dsUrlEncoded/$id`
  * Retrieve a record by ID from a **specific datastore**.
* **`api:ds-create`**
  * **Endpoint:** `POST /ds/$dsUrlEncoded`
  * Create a new record in a **specific datastore**.
* **`api:ds-update`**
  * **Endpoint:** `PUT /ds/$dsUrlEncoded/$id`
  * Update an existing record in a **specific datastore**.
* **`api:ds-query`**
  * **Endpoints:**
    * `POST /ds/query/$dsUrlEncoded` (query a datastore)
    * `GET /ds/watch/$dsUrlEncoded` (subscribe to datastore changes)
  * Query or watch a **specific datastore**.
* **`api:ds-delete`**
  * **Endpoint:** `DELETE /ds/$dsUrlEncoded/$id`
  * Delete a record from a **specific datastore**.

***

### 2. Database Scopes (`db:`)

When requesting database-level access, your application must specify the permission type and the database name. The permissions are:

* **`r`**: Read-only
* **`rw`**: Read and write
* **`rwd`**: Read, write, and delete

A typical database scope looks like:

```
cssCopydb:{permission}:{databaseName}
```

For example:

* **`db:r:file`**
  * **Read-only** access to the `file` database.
* **`db:rw:file`**
  * **Read and write** access to the `file` database.
* **`db:rwd:file`**
  * **Read, write, and delete** access to the `file` database.

> **Note**: The `dbName` often corresponds to an internal Verida database identifier (e.g., `file`), but it can vary depending on the specific database you want to access.

***

### 3. Datastore Scopes (`ds:`)

Similar to databases, **datastore scopes** define the level of access to structured data by referencing a **schema URL** (or a **short-hand** for common schemas). Permissions mirror database scopes:

* **`r`**: Read-only
* **`rw`**: Read and write
* **`rwd`**: Read, write, and delete

#### 3.1 Datastore Scope Format

```
ds:{permission}:{base64EncodedSchemaUrl}
```

where:

* `base64EncodedSchemaUrl` is the base64-encoded URL of the datastore schema, or a **short-hand** if it’s a well-known schema.

For example, the **Files** datastore schema:

```
https://common.schemas.verida.io/file/v0.1.0/schema.json
```

Base64-encoded, it might look like:

```
aHR0cHM6Ly9jb21tb24uc2NoZW1hcy52ZXJpZGEuaW8vZmlsZS92MC4xLjAvc2NoZW1hLmpzb24=
```

Hence, read-only scope for that datastore:

```
ds:r:base64/aHR0cHM6Ly9jb21tb24uc2NoZW1hcy52ZXJpZGEuaW8vZmlsZS92MC4xLjAvc2NoZW1hLmpzb24=
```

> **Tip**: You can generate base64 values using:
>
> * `btoa()` in the browser
> * `Buffer.from("http://...").toString("base64")` in Node/TypeScript

#### 3.2 Datastore Shortcuts

Verida provides **short-hand** references for commonly used datastores. In these cases, you can simply specify the short name instead of the base64-encoded URL. For instance:

| Shortcut              | Description                                   |
| --------------------- | --------------------------------------------- |
| `social-following`    | Social media following (e.g., Facebook pages) |
| `social-post`         | Social media posts                            |
| `social-email`        | Emails                                        |
| `favourite`           | Favourites (e.g., liked videos, bookmarks)    |
| `file`                | Files (e.g., documents)                       |
| `social-chat-group`   | Chat groups (e.g., Telegram groups)           |
| `social-chat-message` | Chat messages (e.g., Telegram messages)       |
| `social-calendar`     | Calendars (e.g., Personal Google Calendar)    |
| `social-event`        | Calendar events (e.g., Meeting with Jane)     |

**Examples with Shortcuts**

* **`ds:r:file`**\
  Read-only access to the **Files** datastore.
* **`ds:rw:social-following`**\
  Read and write access to the **Social Following** datastore.
* **`ds:rwd:social-event`**\
  Read, write, and delete access to the **Social Event** datastore.

***

### Complete Scope List

Below is a combined list of all scopes you may encounter or request:

#### API Scopes

1. **LLM Scopes**
   * `api:llm-prompt`
   * `api:llm-agent-prompt`
   * `api:llm-profile-prompt`
2. **Search Scopes**
   * `api:search-universal`
   * `api:search-ds`
   * `api:search-chat-threads`
3. **Database API**
   * `api:db-get-by-id`
   * `api:db-create`
   * `api:db-update`
   * `api:db-query`
4. **Datastore API**
   * `api:ds-get-by-id`
   * `api:ds-create`
   * `api:ds-update`
   * `api:ds-query`
   * `api:ds-delete`

#### Database Scopes (`db:`)

* **`db:r:{databaseName}`**
* **`db:rw:{databaseName}`**
* **`db:rwd:{databaseName}`**

Examples:

* `db:r:file`
* `db:rw:file`
* `db:rwd:file`

#### Datastore Scopes (`ds:`)

* **`ds:r:{datastoreShortcutOrBase64Url}`**
* **`ds:rw:{datastoreShortcutOrBase64Url}`**
* **`ds:rwd:{datastoreShortcutOrBase64Url}`**

Common shortcuts include:

* `social-following`, `social-post`, `social-email`, `favourite`, `file`, `social-chat-group`, `social-chat-message`, `social-calendar`, `social-event`

Examples:

* `ds:r:file`
* `ds:rw:social-post`
* `ds:rwd:social-event`
* `ds:r:base64/aHR0cHM6Ly9jb21tb24u...` (if using a custom schema URL)

***

### Usage and Best Practices

1. **Request Only Needed Scopes**
   * Align the scopes with the data and endpoints your application genuinely requires. Minimizing scopes reduces security risks and simplifies user acceptance.
2. **Explain Scopes to Users**
   * Provide a clear explanation during the consent flow about why you need each scope. This transparency fosters trust.
3. **Store Tokens Securely**
   * Whether you are using a database or localStorage, always handle tokens and granted scopes in a secure manner.
4. **Check for Scope Changes**
   * The Verida ecosystem may add or update scopes. Always verify the latest scope list from the [Scopes API](https://api.verida.ai/api/rest/v1/auth/scopes) or developer documentation.

***

### Further Resources

* **Scopes API**:\
  [https://api.verida.ai/api/rest/v1/auth/scopes](https://api.verida.ai/api/rest/v1/auth/scopes)\
  Fetch a real-time list of valid scopes, including new or updated scopes.
* **Developer Console**:\
  [https://admin.verida.ai/](scopes.md#scope-types)\
  An easy to use interface to generate authorization requests and use APIs.
* **Verida GitHub**:\
  [https://github.com/verida/](https://github.com/verida/)\
  Explore sample applications and open-source libraries.

***

By combining these scopes effectively, you can harness the power of Verida’s decentralized data ecosystem while respecting user consent and data security.&#x20;
