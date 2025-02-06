# Confidential Compute Litepaper

{% hint style="info" %}
This article was [originally published on verida.network](https://news.verida.network/verida-technical-litepaper-self-sovereign-confidential-compute-network-to-secure-private-ai-part-fb57146c3a02).
{% endhint %}

## Verida Technical Litepaper: Self-Sovereign Confidential Compute Network to Secure Private AI <a href="#a6db" id="a6db"></a>

## Introduction <a href="#a6db" id="a6db"></a>

Verida’s mission has always been clear: empower individuals to own and control their data. Now, we’re taking it further.

This Technical Litepaper presents a high-level outline of how the Verida Network is growing beyond decentralized, privacy preserving databases, to support decentralized, privacy-preserving compute optimized for handling private data. There are [numerous privacy issues currently facing AI](https://www.chriswere.com/p/top-three-data-privacy-issues-facing) that [web3 and decentralized physical infrastructure networks](https://www.chriswere.com/p/how-web3-and-depin-solves-ais-data) can [help solve](https://news.verida.io/verida-is-enabling-the-privacy-preserving-ai-tech-stack-7e9558f822f3). From Verida’s perspective, this represents an expansion of our mission from allowing individuals to control their data to introducing new and powerful ways for users to benefit from their data.

## Current AI Data Challenges <a href="#id-1b18" id="id-1b18"></a>

**We are running out of high-quality data to train LLMs**

Public internet data has been scraped and indexed by AI models, with researchers estimating that by 2026, we will exhaust high-quality text data for training LLMs. Next, we need to access private data, but it’s hard and expensive to access.

**Private enterprise and personal AI agents need to access private data**

There is a lot of excitement around the next phase of AI beyond chat prompts. Digital twins or personal AI agents that know everything about us and support every aspect of our professional and personal lives. However, to make this a reality AI models need access to private, real time context-level user data to deliver more powerful insights and a truly personalized experience.

**Existing AI platforms are not private**

The mainstream infrastructure providers powering the current generation of AI products have full access to prompts and training data, putting sensitive information at risk.

**AI trust and transparency is a challenge**

Regulation is coming to AI and it will become essential that AI models can prove the training data was high quality, ethically sourced. This is critical to reduce bias, misuse and improve safety in AI.

**Data creators aren’t being rewarded**

User-owned data is a critical and valuable resource for AI and those who create the data should benefit from its use. Reddit recently sold user data for $200M, while other organizations have reached similar agreements. Meta is training its AI models on user data from some countries, but excluding European users due to GDPR preventing them from doing so without user consent.

## Verida’s Privacy Preserving Infrastructure <a href="#c154" id="c154"></a>

Verida has already developed the leading private decentralized database storage infrastructure (see [Verida Whitepaper](https://verida.network/whitepaper)) which provides a solid foundation to address the current AI data challenges.

Expanding the Verida network to support privacy-preserving compute enables private, encrypted data to be integrated with leading AI models, ensuring end-to-end privacy, safeguarding data from model owners. This will unlock a new era of hyper-personal and _safe_ AI experiences.

AI services such as ChatGPT have full access to any information users supply and have already been known to leak sensitive data. By enabling model owners access to private data, there is increased risks of data breaches, imperiling privacy, and ultimately limiting AI use cases.

There are three key problems Verida is solving to support secure private AI:

1. **Data Access:** Enabling users to extract and store their private data from third party platforms for use with emerging AI prompts and agents.
2. **Private Storage and Sharing:** Providing secure infrastructure allowing user data to be discoverable, searchable and accessible with user-consent to third party AI platforms operating within verifiable confidential compute environments.
3. **Private Compute:** Provide a verifiable, confidential compute infrastructure enabling agentic AI computation to securely occur on sensitive user data.

Supporting the above tasks, Verida is building a “Private Data Bridge”, allowing users to reclaim their data and use it within a new cohort of personalized AI applications. Users can pull their private data from platforms such as Google, Slack, Notion, email providers, LinkedIn, Amazon, Strava, and much more. This data is encrypted and stored in a user-controlled private data Vault on the Verida network.

It’s important to note that Verida is not building infrastructure for decentralized AI model training, or distributed AI inference. Rather, Verida’s focus is on providing a high performance, secure, trusted and verifiable infrastructure suitable for managing private data appropriate for AI use cases.

We have relationships with third parties that are building; private AI agents, AI data marketplaces and other privacy-centric AI use cases.

## Comparing Current AI Solutions <a href="#id-872f" id="id-872f"></a>

AI solutions can be deployed primarily through two methods: cloud-based/hosted services or on local machines.

Cloud-based AI services, while convenient and scalable, expose sensitive user data to potential risks, as data processing occurs on external servers and may be accessible to third parties.

In contrast, local AI environments offer enhanced security, ensuring that user data remains isolated and inaccessible to other applications or external entities. However, local environments come with significant limitations, including the need for technical expertise that is not available to the majority of users. Moreover, these environments often face performance challenges; for instance, running large language models (LLMs) on standard consumer hardware is typically impractical due to the high computational demands.

Verida’s Confidential Storage and Compute infrastructure offers alternatives to these approaches.

<figure><img src="https://miro.medium.com/v2/resize:fit:561/1*MB-rJ3qdI1gP1pYjGBTgGg.png" alt="" height="450" width="561"><figcaption><p>Comparison of different AI infrastructure options</p></figcaption></figure>

Apple has recently announced [Private Cloud Compute](https://security.apple.com/blog/private-cloud-compute/) that provides a hybrid local + secure cloud approach. AI processing occurs on a local device (ie: mobile phone) by default, then when additional processing power is required, the request is offloaded to Apple’s servers that are operating within a trusted execution environment. This is an impressive offering that is focused on solving important security concerns relating to user data and AI. However, it is centralized, only available to Apple devices and puts significant trust in Apple as they control both the hardware and attestation keys.

## Self-Sovereign AI Interaction Model <a href="#dde2" id="dde2"></a>

Let’s look at what an ideal model of confidential AI architecture looks like. This is an interaction model of how a basic “Self-Sovereign AI” chat interface, using a RAG-style approach, would operate in an end-to-end confidential manner.

<figure><img src="https://miro.medium.com/v2/resize:fit:700/0*KdS6Rcnh58_dUMTs" alt="" height="525" width="700"><figcaption><p><em>Self-Sovereign AI Interaction Model</em></p></figcaption></figure>

The **End User Application** in this example will be a “Chat Prompt” application. A user enters a prompt (i.e., “_Summarize the conversation I had with my mates about the upcoming golf trip_”).

A **Private AI API** endpoint (AI Prompt) receives the chat prompt and breaks down the request. It sends a prompt to the **LLM**, converting the original prompt into a series of search queries. The **LLM** could be an open source or proprietary model. Due to the confidential nature of the secure enclave, proprietary models could be deployed without risk of IP theft by the model owner.

The search queries are sent to the **User Data API** which has access to data previously obtained via Verida’s **Private Data Bridge**. This data includes emails, chat message histories and much more.

The **Private AI API** collates the search query results and sends the relevant responses and original prompt to the **LLM** to produce a final result that is returned to the user.

Verida is currently developing a “showcase” AI agent that implements this architecture and can provide a starting point for other projects to build their own confidential private AI products.

## Confidential Compute <a href="#c9b0" id="c9b0"></a>

A growing number of confidential compute offerings are being offered by the large cloud providers that provide access to Trusted Execution Environments (TEEs). These include: AWS Nitro, Google Confidential Compute and Azure Confidential Compute. Tokenized confidential compute offerings such as [Marlin Oyster](https://www.marlin.org/) and [Super Protocol](https://superprotocol.com/) have also emerged recently.

These compute offerings typically allow a container (such as a Docker instance) to be deployed within a secure enclave on secure TEE hardware. The enclave has a range of verification and security measures that can prove that both the code and the data running in the enclave is the code you expect and that the enclave has been deployed in a tamper-resistant manner.

There are some important limitations to these secure enclaves, namely:

1. There is no direct access available to the enclave from the infrastructure operator. Communication occurs via a dedicated virtual socket between the secure enclave and the host machine _(\*)_.
2. There is no disk storage available, everything must be stored in RAM.
3. Direct GPU access is typically not available within the secure enclave (necessary for high performance LLM training and inference), however this capability is expected to be available in early 2025.

_(\*) In some instances the infrastructure operator controls both the hardware attestation key and the cloud infrastructure which introduces security risks that need to be carefully worked through, but is outside the scope of this document._

The Verida network is effectively a database offering high performance data synchronization and decryption. While secure enclaves do not have local disk access (by design), it is possible to give a secure enclave a private key, enabling the enclave to quickly download user data, load it into memory and perform operations.

While enclaves do not have direct access to the Internet, it is possible to facilitate secure socket connections between the host machine and enclave to “proxy” web requests to the outside world. This increases the surface area of possible attacks on the security of the enclave, but is also a necessary requirement for confidential compute that interacts with other web services.

It is critical that confidential AI inference for user prompts has a fast response time to ensure a high quality experience for end users. Direct GPU access via confidential compute is most likely necessary to meet these requirements. Access to GPUs with TEEs is currently limited, however products such as the [NVIDIA H100](https://developer.nvidia.com/blog/confidential-computing-on-h100-gpus-for-secure-and-trustworthy-ai/) offer these capabilities and these capabilities will be made available for use within the Verida network in due course.

## Self-Sovereign Compute <a href="#id-2ee6" id="id-2ee6"></a>

Verida offers a self-sovereign compute infrastructure stack that exists on top of confidential compute infrastructure.

<figure><img src="https://miro.medium.com/v2/resize:fit:700/0*sZjmmasI5EuY-YHW" alt="" height="525" width="700"><figcaption><p><em>Figure 1: Self-Sovereign Compute Architecture</em></p></figcaption></figure>

The self-sovereign compute infrastructure provides the following guarantees:

1. User data is not accessible by infrastructure node operators.
2. Runtime code can be verified to ensure it is running the expected code.
3. Users are in complete control over their private data and can grant / revoke access to third parties at any time.
4. Third-party developers can build and deploy code that will operate on user data in a confidential manner.
5. Users are in complete control over the compute services that can operate on their data and can grant / revoke access to third parties at any time.

There are two distinct types of compute that have different infrastructure requirements; Stateless Confidential Compute and Stateful Confidential Compute.

## Stateless (Generic) Confidential Compute <a href="#id-4d14" id="id-4d14"></a>

This type of computation is stateless, it retains no user data between API requests. However, it can request user data from other APIs and process that user data in a confidential manner.

Here are some examples of Generic Stateless Compute that would operate on the network.

<figure><img src="https://miro.medium.com/v2/resize:fit:700/0*Aed5EsD33YzURDJE" alt="" height="562" width="700"><figcaption><p><em>Figure 2: Verida Personal Data Bridge</em></p></figcaption></figure>

**Private Data Bridge** facilitates users connecting to third-party platform APIs (ie: Meta, Google, Amazon, etc.). These nodes must operate in a confidential manner as they store API secrets, handle end user access / refresh tokens to the third-party platforms, pull sensitive user data from those platforms, and then use private user keys to store that data in users’ private databases on the Verida network.

**LLM APIs** accept user prompts that contain sensitive user data, so they must operate in a confidential compute environment.

**AI APIs** such as AI prompt services and AI agent services provide the “glue” to interact between user data and LLMs. An AI service can use the User Data APIs (see below) to directly access user data. This enables it to facilitate retrieval-augmented generation (RAG) via the LLM APIs, leveraging user data. These APIs may also save data back to users’ databases as a result of a request (i.e., saving data into a vector database for future RAG queries).

See [“Self-Sovereign AI Interaction Model” from Part 1](https://news.verida.io/verida-technical-litepaper-self-sovereign-confidential-compute-network-to-secure-private-ai-part-fb57146c3a02) for a breakdown of how these generic compute services can interact together to provide AI services on user data.

## Stateful (User) Confidential Compute <a href="#ceb7" id="ceb7"></a>

This type of computation is stateful, where user data remains available (in memory) for an extended period of time. This enhances performance and, ultimately, the user experience for end users.

A User Data API will enable authorized third party applications (such as private AI agents) to easily and quickly access decrypted private user data. It is assumed there is a single User Data API, however in reality it is likely there will be multiple API services that operate on different infrastructure.

Here are some examples of the types of data that would be available for access:

1. Chat history across multiple platforms (Telegram, Signal, Slack, Whatsapp, etc.)
2. Web browser history
3. Corporate knowledge base (ie: Notion, Google Drive, etc)
4. Emails
5. Financial transactions
6. Product purchases
7. Health data

Each of these data types have different volumes and sizes, which will also differ between users. It’s expected the total storage required for an individual user would be somewhere between 100MB and 2GB, whereas enterprise knowledge bases will be much larger.

In the first phase, the focus will be on structured data, not images or videos. This aligns with Verida’s existing storage node infrastructure that provides and aids the development of a first iteration of data schemas for AI data interoperability.

The User Data API exposes endpoints to support the following data services:

1. Authentication for decentralized identities to connect their account to a User Data API Node
2. Authentication to obtain access and refresh tokens for third-party applications
3. Database queries that execute over a user’s data
4. Keyword (Lucene) style search over a user’s data
5. Vector database search over a user’s data

## Connecting Stateful Compute to Decentralized Identities <a href="#id-1629" id="id-1629"></a>

Third party applications obtain an access token that allows scoped access to user data, based on the consent granted by the user.

A decentralized identity on the Verida network can authorize three or more self-sovereign compute nodes on the network, to manage access to their data for third-party applications. This is via the serviceEndpoint capability on the identity’s DID Document. This operates in the same way that the current Verida database storage network allocates storage nodes to be responsible for user data.

Secure enclaves have no disk access, however user data is available (encrypted) on the Verida network and can be synchronized on demand given the appropriate user private key. It’s necessary for user data to be “hot loaded” when required which involves synchronizing the encrypted user data from the Verida network, decrypting it, storing it in memory and then adding other metadata (i.e., search indexes). This occurs when an initial API request is made, ensuring user data is ready for fast access for third-party applications.

After a set period of time of inactivity (i.e., 1 hour) the user data will be unloaded from memory to save resources on the underlying compute node. In this way, a single User Data API node can service requests for multiple decentralized identities at once.

It will be necessary to ensure “hot loading” is fast enough to minimize the first interaction time for end users. It’s also essential these compute nodes have sufficient memory to load data for multiple users at once. Verida has developed an internal proof-of-concept to verify the “hot loading” concept with user data will be a viable solution.

For enhanced privacy and security, the data and execution for each decentralized identity will operate in an isolated VM within the secure enclave of the confidential compute node.

## Confidential Compute Nodes <a href="#id-4221" id="id-4221"></a>

Confidential Compute Nodes running on the Verida Self-Sovereign Compute Network operate a web server within a secure enclave environment to handle compute requests and responses.

There will be different types of nodes (i.e., LLM, User API) that will have different code running on them depending on the service(s) they are providing.

For maximum flexibility, advanced users and developers will be able to run compute nodes locally, on any type of hardware.

Nodes have key requirements they must adhere to:

**GPU access** is required for some compute nodes (i.e., LLM nodes), but not others. As such, the hardware requirements for each node will depend on the type of compute services running on the node.

**Code Verifiability** is critical to ensure trust in the compute and security of user data. Nodes must be able to attest the code they are running has not been tampered with.

**Upgradability** is essential to keep nodes current with the latest software versions, security fixes and other patches. Coordination is required to ensure applications can ensure their code is running on the latest node versions.

**API endpoints** are the entry point for communicating with nodes. It’s essential a web server host operates within the secure enclave to communicate with the outside world.

**SSL termination** must occur within the secure enclave to ensure the host machine can’t access API requests and responses.

**Resource restraints** will exist on each node (i.e., CPU, memory) that will limit the number of active requests they can handle. The network and nodes will need to coordinate this to ensure nodes are selected that have sufficient resources available to meet any given request.

## Interoperability and Extensibility <a href="#id-3526" id="id-3526"></a>

In order to create an efficient and highly interoperable ecosystem of self-sovereign API’s, it’s necessary to have a set of common data standards. Verida’s self-sovereign database storage network provides this necessary infrastructure via guaranteed [data schemas within encrypted datasets](https://developers.verida.network/docs/concepts/schemas), providing a solid foundation for data interoperability.

Developers can build new self-sovereign compute services that can be deployed on the network and then used by other services. This provides an extensible ecosystem of API’s that can all communicate with each other to deliver highly complex solutions for end users.

<figure><img src="https://miro.medium.com/v2/resize:fit:700/0*39g951XWYQNfv_Fv" alt="" height="525" width="700"><figcaption><p><em>Figure 4: Interoperable data between self-sovereign AI services</em></p></figcaption></figure>

Over time, we expect a marketplace of private AI products, services and APIs to evolve.

## Service Discovery <a href="#id-3fb1" id="id-3fb1"></a>

Verida’s self-sovereign compute network will enable infrastructure operators to deploy and register a node of a particular service type. When an API needs to send a request to one of those service types, it can perform a “service lookup” on the Verida network to identify a suitable trusted, verifiable node it can use to send requests of the required service type.

## User Data Security Guarantees <a href="#id-7b44" id="id-7b44"></a>

It is essential to protect user privacy within the ecosystem and prevent user data leaking to non-confidential compute services outside the network. Each service deployed to the network will be running verifiable code, running on verifiable confidential compute infrastructure.

In addition, each service will only communicate with other self-sovereign compute services. Each API request to another self-sovereign compute service will be signed and verified to have been transmitted by another node within the self-sovereign network.

## Tokenized Payment <a href="#id-66a3" id="id-66a3"></a>

The VDA token will be used for payment to access self-sovereign compute services. A more detailed economic model will be provided, however the following key principles are expected to apply.

**End users** will pay on a “per-request” basis to send confidential queries to compute nodes and the services they operate. The cost per request will be calculated in a standardized fashion that balances the computation power of a node, memory usage and request time. Applications can sponsor the request fees on behalf of the user and then charge a subscription fee to cover the cost, plus profit, much like a traditional SaaS model.

**Node operators** will be compensated for providing the confidential compute infrastructure to Verida’s Self-Sovereign Compute Network.

**Builders** of services (i.e., AI Prompts and Agents) will be able to set an additional fee for using their compute services, above and beyond the underlying “per-request” compute cost. This open marketplace for AI Agents and other tools drives innovation and provides a seamless way for developers to generate revenue from the use of their intellectual property.

**Verida Network** will charge a small protocol fee (similar to a blockchain gas fee) on compute fees.

## Other Use Cases <a href="#id-4868" id="id-4868"></a>

## Data Training Marketplaces <a href="#a6ea" id="a6ea"></a>

Verida’s Private Data Bridge allows users to reclaim their private data from platforms such as Meta, Google, X, email, LinkedIn, Strava, and much more.

Users on the Verida network could push their personal data into a confidential compute service that anonymizes their data (or generates synthetic data) which is made available to various AI data marketplaces. This provides an option for users to monetize their data, without risk of data leakage, while unlocking highly valuable and unique datasets such as private messages, financial records, emails, healthcare data for training purposes.

## Managed Crypto Wallets <a href="#a864" id="a864"></a>

There is a vast array of managed wallet services available today that offer different trade-offs between user experience and security.

Having an always available cloud service that can protect user’s private keys, but still provide multiple authorization methods for a user is extremely useful to onboard new users and provide additional backup protection measures for existing users.

Such a managed wallet service becomes rather trivial to build and deploy on the Verida self-sovereign compute network.

## Verifiable Credentials <a href="#id-4f0f" id="id-4f0f"></a>

Verida has extensive experience working with decentralized identity and verifiable credential technology, in combination with many ecosystem partners.

There is a significant pain point in the industry, whereby developers within credential ecosystems are required to integrate many disparate developer SDK’s to offer an end-to-end solution. This is due to the self-sovereign nature of credentials and identity solutions where a private key must be retained on end user devices to facilitate end-to-end security.

Verida’s self-sovereign compute network can provide a viable alternative, whereby application developers can replace complex SDK integrations with simple self-sovereign APIs. This makes integration into mobile applications (such as identity wallets) and traditional web applications much easier, simpler and viable.

This could be used to provide simple API integrations to enable:

1. Identity wallets to obtain access to a user’s verifiable credentials
2. End users to pre-commit selective disclosure rules for third party applications or identity wallets, without disclosing their actual credentials
3. Provide trusted, verifiable universal resolvers
4. Trust registry APIs

Any complex SDK that requires a user’s private key to operate, could be deployed as a micro service on Verida’s self-sovereign compute network to provide a simpler integration and better user experience.

## Conclusion <a href="#id-2c2c" id="id-2c2c"></a>

Verida’s mission to empower individuals with control over their data continues to drive our innovations as we advance our infrastructure. This Litepaper outlines how the Verida Network is evolving from decentralized, privacy-preserving databases to include decentralized, privacy-preserving compute capabilities, addressing critical issues in AI data management and introducing valuable new use cases for user-controlled data.

As AI faces mounting challenges with data quality, privacy, and transparency, Verida is at the forefront of addressing these issues. By expanding our network to support privacy-preserving compute, we enable the more effective safeguarding of private data while allowing it to be securely shared with with leading AI models. This approach ensures end-to-end privacy and opens the door to hyper-personalized and secure AI experiences.

Our solution addresses three fundamental problems: enabling user access to their private data, providing secure storage and sharing, and ensuring confidential computation. Verida’s “Private Data Bridge” allows users to securely reclaim and manage their data from various platforms and facilite its use in personalized AI applications without compromising privacy.

While we are not focusing on decentralized AI model training or distributed inference, Verida is committed to offering high-performance, secure, and trusted infrastructure for managing private data. We are collaborating with partners developing private AI agents, AI data marketplaces, and other privacy-centric AI solutions, paving the way for a more secure and private future in AI. This empowers users to be confident about the ways their data is used, and receive compensation when they do choose to share elements of their personal data.

As we continue to build on these advancements, Verida remains dedicated to transforming how private data is utilized and protected in the evolving landscape of AI.
