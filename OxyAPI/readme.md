# Oxygen API Documentation

## Table of Contents
- [Overview](#overview)
- [Free vs. Premium Features](#free-vs-premium-features)
- [Pricing](#pricing)
- [API Capacities and Limits](#api-capacities-and-limits)
- [Free Version Features](#free-version-features)
- [Premium Version Features](#premium-version-features)
- [Authentication Methods](#authentication-methods)
- [Endpoints](#endpoints)
    - [Image Generation](#image-generation)
    - [Audio Speech](#audio-speech)
    - [Image Classification](#image-classification)
    - [Embeddings](#embeddings)
    - [Chat Completion](#chat-completion)
- [Code Examples](#code-examples)
- [Rate Limiting](#rate-limiting)
- [Error Handling](#error-handling)


<a name="overview"></a>
## Overview

The Oxygen API provides access to over 150 Large Language Models (LLMs) for various tasks, including image generation, audio speech synthesis, image classification, embeddings creation, and chat completion. It offers both free and premium tiers, catering to different user needs and project scales.  The API boasts a wide selection of models from various providers, including OpenAI, Anthropic, MetaAI, Alibaba Cloud, and more.

<a name="free-vs-premium-features"></a>
## Free vs. Premium Features

| Feature | Free Version | Premium Version |
|---|---|---|
| Access to Models | Limited Selection | All 150+ Models |
| Request Limits | Lower Limits (see table below) | Higher Limits (see table below) |
| Plugins | Limited | Full Access |
| Support | Community Support | Priority Support |
| Commercial Use | Allowed | Allowed |

<a name="pricing"></a>
## Pricing

| Tier | Price (monthly) |
|---|---|
| Free | $0 |
| Basic | $5.99 |
| Premium | $9.99 |
| Professional | $16.99 |

<a name="api-capacities-and-limits"></a>
## API Capacities and Limits

This table shows the request limits for different models and pricing tiers.  Note that "Max Tokens" refers to the maximum number of tokens that can be generated in a single request, while "Max Context Tokens" refers to the maximum number of tokens that can be included in the prompt.

| Model | Max Tokens | Max Context Tokens | Free Requests | Basic Requests | Premium Requests | Professional Requests |
|---|---|---|---|---|---|---|
| GPT-4 | 4096 | 128000 | 0 | 150 | 500 | 1200 |
| GPT-3.5-Turbo | 4096 | 128000 | 300 | 500 | 700 | 1600 |
| Claude 3.5 | 4096 | 200000 | 0 | 150 | 500 | 1200 |
| ... | ... | ... | ... | ... | ... | ... |

**Note:** This is not an exhaustive list. Refer to the `models.md` file for the complete list of models and their respective limits.


<a name="free-version-features"></a>
## Free Version Features

The free version of the Oxygen API provides a great starting point for exploring the capabilities of various LLMs. It offers:

* Access to a limited selection of models.
* Lower request limits compared to paid tiers.
* Limited access to plugins.
* Community support.

<a name="premium-version-features"></a>
## Premium Version Features

The premium version of the Oxygen API unlocks the full potential of the platform, offering:

* Access to all 150+ LLMs available on the platform.
* Significantly higher request limits.
* Full access to all plugins.
* Priority support.

<a name="authentication-methods"></a>
## Authentication Methods

The Oxygen API uses API keys for authentication. You can obtain your API key from your dashboard after signing up for an account.  Include your API key in the `Authorization` header of your requests as follows:

```
Authorization: Bearer YOUR_API_KEY
```

<a name="endpoints"></a>
## Endpoints

The Oxygen API offers various endpoints for different tasks, each with its own set of parameters and responses.

<a name="image-generation"></a>
### Image Generation

**Endpoint:** `/v1/images/generations`

**Method:** `POST`

**Parameters:**

| Parameter | Type | Description |
|---|---|---|
| `model` | `string` | The ID of the image generation model to use. (e.g., `stable-diffusion-3`) |
| `prompt` | `string` | The text prompt describing the image to generate. |
| `size` | `string` | The desired image size. (e.g., `1024x1024`) |
| `n` | `integer` | The number of images to generate. |

**Response:**

```json
{
  "created": 1681443485,
  "data": [
    {
      "url": "https://example.com/generated_image.png"
    }
  ]
}
```

<a name="audio-speech"></a>
### Audio Speech

**Endpoint:** `/v1/audio/speech`

**Method:** `POST`

**Parameters:**

| Parameter | Type | Description |
|---|---|---|
| `model` | `string` | The ID of the audio speech model to use. (e.g., `eleven_multilingual_v1`) |
| `voice` | `string` | The ID of the voice to use. |
| `text` | `string` | The text to convert to speech. |

**Response:**

```json
{
  "created": 1681443485,
  "data": [
    {
      "url": "https://example.com/generated_audio.mp3"
    }
  ]
}
```

<a name="image-classification"></a>
### Image Classification

**Endpoint:** `/v1/images/classification`

**Method:** `POST`

**Parameters:**

| Parameter | Type | Description |
|---|---|---|
| `model` | `string` | The ID of the image classification model to use. (e.g., `nsfw-mobile-net-2`) |
| `image` | `string` | The URL of the image to classify. |

**Response:**

```json
{
  "created": 1681443485,
  "data": [
    {
      "label": "cat",
      "confidence": 0.95
    }
  ]
}
```

<a name="embeddings"></a>
### Embeddings

**Endpoint:** `/v1/embeddings`

**Method:** `POST`

**Parameters:**

| Parameter | Type | Description |
|---|---|---|
| `model` | `string` | The ID of the embeddings model to use. (e.g., `text-embedding-ada-002`) |
| `input` | `string` | The text to generate embeddings for. |

**Response:**

```json
{
  "created": 1681443485,
  "data": [
    {
      "embedding": [0.1, 0.2, 0.3, ...]
    }
  ]
}
```

<a name="chat-completion"></a>
### Chat Completion

**Endpoint:** `/v1/chat/completions`

**Method:** `POST`

**Parameters:**

| Parameter | Type | Description |
|---|---|---|
| `model` | `string` | The ID of the chat completion model to use. (e.g., `gpt-3.5-turbo`) |
| `messages` | `array` | An array of messages comprising the conversation history. |
| `temperature` | `float` | Controls the randomness of the generated response. |
| `max_tokens` | `integer` | The maximum number of tokens to generate. |

**Response:**

```json
{
  "created": 1681443485,
  "data": [
    {
      "message": {
        "role": "assistant",
        "content": "This is the generated response."
      }
    }
  ]
}
```

<a name="code-examples"></a>
## Code Examples

Here are some code examples for common use cases:

**Python (using the `requests` library):**

```python
import requests

# Replace with your actual API key
API_KEY = "YOUR_API_KEY"

headers = {
    "Authorization": f"Bearer {API_KEY}"
}

# Image Generation
response = requests.post(
    "https://api.oxyapi.uk/v1/images/generations",
    headers=headers,
    json={
        "model": "stable-diffusion-3",
        "prompt": "A cat sitting on a windowsill",
        "size": "1024x1024",
        "n": 1
    }
)

print(response.json())

# Chat Completion
response = requests.post(
    "https://api.oxyapi.uk/v1/chat/completions",
    headers=headers,
    json={
        "model": "gpt-3.5-turbo",
        "messages": [{"role": "user", "content": "What is the capital of France?"}],
        "temperature": 0.7,
        "max_tokens": 100
    }
)

print(response.json())
```

**JavaScript (using the `fetch` API):**

```javascript
// Replace with your actual API key
const API_KEY = "YOUR_API_KEY";

const headers = {
    "Authorization": `Bearer ${API_KEY}`
};

// Image Generation
fetch("https://api.oxyapi.uk/v1/images/generations", {
    method: "POST",
    headers: headers,
    body: JSON.stringify({
        "model": "stable-diffusion-3",
        "prompt": "A cat sitting on a windowsill",
        "size": "1024x1024",
        "n": 1
    })
})
.then(response => response.json())
.then(data => console.log(data));

// Chat Completion
fetch("https://api.oxyapi.uk/v1/chat/completions", {
    method: "POST",
    headers: headers,
    body: JSON.stringify({
        "model": "gpt-3.5-turbo",
        "messages": [{"role": "user", "content": "What is the capital of France?"}],
        "temperature": 0.7,
        "max_tokens": 100
    })
})
.then(response => response.json())
.then(data => console.log(data));
```


<a name="rate-limiting"></a>
## Rate Limiting

The Oxygen API implements rate limiting to prevent abuse and ensure fair usage for all users. The specific rate limits vary depending on your subscription tier.  You can check your current rate limit status by inspecting the response headers.  If you exceed the rate limit, you will receive a `429 Too Many Requests` error.

<a name="error-handling"></a>
## Error Handling

The Oxygen API returns standard HTTP status codes to indicate the success or failure of your requests.  Here are some common error codes and their meanings:

| Status Code | Description |
|---|---|
| `400 Bad Request` | The request was malformed or missing required parameters. |
| `401 Unauthorized` | The API key was invalid or missing. |
| `404 Not Found` | The requested resource was not found. |
| `429 Too Many Requests` | You have exceeded the rate limit. |
| `500 Internal Server Error` | An unexpected error occurred on the server. |

When an error occurs, the response body will contain a JSON object with more details about the error.  Always check the status code and response body to handle errors gracefully in your application.

