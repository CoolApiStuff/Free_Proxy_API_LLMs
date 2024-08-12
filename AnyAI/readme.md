# AnyAI API Documentation

## Table of Contents

- [Introduction](#introduction)
- [Free vs. Premium Features](#free-vs-premium-features)
- [Pricing](#pricing)
- [API Capacities and Limits](#api-capacities-and-limits)
- [Free Version Features](#free-version-features)
- [Premium Version Features](#premium-version-features)
- [Authentication Methods](#authentication-methods)
- [Rate Limits](#rate-limits)
- [Endpoints](#endpoints)
    - [Chat Completions](#chat-completions-endpoint)
    - [Models](#models-endpoint)
    - [Image Generations](#image-generations-endpoint)
    - [Imagine](#imagine-endpoint)
    - [GlobalAsk](#globalask-endpoint)
    - [Vision](#vision-endpoint)
- [OpenAI Compatibility](#openai-compatibility)
- [Available Models](#available-models)
- [Error Handling](#error-handling)
- [Code Examples](#code-examples)


<a name="introduction"></a>
## Introduction

The AnyAI API provides access to a wide range of Large Language Models (LLMs) and AI functionalities, including chat completions, image generation, and knowledge retrieval. This documentation details the API's functionalities, rate limits, endpoints, and usage instructions. It offers both free and premium plans with varying capabilities and access to both open-source and closed-source models.

<a name="free-vs-premium-features"></a>
## Free vs. Premium Features

| Feature | Free Version | Premium Version |
|---|---|---|
| Access to Open-Source LLMs | Yes | Yes |
| Access to Closed-Source LLMs | Limited (100 requests/day) | More (300 requests/day) |
| DALL-E 3 Requests | 750 requests/day | 750 requests/day |
| GlobalAsk Requests | 750 requests/day | 750 requests/day |
| Imagine Endpoint Requests | 20 requests/day | 20 requests/day |
| Vision Endpoint Requests | 100 requests/day | 100 requests/day |
| Max Characters per Message | 1000 | 5000 |
| API Key Required | No | Yes |


<a name="pricing"></a>
## Pricing

While the documentation doesn't explicitly mention the pricing for the premium plan, it indicates that further information is needed regarding the cost per million tokens for different models. To obtain an API key and clarify the pricing structure, you need to join their Discord server: [https://discord.gg/pMeMK4FwXB](https://discord.gg/pMeMK4FwXB).

<a name="api-capacities-and-limits"></a>
## API Capacities and Limits

| Feature | Free Plan | Premium Plan |
|---|---|---|
| LLMs (Open-source models) | 2000 requests/day, 10 requests/minute | 5000 requests/day, 30 requests/minute |
| Closed-Source LLMs (GPT-4, Claude models) | 100 requests/day, 25 requests/hour | 300 requests/day, 50 requests/hour |
| DALL-E 3 | 750 requests/day, 120 requests/minute | 750 requests/day, 120 requests/minute |


<a name="free-version-features"></a>
## Free Version Features

The free version of the AnyAI API provides access to:

- Limited access to closed-source LLMs like GPT-4 and Claude models (100 requests/day).
- Full access to open-source LLMs like Llama 2.
- DALL-E 3 image generation (750 requests/day).
- GlobalAsk knowledge retrieval (750 requests/day).
- Imagine endpoint for image generation (20 requests/day).
- Vision endpoint for image analysis (100 requests/day).
- Maximum of 1000 characters per message.


<a name="premium-version-features"></a>
## Premium Version Features

The premium version of the AnyAI API offers:

- Increased access to closed-source LLMs (300 requests/day).
- Full access to open-source LLMs.
- DALL-E 3 image generation (750 requests/day).
- GlobalAsk knowledge retrieval (750 requests/day).
- Imagine endpoint for image generation (20 requests/day).
- Vision endpoint for image analysis (100 requests/day).
- Increased maximum characters per message to 5000.


<a name="authentication-methods"></a>
## Authentication Methods

To use the premium features, you need an API key. Include it in the Authorization header:

```
Authorization: Bearer YOUR_API_KEY
```

You can obtain an API key by joining the Discord server: [https://discord.gg/pMeMK4FwXB](https://discord.gg/pMeMK4FwXB)


<a name="rate-limits"></a>
## Rate Limits

The API has different rate limits for free and premium users. These limits are detailed in the tables in the [Free vs. Premium Features](#free-vs-premium-features) and [API Capacities and Limits](#api-capacities-and-limits) sections.


<a name="endpoints"></a>
## Endpoints

### <a name="chat-completions-endpoint"></a> Chat Completions Endpoint

**URL:** `/v1/chat/completions` or `/chat/completions`

**Method:** POST

**Request Body:**

```json
{
  "model": "claude-3-opus",
  "messages": [
    {"role": "system", "content": "System prompt (only the first message, once)"},
    {"role": "user", "content": "Message content"},
    {"role": "assistant", "content": "Assistant response"}
  ],
  "max_tokens": 2048,
  "stream": false,
  "temperature": 0.7,
  "top_p": 0.5,
  "top_k": 0
}
```

**Response:**

```json
{
  "id": "chatcmpl-123",
  "object": "chat.completion",
  "created": 1677652288,
  "model": "claude-3-opus",
  "system_fingerprint": "fp_44709d6fcb",
  "choices": [{
    "index": 0,
    "message": {
      "role": "assistant",
      "content": "Response content"
    },
    "logprobs": null,
    "finish_reason": "stop"
  }],
  "usage": {
    "prompt_tokens": 9,
    "completion_tokens": 12,
    "total_tokens": 21
  }
}
```

### <a name="models-endpoint"></a> Models Endpoint

**URL:** `/v1/models` or `/models`

**Method:** GET

**Response:**

```json
{
  "object": "list",
  "data": [
    {
      "id": "model-id",
      "object": "model",
      "created": 1686935002,
      "owned_by": "provider"
    },
    ...
  ]
}
```

### <a name="image-generations-endpoint"></a> Image Generations Endpoint

**URL:** `/v1/images/generations` or `/images/generations`

**Method:** POST

**Request Body:**

```json
{
  "prompt": "A futuristic cityscape",
  "model": "dall-e-3",
  "n": 1,
  "quality": "hd",
  "response_format": "url",
  "size": "1024x1024"
}
```

**Response:**

```json
{
  "created": 1686935002,
  "data": [
    {
      "url": "https://example.com/generated_image.png"
    }
  ]
}
```

### <a name="imagine-endpoint"></a> Imagine Endpoint

**URL:** `/v1/imagine` or `/imagine`

**Method:** GET

**Query Parameters:**

- `prompt`: Description of the image to generate
- `negative_prompt`: Elements to exclude from the image (optional)
- `width`: Image width (default: 1024)
- `height`: Image height (default: 1024)
- `steps`: Number of generation steps (default: 50)
- `seed`: Random seed for reproducibility (optional)
- `model`: "sdxl", "pluto", "dall-e-2", or "dall-e-3" (default: "sdxl")

**Note:** The Pluto model only accepts the "prompt" and "negative_prompt" parameters.

**Response:** PNG image (Content-Type: image/png)

**Example:**

```
GET /v1/imagine?prompt=A+beautiful+landscape&negative_prompt=rain&width=1024&height=1024&steps=50&seed=123456&model=sdxl
```

### <a name="globalask-endpoint"></a> GlobalAsk Endpoint

**URL:** `/v1/ask` or `/ask`

**Method:** GET

**Query Parameters:**

- `prompt`: The question or prompt for GlobalAsk

**Response:** Text/event-stream with JSON chunks

**Example Response Chunk:**

```json
{
  "message": "Response message",
  "url": "Source URL"
}
```

**GlobalAsk Playground:** [https://api.discord.rocks/globalask-playground](https://api.discord.rocks/globalask-playground)

### <a name="vision-endpoint"></a> Vision Endpoint

**URL:** `/v1/images/vision` or `/images/vision`

**Method:** GET

**Query Parameters:**

- `url`: URL of the image to be described
- `model`: Vision model to use (optional, default: "gemini-pro-vision")

**Valid models:** "gpt-4o", "gpt-4o-mini", "gemini-pro-vision"

**Response:** String description of the image

**Example:**

```
GET /v1/images/vision?url=https://example.com/image.png&model=gemini-pro-vision
```


<a name="openai-compatibility"></a>
## OpenAI Compatibility

To use the AnyAI API with OpenAI-compatible libraries, set the base URL:

```python
openai.base_url = 'https://api.discord.rocks'
```


<a name="available-models"></a>
## Available Models

The AnyAI API supports a wide range of language models. For the most up-to-date list of available models, please use the [Models Endpoint](#models-endpoint).

Some notable models include:

- GPT-4 and GPT-3.5 variants
- Claude-3 variants
- Llama 2 and Llama 3 variants
- Mixtral and Mistral variants
- Various specialized models (e.g., coding, multilingual)

**Closed-Source Models:**

| Model | Provider |
|---|---|
| GPT-4 | OpenAI |
| Claude-3-opus | Anthropic |
| Gemini-1.5-pro | Google |
| GPT-4-turbo | OpenAI |
| Claude-3-sonnet | Anthropic |
| Gemini-1.0-pro | Google |
| GPT-3.5-turbo | OpenAI |
| Claude-3-haiku | Anthropic |

**Open-Source Models:**

| Model | Provider |
|---|---|
| Mixtral-8x22B | Mistral AI |
| LLaMA-3-70B-chat | Meta |
| Cohere Command-r+ | Cohere |
| Yi-34B-Chat | 01-ai |
| Qwen2-72B-Instruct | Qwen |
| WizardLM-2-8x22B | Microsoft |
| Mistral-7B-Instruct-v0.3 | Mistral AI |
| Nous-Hermes-2-Mixtral-8x7B-DPO | NousResearch |
| Qwen1.5-72B-Chat | Qwen |
| DeepSeek-LLM-67B-Chat | DeepSeek AI |
| SOLAR-10.7B-Instruct-v1.0 | Upstage |
| Phi-3 | Microsoft |
| OLMo-7B-Instruct | AllenAI |
| Gemma-7B-it | Google |
| OpenChat-3.5 | OpenChat |
| Vicuna-13B-v1.5 | LMSYS |
| CodeLlama-34B-Python | Meta |
| Sparkdesk | iFlytek |


<a name="error-handling"></a>
## Error Handling

While the documentation doesn't explicitly provide error handling guidelines, it's recommended to implement robust error handling in your applications. This includes:

- Checking for HTTP status codes in the responses.
- Parsing error messages returned in the response body.
- Implementing retry mechanisms with exponential backoff for transient errors.
- Setting appropriate timeouts for requests.


<a name="code-examples"></a>
## Code Examples

**Python Example (Chat Completion):**

```python
import openai

openai.base_url = 'https://api.discord.rocks'
openai.api_key = 'YOUR_API_KEY'

response = openai.ChatCompletion.create(
  model="gpt-3.5-turbo",
  messages=[
    {"role": "system", "content": "You are a helpful assistant."},
    {"role": "user", "content": "What is the capital of France?"}
  ]
)

print(response.choices[0].message.content)
```

**Python Example (Image Generation):**

```python
import openai

openai.base_url = 'https://api.discord.rocks'
openai.api_key = 'YOUR_API_KEY'

response = openai.Image.create(
  prompt="A futuristic cityscape",
  n=1,
  size="1024x1024"
)

image_url = response.data[0].url
print(image_url)
```
