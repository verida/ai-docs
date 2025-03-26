---
icon: webhook
---

# Overview

The Verida [PersonalAgentKit](https://github.com/verida/personal-agent-kit/) provides integrations with AI frameworks for simple integration into your applications.

For the first release, we support [langgraph.md](langgraph.md "mention") tools to easily integrate with any LangChain / LangGraph application.

Verida PersonalAgentKit supported the following tools:

1. **Profiles** — Allow the LLM to know about your external profiles (ie: Google or Telegram accounts)
2. **Query** — Allow the LLM to query your data (ie: Query your emails, message history, Youtube favourites etc.)
3. **Get Record** — Allow the LLM to fetch a specific record (ie: A specific file or a specific email)
4. **Chat Search** — Allow the LLM to perform a keyword search of your message chat threads
5. **Datastore Search** — Allow the LLM to perform a keyword search across any of your supported data (ie: Find all emails that mention "utility bills")
6. **Universal Search** — Allow the LLM to perform a keyword search across all your data (ie: Find all mentions of "devcon 2025" in all my messages, emails and favourites)
7. **User Information** — Allow the LLM to know more about the user account (DID) on the Verida network and what data permissions it can access.

## Which LLM to use?

Not all LLM's are created equal. When you use these tools, the LLM must be capable of understanding the tool description and parameters to correctly call the tools in a useful way to respond to a user's prompt.

Here is what we have learned about leading LLM's to date:

1. _**Llama 3.3-70B**_ — Recommended. Works well. Open source.
2. **Claude Haiku 3.5** — Recommended. Works very well.
3. _**OpenAI (gpt-4o-mini, gpt-4o)**_ — Not recommended. It fails to leverage the `selector` and `sort` parameters from the Query tool for no obvious reason.&#x20;

### LLM Provider QuickLinks

1. [Get an OpenAI API key](https://platform.openai.com/docs/quickstart#create-and-export-an-api-key)
2. [Get a RedPill AI key](https://red-pill.ai/) (Highly secure, runs Llama 3.3-70B in a TEE, slow)
3. [Get an Anthropic key](https://www.anthropic.com/) (for Claude)
4. [Get a Groq key](https://groq.com/) (Groq is fast)

### LLM Privacy Considerations

{% hint style="warning" %}
Centralized LLM services (OpenAI, Anthropic, Groq etc.) can access your prompts and any data sent to them.
{% endhint %}

Verida's API's operate within a secure, confidential compute, environment ensuring that user data is only exposed via the API requests with the permissions granted by a user.

When you connect a LLM to the Verida API's, the LLM can't access all the user data, but it can access any data response from the API's. For example; if you request a summary of your last 24 hours of emails, those emails will be sent to the LLM for processing, but the LLM can't automatically access all your emails.

This is very important to understand, because you are trusting these centralized LLM services to not expose your prompts or data sent to their LLM's. These could be exposed by malicious employees or as a result of a third party hack on that service.

### How to Secure your LLM Requests

There are two key ways you can eliminate the security risks associated with centralized LLM services:

1. Operate the LLM on a local device that you control
2. Use a LLM from a third party service that runs within a Trusted Execution Environment (TEE) such as [Redpill AI](https://red-pill.ai/) (Very secure, but also very slow in our testing as of 26 Mar 2025).
