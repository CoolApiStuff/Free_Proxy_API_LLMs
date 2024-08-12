# QuantumAI API Documentation

## Table of Contents

- [Overview](#overview)
- [Free vs. Premium Features](#free-vs-premium-features)
- [Pricing](#pricing)
- [API Capacities and Limits](#api-capacities-and-limits)
- [Free Version Features](#free-version-features)
- [Premium Version Features](#premium-version-features)
- [Authentication Methods](#authentication-methods)
- [Endpoints](#endpoints)
    - [Models List](#models-list)
    - [Chat Completions](#chat-completions)
- [Code Examples](#code-examples)
- [Rate Limiting](#rate-limiting)
- [Error Handling](#error-handling)
- [Available Models](#available-models)

<a name="overview"></a>
## Overview

The QuantumAI API provides access to a wide range of Large Language Models (LLMs) for various tasks, including text embedding, code generation, chatbots, image generation, and speech-to-text. It offers both free and premium (QuantumAI Pro and Enterprise) plans with different usage limits and features.

<a name="free-vs-premium-features"></a>
## Free vs. Premium Features

| Feature | Free Version | QuantumAI Pro | Enterprise |
|---|---|---|---|
| Requests per Day | 850 | 7500 | 1,000,000 (Negotiable) |
| Requests per Minute | 10 | 30 | 300,000 (Negotiable) |
| Early Access to Models | No | Yes | Yes |
| Custom Plans Available | No | Yes | Yes |
| Access to All Models | Limited | Yes | Yes |

<a name="pricing"></a>
## Pricing

| Plan | Price |
|---|---|
| Free | Free |
| Paid | Not Specified |
| QuantumAI Pro Monthly | $10/month |
| QuantumAI Pro Lifetime | $50 one-time payment |
| QuantumAI Pro Yearly | $120/year |
| Enterprise | Contact for custom pricing |

<a name="api-capacities-and-limits"></a>
## API Capacities and Limits

| Plan | Requests per Day | Requests per Minute |
|---|---|---|
| Free | 850 | 10 |
| Paid | 8500 | 20 |
| QuantumAI Pro | 7500 | 30 |
| Enterprise | 1,000,000 (Negotiable) | 300,000 (Negotiable) |

<a name="free-version-features"></a>
## Free Version Features

The free version of QuantumAI allows users to access a limited set of models with a daily limit of 850 requests and a per-minute limit of 10 requests. 

<a name="premium-version-features"></a>
## Premium Version Features

**QuantumAI Pro:**

* **Early Access to Models:** Pro users get early access to new and advanced models before they are released to the public.
* **Higher Rate Limits:** Pro users have significantly higher rate limits, allowing for more frequent requests.
* **Access to All Models:** Pro users have access to all available models, including Claude 3 Opus, CMDR+, and more.
* **Custom Plans:** For users with even higher usage needs, custom plans are available upon request.

**Enterprise:**

* **Highest Rate Limits:** Enterprise users have the highest rate limits, suitable for large-scale applications.
* **Negotiable Limits:** Request limits can be negotiated based on specific usage requirements.
* **Access to All Models:** Enterprise users have access to all available models.
* **Custom Plans:** Tailored solutions are available to meet specific enterprise needs.

<a name="authentication-methods"></a>
## Authentication Methods

Authentication is handled through an API key. You can manage your API key using the `/manage-key` command in the QuantumAI Discord bot.

<a name="endpoints"></a>
## Endpoints

<a name="models-list"></a>
### Models List

**Endpoint:**

```
https://api.qtm-ai.com/v1/models
```

**Method:**

`GET`

**Description:**

Retrieves a list of all available models.

**Response:**

```json
{
  "object": "list",
  "data": [
    {
      "id": "text-embedding-ada-002",
      "object": "model",
      "created": 1686935002,
      "owned_by": "QTMAI"
    },
    // ... more models
  ]
}
```

<a name="chat-completions"></a>
### Chat Completions

**Endpoint:**

```
https://api.qtm-ai.com/v1/chat/completions
```

**Method:**

`POST`

**Description:**

Sends a request to a specific model for chat completion.

**Parameters:**

* `model` (string, required): The ID of the model to use.
* `messages` (array, required): A list of messages comprising the conversation. Each message is an object with `role` (either "system", "user", or "assistant") and `content` (the message text).
* `temperature` (number, optional): Controls the randomness of the response.
* `max_tokens` (number, optional): Limits the length of the response.
* `n` (number, optional): The number of responses to generate.
* `stop` (string or array, optional): Sequences where the API will stop generating further tokens.
* `presence_penalty` (number, optional): Penalizes new tokens based on their existing presence in the text.
* `frequency_penalty` (number, optional): Penalizes new tokens based on their frequency in the text.
* `logit_bias` (object, optional): Modifies the likelihood of specified tokens appearing in the completion.

**Response:**

```json
{
  "id": "chatcmpl-7t9JcS8v6dPYHfQ4bWI7lQ0l78l8a",
  "object": "chat.completion",
  "created": 1690429140,
  "model": "gpt-3.5-turbo-0613",
  "choices": [
    {
      "index": 0,
      "message": {
        "role": "assistant",
        "content": "Hello there! How can I help you today?"
      },
      "finish_reason": "stop"
    }
  ],
  "usage": {
    "prompt_tokens": 9,
    "completion_tokens": 12,
    "total_tokens": 21
  }
}
```

<a name="code-examples"></a>
## Code Examples

**Python Example using the `requests` library:**

```python
import requests
import json

API_KEY = "YOUR_API_KEY"
BASE_URL = "https://api.qtm-ai.com/v1"

headers = {
    "Authorization": f"Bearer {API_KEY}"
}

# Get list of models
models_response = requests.get(f"{BASE_URL}/models", headers=headers)
print(models_response.json())

# Chat completion example
chat_data = {
    "model": "gpt-3.5-turbo",
    "messages": [{"role": "user", "content": "Hello, how are you?"}]
}
chat_response = requests.post(f"{BASE_URL}/chat/completions", headers=headers, json=chat_data)
print(chat_response.json())
```

<a name="rate-limiting"></a>
## Rate Limiting

Rate limits are in place to ensure fair usage and prevent abuse of the API. The specific limits depend on the chosen plan (see the "API Capacities and Limits" table above). Exceeding these limits may result in temporary suspension of access or other penalties.

<a name="error-handling"></a>
## Error Handling

The API returns standard HTTP status codes to indicate success or failure. Common error codes include:

* **400 Bad Request:** Indicates an invalid request format or missing parameters.
* **401 Unauthorized:** Indicates an invalid or missing API key.
* **429 Too Many Requests:** Indicates that the rate limit has been exceeded.
* **500 Internal Server Error:** Indicates a server-side error.

When an error occurs, the response will include a JSON object with an `error` field containing details about the error.

<a name="available-models"></a>
## Available Models

The QuantumAI API offers access to a wide range of models, including:

* **Text Embedding:** `text-embedding-ada-002`, `text-embedding-3-small`, `text-embedding-3-large`
* **Large Language Models (LLMs):** `gpt-4o`, `gpt-4o-mini`, `gemma2-9b-it`, `llama3-70b-8192`, `gpt-4-turbo`, `gpt-3.5-turbo`, `claude-3.5-sonnet`, `claude-3-opus`, `command-r-plus`, and many more.
* **Code Generation:** `deepseek-coder`
* **Image Generation:** `dall-e-3`, `dall-e-2`
* **Speech-to-Text:** `whisper-large-v3`, `whisper-1`

For a complete and up-to-date list of available models, please refer to the [Models List Endpoint](#models-list).
