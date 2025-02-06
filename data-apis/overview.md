---
description: Overview of Data APIs with links to full documentation
icon: server
---

# Overview

Verida supports a network of decentralized, confidential APIs to simplify access to data stored within decentralized accounts on the Verida Network.

{% hint style="info" %}
Quick links:

* [Developer Console](https://admin.verida.ai/)
* [User Data API Documentation](https://user-apis.verida.network/)
* [Postman API](https://github.com/verida/data-connector-server/tree/develop/postman/collections)
{% endhint %}

These APIs enable developers to enable their third party applications to access the following services for a given Verida Account:

1. [Databases](https://user-apis.verida.network/#27038fc3-3555-4fd7-a689-6763a69881b1)
   1. [Query a user database](https://user-apis.verida.network/#934196b1-7136-4f27-a593-0750bcfe6fa9)
   2. [Fetch a database record](https://user-apis.verida.network/#e4408ed9-1e13-495b-810b-4b4ded8f3eb0)
   3. [Watch (live stream) changes to a database](https://user-apis.verida.network/#13505bf6-d366-49f7-bdfa-71a31275c4ee)
2. [Datastores](https://user-apis.verida.network/#fc5afd3f-34d1-4239-898f-07a12f52a77b)&#x20;
   1. [Query a user datastore](https://user-apis.verida.network/#499008b7-333a-4e61-bb86-1f96e6eda966)
   2. [Fetch a datastore record](https://user-apis.verida.network/#801cdf87-30f2-4dbb-ac84-e18d9d1ab3df)
   3. [Watch (live stream) changes to a datastore](https://user-apis.verida.network/#801cdf87-30f2-4dbb-ac84-e18d9d1ab3df)
3. [Large Language Models (Artificial Intelligence)](https://user-apis.verida.network/#e48b027d-7ad4-447a-8795-3398bbeee421)
   1. [Basic prompt](https://user-apis.verida.network/#e33184e6-5685-4c83-93b9-1d12d1349d7c)
   2. [Personal prompt](https://user-apis.verida.network/#61bf5cf2-cb2e-43af-b592-f89d0b0d291a)

These APIs are currently read only, but will be expanded in the future to support:

1. Writing data
2. Accessing third party services (ie: send an email, order an Uber, send a Telegram message)

### Postman API's

If you are familiar with Postman, you can load our pre-built [Postman API's](https://github.com/verida/data-connector-server/tree/develop/postman/collections) to easily access the Verida API's from your local machine.

### Developer Console

You can obtain an auth token for a Verida account within the [Developer Console](https://admin.verida.ai/) and use the Sandbox to make API requests within your browser to learn how the various endpoints work with real data.

### Hot Loading User Data

User data is "hot loaded" onto a confidential compute node on-demand. Within the secure enclave, user data is syncronized from the Verida network, decrypted and then loaded into memory for rapid access via API endpoints.

User data is then processed and made available in a variety of different ways:

* Traditional database queries
* Keyword search with ranking, filtering etc.
* AI prompt with RAG access to user data

{% hint style="info" %}
In the future, we plan to expand the types of user data services available. Feel free to request additional types of data services that will help make your application development easier.
{% endhint %}

User Data remains in memory on the compute node while a user (or authorized application) is actively making API requests. If there are no requests for 30 minutes, the data in memory will be deleted and need to be hot-loaded again in the future.
