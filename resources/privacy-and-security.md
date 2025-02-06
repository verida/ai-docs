---
description: >-
  Learn how Verida APIs enforce privacy and security of user data within a
  decentralized environment
icon: unlock-keyhole
---

# Privacy & Security

Verida APIs are built on a first iteration of the Verida Confidential Compute infrastructure. They are designed to find the optimum balance between decentralization, security, privacy and performance.

## Confidential Compute

Verida APIs are running within a confidential computation environment. This means that no-one, not even the underlying infrastructure provider running the API server can access any user data or view the computation occurring on the node.

The first iteration of Verida's Confidential Compute nodes are running inside [Marlin Oyster](https://www.marlin.org/oyster) Trusted Execution Environments (TEE). These nodes provide numerous security guarantees and capabilities:

* Computation occurs within a secure enclave where the node operator has zero visibility
* SSL terminates within the secure enclave, eliminating man-in-the-middle attacks
* Server code is verified to be the expected code
* No data is stored to external disks. All data is secured in memory.

The Verida Foundation is operating the first cohort of Confidential Compute nodes and will open up to node operators in the future.

{% hint style="info" %}
Learn more:

* [Self-sovereign confidential compute Litepaper](https://cdn.prod.website-files.com/669e543b029da50b2d46c454/66fefa6b2170e851c66166e8_Verida%20Technical%20Litepaper_%20Self-Sovereign%20Confidential%20Compute%20to%20Secure%20Private%20AI.pdf)
* [Marlin Oyster in depth](https://docs.marlin.org/learn/oyster/introduction)
{% endhint %}

## Confidential Storage

Verida APIs integrate the [Verida Client SDK](broken-reference) within the secure enclave on each confidential compute node. User data is syncronized from the Verida network, decrypted and then loaded into memory for rapid access via API endpoints.

As such, user data retains all the security and privacy benefits of the Verida Network and user data never leaves the secure enclave, accept via user authorized API requests.

{% hint style="info" %}
Learn more:

* [Core Concepts](broken-reference)
* [Verida Whitepaper](broken-reference)
{% endhint %}

## LLM Privacy \[beta]

{% hint style="warning" %}
Important privacy notice for the beta release
{% endhint %}

The large language models (LLM) currently used in the Verida APIs are _not_ currently running in a Verida Confidential Compute secure enclave. Secure enclaves do not currently support GPU access which is necessary for performant LLM operations.

The beta release provides the option of using [Amazon Web Services Bedrock](https://aws.amazon.com/bedrock/) or your own LLM.

This is a temporary solution as we are collaborating with partners to enable LLM's to run efficiently and cost effectively within secure enclaves. While this is not perfect, we believe the [AWS Bedrock privacy architecture and security model](https://aws.amazon.com/bedrock/security-compliance/) provides adequate protections for this alpha release, while those with highly sensitive requirements can still provide their own custom LLM.

From the AWS documentation:

> Amazon Bedrock doesn't store or log your prompts and completions. Amazon Bedrock doesn't use your prompts and completions to train any AWS models and doesn't distribute them to third parties.
>
> AWS complies with ISO 27018, a code of practice that focuses on protection of personal data in the cloud. It extends ISO information security standard 27001 to cover the regulatory requirements for the protection of personally identifiable information (PII) or personal data for the public cloud computing environment and specifies implementation guidance based on ISO 27002 controls that is applicable to PII processed by public cloud service providers. For more information, or to view the AWS ISO 27018 Certification, see the [AWS ISO 27018 Compliance](https://aws.amazon.com/compliance/iso-27018-faqs/) webpage

## Custom LLM

You can provide your own OpenAI compatible LLM endpoint and API key through the LLM API's, except the Agent endpoint as it requires a proprietary LLM to perform at it's best.

## Source Code

The source code for the APIs are open source and are contained within the [Data Connector Server Github repo](https://github.com/verida/data-connector-server).
