---
description: >-
  The emergence of Decentralized Physical Infrastructure Networks (DePIN) are a
  linchpin for providing privacy preserving decentralized infrastructure to
  power the next generation of large language mode
---

# Web3 & DePIN solves AI's privacy problems

{% hint style="info" %}
This article was [originally published by Verida co-founder Chris Were](https://www.chriswere.com/p/how-web3-and-depin-solves-ais-data).
{% endhint %}

Artificial intelligence (AI) has become an undeniable force in shaping our world. From personalized recommendations to medical diagnosis, AI's impact is undeniable. However, alongside its potential lies a looming concern: _**data privacy**_. Traditional AI models typically rely on centralized data storage and centralized computation, raising concerns about ownership, control, and potential misuse.

See part 1 of this series, “[Top3 data privacy issues facing AI today](https://www.chriswere.com/p/top-three-data-privacy-issues-facing)”, for a breakdown of key privacy issues which we will explain how web3 can help alleviate these problems.

The emergence of Decentralized Physical Infrastructure Networks (DePIN) are a linchpin for providing privacy preserving decentralized infrastructure to power the next generation of large language models (LLMs).

At a high level, DePINs can provide access to decentralized computation and storage resources that are beyond the control of any single organization. If this computation and storage can be built in such a way that it is privacy preserving; ie: those operating the infrastructure have no access to underlying data or computation occurring, this is an incredibly robust foundation for privacy preserving AI.

Let’s dive deeper into how that would look, when addressing the top three data privacy issues.

### **Privacy of user prompts**

Safeguarding privacy of user prompts has become an increasingly critical concern in the world of AI.

An end user can initiate a connection with a LLM hosted within a decentralized privacy-prserving compute engine called a Trusted Execution Environment (TEE), which provides a public encryption key. The end user encrypts their AI prompts using that public key and sends the encrypted prompts to the secure LLM.

Within this privacy-preserving environment, the encrypted prompts undergo decryption using a key only known by the TEE. This specialized infrastructure is designed to uphold the confidentiality and integrity of user data throughout the computation process.

Subsequently, the decrypted prompts are fed into the LLM for processing. The LLM generates responses based on the decrypted prompts without ever revealing the original, unencrypted input to any party beyond the authorized entities. This ensures that sensitive information remains confidential and inaccessible to any unauthorized parties, including the infrastructure owner.

By employing such privacy-preserving measures, users can engage with AI systems confidently, knowing that their data remains protected and their privacy upheld throughout the interaction. This approach not only enhances trust between users and AI systems but also aligns with evolving regulatory frameworks aimed at safeguarding personal data.

### **Privacy of custom trained AI models**

In a similar fashion, decentralized technology can be used to protect the privacy of custom-trained AI models that are leveraging proprietary data and sensitive information.

This starts with preparing and curating the training dataset in a manner that mitigates the risk of exposing sensitive information. Techniques such as data anonymization, differential privacy, and federated learning can be employed to anonymize or decentralize the data, thereby minimizing the potential for privacy breaches.

Next, an end user with a custom-trained Language Model (LLM) safeguards its privacy by encrypting the model before uploading it to a decentralized Trusted Execution Environment.

Once the encrypted custom-trained LLM is uploaded to the privacy-preserving compute engine, the infrastructure decrypts it using keys known only to TEE. This decryption process occurs within the secure confines of the compute engine, ensuring that the confidentiality of the model remains intact.

Throughout the training process, the privacy-preserving compute engine facilitates secure communication between the end user's infrastructure and any external parties involved in the training process, ensuring that sensitive data remains encrypted and confidential at all times. In a decentralized world, this data sharing infrastructure and communication will likely exist on a highly secure and fast protocol such as the [Verida Network](https://www.verida.network/).

By adopting a privacy-preserving approach to model training, organizations can mitigate the risk of data breaches and unauthorized access while fostering trust among users and stakeholders. This commitment to privacy not only aligns with regulatory requirements but also reflects a dedication to ethical AI practices in an increasingly data-centric landscape.

### **Private data to train AI**

AI models are only as good as the data they have access to. The vast majority of data is generated on behalf of, or by, individuals. This data is immensely valuable for training AI models, but must be protected at all costs due to its sensitivity.

End users can safeguard their private information by encrypting it into private training datasets before submission to a LLM training program. This process ensures that the underlying data remains confidential throughout the training phase.

Operating within a privacy-preserving compute engine, the LLM training program decrypts the encrypted training data for model training purposes while upholding the integrity and confidentiality of the original data. This approach mirrors the principles applied in safeguarding user prompts, wherein the privacy-preserving computation facilitates secure decryption and utilization of the data without exposing its contents to unauthorized parties.

By leveraging encrypted training data, organizations and individuals can harness the power of AI model training while mitigating the risks associated with data exposure. This approach enables the development of AI models tailored to specific use cases, such as utilizing personal health data to train LLMs for healthcare research applications or crafting hyper-personalized LLMs for individual use cases, such as digital AI assistants.

Following the completion of training, the resulting LLM holds valuable insights and capabilities derived from the encrypted training data, yet the original data remains confidential and undisclosed. This ensures that sensitive information remains protected, even as the AI model becomes operational and begins to deliver value.

To further bolster privacy and control over the trained LLM, organizations and individuals can leverage platforms like the [Verida Network](https://www.verida.network/). Here, the trained model can be securely stored, initially under the private control of the end user who created it. Utilizing Verida's permission tools, users retain the ability to manage access to the LLM, granting permissions to other users as desired. Additionally, users may choose to monetize access to their trained models by charging others with crypto tokens for accessing and utilizing the model's capabilities.
