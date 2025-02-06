---
description: A breakdown on how to make personal data available for AI use cases
---

# Dynamic Loading of Data for Realtime AI

{% hint style="info" %}
This article was [originally published by Verida co-founder Chris Were](https://www.chriswere.com/p/dynamic-loading-of-personal-data).
{% endhint %}

At [Verida](https://verida.network/), We are working rapidly towards enabling personal data to be connected to AI for training and inference, in an end-to-end privacy preserving manner.

One of the questions to answer is how fast can data, stored in a decentralized database storage network like Verida, be made available to a personal AI agent. This is a critical question as huge time lags will create a poor user experience, making any personal AI products unviable.

There are many ways to use AI to communicate with data, however in this case we are assuming a Retrieval-Augmented Generation (RAG) approach.

### Dynamic User Data Queries

The current architecture we are researching involves a “User Data API” that unlocks personal data stored (encrypted) on the Verida network, decrypts the data and then makes it available to AI agents and large language models (LLM’s) on demand.

This poses key latency questions:

1. What is the latency to fetch encrypted data from the network?
2. What is the latency to decrypt the data and make it queryable?
3. What is the latency to make the data searchable via Lucene style search queries?

While (3) isn’t absolutely necessary, at this stage it seems reasonable to assume a Lucene style search is a powerful tool to allow fast, flexible search queries across user data.

### Test Setup

I used an early version of the [Verida Personal Data Bridge](https://news.verida.io/building-a-personal-data-bridge-to-enable-personal-ai-0b5dde3e0f09) ([source code](https://github.com/verida/data-connector-server)) to pull my most recent 4,000 emails. This resulted in 250MB of raw database data (including PDF attachments converted to text), which became 330MB once database indexes were included.

I then ran the [Verida User Data API](https://github.com/verida/user-data-api/tree/feature/2-lucene-support) to hit the search endpoint that searches all my data matching the email schema (https://common.schemas.verida.io/social/email/v0.1.0/schema.json):\
\
http://localhost:5022/search/ds/aHR0cHM6Ly9jb21tb24uc2NoZW1hcy52ZXJpZGEuaW8vc29jaWFsL2VtYWlsL3YwLjEuMC9zY2hlbWEuanNvbg===?q=name:Luca

For testing purposes, the _Personal Data Bridge_ and _User Data API_ are running locally on my Macbook Pro. The Verida account is on the _Banksia_ testnet, connected to a _Storage Node_ running on my local machine.

### Test Results

Here’s the timed output from this initial set of tests:

#### Latency

Making a /_search_ request involves the following time sensitive operations:

1. Time to sync encrypted user data from the Verida network to the local machine
2. Time to decrypt the user data into a decrypted database
3. Time to load all records from the decrypted database into memory
4. Time to load all data into an in memory Lucene index and query it

The screenshot shows three requests running over 4,000 of my personal emails.

**Request 1**

The first request took 3m 41s to complete steps 1,2,3.

Step 4 took an incredibly fast 38 ms.

**Request 2**

The second request used a cached copy of the Lucene index so only needed to complete step 4, again returning results in 38 ms.

**Request 3**

For the third request, I shut down the server, which cleared the in memory Lucene cache.

This request didn’t need to complete step 1. It completed steps 2 and 3 in 34s and generated the Lucene results in 26ms.

_Note: Step 1 is actually pulling data from a Storage Node running on my local machine, not the network itself. As such step 1 is a bit faster than real world usage which would have this code running in data centres with fast pipes._

#### Memory

The baseline memory usage of the _User Data API_ server is (bytes):

```
{
    "rss": 115982336,
    "heapTotal": 36827136,
    "heapUsed": 33001104,
    "external": 2117266,
    "arrayBuffers": 54788
}
```

After loading the data in-memory (bytes):

```
{
    "rss": 772591616,
    "heapTotal": 362926080,
    "heapUsed": 351119608,
    "external": 2156712,
    "arrayBuffers": 82355
}
```

This shows an increase in memory usage for the process from a baseline of 115MB to 772MB.

### Discussion

Here’s a breakdown of the learnings and a discussion on each.

It’s important to note that this infrastructure is intended to be run within secure enclaves to guarantee end-to-end privacy of user data. As it currently stands, secure enclaves only support in-memory storage, with no access to long term physical disk storage.

#### Latency

These are roughly extrapolated times for each step:

**Step 1:** Sync encrypted data: \~3 minutes

**Step 2 & 3:** Locally decrypt data and load into memory: \~34 seconds

**Step 4:** Load data into Lucene and run query: 34 milliseconds

The time to query the data is incredibly fast at 34ms, which is a huge positive.

However, the time to load the data in Step 1 is a blocker to a great user experience. That being said, this step only needs to occur once for any given server.

Under the Verida model of using decentralized identifiers, each Verida account will specify specific confidential compute nodes to act on their behalf. These nodes can sync this data once and then receive regular updates (using the Verida network real-time sync capabilities), keeping it up-to-date at all times.

The 34 seconds to decrypt and load into memory only needs to happen when the _User Data API_ doesn’t have user data in it’s memory cache. This will happen when; 1) The server starts for the first time, or 2) If the cache is cleared (likely to happen after a period of inactivity for a user).

In reality, there may be a 30 second delay for this load process when a user makes their first request and then all subsequent requests should be very fast. Better hardware will drastically improve this load time.

#### Memory Usage

Memory usage ballooned from 115MB to 772MB, an increase of 657MB. The raw uncompressed data (stored in memory database) was 330MB including indexes. 657MB is almost exactly 2x330MB which makes sense, because the data is actually loaded into memory twice. One copy is an in-memory database, the second copy is an in-memory Lucene database.

It’s quite possible the Lucene search service proves to be more useful than the in-memory database, allowing it to be dropped and halving that memory usage.

A future piece of work is to investigate running Lucene locally within the secure enclave, instead of storing in-memory. This would potentially eliminate the 30 second load time and significantly reduce the memory usage of the _User Data API_ server.

#### 4,000 emails?

Our vision is to enable AI to access all your digital data; email history, message history from chat platforms, search and browser history, health care data, financial records and more. That obviously requires a lot more than the 330MB of data used in this example.

The _Personal Data Bridge_ supports pulling Facebook page likes and posts. I have pulled down over 3,000 facebook posts (excluding images and videos) which was less than 10MB.

We are still learning the volume of data for each dataset as we connect more sources to the _Personal Data Bridge_, but it’s probably safe to assume that email will be the largest data set for most people.

In my case 4,000 emails represented just 2 months of one of my multiple inboxes. The vast majority of those messages are junk / spam that I never intend to read. It may be sensible to add an additional processing layer over the data to eliminate emails that aren’t worth indexing. This will save memory and reduce time.

Extending that idea further, there will likely be a need to build additional metadata based on your personal data to help AI assistants to quickly know more about you. For example, you can enable a LLM to search your email and social media history to create a profile for you; age, gender, family, income, food preferences and much more. This is incredibly useful context to help guide any personal AI assistant, when combined with conducting real time search queries for specific prompts.

### Where next?

The current focus is getting an end-to-end solution that can be run on a local machine to connect your personal data to AI LLM’s.

While there are some performance bottlenecks mentioned above that could be investigated further, there is nothing that is an obvious blocker.

To that end, the next key priority is to be able to write a prompt (ie: _Create a haiku of the conversation I had with my Mum about Mars_) and have it sent to a locally running LLM (ie: Llama3) that has access to user data via the Lucene index to produce a meaningful result.
