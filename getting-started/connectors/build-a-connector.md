---
icon: pencil
description: Get started by building a new API Connector
---

# Build a Connector

We actively encourage the development of any new data providers that expand the available API's users can connect to pull their personal data.

You can browse the [open issues for new connectors](https://github.com/verida/data-connector-server/issues?q=is%3Aissue+is%3Aopen+label%3Anew-connector).

Key terms:

1. **Provider:** A data provider object (ie: `facebook`) that manages a user authenticating with the provider to establish a connection.
2. **Connection:** A specific connection that a user has made with a provider. Connections are stored in a user's Verida Vault.
3. **Handler:** Providers have multiple handlers (ie: the `google` provider has handlers `gmail`, `youtube`) that manage specific configuration options and performs the necessary syncronization
4. **Schema:** Syncronized data must be mapped to a relevant schema, for instance the [Gmail handler](https://github.com/verida/data-connector-server/blob/main/src/providers/google/gmail.ts) syncronizes data to the [Email schema](https://common.schemas.verida.io/social/email/v0.1.0/schema.json). The [serverconfig.example.json](https://github.com/verida/data-connector-server/blob/main/src/serverconfig.example.json#L26) file lists the standard schemas.

## Getting Setup

You will need to first setup your environment by running the [Data Connector Server](https://github.com/verida/data-connector-server) on your local machine:

```bash
git clone https://github.com/verida/data-connector-server.git
cd data-connector-server
yarn
cp serverconfig.example.json serverconfig.local.json
```

You will need to update your local configuration variables:

* **accessCheckEnabled:** false
* **testVeridaKey:** Create a new Verida account using the Verida Wallet

And then start the server:

```bash
yarn run dev
```

You can now open the developer admin interface at [https://localhost:5021/](https://localhost:5021/).

## Basic Structure

A data connector is made up of the core `provider`class and then one or more `handler`classes. For example, for Google we have a [Google Provider](https://github.com/verida/data-connector-server/blob/main/src/providers/google/index.ts) and then a [Gmail handler](https://github.com/verida/data-connector-server/blob/main/src/providers/google/gmail.ts), [Youtube Favourite handler](https://github.com/verida/data-connector-server/blob/main/src/providers/google/youtube-favourite.ts), [Youtube Post handler](https://github.com/verida/data-connector-server/blob/main/src/providers/google/youtube-post.ts) etc.

It's strongly recommended to copy an existing connector as a starting point and then update the authentication and API code to suit your new connector. Similarly, it's strongly recommended to copy an existing handler that matches the data schema you are populating. ie: If it's a social media platform and you are saving social media posts, start with the [Youtube Post handler](https://github.com/verida/data-connector-server/blob/main/src/providers/google/youtube-post.ts).

### **Provider Class**

Here are the key steps for implementing your provider class:

1. Create `src/providers/<provider-name>/index.ts` extending [BaseProvider](https://github.com/verida/data-connector-server/blob/main/docs/src/providers/BaseProvider.ts)
2. Create `assets/<provider-name>/icon.png` with the official icon for the data connector. Must be 256x256 pixels.
3. Create an exported Typescript interface called `ConfigInterface` that defines the configuration options available for the API.

**Other considerations:**

1. The authentication must use `passport-js` if an existing authentication module exists.
2. The official npm package of the API in question must be used if it exists.
3. There should be no console output, instead use `log4js` with sensible logging (`trace`, `debug`, `info`, `error`)
4. Use appropriate Verida data schemas if they exist (see list in [serverconfig.example.json](https://github.com/verida/data-connector-server/blob/main/src/serverconfig.example.json)).
5. Do NOT commit a PR with any API keys, accessTokens or other secrets!

### **Handler Class**

The data source handler must populate the appropriate schema with relant fields sourced from the API. Each handler typically is responsible for one data schema. There are exceptions to this rule, for example a chat application where a handler may populate the `chat group` and the `chat message`schemas in the one handler.

While the fields may vary, at a minimum the handler must populate the following fields:

* `_id` - A unique ID of this record that includes the provider name, profile identifier and the item identifier. This guarantees uniqueness even if the user connects the same source twice. Use `Handler.buildItemId(itemId: string)` to build the `_id` correctly.
* `name` - A human readable name that best represents the record
* `sourceApplication` - URL of the application the data was sourced from. Remove any `www` prefix. Use `https` if available.
* `sourceId` - Unique ID of the record sourced from the API
* `sourceData` - Full, unaltered JSON of the data retreived from the API. This allows a future upgrade path to add more data into the schema from the original data.
* `insertedAt` - Date/time the data was inserted. If not available in the API, use another date/time that is an approximation, or worst case scenario use the current date/time.

Some common optional fields include:

* `uri` - A URL to view the pi
* `icon` - A small icon representing the data
* `summary` - A brief summary of the recrod
* `uri` - A public link to the unique record in the application (ie: Tweet URL) **Token Expiry / Refresh Tokens**

It's essential handlers catch any errors relating to token expiry and handles them appropriately:

1. Expired access token, refresh token available. Obtain a new access token and call `provider.updateConnection()` to set the new access token, which will then be automatically saved
2. Expired refresh token. Throw a TokenExpiredError()

### **Configuration**

You must create an entry in [src/serverconfig.json](https://github.com/verida/data-connector-server/blob/main/docs/src/serverconfig.json) for the provider that provides the default configuration for the data connector.

## Managing Sync Position

Your connector and handlers must track the progress of the sync to ensure that if something goes wrong or the sync is stopped for any reason, it can pickup where it left off without any issues.

Typically the sync does the following:

1. Does an initial sync of all available data
2. Does a catch-up sync of new data

The sync process should always sync in batches, with a configurable batch size, to allow the sync manager to start / stop the sync as required.

There is an [ItemsRangeTracker helper class](https://github.com/verida/data-connector-server/blob/main/src/helpers/itemsRangeTracker.ts) used by many of the existing handlers. This class is designed to track the sync progress within a known set of record identifiers (or timestamps). It supports importing the current sync position from a saved string in the user's database, and exporting the current sync position for saving in the user's database.

It supports `updateRange`and `completedRange`methods that update the sync status when a range of records has completed processing.

{% hint style="info" %}
You can see ItemsRangeTracker being used in the [Gmail handler](https://github.com/verida/data-connector-server/blob/main/src/providers/google/gmail.ts) and [Telegram Chat Message handler](https://github.com/verida/data-connector-server/blob/main/src/providers/telegram/chat-message.ts), among others.&#x20;
{% endhint %}

## Provider Options

Handlers can provide configurable options that a user can modify. For example, the [Telegram Chat Message handler](https://github.com/verida/data-connector-server/blob/41dbec1a51e4e60468c4c130c99c2b4498822130/src/providers/telegram/chat-message.ts#L46) allows a user to specify what types of chat messages are syncronized (ie: Private, Secret, Basic etc.).

Ensure your handler specfies appropriate default values for all options as there is the user interface for users to select these options is not yet available.

## Command Line Tools

When building your own connector, it can be very helpful to use the command line tools to connect your new provider, manually sync data, reset your connector and show data that has syncronized.

View all available commands:

```bash
yarn run cli --help
```

Outputs:

```
Commands

  Connect         Connect to a third party data provider and save the credentials into  
                  the Verida: Vault context                                             
  Sync            Sync to a third party data provider and save the credentials into the 
                  Verida: Vault context                                                 
  Data            Show data for a given schema                                          
  ResetProvider   Clear all the data and reset sync positions for a provider            
  Connections     Show data for a given schema
```

## Unit Tests

You must implement unit tests in the director `/test/<provider-name>/<handler-name>.ts` file that contains appropriate unit tests that demonstrates successful fetching of data, successful handling of API errors and any other relevant edge cases.

When running the tests, you will need to ensure your `serverconfig.local.config` has `verida.testVeridaKey`set with the seed phrase of a Verida Account that will be storing your user data.

Your test Verida Account may have multiple connections to the same provider. In that case you can specify a specific providerId when running unit tests `--providerId=<12345>` .

## Documentation

Each data source provider must contain the following:

1. `src/providers/<provider-name>/README.md` containing:
   1. Instructions on how to obtain any necessary API keys for the server
   2. Instructions on how to configure the provider
   3. Any limitations of the provider (ie: Only fetches maximum of 1,000 records)
   4. Any issues where the data provided doesn't exactly match the schema
   5. Details of any new schemas created to support this API connector or modifications to existing schemas (including a link to a PR that contains the proposed schema changes in the [@verida/schemas-common](https://github.com/verida/schemas-common) repo)
   6. Details of any future improvements or features that could be considered
   7. Details of any performance considerations
   8. Details of any known issues with the data source API being used
