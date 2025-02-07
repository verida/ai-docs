---
icon: plug
---

# Connectors

Users can connect multiple data sources to their Verida account via the [Verida Vault](../../resources/verida-vault.md). Data is syncronized on demand and stored to the user's encrypted databases on the [Verida Network](https://www.verida.network/).

{% hint style="info" %}
Looking to build your own connector? See our [Build a Connector](build-a-connector.md) getting started guide.
{% endhint %}

## Supported Connectors

1. **Google**
   1. Gmail
      1. Email
   2. Google Calendar
      1. Calendars
      2. Events
   3. Google Drive
      1. Files
   4. Youtube
      1. Following
      2. Likes
      3. Subscriptions
      4. Posted Videos
2. **Telegram**
   1. Groups
   2. Messages

## In Development Connectors

1. Notion
2. Slack
3. Facebook
4. Fireflies
5. Spotify

{% hint style="success" %}
You can view a list of completed, in progress and planned connectors in the [Connectors Roadmap](https://roadmap.verida.ai/)
{% endhint %}

## Connection Framework

Verida's Data Connections framework makes it easy for users to connect and pull their personal data from platforms like Google, Telegram, or Facebook into their private storage. The framework facilitates tasks like signing in, verifying access, and syncing user data from these centralized platforms.

The Verida Data Connection framework source code is open source and [available on GitHub](https://github.com/verida/data-connector-server/). A full list of connectors can be found in the [providers folder](https://github.com/verida/data-connector-server/tree/main/src/providers).

### Connection Handlers

Connections (ie: Google) have multiple handlers (ie: Gmail, Calendar etc.) that process different types of data available for a given connection. These handlers typically require specific permission to be granted when authorizing the connection. For example; A user will need to permit Verida access to the "Calendar" otherwise that data won't synchronize.

Handlers have built-in options specific to their functionality. For example; The Telegram handler has an option to only sync groups with less than 50 participants.

{% hint style="warning" %}
Handler options are currently implemented in the backend and will be made available in the user interface soon.
{% endhint %}

### Request a Connector

You can request a new connector via our roadmap here:

[https://roadmap.verida.ai/data-connectors](https://roadmap.verida.ai/data-connectors)

## Fetching Historical Data

The default setting for all handlers is to fetch data up to 3 months old. In the future users will be able to customize this to increase the historical data to fetch. This will obviously increase the amount of data storage and memory usage for that user's data.
