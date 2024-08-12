## Fresed API Documentation

### Table of Contents

- [Overview](#overview)
- [Free vs. Premium Features](#free-vs-premium-features)
- [Pricing](#pricing)
- [API Capacities and Limits](#api-capacities-and-limits)
- [Free Version Features](#free-version-features)
- [Premium Version Features](#premium-version-features)
- [Authentication Methods](#authentication-methods)
- [API Endpoints](#api-endpoints)
    - [Chat Completions](#chat-completions)
    - [Image Generation](#image-generation)
    - [Speech Generation](#speech-generation)
    - [Temporary Email Service](#temporary-email-service)
    - [Models List](#models-list)
    - [API Status](#api-status)
    - [Referral System](#referral-system)
    - [Limit System](#limit-system)
    - [Donation Information](#donation-information)
- [Code Examples](#code-examples)
    - [Chat Completion](#chat-completion-example)
    - [Image Generation](#image-generation-example)
    - [Speech Generation](#speech-generation-example)
    - [Temporary Email](#temporary-email-example)
- [Rate Limiting](#rate-limiting)
- [Error Handling](#error-handling)


<a name="overview"></a>
## Overview

The Fresed API provides access to various AI models, including GPT-4, Claude, and others, for diverse tasks such as chat completions, image generation, speech generation, and temporary email services. It offers both free and premium access with different features and limitations. This documentation provides a comprehensive guide to using the Fresed API.

<a name="free-vs-premium-features"></a>
## Free vs. Premium Features

| Feature | Free Version | Premium Version |
|---|---|---|
| Daily Tokens | 80,000 | Unlimited (with $100/month subscription) |
| GPT-4 Requests | 125 per day | Unlimited (with $100/month subscription) |
| Claude Access | No | Yes (with $3/month subscription) |
| Request Limit | 100 requests/day in Request Mode | No limit in Token Mode |
| Token Mode | Yes | Yes |
| Request Mode | Yes | Yes |
| Referral Program | Yes | Yes |


<a name="pricing"></a>
## Pricing

| Feature | Price |
|---|---|
| Free Tier | $0 |
| Claude Access | $3/month |
| Unlimited Access | $100/month |
| Donations (Tokens/month) |  |
| - $5  | 320,000 |
| - $10 | 960,000 |
| - $15 | 1,600,000 |


<a name="api-capacities-and-limits"></a>
## API Capacities and Limits

| Feature | Limit |
|---|---|
| Default Daily Tokens | 80,000 |
| Token Mode Daily Tokens | 80,000 |
| Request Mode Daily Requests | 100 |
| Tokens per Request (Request Mode) | 800 |
| Approximate Free GPT-4 Requests/day | 125 |


<a name="free-version-features"></a>
## Free Version Features

The free version of the Fresed API offers:

* 80,000 tokens per day.
* Access to various AI models, excluding Claude.
* Approximately 1000 or 125 free GPT-4 requests per day.
* Two limit modes: Token Mode and Request Mode.
* Access to the referral program.

<a name="premium-version-features"></a>
## Premium Version Features

The premium version of the Fresed API offers:

* Unlimited tokens with the $100/month subscription.
* Access to Claude with the $3/month subscription.
* Unlimited GPT-4 requests with the $100/month subscription.
* No request limit in Token Mode.
* Access to the referral program.

<a name="authentication-methods"></a>
## Authentication Methods

The Fresed API uses API keys for authentication. You can generate your API key through the FresedGPT Discord or Telegram bot.

1. **Discord:** Join the [FresedGPT Discord](https://discord.gg/JecEC5my4T) server and use the `/gen_key`, `/show_key`, or `/generate_key` commands.
2. **Telegram Bot:** Access the [FresedGPT Telegram Bot](https://t.me/GPTFresedEN_bot) and use the corresponding commands.

Include your API key in the `Authorization` header of your requests as a Bearer token:

```
Authorization: Bearer your_api_key
```

<a name="api-endpoints"></a>
## API Endpoints

<a name="chat-completions"></a>
### Chat Completions

* **Endpoint:** `https://fresedgpt.space/v1/chat/completions`
* **Method:** `POST`
* **Description:** This endpoint is used for generating chat completions using various language models.

<a name="image-generation"></a>
### Image Generation

* **Endpoint:** `https://fresedgpt.space/v1/images/generations`
* **Method:** `POST`
* **Description:** This endpoint is used for generating images based on text prompts.

<a name="speech-generation"></a>
### Speech Generation

* **Endpoint:** `https://fresedgpt.space/v1/audio/speech`
* **Method:** `POST`
* **Description:** This endpoint is used for generating speech from text input.

<a name="temporary-email-service"></a>
### Temporary Email Service

* **Endpoint (Generate):** `https://fresedgpt.space/v1/temp_mail/generate`
* **Method:** `POST`
* **Description:** This endpoint generates a temporary email address.

* **Endpoint (Retrieve Messages):** `https://fresedgpt.space/v1/temp_mail/messages/{identifier}`
* **Method:** `GET`
* **Description:** This endpoint retrieves messages for a specific temporary email address using its identifier.

<a name="models-list"></a>
### Models List

* **Endpoint:** `https://fresedgpt.space/v1/models`
* **Method:** `GET`
* **Description:** This endpoint provides a list of supported models and their token coefficients.

<a name="api-status"></a>
### API Status

* **Endpoint:** `https://stats.uptimerobot.com/UPZd5tBI9z/796838663`
* **Description:** This link leads to the API status monitoring page.

<a name="referral-system"></a>
### Referral System

The Fresed API features a referral system where users can earn tokens by referring others.

* **Referral Code:** Each user has a unique referral code accessible via the `/user_info` command in the Discord or Telegram bot.
* **Activating a Referral Code:** Use the `/activate_referral` command in the Discord or Telegram bot to activate a referral code.
* **Referral Rewards:**
    * 5 referrals: 85,000 tokens/day for a month (Claude access)
    * 10 referrals: 160,000 tokens/day for a month
    * 20 referrals: 320,000 tokens/day for a month
    * 40 referrals: 960,000 tokens/day for a month
    * 60 referrals: 1,600,000 tokens/day for a month


<a name="limit-system"></a>
### Limit System

The Fresed API has a limit system with two modes:

* **Token Mode:**
    * 80,000 tokens per day.
    * No limit on the number of requests per minute.
* **Request Mode:**
    * 100 requests per day.
    * Each request consumes 800 tokens.

You can switch between modes using the `/set_limit_mode` command in the Discord or Telegram bot. Check your limit information using the `/all_limits` command.

<a name="donation-information"></a>
### Donation Information

Users can donate to support the service and receive additional tokens per month:

* $5: 320,000 tokens
* $10: 960,000 tokens
* $15: 1,600,000 tokens

Contact @fresed for other donation amounts.


---

<a name="code-examples"></a>
## Code Examples

<a name="chat-completion-example"></a>
### Chat Completion Example (Python)

```python
from openai import AsyncOpenAI

client = AsyncOpenAI(
    api_key='your_api_key',
    base_url='https://fresedgpt.space/v1'
)

async def test_create_chat_completion():
    stream = await client.chat.completions.create(
        messages=[{'role': 'user', 'content': 'hi'}],
        model='gpt-4',
        stream=True
    )

    async for chunk in stream:
        print(chunk.choices[0].delta.content or '', end='')

if __name__ == '__main__':
    import asyncio
    asyncio.run(test_create_chat_completion())
```

<a name="image-generation-example"></a>
### Image Generation Example (Python)

```python
from openai import OpenAI

client = OpenAI(base_url='https://fresedgpt.space/v1', api_key='your_api_key')

response = client.images.generate(
    model="midjourney",
    prompt="a white siamese cat",
    size="1024x1024"
)

print(response)
```

<a name="speech-generation-example"></a>
### Speech Generation Example (Python)

```python
from openai import OpenAI

client = OpenAI(
    api_key='your_api_key',
    base_url='https://fresedgpt.space/v1'
)

response = client.audio.speech.create(
    model="tts-1",
    voice="alloy",
    input="hi"
)

print(response)
response.stream_to_file("output.mp3")
```

<a name="temporary-email-example"></a>
### Temporary Email Example (Python)

```python
import httpx
import asyncio

BASE_URL = "https://fresedgpt.space/v1"
API_KEY = "your_api_key"

async def generate_temp_mail():
    async with httpx.AsyncClient() as client:
        headers = {
            "Authorization": f"Bearer {API_KEY}",
            "Content-Type": "application/json"
        }
        response = await client.post(f"{BASE_URL}/temp_mail/generate", headers=headers)
        if response.status_code == 200:
            data = response.json()
            print("Generated Email:", data["email"])
            print("Identifier:", data["identifier"])
            return data["identifier"]
        else:
            print("Failed to generate email:", response.text)
            return None

async def get_temp_mail_messages(identifier):
    async with httpx.AsyncClient() as client:
        headers = {
            "Authorization": f"Bearer {API_KEY}",
            "Content-Type": "application/json"
        }
        response = await client.get(f"{BASE_URL}/temp_mail/messages/{identifier}", headers=headers)
        if response.status_code == 200:
            messages = response.json()["messages"]
            print("Messages:", messages)
        else:
            print("Failed to get messages:", response.text)

async def main():
    identifier = await generate_temp_mail()
    if identifier:
        input("Press Enter to check for messages...")
        await get_temp_mail_messages(identifier)

if __name__ == "__main__":
    asyncio.run(main())
```

<a name="rate-limiting"></a>
## Rate Limiting

The Fresed API has rate limits to ensure fair usage and prevent abuse. The specific rate limits are not explicitly mentioned in the provided documentation. However, the documentation mentions two usage modes, **Token Mode** and **Request Mode**, which have their own limitations. It's recommended to monitor your usage and contact Fresed support if you encounter rate limiting issues.

<a name="error-handling"></a>
## Error Handling

The Fresed API returns standard HTTP status codes to indicate the success or failure of requests.  Here are some common error codes:

* **400 Bad Request:** This indicates an error with the request, such as invalid parameters.
* **401 Unauthorized:** This indicates that the request was not authorized, likely due to an invalid or missing API key.
* **429 Too Many Requests:** This indicates that you have exceeded the rate limit.
* **500 Internal Server Error:** This indicates an error on the server side.

It is recommended to implement proper error handling in your application to gracefully handle these situations.  You can check the response status code and the response body for more details about the error.



