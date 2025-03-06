---
icon: robot
---

# AI Prompts

Verida’s **LLM APIs** enable your application to run **Large Language Model** prompts. Depending on the scope granted, these prompts can range from **basic text generation** to **context-enriched** prompts powered by user data. Below is an overview of the available LLM endpoints, the required scopes, and their respective credit costs.

***

### 1. LLM Prompt ()

* **Summary**: Runs an LLM prompt **without access to user data**. This is ideal for basic text generation, summarization, or other language tasks where user data context is not needed.
* **Credits Usage**: **2 credits**
* **Scope**: `api:llm-prompt`

#### Example Usage

```bash
curl -X POST "https://api.verida.ai/api/rest/v1/llm/prompt" \
     -H "Authorization: Bearer YOUR_AUTH_TOKEN" \
     -H "Content-Type: application/json" \
     -d '{
       "prompt": "Write a short poem about blockchain."
     }'
```

**Response** (example):

```json
{
  "completion": "Blockchain’s ledger forged in trust,\nWhere bits of code hold knowledge robust,\nConnecting minds across the globe,\nEmpowering dreams in digital robe."
}
```

For full request/response structures and parameters, see the\
[LLM Prompt Documentation](https://user-apis.verida.network/#934196b1-7136-4f27-a593-0750bcfe6fa9).

***

### 2. LLM Agent Prompt

* **Summary**: Runs an LLM **agent prompt** that **has access to user data**. This allows you to leverage personal datastore or database records (based on your granted scopes) as context for the LLM, enabling personalized recommendations, summaries, or insights. This is avery intensive request as it can involve multiple LLM requests and multiple data queries.
* **Credits Usage**: **5 credits**
* **Scope Required**: `api:llm-agent-prompt`

#### Example Usage

```bash
curl -X POST "https://api.verida.ai/api/rest/v1/llm/agent-prompt" \
     -H "Authorization: Bearer YOUR_AUTH_TOKEN" \
     -H "Content-Type: application/json" \
     -d '{
       "prompt": "Summarize my recent meeting notes and suggest next steps.",
       "context": {
         "dsUrlEncoded": "aHR0cHM6Ly9jb21tb24uc2NoZW1hcy52ZXJpZGEuaW8vZmlsZS92MC4xLjAvc2NoZW1hLmpzb24=", 
         "queryFilters": { "meetingTopic": "Project Alpha" }
       }
     }'
```

**Response** (example):

```json
{
  "completion": "Your recent meeting notes focus on Project Alpha’s roadmap. Key takeaways include ... Next recommended steps:..."
}
```

> **Note**: The LLM agent uses the provided `context` to query datastores or databases your token is authorized to access. Ensure you request the necessary datastore or database scopes (e.g., `ds:r:file` or similar) alongside `api:llm-agent-prompt`.

For more advanced usage and available parameters, consult the\
[LLM Agent Prompt Documentation](https://user-apis.verida.network/#934196b1-7136-4f27-a593-0750bcfe6fa9).

***

### 3. LLM Profile Prompt

* **Summary**: Generates or refines a **user profile** by analyzing user data. Ideal for creating advanced personalized experiences, such as dynamic user profiles, recommendation engines, or curated content based on a user’s personal data footprint.
* **Credits Usage**: **10 credits**
* **Scope Required**: `api:llm-profile-prompt`

#### Example Usage

```bash
curl -X POST "https://api.verida.ai/api/rest/v1/llm/profile-prompt" \
     -H "Authorization: Bearer YOUR_AUTH_TOKEN" \
     -H "Content-Type: application/json" \
     -d '{
       "prompt": "Generate a professional summary and skill set based on user’s resume data.",
       "context": {
         "dsUrlEncoded": "aHR0cHM6Ly9jb21tb24uc2NoZW1hcy52ZXJpZGEuaW8vZmlsZS92MC4xLjAvc2NoZW1hLmpzb24=", 
         "queryFilters": { "documentType": "resume" }
       }
     }'
```

**Response** (example):

```json
{
  "completion": "John is a full-stack developer with 5+ years experience in React, Node.js, and blockchain..."
}
```

> **Tip**: Because `api:llm-profile-prompt` can involve analyzing potentially large volumes of user data, it consumes more credits (10 credits). Make sure your token and user have granted the necessary access to the relevant datastores or databases.

For detailed query structures, limitations, and best practices, check the\
[LLM Profile Prompt Documentation](https://user-apis.verida.network/#934196b1-7136-4f27-a593-0750bcfe6fa9).

***

### Best Practices

1. **Minimal Scope Principle**\
   Only request the LLM scope(s) you truly need. For instance, if you only require basic text generation, request `api:llm-prompt` rather than the more credit-expensive `api:llm-agent-prompt` or `api:llm-profile-prompt`.
2. **Efficient Prompting**\
   Write concise prompts and consider the size of any included user context to avoid unnecessary token or data usage.
3. **Store Results Securely**\
   If you need to retain LLM-generated data, store it in a datastore or database with the appropriate permissions.
4. **Token & Scope Validation**\
   Always confirm your `auth_token` includes the correct LLM scope before invoking these endpoints.
5. **Handle Errors Gracefully**\
   LLM endpoints may return standard HTTP error codes or custom error messages. Review responses carefully and provide clear feedback to users if something goes wrong.
