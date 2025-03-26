---
description: >-
  Learn more about how the Verida Confidential Compute API's ensure maximum data
  privacy and how that impacts API performance.
icon: gauge-max
---

# API Performance

When an AI request is made to access user data, the data is queried within the Verida confidential compute environment (see [privacy-and-security.md](../resources/privacy-and-security.md "mention")).

This environment operates entirely in memory for maximum security. As a result encrypted user data must be downloaded from the Verida network, decrypted in-memory, and then processed. Depending on the type and volume of data being requested, this can take seconds through to many minutes.

## Example request

A simple query such as "how many emails have I sent" requires the following steps:

1. Authenticate the provided API token \[milliseconds]
2. Connect to the Verida network \[seconds]
3. Download the user's data from the email database \[seconds - minutes depending on data volume]
4. Decrypt the user data \[seconds - minutes depending on data volume]
5. Query all the user data with a filter to only find emails I have sent \[seconds]
6. Return the result \[milliseconds]

The confidential compute environment implements caching (see below), so the above steps 2-4 are only required on the first request that&#x20;

## Caching to increase performance

In order to increase performance, the confidential compute environment caches (in encrypted memory) the user's Verida network connection and any downloaded user data.

{% hint style="warning" %}
This cache currently expires after 30 minutes of inactivity, so if there is a delay of 30 minutes between requests, the caching has no impact.
{% endhint %}

Storing data in memory is expensive, so there is a cost / benefit consideration to how long data should be kept in memory.

## Future enhancements

1. Have a dynamic caching model that learns user's usage patterns and customizes cache duration and timing.
2. Enabling users to configure their caching model and directly relate to the cost of accessing the service (ie: Pay a little extra to always have user data available between 7am - 10am).
3. Enable on-disk encryption of cached data to avoid it being downloaded over and over again; there are important privacy / security implications and decentralized architecture considerations that require careful thought with this model.
