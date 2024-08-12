# AnyAI API Documentation

## Table of Contents
1. [Introduction](#introduction)
2. [Rate Limits](#rate-limits)
3. [API Key](#api-key)
4. [Endpoints](#endpoints)
   - [Chat Completions](#chat-completions-endpoint)
   - [Models](#models-endpoint)
   - [Image Generations](#image-generations-endpoint)
   - [Imagine](#imagine-endpoint)
   - [GlobalAsk](#globalask-endpoint)
   - [Vision](#vision-endpoint)
5. [OpenAI Compatibility](#openai-compatibility)
6. [Available Models](#available-models)

## Introduction

This documentation provides information on using the AnyAI API, including rate limits, endpoints, and usage instructions.

## Rate Limits

### Free Plan
| Feature | Per Minute | Per Hour | Per Day |
|---------|------------|----------|---------|
| LLMs | 10 | - | 2000 |
| Closed-Source LLMs | - | 25 | 100 |
| DALL-E 3 | 120 | - | 750 |
| GlobalAsk | 120 | - | 750 |
| Imagine endpoint | - | - | 20 |
| Vision endpoint | - | 25 | 100 |

**Max characters per message:** 1000

### Premium Plan
| Feature | Per Minute | Per Hour | Per Day |
|---------|------------|----------|---------|
| LLMs | 30 | - | 5000 |
| Closed-Source LLMs | - | 50 | 300 |
| DALL-E 3 | 120 | - | 750 |
| GlobalAsk | 120 | - | 750 |
| Imagine endpoint | - | - | 20 |
| Vision endpoint | - | 25 | 100 |

**Max characters per message:** 5000

## API Key

To use the premium features, you need an API key. Include it in the Authorization header:

```
Authorization: Bearer YOUR_API_KEY
```

To check your API key usage:

```
GET /check?key=<YOUR_API_KEY>
```

To obtain an API key, join the Discord server: [https://discord.gg/pMeMK4FwXB](https://discord.gg/pMeMK4FwXB)

## Endpoints

### Chat Completions Endpoint

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

### Models Endpoint

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

### Image Generations Endpoint

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

### Imagine Endpoint

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

### GlobalAsk Endpoint

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

### Vision Endpoint

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

## OpenAI Compatibility

To use the AnyAI API with OpenAI-compatible libraries, set the base URL:

```python
openai.base_url = 'https://api.discord.rocks'
```

## Available Models

The AnyAI API supports a wide range of language models. For the most up-to-date list of available models, please use the [Models Endpoint](#models-endpoint).

Some notable models include:
- GPT-4 and GPT-3.5 variants
- Claude-3 variants
- Llama 2 and Llama 3 variants
- Mixtral and Mistral variants
- Various specialized models (e.g., coding, multilingual)

For the complete list and latest additions, always refer to the Models Endpoint.


---

# Models

{"data":[{"created":1686935002,"id":"claude-3-haiku-20240307","object":"model","owned_by":"anthorpic"},{"created":1686935002,"id":"claude-3-sonnet-20240229","object":"model","owned_by":"anthorpic"},{"created":1686935002,"id":"claude-3-5-sonnet-20240620","object":"model","owned_by":"anthorpic"},{"created":1686935002,"id":"claude-3-opus-20240229","object":"model","owned_by":"anthorpic"},{"created":1686935002,"id":"gpt-4","object":"model","owned_by":"openai"},{"created":1686935002,"id":"gpt-4-0613","object":"model","owned_by":"openai"},{"created":1686935002,"id":"gpt-4-turbo","object":"model","owned_by":"openai"},{"created":1686935002,"id":"gpt-4o-mini-2024-07-18","object":"model","owned_by":"openai"},{"created":1686935002,"id":"gpt-4o-mini","object":"model","owned_by":"openai"},{"created":1686935002,"id":"gpt-3.5-turbo","object":"model","owned_by":"openai"},{"created":1686935002,"id":"gpt-3.5-turbo-0125","object":"model","owned_by":"openai"},{"created":1686935002,"id":"gpt-3.5-turbo-1106","object":"model","owned_by":"openai"},{"created":1686935002,"id":"gpt-3.5-turbo-16k","object":"model","owned_by":"openai"},{"created":1686935002,"id":"gpt-3.5-turbo-0613","object":"model","owned_by":"openai"},{"created":1686935002,"id":"gpt-3.5-turbo-16k-0613","object":"model","owned_by":"openai"},{"created":1686935002,"id":"gpt-4o","object":"model","owned_by":"openai"},{"created":0,"id":"llama-3-70b-chat","object":"model","owned_by":"meta-llama"},{"created":0,"id":"llama-3-70b-chat-turbo","object":"model","owned_by":"meta-llama"},{"created":0,"id":"llama-3-8b-chat","object":"model","owned_by":"meta-llama"},{"created":0,"id":"llama-3-8b-chat-turbo","object":"model","owned_by":"meta-llama"},{"created":0,"id":"llama-3-70b-chat-lite","object":"model","owned_by":"meta-llama"},{"created":0,"id":"llama-3-8b-chat-lite","object":"model","owned_by":"meta-llama"},{"created":0,"id":"llama-2-70b-chat","object":"model","owned_by":"meta-llama"},{"created":0,"id":"llama-2-13b-chat","object":"model","owned_by":"meta-llama"},{"created":0,"id":"llama-2-7b-chat","object":"model","owned_by":"meta-llama"},{"created":0,"id":"llama-3.1-405b-turbo","object":"model","owned_by":"meta-llama"},{"created":0,"id":"llama-3.1-70b-turbo","object":"model","owned_by":"meta-llama"},{"created":0,"id":"llama-3.1-8b-turbo","object":"model","owned_by":"meta-llama"},{"created":0,"id":"LlamaGuard-2-8b","object":"model","owned_by":"meta-llama"},{"created":0,"id":"Yi-34B-Chat","object":"model","owned_by":"01-ai"},{"created":0,"id":"Yi-34B","object":"model","owned_by":"01-ai"},{"created":0,"id":"Yi-6B","object":"model","owned_by":"01-ai"},{"created":0,"id":"Mixtral-8x7B-v0.1","object":"model","owned_by":"mistral-ai"},{"created":0,"id":"Mixtral-8x22B","object":"model","owned_by":"mistral-ai"},{"created":0,"id":"Mixtral-8x7B-Instruct-v0.1","object":"model","owned_by":"mistral-ai"},{"created":0,"id":"Mixtral-8x22B-Instruct-v0.1","object":"model","owned_by":"mistral-ai"},{"created":0,"id":"Mistral-7B-Instruct-v0.1","object":"model","owned_by":"mistral-ai"},{"created":0,"id":"Mistral-7B-Instruct-v0.2","object":"model","owned_by":"mistral-ai"},{"created":0,"id":"Mistral-7B-Instruct-v0.3","object":"model","owned_by":"mistral-ai"},{"created":0,"id":"openchat-3.5","object":"model","owned_by":"openchat"},{"created":0,"id":"WizardLM-13B-V1.2","object":"model","owned_by":"wizardlm"},{"created":0,"id":"WizardCoder-Python-34B-V1.0","object":"model","owned_by":"wizardlm"},{"created":0,"id":"Qwen1.5-0.5B-Chat","object":"model","owned_by":"qwen"},{"created":0,"id":"Qwen1.5-1.8B-Chat","object":"model","owned_by":"qwen"},{"created":0,"id":"Qwen1.5-4B-Chat","object":"model","owned_by":"qwen"},{"created":0,"id":"Qwen1.5-7B-Chat","object":"model","owned_by":"qwen"},{"created":0,"id":"Qwen1.5-14B-Chat","object":"model","owned_by":"qwen"},{"created":0,"id":"Qwen1.5-72B-Chat","object":"model","owned_by":"qwen"},{"created":0,"id":"Qwen1.5-110B-Chat","object":"model","owned_by":"qwen"},{"created":0,"id":"Qwen2-72B-Instruct","object":"model","owned_by":"qwen"},{"created":0,"id":"gemma-2b-it","object":"model","owned_by":"google"},{"created":0,"id":"gemma-7b-it","object":"model","owned_by":"google"},{"created":0,"id":"gemma-2b","object":"model","owned_by":"google"},{"created":0,"id":"gemma-7b","object":"model","owned_by":"google"},{"created":0,"id":"dbrx-instruct","object":"model","owned_by":"databricks"},{"created":0,"id":"vicuna-7b-v1.5","object":"model","owned_by":"lmsys"},{"created":0,"id":"vicuna-13b-v1.5","object":"model","owned_by":"lmsys"},{"created":0,"id":"dolphin-2.5-mixtral-8x7b","object":"model","owned_by":"cognitivecomputations"},{"created":0,"id":"deepseek-coder-33b-instruct","object":"model","owned_by":"deepseek-ai"},{"created":0,"id":"deepseek-coder-67b-instruct","object":"model","owned_by":"deepseek-ai"},{"created":0,"id":"deepseek-llm-67b-chat","object":"model","owned_by":"deepseek-ai"},{"created":0,"id":"Nous-Capybara-7B-V1p9","object":"model","owned_by":"NousResearch"},{"created":0,"id":"Nous-Hermes-2-Mixtral-8x7B-DPO","object":"model","owned_by":"NousResearch"},{"created":0,"id":"Nous-Hermes-2-Mixtral-8x7B-SFT","object":"model","owned_by":"NousResearch"},{"created":0,"id":"Nous-Hermes-llama-2-7b","object":"model","owned_by":"NousResearch"},{"created":0,"id":"Nous-Hermes-Llama2-13b","object":"model","owned_by":"NousResearch"},{"created":0,"id":"Nous-Hermes-2-Yi-34B","object":"model","owned_by":"NousResearch"},{"created":0,"id":"Mistral-7B-OpenOrca","object":"model","owned_by":"Open-Orca"},{"created":0,"id":"alpaca-7b","object":"model","owned_by":"togethercomputer"},{"created":0,"id":"OpenHermes-2-Mistral-7B","object":"model","owned_by":"teknium"},{"created":0,"id":"OpenHermes-2.5-Mistral-7B","object":"model","owned_by":"teknium"},{"created":0,"id":"phi-2","object":"model","owned_by":"microsoft"},{"created":0,"id":"phi-3","object":"model","owned_by":"microsoft"},{"created":0,"id":"WizardLM-2-8x22B","object":"model","owned_by":"microsoft"},{"created":0,"id":"NexusRaven-V2-13B","object":"model","owned_by":"Nexusflow"},{"created":0,"id":"Phind-CodeLlama-34B-v2","object":"model","owned_by":"Phind"},{"created":0,"id":"CodeLlama-7b-Python-hf","object":"model","owned_by":"codellama"},{"created":0,"id":"CodeLlama-7b-Python","object":"model","owned_by":"codellama"},{"created":0,"id":"CodeLlama-13b-Python-hf","object":"model","owned_by":"codellama"},{"created":0,"id":"CodeLlama-34b-Python-hf","object":"model","owned_by":"codellama"},{"created":0,"id":"CodeLlama-70b-Python-hf","object":"model","owned_by":"codellama"},{"created":0,"id":"snowflake-arctic-instruct","object":"model","owned_by":"Snoflake"},{"created":0,"id":"SOLAR-10.7B-Instruct-v1.0","object":"model","owned_by":"upstage"},{"created":0,"id":"StripedHyena-Hessian-7B","object":"model","owned_by":"togethercomputer"},{"created":0,"id":"StripedHyena-Nous-7B","object":"model","owned_by":"togethercomputer"},{"created":0,"id":"Llama-2-7B-32K-Instruct","object":"model","owned_by":"togethercomputer"},{"created":0,"id":"CodeLlama-13b-Instruct","object":"model","owned_by":"togethercomputer"},{"created":0,"id":"evo-1-131k-base","object":"model","owned_by":"togethercomputer"},{"created":0,"id":"OLMo-7B-Instruct","object":"model","owned_by":"allenai"},{"created":0,"id":"Platypus2-70B-instruct","object":"model","owned_by":"garage-bAInd"},{"created":0,"id":"Snorkel-Mistral-PairRM-DPO","object":"model","owned_by":"snorkelai"},{"created":0,"id":"ReMM-SLERP-L2-13B","object":"model","owned_by":"Undi95"},{"created":0,"id":"MythoMax-L2-13b","object":"model","owned_by":"Gryphe"},{"created":0,"id":"chronos-hermes-13b","object":"model","owned_by":"Autism"},{"created":0,"id":"Llama-Guard-7b","object":"model","owned_by":"Meta-Llama"},{"created":0,"id":"gemma-2-9b-it","object":"model","owned_by":"google"},{"created":0,"id":"gemma-2-27b-it","object":"model","owned_by":"google"},{"created":0,"id":"Toppy-M-7B","object":"model","owned_by":"Undi95"},{"created":1686935002,"id":"gemini-1.5-flash","object":"model","owned_by":"google/getlazy.ai"},{"created":1686935002,"id":"gemini-1.5-pro","object":"model","owned_by":"google/getlazy.ai"},{"created":1686935002,"id":"gemini-1.0-pro","object":"model","owned_by":"google/getlazy.ai"},{"created":0,"id":"command-r+","object":"model","owned_by":"cohere"},{"created":0,"id":"sparkdesk","object":"model","owned_by":"iFlytek"}],"object":"list"}