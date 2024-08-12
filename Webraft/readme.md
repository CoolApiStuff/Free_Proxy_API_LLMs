# Webraft Free API Documentation

[Webraft Link](https://api3.webraft.in/)

<a name="table-of-contents"></a>

## Table of Contents
- [Overview](#overview)
    - [Free vs Premium](#free-vs-premium)
    - [Pricing](#pricing)
    - [API Capacity and Limits](#api-capacity-and-limits)
- [Free Version Features](#free-version-features)
    - [Text Models](#text-models)
    - [Image Models](#image-models)
- [Premium Version Features](#premium-version-features)
- [Authentication Methods](#authentication-methods)
- [Endpoints](#endpoints)
    - [Chat Completion](#chat-completion)
    - [Text Completion](#text-completion)
    - [Image Generation](#image-generation)
    - [Image Classification](#image-classification)
    - [Image-to-Text](#image-to-text)
    - [List Models](#list-models)
- [Code Examples](#code-examples)
    - [Listing Models](#listing-models-example)
    - [Using Claude Models](#using-claude-models-example)
    - [Image Classification](#image-classification-example)
    - [Image-to-Text](#image-to-text-example)
    - [Image Generation](#image-generation-example)
    - [GPT 3.5 Turbo](#gpt-35-turbo-example)
    - [GPT 3.5 Turbo with Image Input](#gpt-35-turbo-with-image-input-example)
- [Rate Limiting](#rate-limiting)
- [Error Handling](#error-handling)
- [FAQ](#faq)
- [Partners](#partners)


<a name="overview"></a>

## Overview

WebraftAI API is a service that provides access to a wide variety of open and closed-source AI models, both free and paid. It offers functionalities like chat completion, image generation, and more.

<a name="free-vs-premium"></a>

### Free vs Premium

| Feature                    | Free Version | Premium Version |
|----------------------------|---------------|-----------------|
| Daily API Credits           | 500           | 2k - 60k        |
| Non-Replenishing Credits  | 0             | 500 - 30k       |
| Daily Credits-V2          | N/A           | 350 - 40k       |
| Model Access               | Limited        | Extensive      |
| Early Model Access         | No            | Yes             |
| Exclusive Models           | No            | Yes             |
| Early Access to AI Services| No            | Yes             | 
| Discord Perks             | No            | Yes             |
| Discounted Hostings       | No            | Some Tiers     |
| Private Endpoints         | No            | Higher Tiers    |
| Dedicated Server           | No            | Highest Tier    |
| Access to Claude 3         | No            | Higher Tiers    |
| Access to SynapseLLM      | No            | Higher Tiers    |
| Local AI Models           | No            | Pro Tier        |


<a name="pricing"></a>

### Pricing

| Tier            | Price (€/month) |  API Credits (Daily) | Non-Replenishing Credits | Credits-V2 (Daily)|
|-----------------|-----------------|----------------------|-------------------------|--------------------|
| Basic           | 3                | 2k                    | 0                       | 350                |
| Medium          | 6                | 4k                    | 500                     | 1k                 |
| Pro             | 10               | 8k                    | 1k                      | 1k                 |
| Ultra           | 17.50            | 16k                   | 2k                      | 2k                 |
| Ultra Pro Max  | 27.50            | 48k                   | 6k                      | 6k                 |
| Rich            | 58               | 60k                   | 30k                     | 40k                |

**Note:** Prices are subject to VAT.

<a name="api-capacity-and-limits"></a>

### API Capacity and Limits

| Feature          | Limit                               |
|------------------|------------------------------------|
| Server Location   | Germany (API), Mumbai (Inference) |
| Free Credits     | 500                                 |
| Credit Replenish | 24 hours                           |
| Rate Limit       | 5 requests/second, 60 requests/minute |

<a name="free-version-features"></a>

## Free Version Features

The free version of the WebraftAI API offers access to a wide range of text and image models with a daily limit of 500 credits. 

<a name="text-models"></a>

### Text Models

The free version provides access to numerous text models with varying capabilities, including:

| Model ID | Model Name | Description |
|---|---|---|
| `gpt-3.5-turbo` | GPT-3.5 Turbo | A powerful and versatile large language model. |
| `text-davinci-003` | Text Davinci 003 | Another powerful and versatile large language model. |
| `claude-instant-v1` | Claude Instant v1 | A fast and efficient version of the Claude model. |
| `llama2-70b` | Llama 2 70b | A 70B parameter model from the Llama 2 family. |
|  ... and many more |  | See the full list in the `freetextmodels.md` file. |

<a name="image-models"></a>

### Image Models

The free version also provides access to a variety of image models, including:

| Model ID | Model Name | Description |
|---|---|---|
| `stable-diffusion-v1-4` | Stable Diffusion v1-4 | A popular and versatile text-to-image model. |
| `realistic-vision-v5-1` | Realistic Vision v5-1 | A model trained to generate realistic images. |
| `dalle-3-xl` | DALL-E 3 XL | A powerful text-to-image model from OpenAI. |
| `openjourney-v5` | Openjourney v5 | A model known for its artistic and creative style. |
| ... and many more |  | See the full list in the `imagemodels.md` file. |

<a name="premium-version-features"></a>

## Premium Version Features

The premium version of the WebraftAI API offers several advantages over the free version, including:

- **Increased daily credits:** Premium tiers offer significantly more daily credits, ranging from 2,000 to 60,000.
- **Non-replenishing credits:** Some tiers provide a pool of non-replenishing credits that can be used at any time.
- **Access to exclusive models:** Premium users gain access to a wider range of models, including more powerful and specialized ones.
- **Early access to new models and services:** Premium users get early access to newly released models and AI services.
- **Discord perks:** Premium users receive special perks on the Webraft Discord server.
- **Discounted hostings:** Some premium tiers offer discounts on hosting services.
- **Private endpoints:** Higher tiers provide private endpoints for increased stability and performance.
- **Dedicated server:** The highest tier offers a dedicated server for maximum performance and control.

<a name="authentication-methods"></a>

## Authentication Methods

WebraftAI API uses API keys for authentication. You need to include your API key in the `Authorization` header of your requests:

```
Authorization: Bearer YOUR_API_KEY
```

<a name="endpoints"></a>

## Endpoints

<a name="chat-completion"></a>

### Chat Completion

- **Endpoint:**
    - Free: `https://api.webraft.in/freeapi/chat/completions`
    - Paid: `https://api.webraft.in/v1/chat/completions`
- **Method:** `POST`
- **Description:** This endpoint is used for chat-based interactions with language models.
- **Request Body:** This endpoint accepts a JSON object with parameters like `model`, `messages`, and other options as defined in the OpenAI API documentation.

<a name="text-completion"></a>

### Text Completion

- **Endpoint:** `https://freeapi-proxy001-webraftai.run-us-west2.goorm.app/v1/completions`
- **Method:** `POST`
- **Description:** This endpoint is used for generating text completions based on a given prompt.
- **Request Body:** This endpoint accepts a JSON object with parameters like `model`, `prompt`, and other options as defined in the OpenAI API documentation.

<a name="image-generation"></a>

### Image Generation

- **Endpoint:**
    - `http://5.199.130.218:1234/v1/images/generations`
    - `http://5.199.130.218:1234/api/images/generations`
- **Method:** `POST`
- **Description:** This endpoint is used for generating images from text prompts.
- **Request Body:** This endpoint accepts a JSON object with parameters like `prompt`, `model`, and other options.

<a name="image-classification"></a>

### Image Classification

- **Endpoint:** `http://5.199.130.218:1234/api/images/classification`
- **Method:** `POST`
- **Description:** This endpoint is used for classifying images.
- **Request Body:** This endpoint accepts a JSON object with parameters like `image_file` (a URL to the image) and `model`.

<a name="image-to-text"></a>

### Image-to-Text

- **Endpoint:** `http://5.199.130.218:1234/api/image-to-text`
- **Method:** `POST`
- **Description:** This endpoint is used for generating text descriptions of images.
- **Request Body:** This endpoint accepts a JSON object with parameters like `image_file` (a URL to the image) and `model`.

<a name="list-models"></a>

### List Models

- **Endpoint:**
    - Free: `https://api.webraft.in/freeapi/models`
    - Paid: `https://api.webraft.in/v1/models`
- **Method:** `GET`
- **Description:** This endpoint retrieves a list of available models.


<a name="code-examples"></a>

## Code Examples

<a name="listing-models-example"></a>

### Listing Models

- **Curl:**

```bash
curl https://api.webraft.in/freeapi/models \
    -H "Authorization: Bearer {YOUR_API_KEY}" 
```

- **Python:**

```python
import openai
openai.api_key = "Your_API_KEY"
openai.api_base ="https://api.webraft.in/freeapi"
openai.Model.list() 
```

- **NodeJS:**
    - Use the `fetch` method as the official OpenAI NodeJS package does not support custom URL endpoints.

<a name="using-claude-models-example"></a>

### Using Claude Models

- **Python:**

```python
import openai
openai.api_key = "Your API key"
openai.api_base = "https://api.webraft.in/freeapi"
completion = openai.ChatCompletion.create(
  model="claude-instant-1",
  messages=[
    {"role": "system", "content":"You are a helpful AI Assistant"},
    {"role": "user", "content": "Hello!"}
  ]
)

print(completion.choices[0].message)
```

- **Curl:**

```bash
curl https://api.webraft.in/freeapi/chat/completions \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer YOUR_API_KEY" \
  -d '{
    "model": "claude-instant-1",
    "messages": [
      {
      "role":"system",
      "content":"You are a helpful AI Assistant"
      },
      {
        "role": "user",
        "content": "Hello!"
      }
      
    ]
  }'
```

<a name="image-classification-example"></a>

### Image Classification (Python)

```python
import requests
headers = {
    "Content-Type":"application/json",
    "Authorization":"Bearer Your_API_Key"
}
data = {
    "image_file":"https://static01.nyt.com/images/2021/09/14/science/07CAT-STRIPES/07CAT-STRIPES-jumbo.jpg",
    "model":"vit-base-patch16-244"
}
response = requests.post("https://api.webraft.in/api/images/classification",headers=headers, json=data)
try:
    response.raise_for_status()
    response2 = response.json()
    print(response2)
except requests.exceptions.HTTPError as http_err:
    print(f"HTTP error occurred: {http_err}")
except requests.exceptions.RequestException as req_err:
    print(f"Request exception occurred: {req_err}")
except requests.exceptions.JSONDecodeError as json_err:
    print(f"JSON decode error occurred: {json_err}")
```


<a name="image-to-text-example"></a>

### Image-to-Text (Python)

```python
import requests
headers = {
    "Content-Type":"application/json",
    "Authorization":"Bearer YOUR_API_KEY"
}
data = {
    "image_file":"https://static01.nyt.com/images/2021/09/14/science/07CAT-STRIPES/07CAT-STRIPES-jumbo.jpg",
    "model":"git-large-coco"
}
response = requests.post("https://api.webraft.in/api/image-to-text",headers=headers, json=data)
try:
    response.raise_for_status()
    response2 = response.json()
    print(response2)
except requests.exceptions.HTTPError as http_err:
    print(f"HTTP error occurred: {http_err}")
except requests.exceptions.RequestException as req_err:
    print(f"Request exception occurred: {req_err}")
except requests.exceptions.JSONDecodeError as json_err:
    print(f"JSON decode error occurred: {json_err}")
```

<a name="image-generation-example"></a>

### Image Generation (Python)

```python
import requests
data = {"prompt":"a dog running in a house",
        "model":"stable-diffusion-2"
        }
headers = {
    "Content-type":"application/json",
    "Authorization": "Bearer YOUR_API_KEY"
}
response = requests.post("http://api.webraft.in:1234/api/images/generations",json=data, headers=headers)
response = response.json()
print(response)
```

<a name="gpt-35-turbo-example"></a>

### GPT 3.5-Turbo Model (Python)

```python
import requests

api_key = "YOUR API KEY"

url = 'https://api.webraft.in/freeapi/chat/completions'
headers = {
    'Authorization': f'Bearer {api_key}',
    'Content-Type': 'application/json'
}

data = {
    "model": "gpt-3.5-turbo",
    "max_tokens": 100,
    "messages": [
        {
            "role": "system",
            "content": "You are an helpful assistant."
        },
        {
            "role": "user",
            "content": "hi"
        }
    ]
}

response = requests.post(url, headers=headers, json=data)

try:
    response_data = response.json()
    print(response_data)
except requests.exceptions.JSONDecodeError as e:
    print("JSON Decode Error:", e)
    print("Response Content:", response.content)
```

<a name="gpt-35-turbo-with-image-input-example"></a>

### GPT 3.5-Turbo Model with Image and text input concurrently (Python)

```python
import requests

api_key = "YOUR_API_KEY"

url = 'https://paidapi-proxy003-webraftai.run-us-west2.goorm.app/v1/chat/completions' # Only available to  paid users.
headers = {
    'Authorization': f'Bearer {api_key}',
    'Content-Type': 'application/json'
}

data = {
    "model": "gpt-3.5-turbo",
    "max_tokens": 3000,
    "messages": [
        {
            "role": "system",
            "content": "You are a helpful assistant."
        },
        {
            "role": "user",
            "content": "what is in this image?"
        }
    ],
    "image_link":"https://iso.500px.com/wp-content/uploads/2022/07/Sunset-somewhere-in-Iowa-By-Vath.-Sok-2.jpeg"
}

response = requests.post(url, headers=headers, json=data)

try:
    response_data = response.json()
    print(response_data)
except requests.exceptions.JSONDecodeError as e:
    print("JSON Decode Error:", e)
    print("Response Content:", response.content)
```

**Note:** This endpoint is only available to paid users. It's currently in beta and may have limitations.

<a name="rate-limiting"></a>

## Rate Limiting

To prevent abuse and ensure fair usage, the WebraftAI API enforces rate limits:

- **5 requests per second:** You can make a maximum of 5 requests per second.
- **60 requests per minute:** You can make a maximum of 60 requests per minute.

If you exceed these limits, your requests will be throttled, and you may receive error responses.

<a name="error-handling"></a>

## Error Handling

The WebraftAI API returns standard HTTP status codes to indicate the success or failure of your requests. Common error codes include:

- **429 Too Many Requests:** This indicates that you have exceeded the rate limit.
- **401 Unauthorized:** This indicates that your API key is invalid or missing.
- **500 Internal Server Error:** This indicates a server-side error.

When an error occurs, the API response will include a JSON object with more details about the error.

<a name="faq"></a>

## FAQ

- **What is Webraft?**
    - Webraft is a technology website that provides various tools and services, including the WebraftAI API.

- **What is WebraftAI API?**
    - WebraftAI API provides access to various open and closed-source AI models through an API.

- **What are the daily credits?**
    - Daily credits are replenished every 24 hours. Free users get 500 daily credits.

- **What is the rate limit?**
    - The rate limit is 5 requests per second and 60 requests per minute.

- **Is GPT-4-32K available for free?**
    - No, GPT-4-32k is only available to paid users.

- **What do I get if I boost or donate?**
    - Please refer to the `Donations` section on the Webraft platform.

- **How to get a key?**
    - Go to `🔧・ᴄᴏᴍᴍᴀɴᴅs` or `🧠・ᴀɪ-ʙᴏᴛs` and run the `!key` or `/key` command.

- **Why are there different API URLs?**
    - Free users use `https://api.webraft.in/freeapi`, while paid users use `https://api.webraft.in/v1`.

- **Why is the Free API endpoint not working?**
    - Possible reasons include:
        - API downtime (contact the Webraft team).
        - Fallback issues (try again later).
        - Compatibility problems with your program.

<a name="partners"></a>

## Partners

- **Skailar:** An API service with various models, including 32k context length (for donors).
- **HareProxy and DarkGPT API:** Acquired by Webraft in their early stages.


This comprehensive documentation should provide a clear understanding of the WebraftAI API, its features, and how to use it effectively. If there's anything else I can help you with, just let me know!
