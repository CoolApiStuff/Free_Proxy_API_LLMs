# ShuttleAI API Documentation

## Table of Contents

- [Overview](#overview)
- [Features](#features)
    - [Free vs. Premium Features](#free-vs-premium-features)
    - [Pricing](#pricing)
    - [API Capacities and Limits](#api-capacities-and-limits)
- [Free Version Features](#free-version-features)
- [Premium Version Features](#premium-version-features)
- [Authentication Methods](#authentication-methods)
- [Endpoints](#endpoints)
    - [Create Audio Generation](#create-audio-generation)
    - [Create Audio Transcription](#create-audio-transcription)
    - [Create Audio Translation](#create-audio-translation)
    - [Create Chat Completions](#create-chat-completions)
    - [Create Embedding](#create-embedding)
    - [Create Image Generation](#create-image-generation)
    - [Create Moderation](#create-moderation)
- [Code Examples](#code-examples)
    - [Basic Chat Completion](#basic-chat-completion)
    - [Streaming Chat Completion](#streaming-chat-completion)
    - [Tool Calling: Get Current Weather](#tool-calling-get-current-weather)
    - [Web Access](#web-access)
- [Rate Limiting](#rate-limiting)
- [Error Handling](#error-handling)
    - [API Errors](#api-errors)

<a name="overview"></a>

## Overview

The ShuttleAI API provides access to a wide range of AI models for various tasks, including text generation, image generation, audio processing, web search, and more. It offers both free and premium tiers with different features and capabilities.

<a name="features"></a>

## Features

### <a name="free-vs-premium-features"></a>Free vs. Premium Features

| Feature | Free Version | Premium Version |
|---|---|---|
| API Access | Yes | Yes |
| Model Selection | Limited | Extensive |
| Premium Models | No | Yes |
| Private Community | No | Yes |
| Priority API Support | No | Yes |
| Beta Access & Testing | No | Yes |
| Dedicated Servers | No | Yes |

### <a name="pricing"></a>Pricing

| Plan | Price |
|---|---|
| Free | $0 per month |
| Pro | $9.99 per month |
| Business | $19.99 per month |
| Enterprise | $49.99 per month |

### <a name="api-capacities-and-limits"></a>API Capacities and Limits

| Plan | Calls per Minute | Calls per Day |
|---|---|---|
| Free | 5 | 500 |
| Pro | 20 | 3000 |
| Business | 40 | 6000 |
| Enterprise | 100 | 15000 |

<a name="free-version-features"></a>

## Free Version Features

The free version of the ShuttleAI API provides access to a limited selection of models and basic API functionality. Users can make up to 5 calls per minute and 500 calls per day.

<a name="premium-version-features"></a>

## Premium Version Features

Premium versions of the ShuttleAI API offer several advantages over the free version, including:

- Access to a wider range of models, including premium models.
- Higher API call limits.
- Access to a private community for support and discussions.
- Priority API support.
- Beta access to new features and models.
- Dedicated servers for improved performance and reliability.

<a name="authentication-methods"></a>

## Authentication Methods

The ShuttleAI API uses API key authentication. You can obtain your API key from your ShuttleAI dashboard after registering for an account.

To authenticate your API requests, include your API key in the `Authorization` header using the `Bearer` scheme:

```
Authorization: Bearer YOUR_API_KEY
```

**Environment Variables:**

You can simplify authentication by setting your API key as an environment variable. This eliminates the need to manually include the key in your code.

**Windows (cmd):**

```
setx SHUTTLEAI_API_KEY "YOUR_API_KEY"
```

**Windows (PowerShell):**

```
$env:SHUTTLEAI_API_KEY = "YOUR_API_KEY"
```

**Linux/macOS:**

```
export SHUTTLEAI_API_KEY="YOUR_API_KEY"
```

<a name="endpoints"></a>

## Endpoints

### <a name="create-audio-generation"></a>Create Audio Generation

**Endpoint:** `/v1/audio/speech`

**Method:** `POST`

**Description:** Generates audio from text input.

**Request Body:**

| Parameter | Type | Description | Required |
|---|---|---|---|
| `model` | `string` | The ID of the model to use for audio generation. | Yes |
| `input` | `string` | The text to convert to speech. | Yes |
| `voice` | `string` | The voice to use for the generation. Voices can be found [here](VOICE_DOCUMENTATION_URL). | Yes |

**Response:**

| Parameter | Type | Description |
|---|---|---|
| `chars` | `integer` | The number of characters in the generated audio. |
| `data` | `object` | An object containing the generated audio data. |
| `url` | `string` | The URL of the generated audio file. |
| `expiresIn` | `integer` | The time in seconds until the generated audio file expires. |
| `model` | `string` | The ID of the model used for audio generation. |

**Example Request (cURL):**

```curl
curl --request POST \
--url https://api.shuttleai.app/v1/audio/speech \
--header 'Authorization: Bearer <token>' \
--header 'Content-Type: application/json' \
--data '{
"model": "<string>",
"input": "<string>",
"voice": "<string>"
}'
```

**Example Response (JSON):**

```json
{
"chars": 123,
"data": {
},
"url": "<string>",
"expiresIn": 123,
"model": "<string>"
}
```

### <a name="create-audio-transcription"></a>Create Audio Transcription

**Endpoint:** `/v1/audio/transcriptions`

**Method:** `POST`

**Description:** Transcribes audio to text.

**Request Body:**

| Parameter | Type | Description | Required |
|---|---|---|---|
| `file` | `string` | The audio file to transcribe. | Yes |
| `model` | `string` | The ID of the model to use for transcription. Defaults to `whisper-large`. | No |

**Response:**

| Parameter | Type | Description |
|---|---|---|
| `text` | `string` | The transcribed text. |

**Example Request (cURL):**

```curl
curl --request POST \
--url https://api.shuttleai.app/v1/audio/transcriptions \
--header 'Authorization: Bearer <token>' \
--header 'Content-Type: multipart/form-data' \
--form 'file=<string>' \
--form 'model=<string>'
```

**Example Response (JSON):**

```json
{
"text": "<string>"
}
```

### <a name="create-audio-translation"></a>Create Audio Translation

**Endpoint:** `/v1/audio/translations`

**Method:** `POST`

**Description:** Translates audio to text in a different language.

**Request Body:**

| Parameter | Type | Description | Required |
|---|---|---|---|
| `file` | `string` | The audio file to translate. | Yes |
| `model` | `string` | The ID of the model to use for translation. Defaults to `whisper-large`. | No |

**Response:**

| Parameter | Type | Description |
|---|---|---|
| `text` | `string` | The translated text. |

**Example Request (cURL):**

```curl
curl --request POST \
--url https://api.shuttleai.app/v1/audio/translations \
--header 'Authorization: Bearer <token>' \
--header 'Content-Type: multipart/form-data' \
--form 'file=<string>' \
--form 'model=<string>'
```

**Example Response (JSON):**

```json
{
"text": "<string>"
}
```

### <a name="create-chat-completions"></a>Create Chat Completions

**Endpoint:** `/v1/chat/completions`

**Method:** `POST`

**Description:** Generates a chat completion based on a conversation history.

**Request Body:**

| Parameter | Type | Description | Required |
|---|---|---|---|
| `model` | `string` | The ID of the model to use for chat completion. | Yes |
| `messages` | `object[]` | The list of messages in the conversation history. | Yes |
| `max_tokens` | `integer` | The maximum number of tokens to generate. | No |
| `temperature` | `number` | The temperature of the sampling distribution. | No |
| `top_p` | `number` | The cumulative probability of the top tokens to keep in the nucleus of the distribution. | No |
| `tools` | `object[]` | The list of tools to use for the generation. | No |
| `tool_choice` | `string` | The tool choice strategy. Defaults to `auto` for automatic tool choice. | No |
| `internet` | `boolean` | Whether to use the internet for the generation. Model limitations apply. Defaults to `true` for Bing models. | No |
| `citations` | `boolean` | Whether to include citations in the generation. For use in `owned_by: bing/openai` models only. Defaults to `true`. | No |
| `tone` | `string` | The tone of the generation. For use in `owned_by: bing/openai` models only. Defaults to `precise`. | No |
| `raw` | `boolean` | Whether to return the raw response. For use in `owned_by: bing/openai` models only! Returns Bing AI Suggestions and Search Results. Defaults to `false`. | No |
| `image` | `string` | The URL of the image to use for the generation. Model limitations apply. | No |

**Response:**

| Parameter | Type | Description |
|---|---|---|
| `id` | `string` | The ID of the chat completion. |
| `object` | `string` | The object type, which is always `chat.completion`. |
| `created` | `integer` | The timestamp of when the chat completion was created. |
| `model` | `string` | The ID of the model used for chat completion. |
| `choices` | `object[]` | An array of chat completion choices. |
| `usage` | `object` | An object containing token usage information. |
| `system_fingerprint` | `string` | A unique identifier for the system that generated the chat completion. |

**Example Request (cURL):**

```curl
curl --request POST \
--url https://api.shuttleai.app/v1/chat/completions \
--header 'Authorization: Bearer <token>' \
--header 'Content-Type: application/json' \
--data '{
"model": "<string>",
"messages":[
{
"role": "<string>",
"content": "<string>"
}
],
"max_tokens": 123,
"temperature": 123,
"top_p": 123,
"tools": [
{
"type": "<string>",
"function": {
"name": "<string>",
"parameters":{}
}
}
],
"tool_choice": "<string>",
"internet": true,
"citations": true,
"tone": "<string>",
"raw": true,
"image": "<string>"
}'
```

**Example Response (JSON):**

```json
{
"id": "<string>",
"object": "<string>",
"created": 123,
"model": "<string>",
"choices":[
{
"index": 123,
"logprobs": {},
"finish_reason": "<string>",
"message": {
"content": "<string>",
"role": "<string>"
}
}
],
"usage": {
"prompt_tokens": 123,
"completion_tokens": 123,
"total_tokens": 123
},
"system_fingerprint": "<string>"
}
```

### <a name="create-embedding"></a>Create Embedding

**Endpoint:** `/v1/embeddings`

**Method:** `POST`

**Description:** Generates embeddings for text input.

**Request Body:**

| Parameter | Type | Description | Required |
|---|---|---|---|
| `model` | `string` | The ID of the model to use for embedding generation. | Yes |
| `input` | `string` | The text to generate embeddings for. | Yes |

**Response:**

| Parameter | Type | Description |
|---|---|---|
| `object` | `string` | The object type, which is always `embedding`. |
| `data` | `any[]` | An array of embedding values. |
| `model` | `string` | The ID of the model used for embedding generation. |

**Example Request (cURL):**

```curl
curl --request POST \
--url https://api.shuttleai.app/v1/embeddings \
--header 'Authorization: Bearer <token>' \
--header 'Content-Type: application/json' \
--data '{
"model": "<string>",
"input": "<string>"
}'
```

**Example Response (JSON):**

```json
{
"object": "<string>",
"data": [
"<any>"
],
"model": "<string>"
}
```

### <a name="create-image-generation"></a>Create Image Generation

**Endpoint:** `/v1/images/generations`

**Method:** `POST`

**Description:** Generates an image from a text prompt.

**Request Body:**

| Parameter | Type | Description | Required |
|---|---|---|---|
| `model` | `string` | The ID of the model to use for image generation. | Yes |
| `prompt` | `string` | The text prompt describing the desired image. | Yes |

**Response:**

| Parameter | Type | Description |
|---|---|---|
| `created` | `number` | The timestamp of when the image was created. |
| `data` | `object[]` | An array of objects containing the generated image URLs. |

**Example Request (cURL):**

```curl
curl --request POST \
--url https://api.shuttleai.app/v1/images/generations \
--header 'Authorization: Bearer <token>' \
--header 'Content-Type: application/json' \
--data '{
"model": "<string>",
"prompt": "<string>"
}'
```

**Example Response (JSON):**

```json
{
"created": 123,
"data": [
{
"url": "<string>"
}
]
}
```

### <a name="create-moderation"></a>Create Moderation

**Endpoint:** `/v1/moderations`

**Method:** `POST`

**Description:** Analyzes text input for potentially harmful content.

**Request Body:**

| Parameter | Type | Description | Required |
|---|---|---|---|
| `input` | `string` | The text to analyze. | Yes |
| `model` | `string` | The ID of the model to use for moderation. Defaults to `text-moderation-stable`. | No |

**Response:**

| Parameter | Type | Description |
|---|---|---|
| `id` | `string` | The ID of the moderation analysis. |
| `model` | `string` | The ID of the model used for moderation. |
| `result` | `object` | An object containing the moderation analysis results. |

**Example Request (cURL):**

```curl
curl --request POST \
--url https://api.shuttleai.app/v1/moderations \
--header 'Authorization: Bearer <token>' \
--header 'Content-Type: application/json' \
--data '{
"input": "<string>",
"model": "<string>"
}'
```

**Example Response (JSON):**

```json
{
"id": "<string>",
"model": "<string>",
"result": {
"flagged": true,
"categories": {},
"category_scores": {}
}
}
```

<a name="code-examples"></a>

## Code Examples

### <a name="basic-chat-completion"></a>Basic Chat Completion

```python
from shuttleai import AsyncShuttleAI
import asyncio

async def main():
    async with AsyncShuttleAI() as shuttleai:
        response = await shuttleai.chat.completions.create(
            model="shuttle-2-turbo",
            messages=[{"role":"user","content":"write me a short story about bees"}],
            stream=False
        )
        print(response.choices[0].message.content)

if __name__ == "__main__":
    asyncio.run(main())
```

### <a name="streaming-chat-completion"></a>Streaming Chat Completion

```python
from shuttleai import ShuttleAI

async def main():
    async with AsyncShuttleAI("$SHUTTLEAI_API_KEY", timeout=300) as shuttleai:
        response = await shuttleai.chat.completions.create(
            model="gpt-4",
            messages=[{"role": "user", "content": "write me a short story about bees"}],
            stream=True
        )
        async for chunk in response:
            print(chunk.choices[0].delta.content)

if __name__ == "__main__":
    asyncio.run(main())
```

### <a name="tool-calling-get-current-weather"></a>Tool Calling: Get Current Weather

```python
import random
from shuttleai import *

# Define the tool
tools = [
    {
        "type": "function",
        "function": {
            "name": "get_current_weather",
            "description": "Get the current weather in a given location",
            "parameters": {
                "type": "object",
                "properties": {
                    "location": {
                        "type": "string",
                        "description": "The city and state, e.g. San Francisco, CA",
                    },
                    "unit": {"type": "string", "enum": ["celsius", "fahrenheit"]},
                },
                "required": ["location"],
            },
        },
    }
]

# Define the function
def get_current_weather(location: str, unit: str = "fahrenheit"):
    # ... (Implementation for fetching weather data)

# Make the API request
async def main():
    async with ShuttleAsyncClient() as shuttle:
        response = await shuttle.chat_completion(
            model="gemini-pro",
            messages=[{"role": "user", "content": "What is the current weather like in Los Angeles California?"}],
            tools=tools,
            tool_choice="auto"
        )
        # ... (Process the response and call the function)

if __name__ == "__main__":
    asyncio.run(main())
```

### <a name="web-access"></a>Web Access

```python
import json, httpx, asyncio
from urllib.parse import quote
from shuttleai import *

# Define the web search function
def search_web(query: str, model: str = "search-ddg", limit: int = 5):
    # ... (Implementation for web search)

# Define the tool
tools = [
    {
        "type": "function",
        "function": {
            "name": "search_web",
            "description": "Searches the web for a given query.",
            "parameters": {
                # ... (Parameters for web search)
            },
        },
    }
]

# Make the API request
async def main():
    convo = [
        # ... (Conversation history)
    ]
    async with ShuttleAsyncClient("$SHUTTLEAI_API_KEY", 120) as shuttle:
        first_response = await shuttle.chat_completion(
            # ... (API request parameters)
        )
        # ... (Process the response and call the web search function)

if __name__ == "__main__":
    asyncio.run(main())
```

<a name="rate-limiting"></a>

## Rate Limiting

The ShuttleAI API has rate limits to prevent abuse and ensure fair usage for all users. The specific rate limits vary depending on your plan. Refer to the [API Capacities and Limits](#api-capacities-and-limits) table for details.

If you exceed your rate limit, you will receive a `429` error response. You can retry your request after a brief wait.

<a name="error-handling"></a>

## Error Handling

### <a name="api-errors"></a>API Errors

The ShuttleAI API returns standard HTTP status codes to indicate the success or failure of your requests. Here is an overview of common error codes:

| Code | Description | Cause | Solution |
|---|---|---|---|
| `400` | Bad Request | The request body is invalid. | Ensure your request body is valid. |
| `401` | Unauthorized | Missing or invalid `Authorization` header. | Ensure you are sending an `Authorization` header using the `Bearer` scheme with a valid API key. |
| `402` | Payment Required | You are trying to access a premium model without a premium plan. | Upgrade your plan to access this model. |
| `403` | Forbidden | Your API key or IP address has been banned. | Contact ShuttleAI to resolve the issue. |
| `429` | Too Many Requests | You have exceeded your rate limit. | Wait until the next minute or day to continue using the API. |
| `500` | Internal Server Error | Server/provider issues. | Retry your request after a brief wait and contact ShuttleAI if the issue persists. Check the status page. |
| `503` | Service Unavailable | ShuttleAI servers are experiencing high traffic. | Retry your request after a brief wait and contact ShuttleAI if the issue persists. Check the status page. |

**Python Library Errors:**

The official Python library may raise exceptions for various errors. Refer to the library's documentation for details on specific exceptions and how to handle them.
