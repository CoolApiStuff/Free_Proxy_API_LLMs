# API Documentation

## Table of Contents

- [Overview](#overview)
- [Free vs. Premium Features](#free-vs-premium-features)
- [Pricing](#pricing)
- [API Capacities and Limits](#api-capacities-and-limits)
- [Free Version Features](#free-version-features)
- [Premium Version Features](#premium-version-features)
- [Authentication Methods](#authentication-methods)
- [Endpoints](#endpoints)
    - [CosmosRP-Pro](#cosmosrp-pro)
    - [CosmosRP-Pro-IT](#cosmosrp-pro-it)
    - [CosmosRP](#cosmosrp)
    - [CosmosRP-IT](#cosmosrp-it)
    - [Pai-001](#pai-001)
    - [Pai-001-RP](#pai-001-rp)
    - [Pai-001-Light](#pai-001-light)
    - [Pai-001-Light-RP](#pai-001-light-rp)
- [Code Examples](#code-examples)
- [Rate Limiting](#rate-limiting)
- [Error Handling](#error-handling)

<a name="overview"></a>
## Overview

This API provides access to a variety of large language models, suitable for various tasks such as roleplaying and general text generation. It offers both free and premium access, with different features and limitations.

<a name="free-vs-premium-features"></a>
## Free vs. Premium Features

| Feature               | Free Version                                    | Premium Version                                                                       |
|------------------------|-------------------------------------------------|------------------------------------------------------------------------------------|
| Available Models        | CosmosRP, CosmosRP-IT                           | CosmosRP-Pro, CosmosRP-Pro-IT, Pai-001, Pai-001-RP, Pai-001-Light, Pai-001-Light-RP |
| Context Size          | Up to 8k tokens                                | Up to 32k tokens                                                                    |
| Daily API Credits      | 250                                            | 500 - 2000 (depending on the support tier)                                        |
| Rate Limit            | 3 requests per 15 seconds (1 per 5 seconds)     | 10 requests per 15 seconds                                                          |
| IP Lock               | Yes                                             | No                                                                                   |
| Unlimited Usage       | Only for CosmosRP and CosmosRP-IT models        | For CosmosRP-Pro and CosmosRP-Pro-IT with Supporter I tier and above                |


<a name="pricing"></a>
## Pricing

| Support Tier        | Daily API Credits | Price      |
|--------------------|--------------------|-------------|
| Standard            | 250                | Free        |
| Supporter           | 500                | (Support Us) |
| Supporter I         | 750                | (Support Us) |
| Supporter II        | 1000               | (Support Us) |
| Supporter III       | 1250               | (Support Us) |
| Supporter IV       | 1500               | (Support Us) |
| Supporter V        | 2000               | (Support Us) |

<a name="api-capacities-and-limits"></a>
## API Capacities and Limits

| Feature               | Limit                                       |
|------------------------|--------------------------------------------|
| Global Rate Limit      | 100 requests per 10 seconds                 |
| Standard Key Rate Limit | 3 requests per 15 seconds (1 per 5 seconds) |
| Supporter Key Rate Limit| 10 requests per 15 seconds                  |
| Temporary Block        | 10 seconds                                  |

<a name="free-version-features"></a>
## Free Version Features

The free version provides access to the following:

* **CosmosRP and CosmosRP-IT models:** These models offer excellent quality for roleplaying and general text generation, with a context size of 8k tokens.
* **Unlimited usage:** You can use these models without any limitations on the number of requests.
* **No API key required:** You can access these models without the need for an API key.

<a name="premium-version-features"></a>
## Premium Version Features

The premium version, accessible through the Supporter program, offers:

* **Access to all models:** Including CosmosRP-Pro, CosmosRP-Pro-IT, Pai-001, Pai-001-RP, Pai-001-Light, and Pai-001-Light-RP.
* **Higher context sizes:** Up to 32k tokens, allowing for more extensive and detailed conversations.
* **Increased daily API credits:** Ranging from 500 to 2000 credits per day, depending on the support tier.
* **Higher rate limits:** Allowing for more requests within a given time frame.
* **No IP lock:** You can use your API key from any IP address.
* **Unlimited usage for CosmosRP-Pro and CosmosRP-Pro-IT:** For Supporter I tier and above.

<a name="authentication-methods"></a>
## Authentication Methods

Authentication is done using Bearer tokens. You need to include your API key in the `Authorization` header of your requests:

```
Authorization: Bearer pk-[YOUR_API_KEY]
```

<a name="endpoints"></a>
## Endpoints

All endpoints use the `POST` method and accept a JSON payload.

<a name="cosmosrp-pro"></a>
### CosmosRP-Pro

* **Base URL:** `https://api.pawan.krd/cosmosrp-pro/v1`
* **Full URL:** `https://api.pawan.krd/cosmosrp-pro/v1/chat/completions`
* **Availability:** Supporters Only
* **Usage:** 1 Credit per 10,000 tokens (Unlimited for Supporter I and higher)

<a name="cosmosrp-pro-it"></a>
### CosmosRP-Pro-IT (Instructed Version)

* **Base URL:** `https://api.pawan.krd/cosmosrp-pro-it/v1`
* **Full URL:** `https://api.pawan.krd/cosmosrp-pro-it/v1/chat/completions`
* **Availability:** Supporters Only
* **Usage:** 1 Credit per 10,000 tokens (Unlimited for Supporter I and higher)

<a name="cosmosrp"></a>
### CosmosRP

* **Base URL:** `https://api.pawan.krd/cosmosrp/v1`
* **Full URL:** `https://api.pawan.krd/cosmosrp/v1/chat/completions`
* **Availability:** Public, Free
* **Usage:** Unlimited

<a name="cosmosrp-it"></a>
### CosmosRP-IT (Instructed Version)

* **Base URL:** `https://api.pawan.krd/cosmosrp-it/v1`
* **Full URL:** `https://api.pawan.krd/cosmosrp-it/v1/chat/completions`
* **Availability:** Public, Free
* **Usage:** Unlimited

<a name="pai-001"></a>
### Pai-001

* **Base URL:** `https://api.pawan.krd/pai-001/v1`
* **Availability:** Public
* **Usage:** 1 Credit per 2,000 tokens

<a name="pai-001-rp"></a>
### Pai-001-RP

* **Base URL:** `https://api.pawan.krd/pai-001-rp/v1`
* **Availability:** Public
* **Usage:** 1 Credit per 2,000 tokens

<a name="pai-001-light"></a>
### Pai-001-Light

* **Base URL:** `https://api.pawan.krd/pai-001-light/v1`
* **Availability:** Public
* **Usage:** 1 Credit per 4,000 tokens

<a name="pai-001-light-rp"></a>
### Pai-001-Light-RP

* **Base URL:** `https://api.pawan.krd/pai-001-light-rp/v1`
* **Availability:** Public
* **Usage:** 1 Credit per 4,000 tokens

<a name="code-examples"></a>
## Code Examples

**Example using curl for CosmosRP:**

```bash
curl --location --request POST 'https://api.pawan.krd/cosmosrp/v1/chat/completions' \
--header 'Content-Type: application/json' \
--data-raw '{
    "messages": [
        {"role": "system", "content": "You are a helpful assistant."},
        {"role": "user", "content": "What is the capital of France?"}
    ]
}'
```

**Example using Python for Pai-001:**

```python
import requests

headers = {
    'Authorization': 'Bearer pk-[YOUR_API_KEY]',
    'Content-Type': 'application/json'
}

data = {
    "messages": [
        {"role": "system", "content": "You are a helpful assistant."},
        {"role": "user", "content": "Write a short story about a cat."}
    ]
}

response = requests.post('https://api.pawan.krd/pai-001/v1/chat/completions', headers=headers, json=data)

print(response.json())
```

<a name="rate-limiting"></a>
## Rate Limiting

The API has different rate limits depending on your access level:

* **Global Rate Limit:** 100 requests per 10 seconds.
* **Standard Key Rate Limit:** 3 requests per 15 seconds (1 per 5 seconds).
* **Supporter Key Rate Limit:** 10 requests per 15 seconds.

Exceeding these limits will result in a temporary block of 10 seconds.

<a name="error-handling"></a>
## Error Handling

The API returns standard HTTP status codes to indicate the outcome of a request. Here are some common error codes:

* **400 Bad Request:** Indicates an issue with the request payload, such as missing or invalid parameters.
* **401 Unauthorized:** Indicates that the provided API key is invalid or missing.
* **429 Too Many Requests:** Indicates that you have exceeded the rate limit.
* **500 Internal Server Error:** Indicates an unexpected error on the server side.

The response body will usually contain more details about the error.

**Example Error Response:**

```json
{
    "error": {
        "message": "You have exceeded the rate limit.",
        "type": "rate_limit_exceeded",
        "code": 429
    }
}
```

