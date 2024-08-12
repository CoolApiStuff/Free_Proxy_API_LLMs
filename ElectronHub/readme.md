# Electron Hub API Documentation

## Table of Contents
- [Overview](#overview)
- [Subscription Plans](#subscription-plans)
  - [Free vs. Premium Features](#free-vs-premium-features)
  - [Pricing Table](#pricing-table)
  - [API Capacities and Limits](#api-capacities-and-limits)
- [Free Version Features](#free-version-features)
- [Premium Version Features](#premium-version-features)
- [Authentication Methods](#authentication-methods)
- [Endpoints](#endpoints)
- [Available Models](#available-models)
    - [Chat Models](#chat-models)
    - [Image Models](#image-models)
    - [Video Models](#video-models)
    - [Audio Models](#audio-models)
- [Code Examples](#code-examples)
- [Rate Limiting](#rate-limiting)
- [Error Handling](#error-handling)

<a name="overview"></a>
## Overview

The Electron Hub API provides access to a wide range of AI models, encompassing capabilities such as text and code generation, image and audio creation, and even video generation.  It offers a flexible and cost-effective solution for developers and businesses seeking to integrate AI functionalities into their applications.

<a name="subscription-plans"></a>
## Subscription Plans

Electron Hub provides various subscription plans tailored to diverse needs. Each plan offers distinct benefits and limitations:


<a name="free-vs-premium-features"></a>
### Free vs. Premium Features

| Feature                      | Free Version              | Starter Plan             | Pro Plan                | Business Plan           |
|------------------------------|---------------------------|--------------------------|-------------------------|--------------------------|
| Daily Credits                | 500                      | 4,000                     | 10,000                  | 30,000                   |
| Messages (GPT-4o)          | 100                      | 800                      | 2,000                   | 6,000                    |
| Rate Limit (requests/min)    | 5                         | 20                        | 40                      | 60                       |
| Support                      | Basic bug and error support | Priority bug and error support | Higher priority for bugs, API, coding | Highest priority for all issues |
| Advanced Features            | No                        | Yes                       | Yes                      | Yes                       |
| Early Access to New Models  | No                        | No                        | Yes                      | Yes                       |
| Hands-on Coding Assistance  | No                        | No                        | No                       | Yes                       |


<a name="pricing-table"></a>
### Pricing Table

| Plan        | Price (monthly) |
|--------------|-----------------|
| Free         | $0              |
| Starter       | $5              |
| Pro           | $29             |
| Business     | $49             |


<a name="api-capacities-and-limits"></a>
### API Capacities and Limits

| Plan        | Daily Credits | Messages (GPT-4o) | Rate Limit (requests/min) |
|--------------|---------------|-------------------|---------------------------|
| Free         | 500           | 100              | 5                        |
| Starter       | 4,000          | 800              | 20                       |
| Pro           | 10,000         | 2,000            | 40                      |
| Business     | 30,000         | 6,000            | 60                       |


<a name="free-version-features"></a>
## Free Version Features

The Free Plan offers basic functionalities to get started with the Electron Hub API:

- **500 daily credits:** Allows for experimentation and testing of various models.
- **Basic support:** Provides assistance with bugs and errors.
- **Limited rate limit:** 5 requests per minute.


<a name="premium-version-features"></a>
## Premium Version Features

Premium plans unlock enhanced features and higher usage limits:

- **Increased daily credits:** Enables more extensive usage and larger-scale projects.
- **Priority support:** Offers faster and more comprehensive assistance.
- **Higher rate limits:** Facilitates smoother integration and faster response times.
- **Access to advanced features:** Unlocks specific models and functionalities not available in the Free Plan.
- **Early access to new models:** Provides a competitive edge by granting access to the latest AI advancements.
- **Hands-on coding assistance (Business Plan):** Offers personalized support for coding, API integrations, and more.


<a name="authentication-methods"></a>
## Authentication Methods

**API Key:**

To use the Electron Hub API, you need to obtain an API key. You can create your API key using the `/key` command at ⁠︱💬・text-ai.

**How to use your API Key:**

Include your API key in the `Authorization` header of your requests, prefixed with `Bearer`. For example:

```
Authorization: Bearer YOUR_API_KEY
```

<a name="endpoints"></a>
## Endpoints

**Base URLs:**

- `https://api.electronhub.top/`
- `https://api.electronhub.top/v1`

**Endpoints Table:**

| Endpoint                    | Methods                      | URL                                                 | Description                                                                  |
|-----------------------------|------------------------------|----------------------------------------------------|------------------------------------------------------------------------------|
| Models                      | GET, POST, PUT, PATCH, HEAD | `https://api.electronhub.top/models`                | Retrieve information about available models or manage custom models.          |
|                             |                               | `https://api.electronhub.top/v1/models`            |                                                                              |
|                             |                               | `https://api.electronhub.top/models/{model}`        | Retrieve information about a specific model.                                |
|                             |                               | `https://api.electronhub.top/v1/models/{model}`      |                                                                              |
| Chat Completions            | POST, OPTIONS               | `https://api.electronhub.top/chat/completions`      | Generate text completions using chat-based models.                            |
|                             |                               | `https://api.electronhub.top/v1/chat/completions`    |                                                                              |
| Image Generations           | POST, OPTIONS               | `https://api.electronhub.top/images/generations`     | Generate images from text prompts.                                            |
|                             |                               | `https://api.electronhub.top/v1/images/generations`   |                                                                              |
| Image Edits                 | POST, OPTIONS               | `https://api.electronhub.top/images/edits`           | Edit or modify existing images.                                               |
|                             |                               | `https://api.electronhub.top/v1/images/edits`         |                                                                              |
| Text-to-Speech              | POST, OPTIONS               | `https://api.electronhub.top/audio/speech`          | Convert text to speech.                                                      |
|                             |                               | `https://api.electronhub.top/v1/audio/speech`        |                                                                              |
| Music Generations (Custom) | POST, OPTIONS               | `https://api.electronhub.top/audio/music`           | Generate custom music.                                                       |
|                             |                               | `https://api.electronhub.top/v1/audio/music`         |                                                                              |
| Video Generations (Custom) | POST, OPTIONS               | `https://api.electronhub.top/videos/generations`     | Generate custom videos.                                                       |
|                             |                               | `https://api.electronhub.top/v1/videos/generations`   |                                                                              |

<a name="available-models"></a>
## Available Models

Electron Hub offers a diverse selection of AI models categorized by their function:

<a name="chat-models"></a>
### Chat Models

These models are designed for conversational AI and text generation tasks.

| Model                           | Tokens     | Endpoint               | Cost (credits) |
|---------------------------------|-------------|-------------------------|----------------|
| gpt-3.5-turbo                    | 4000       | `/v1/chat/completions`  | 1              |
| gpt-3.5-turbo-vision             | 4000       | `/v1/chat/completions`  | 2              |
| gpt-3.5-turbo-16k                | 16000      | `/v1/chat/completions`  | 1              |
| gpt-3.5-turbo-16k-0613           | 16000      | `/v1/chat/completions`  | 1              |
| ... (see `models.md` for the full list) | ... | ... | ... |

<a name="image-models"></a>
### Image Models

These models are capable of generating and editing images based on text prompts.

| Model                         | Tokens   | Endpoint(s)                           | Cost (credits) | NSFW |
|------------------------------|----------|----------------------------------------|----------------|------|
| stable-diffusion-v1-4         | 100      | `/v1/images/generations`              | 2              | No   |
| stable-diffusion-v2           | 100      | `/v1/images/generations`              | 2              | No   |
| stable-diffusion-v2-1         | 100      | `/v1/images/generations`              | 2              | No   |
| ... (see `models.md` for the full list) | ... | ... | ... | ... |


<a name="video-models"></a>
### Video Models

These models are designed for generating custom videos.

| Model          | Tokens | Endpoint              | Cost (credits) |
|-----------------|--------|----------------------|----------------|
| t2v-turbo       | 80     | `/v1/videos/generations` | 30             |
| svd-turbo       | 80     | `/v1/videos/generations` | 20             |
| dream-machine   | 500    | `/v1/videos/generations` | 80             |


<a name="audio-models"></a>
### Audio Models

These models are used for text-to-speech and music generation tasks.

| Model                      | Tokens | Endpoint          | Cost (credits) |
|---------------------------|--------|--------------------|----------------|
| eleven-multilingual-v2     | 500    | `/v1/audio/speech` | 5              |
| suno-v3.5                 | 500    | `/v1/audio/music`  | 20             |

---

<a name="code-examples"></a>
## Code Examples

This section provides code examples for common use cases, demonstrating how to interact with the Electron Hub API using different programming languages.

**Example: Generating Text with GPT-3.5-turbo using Python:**

```python
import requests
import json

api_key = "YOUR_API_KEY"
url = "https://api.electronhub.top/v1/chat/completions"
headers = {
    "Authorization": f"Bearer {api_key}",
    "Content-Type": "application/json"
}

data = {
    "model": "gpt-3.5-turbo",
    "messages": [{"role": "user", "content": "Write a short story about a cat."}]
}

response = requests.post(url, headers=headers, data=json.dumps(data))

if response.status_code == 200:
    print(response.json()["choices"][0]["message"]["content"])
else:
    print(f"Request failed with status code: {response.status_code}")
```

**Example: Generating an Image with Stable Diffusion using JavaScript:**

```javascript
const apiKey = "YOUR_API_KEY";
const url = "https://api.electronhub.top/v1/images/generations";
const headers = {
  Authorization: `Bearer ${apiKey}`,
  "Content-Type": "application/json"
};

const data = {
  model: "stable-diffusion-v1-4",
  prompt: "A futuristic cityscape with flying cars"
};

fetch(url, {
  method: "POST",
  headers: headers,
  body: JSON.stringify(data)
})
  .then(response => response.json())
  .then(data => console.log(data.data[0].url))
  .catch(error => console.error("Error:", error));
```

<a name="rate-limiting"></a>
## Rate Limiting

The Electron Hub API employs rate limiting to ensure fair usage and prevent abuse. The specific rate limits vary depending on your subscription plan:

| Plan        | Rate Limit (requests/min) |
|--------------|---------------------------|
| Free         | 5                         |
| Starter       | 20                        |
| Pro           | 40                      |
| Business     | 60                       |

If you exceed the rate limit for your plan, you will receive a `429 Too Many Requests` error.  Implement proper error handling and backoff mechanisms in your application to gracefully handle rate limiting.

<a name="error-handling"></a>
## Error Handling

The Electron Hub API returns standard HTTP status codes to indicate the success or failure of your requests.  Familiarize yourself with these codes to effectively handle errors:

| Status Code | Description                                                                                                                                                                  |
|-------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 200         | OK - The request was successful.                                                                                                                                                |
| 400         | Bad Request - The request was malformed or missing required parameters.                                                                                                           |
| 401         | Unauthorized - The API key is invalid or missing.                                                                                                                            |
| 403         | Forbidden - You do not have permission to access the requested resource.                                                                                                      |
| 429         | Too Many Requests - You have exceeded the rate limit for your plan.                                                                                                            |
| 500         | Internal Server Error - An unexpected error occurred on the server.                                                                                                           |

**Recommendations:**

- Implement robust error handling in your application to catch and handle potential errors gracefully.
- Use the returned status codes and error messages to diagnose and resolve issues.
- Consider implementing exponential backoff strategies to handle rate limiting errors effectively.



