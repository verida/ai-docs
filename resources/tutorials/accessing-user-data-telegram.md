# Accessing User Data (Telegram)

This tutorial will walk through how to use Verida API's to access user data, with a focus on accessing Telegram data.

{% embed url="https://youtu.be/jPzSWLMVN_4" %}

### Getting started

If you haven't already, register a Verida Account, sign into the [developer-console.md](../../getting-started/developer-console.md "mention") and obtain an Auth token so you can make API requests.

### Making an API requests

Once you have an auth token, you must include it in your API requests.

Here are some examples of API requests to the AI agent endpoint.

**Command line (via curl):**

```bash
curl -X POST -H "Authorization: Bearer <authToken>" "https://api.verida.ai/api/rest/v1/llm/agent" \
  -H "Content-Type: application/json" \
  -d '{}'
```

**Node.js:**

```typescript
const axios = require('axios');

axios({
  method: 'POST',
  url: 'https://api.verida.ai/api/rest/v1/llm/agent',
  data: {},
  headers: {
    'Content-Type': 'application/json',
    'Authorization': 'Bearer <authToken>'
  }
})
.then(res => {
  console.log(res.data)
})
.catch(err => {
  console.error(err)
})
```

{% hint style="info" %}
**Useful resources:**

1. Make example requests with the [Developer Console Sandbox](https://admin.verida.ai/sandbox/api-requests)
2. [API requests documentation](../../getting-started/api-requests.md)
3. [Overview of all API endpoints](../../data-apis/overview.md)
4. [API Reference Documentation](https://user-apis.verida.network/)
{% endhint %}

### Fetching Telegram Data

When a user connects their Telegram account, their groups and messages are syncronized and the data is normalized into common data types. See [data-types.md](../../data-apis/data-types.md "mention") to learn more.

Telegram populates two data schemas:

* Social Chat Group ([view data schema](https://common.schemas.verida.io/social/chat/group/v0.1.0/schema.json))
* Social Chat Message ([view data schema](https://common.schemas.verida.io/social/chat/message/v0.1.0/schema.json))

We need to query these schemas using the [#id-4.-query-a-datastore](../../data-apis/queries.md#id-4.-query-a-datastore "mention") API endpoint.

### List the user's Telegram groups

Let's start with an example to fetch all the Telegram chat groups a user is in. We need to make an API request to the `/ds/query`endpoint (`https://api.verida.ai/api/rest/v1/ds/query/`).

This endpoint takes a schema, in our case we want the social chat group schema ([https://common.schemas.verida.io/social/chat/group/v0.1.0/schema.json](https://common.schemas.verida.io/social/chat/group/v0.1.0/schema.json)), however we don't send the actual schema URL, we base64 encoded it.

**Node.js example:**

```typescript
const axios = require('axios');

const schemaUrl = 'https://common.schemas.verida.io/social/chat/group/v0.1.0/schema.json';
const schemaUrlEncoded = bvoa(schemaUrl);

axios({
  method: 'POST',
  url: `https://api.verida.ai/api/rest/v1/ds/query/${schemaUrlEncoded}`,
  data: {
  "options": {
    "sort": [
      {
        "_id": "desc"
      }
    ],
    "limit": 20
  }
},
  headers: {
    'Content-Type': 'application/json',
    'Authorization': 'Bearer <authToken>'
  }
})
.then(res => {
  console.log(res.data)
})
.catch(err => {
  console.error(err)
})
```

[View the example JSON response of a chat group](../../data-apis/data-examples.md#chat-group).

### List the user's Telegram messages

Let's now fetch all of a user's Telegram messages. Instead of querying the Chat Group datastore, we need to query the Chat Message datastore.

We also want to fetch only telegram messages, so apply a filter:

```typescript
const axios = require('axios');

const schemaUrl = 'https://common.schemas.verida.io/social/chat/message/v0.1.0/schema.json';
const schemaUrlEncoded = bvoa(schemaUrl);

axios({
  method: 'POST',
  url: `https://api.verida.ai/api/rest/v1/ds/query/${schemaUrlEncoded}`,
  data: {
  "query": {
    "sourceApplication": "https://telegram.com"
  },
  "options": {
    "sort": [
      {
        "_id": "desc"
      }
    ],
    "limit": 20
  }
},
  headers: {
    'Content-Type': 'application/json',
    'Authorization': 'Bearer <authToken>'
  }
})
.then(res => {
  console.log(res.data)
})
.catch(err => {
  console.error(err)
})
```

[View the example JSON response for a chat message](../../data-apis/data-examples.md#chat-message).

We can update the `query`to restrict to only include results from:

* A particular group
* Messages sent by me
* Messages sent after Jan 1st 2025

```json
{
    "sourceApplication": "https://telegram.com",
    "groupId": "telegram-456049390--579961374",
    "type": "send",
    "sentAt": {
        "$gte": "2025-01-01"
    }
}
```

### Counting messages or groups

You may want to make requests such as:

1. How many messages sent by a user?
2. How many groups is a user part of?

It is possible to use the `/query` API endpoint and loop through all the pages of data to count, but that is highly inefficient.

This functionality will be coming very shortly with a new `/count` endpoint.&#x20;

### User information

You may want to learn more about a user's profile on Telegram, for example:

1. Is the account verified?
2. Phone number
3. Username
4. Profile pic

This data is currently syncronized, but not available via the API.

This functionality will be coming very shortly with a new `/profile` endpoint











