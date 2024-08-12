# GPT4ALL API Documentation

## Table of Contents

- [Overview](#overview)
- [Free vs. Premium Features](#free-vs-premium-features)
- [Pricing](#pricing)
- [API Capacities and Limits](#api-capacities-and-limits)
- [Free Version Features](#free-version-features)
- [Premium Version Features](#premium-version-features)
- [Authentication Methods](#authentication-methods)
- [Endpoints](#endpoints)
    - [/v1/chat/completions](#v1chatcompletions)
    - [/v1/image/generations](#v1imagegenerations)
- [Code Examples](#code-examples)
- [Rate Limiting](#rate-limiting)
- [Error Handling](#error-handling)
- [Specific Model Details](#models)
    - [OpenAI Models](#openai-models)
    - [Open Source Models](#open-source-models)
- [Pricing Per Model](#pricing-per-model)
    - [Price per 1K tokens (LLMs)](#price-per-1k-tokens-llms)
    - [Price per generation (Image generators models)](#price-per-generation-image-generators-models)
- [Additional Information](#additional-information)

<a name="overview"></a>
## Overview

The GPT4ALL API provides access to a variety of large language models (LLMs) and image generation models, including those from OpenAI and open-source providers. It offers both free and premium tiers, each with different capabilities and limitations. This documentation details the API's functionality, pricing, and usage guidelines.

<a name="free-vs-premium-features"></a>
## Free vs. Premium Features

| Feature                     | Free Version                                 | Premium Version                                    |
|------------------------------|---------------------------------------------|----------------------------------------------------|
| Monthly Balance              | $4                                         | $20 - Unlimited (depending on the tier)           |
| Access to Premium Models     | Limited                                     | All models available                             |
| Rate Limits                  | Lower (e.g., 15 requests/minute for chat) | Higher (e.g., 50-12000 requests/minute for chat) |
| Daily Request Limits         | Lower (e.g., 200 requests/day for chat)   | Higher (e.g., 800-12000 requests/day for chat)   |
| Image Generation Limits      | Lower (e.g., 8 requests/minute)            | Higher (e.g., 30-350 requests/day)               |


<a name="pricing"></a>
## Pricing

| Tier   | Monthly Fee | Balance      | Access to Premium Models |
|--------|--------------|--------------|------------------------------|
| Free   | $0           | $4           | Limited                      |
| Tier 1 | $5           | $20/month    | Yes                          |
| Tier 2 | $8           | $40/month    | Yes                          |
| Tier 3 | $12          | Unlimited    | Yes                          |
| Tier 4 | $16          | Unlimited    | Yes                          |
| Tier 5 | $20          | Unlimited    | Yes                          |
| Tier 6 | $24          | Unlimited    | Yes                          |


<a name="api-capacities-and-limits"></a>
## API Capacities and Limits

| Endpoint                     | Free       | Tier 1      | Tier 2      | Tier 3   | Tier 4   | Tier 5   | Tier 6   |
|-----------------------------|------------|-------------|-------------|----------|----------|----------|----------|
| `/v1/chat/completions`     | 15/m 200/d | 50/m 800/d  | 80/m 1300/d | 2500/d   | 4200/d   | 7500/d   | 12000/d  |
| `/v1/image/generations`    | 8/m 60/d   | 30/m 120/d  | 60/m 160/d  | 350/d    | 350/d    | 350/d    | 350/d    |

*Note: The rates are expressed as requests per minute (m) and requests per day (d).*

<a name="free-version-features"></a>
## Free Version Features

- Access to a limited set of LLMs and image generation models.
- $4 monthly balance for usage.
- Lower rate limits compared to premium tiers.

<a name="premium-version-features"></a>
## Premium Version Features

- Access to all available LLMs and image generation models, including premium models like GPT-4.
- Increased monthly balance or unlimited usage depending on the tier.
- Significantly higher rate limits, allowing for more frequent requests.


<a name="authentication-methods"></a>
## Authentication Methods

To use the GPT4ALL API, you need to obtain an API token. You can get your token by using the `/token` command in the [GPT4ALL Telegram bot](https://t.me/gpt4all_robot).

<a name="endpoints"></a>
## Endpoints

### <a name="v1chatcompletions"></a> /v1/chat/completions

This endpoint is used for interacting with the chat-based LLMs.

**Parameters:**

- `model` (string): The name of the model to use (e.g., "gpt-4o-mini", "gpt-3.5-turbo").
- `messages` (array): An array of message objects, each with a `role` (either "system", "user", or "assistant") and `content` (the text of the message).
- `stream` (boolean): Whether to stream the response back or wait for the entire response to be generated.

**Response:**

- `choices` (array): An array of choice objects, each with a `message` object containing the generated text.
- `usage` (object): An object containing information about the token usage.

### <a name="v1imagegenerations"></a> /v1/image/generations

This endpoint is used for generating images using the available image generation models.

**Parameters:**

- `model` (string): The name of the image generation model to use (e.g., "dall-e-3", "sdxl").
- `prompt` (string): The text prompt describing the image to generate.
- `n` (integer): The number of images to generate (defaults to 1).
- `size` (string): The size of the generated images (e.g., "256x256", "512x512").

**Response:**

- `created` (integer): The timestamp of when the image was created.
- `data` (array): An array of image objects, each with a `url` to the generated image.


<a name="code-examples"></a>
## Code Examples

**Python Example (Chat Completion):**

```python
from openai import OpenAI

client = OpenAI(api_key="YOUR_TOKEN", base_url="https://api.gpt4-all.xyz/v1")

response = client.chat.completions.create(
    model="gpt-4o-mini",
    messages=[{"role": "user", "content": "hi"}],
    stream=False,
)

print(response.choices[0].message.content)
```

**Python Example (Image Generation):**

```python
from openai import OpenAI

client = OpenAI(api_key="YOUR_TOKEN", base_url="https://api.gpt4-all.xyz/v1")

response = client.images.generate(
    model="dall-e-3",
    prompt="A cat sitting on a windowsill",
    n=1,
    size="256x256"
)

print(response.data[0].url)
```

<a name="rate-limiting"></a>
## Rate Limiting

The API has rate limits to prevent abuse and ensure fair usage. The specific limits depend on your subscription tier and are detailed in the [API Capacities and Limits](#api-capacities-and-limits) section.

<a name="error-handling"></a>
## Error Handling

The API will return standard HTTP error codes to indicate issues. Common error codes include:

- `429 Too Many Requests`: You have exceeded the rate limit.
- `401 Unauthorized`: Your API token is invalid or missing.
- `400 Bad Request`: Your request is malformed or missing required parameters.

You should implement proper error handling in your application to gracefully handle these situations.

## Specific Model Details

<a name="models"></a>
### OpenAI Models

* **gpt-4o / gpt-4o-2024-05-13 (premium):** A powerful large language model with advanced reasoning and comprehension capabilities.
* **gpt-4o-mini / gpt-4o-mini-2024-07-18 (premium):** A smaller, faster version of gpt-4o, suitable for tasks requiring quicker responses.
* **gpt-4-turbo / gpt-4-turbo-2024-04-09 (premium):** An optimized version of GPT-4, balancing performance and cost-effectiveness.
* **gpt-4-0125-preview (premium):** A preview version of GPT-4 with specific features and improvements.
* **gpt-4-1106-preview:** A preview version of GPT-4 with specific features and improvements.
* **gpt-4-32k:** A version of GPT-4 with a larger context window, allowing for processing longer text inputs.
* **gpt-4:** The standard version of GPT-4, offering a balance of capabilities and cost.
* **gpt-3.5-turbo-16k:** A version of GPT-3.5-turbo with a larger context window.
* **gpt-3.5-turbo:** A fast and efficient model suitable for various conversational tasks.
* **dall-e-3:** A powerful image generation model capable of creating realistic and creative images from text prompts.

### <a name="open-source-models"></a> Open Source Models

* **gemma-7b-it:** An Italian language model.
* **mixtral-8x7b:** A powerful open-source language model.
* **llama-3-70b:** A large language model from the LLaMA family.
* **llama-3-8b:** A smaller, faster version of the LLaMA model.
* **llama-3.1-405b:** A large and powerful LLaMA model.
* **llama-3.1-70b:** A large language model from the LLaMA family.
* **wizardlm-2-8x22b:** A powerful open-source language model.
* **mixtral-8x22b:** A powerful open-source language model.
* **sdxl:** A stable diffusion model for generating high-quality images.

**Note:** Model availability and performance may vary. Refer to the official documentation for the most up-to-date information.


## <a name="pricing-per-model"></a> Pricing Per Model

### Price per 1K tokens (LLMs)

| Model                  | Input Price ($) | Output Price ($) |
|--------------------------|-----------------|------------------|
| gpt-4o                  | 0.005           | 0.015            |
| gpt-4o-mini              | 0.00015         | 0.0006           |
| gpt-4-turbo              | 0.01            | 0.03             |
| gpt-4-0125-preview        | 0.01            | 0.02             |
| gpt-4-1106-preview        | 0.01            | 0.03             |
| gpt-4-32k                | 0.06            | 0.10             |
| gpt-4                    | 0.03            | 0.04             |
| gpt-3.5-turbo-16k        | 0.003           | 0.004            |
| gpt-3.5-turbo            | 0.0005          | 0.0014           |
| llama3-70b              | 0.0012          | 0.0014           |
| llama3-8b              | 0.0008          | 0.0009           |
| llama-3.1-405b          | 0.004           | 0.005            |
| llama-3.1-70b          | 0.0012          | 0.002            |
| mixtral-8x7b            | 0.001           | 0.002            |
| gemma-7b-it            | 0.0004          | 0.0005           |
| wizardlm-2-8x22B        | 0.002           | 0.004            |
| mixtral-8x22b            | 0.0015          | 0.0017           |

### Price per generation (Image generators models)

| Model      | Price ($) |
|-------------|-----------|
| dall-e-3   | 0.04      |
| sdxl       | 0.02      |


## <a name="additional-information"></a> Additional Information

- **Tokenization:** The API uses a specific tokenization method to count tokens. Refer to the official documentation for details on how tokens are calculated.
- **Context Window:** Different models have different context window sizes, which limit the amount of text they can process in a single request.
- **Streaming Responses:** The `stream` parameter allows you to receive responses incrementally, which can be useful for long-running tasks or providing real-time feedback to users.
- **Fine-tuning:** The API may offer fine-tuning capabilities in the future, allowing you to customize models for specific tasks or domains.



