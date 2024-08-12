# VisionCraft API Documentation

<a name="table-of-contents"></a>
## Table of Contents

- [Overview](#overview)
- [Free vs. Premium Features](#free-vs-premium-features)
- [Pricing](#pricing)
- [API Capacities and Limits](#api-capacities-and-limits)
- [Free Version Features](#free-version-features)
- [Premium Version Features](#premium-version-features)
- [Authentication Methods](#authentication-methods)
- [Endpoints](#endpoints)
    - [LLM Endpoints](#llm-endpoints)
        - [List Available LLM Models](#list-available-llm-models)
        - [Text Generation](#text-generation-endpoint)
    - [Image Generation Endpoints](#image-generation-endpoints)
        - [Generate Image](#generate-image)
        - [List Available Samplers](#list-available-samplers)
        - [List Available Models](#list-available-models)
        - [List Available Loras](#list-available-loras)
    - [Text-to-GIF Generation Endpoint](#text-to-gif-generation-endpoint)
        - [Generate GIF](#generate-gif)
    - [GIF Generation Endpoint](#gif-generation-endpoint)
        - [Generate GIF (Alternative)](#generate-gif-alternative)
- [Code Examples](#code-examples)
    - [LLM Examples](#llm-examples)
        - [Python (Add Image to Request)](#python-add-image-to-request)
        - [JavaScript (Node.js) (Add Image to Request)](#javascript-node-js-add-image-to-request)
        - [cURL (Add Image to Request)](#curl-add-image-to-request)
        - [Python (Available Models)](#python-available-models)
        - [JavaScript (Node.js) (Available Models)](#javascript-node-js-available-models)
        - [cURL (Available Models)](#curl-available-models)
        - [Python (Text Generation)](#python-text-generation)
        - [JavaScript (Node.js) (Text Generation)](#javascript-node-js-text-generation)
        - [cURL (Text Generation)](#curl-text-generation)
    - [Image Generation Examples](#image-generation-examples)
        - [Python](#python-image-generation)
        - [JavaScript (Node.js)](#javascript-node-js-image-generation)
        - [cURL](#curl-image-generation)
    - [Text-to-GIF Generation Examples](#text-to-gif-generation-examples)
        - [Python](#python-text-to-gif-generation)
        - [JavaScript (Node.js)](#javascript-node-js-text-to-gif-generation)
        - [cURL](#curl-text-to-gif-generation)
    - [GIF Generation Examples](#gif-generation-examples)
        - [Python](#python-gif-generation)
        - [JavaScript (Node.js)](#javascript-node-js-gif-generation)
        - [cURL](#curl-gif-generation)
- [Rate Limiting](#rate-limiting)
- [Error Handling](#error-handling)
- [Links](#links)

<a name="overview"></a>
## Overview

The VisionCraft API offers a powerful suite of AI models for various tasks, including text generation, image generation, and GIF generation. It provides access to a diverse range of Large Language Models (LLMs) and Stable Diffusion models. The API offers both free and premium subscription tiers, catering to different usage needs and budgets.

<a name="free-vs-premium-features"></a>
## Free vs. Premium Features

| Feature | Free Version | Premium Version (Tier 1 & Tier 2) |
|---|---|---|
| Access to all models | Yes | Yes |
| Requests per second | Limited (see [Limits](https://api.visioncraft.top/limits)) | Increased (Tier 1) / Unlimited (Tier 2) |
| Image Generation Resolution | Up to 1024x1024 | Up to 1024x1024 |
| GIF Generation | Yes | Yes |
| Multimodal Capabilities (LLaVA) | Yes | Yes |
| Priority Support | No | Yes |

<a name="pricing"></a>
## Pricing

| Tier | Price |
|---|---|
| Free | Free |
| Tier 1 | $10/month |
| Tier 2 | $20/month |
| Free Tier 1 for 24 hours | Available once every 7 days |

<a name="api-capacities-and-limits"></a>
## API Capacities and Limits

Please refer to the official API Limits documentation for the most up-to-date information: [https://api.visioncraft.top/limits](https://api.visioncraft.top/limits)

<a name="free-version-features"></a>
## Free Version Features

The free version of the VisionCraft API provides access to all models, including LLMs and Stable Diffusion models, with a limited number of requests per second. This tier is ideal for users who are just starting out or have low-volume requirements.

<a name="premium-version-features"></a>
## Premium Version Features

The premium version of the VisionCraft API, available in Tier 1 and Tier 2, offers increased or unlimited requests per second, depending on the tier. This allows for higher throughput and faster processing of requests. Premium users also receive priority support.

<a name="authentication-methods"></a>
## Authentication Methods

The VisionCraft API uses API keys for authentication. You can obtain an API key by following these steps:

1. Subscribe to the VisionCraft Telegram channel: [https://t.me/visioncraft_channel](https://t.me/visioncraft_channel)
2. Send the `/key` command to the VisionCraft bot: [https://t.me/VisionCraft_bot](https://t.me/VisionCraft_bot)

Once you have your API key, include it in the `Authorization` header of your requests as a Bearer token:

```
Authorization: Bearer your_api_key
```

<a name="endpoints"></a>
## Endpoints

The VisionCraft API provides several endpoints for different functionalities.

<a name="llm-endpoints"></a>
### LLM Endpoints

<a name="list-available-llm-models"></a>
#### List Available LLM Models

```
GET https://visioncraft.top/models-llm
```

**Response:**

```json
["lzlv_70b_fp16_hf", "CodeLlama-34b-Instruct-hf", ...]
```

<a name="text-generation-endpoint"></a>
#### Text Generation

```
POST https://visioncraft.top/v1/chat/completions
```

**Parameters:**

| Parameter | Type | Description |
|---|---|---|
| `model`* | string | The name of the chosen LLM model |
| `max_tokens` | integer | Maximum length of the generated text (min: `128`, max: `100000`, default: `512`) |
| `temperature` | float | Sampling temperature. 0 means deterministic output, values >1 encourage diversity (min: `0`, max: `100`, default: `0.7`) |
| `top_p` | float | Probability threshold for token sampling (min: `0`, max: `1`, default: `0.9`) |
| `top_k` | integer | Number of top tokens to sample from (min: `0`, max: `99999`, default: `0`) |
| `repetition_penalty` | float | Penalty for token repetition (min: `0.01`, max: `5`, default: `1`) |
| `presence_penalty` | float | Positive values penalize new tokens based on their presence in the text so far (min: `-2`, max: `2`, default: `0`) |
| `frequency_penalty` | float | Positive values penalize new tokens based on their frequency in the text so far (min: `-2`, max: `2`, default: `0`) |
| `messages`* | list | Messages to the LLM |

<sup>* Required parameters</sup>

**Request Example:**

```json
{
  "model": "Mixtral-8x7B-Instruct-v0.1",
  "messages": [
    {
      "role": "user",
      "content": 'There are 50 books in a library. Sam decides to read 5 of the books. How many books are there now? If there are 45 books, say "1". Else, if there is the same amount of books, say "2".'
    }
  ]
}
```

<a name="image-generation-endpoints"></a>
### Image Generation Endpoints

<a name="generate-image"></a>
#### Generate Image

```
POST https://visioncraft.top/sd
```

**Parameters:**

| Parameter | Type | Description |
|---|---|---|
| `token`* | string | Your API key |
| `model`* | string | One of the available SD models |
| `prompt`* | string | A text prompt for generation |
| `negative_prompt` | string | Text prompt that the model shouldn't be drawn on the picture |
| `sampler` | string | One of the available SD samplers |
| `steps` | integer | How many times to iteratively improve the image (min: `1`, max: `35`, default: `35`) |
| `width` | integer | Generated image width (min: `64`, max: `1024`, default: `1024`) |
| `height` | integer | Generated image height (min: `64`, max: `1024`, default: `1024`) |
| `cfg_scale` | integer | How strongly the image should conform to the text (min: `1`, max: `30`, default: `7`) |
| `loras` | dict | Dictionary of available loras (max `5` in dict) |

<sup>* Required parameters</sup>

**Request Example:**

```json
{
  "model": "sdxl-base",
  "prompt": "Beautiful landscape",
  "negative_prompt": "bad quality",
  "token": "your_api_key",
  "sampler": "Euler",
  "steps": 30,
  "width": 1024,
  "height": 1024,
  "cfg_scale": 7,
  "loras": {}
}
```

<a name="list-available-samplers"></a>
#### List Available Samplers

```
GET https://visioncraft.top/sd/samplers
```

**Response:**

```json
["Euler a", "Euler", "LMS", ...]
```

<a name="list-available-models"></a>
#### List Available Models

```
GET https://visioncraft.top/sd/models
```

**Response:**

```json
["sdxl-base", "sdxl-refiner", "deliberate_v2", ...]
```

<a name="list-available-loras"></a>
#### List Available Loras

```
GET https://visioncraft.top/sd/loras
```

**Response:**

```json
["add_detail", "analog_diffusion_1.0", "anireality_mix", ...]
```

<a name="text-to-gif-generation-endpoint"></a>
### Text-to-GIF Generation Endpoint

<a name="generate-gif"></a>
#### Generate GIF

```
POST https://visioncraft.top/text2gif
```

**Parameters:**

| Parameter | Type | Description |
|---|---|---|
| `token`* | string | Your API key |
| `prompt`* | string | A text prompt to generate a GIF from |

<sup>* Required parameters</sup>

**Request Example:**

```json
{
  "token": "your_api_key",
  "prompt": "A cat playing with a ball of yarn"
}
```

<a name="gif-generation-endpoint"></a>
### GIF Generation Endpoint

<a name="generate-gif-alternative"></a>
#### Generate GIF (Alternative)

```
POST https://visioncraft.top/generate-gif
```

**Parameters:**

| Parameter | Type | Description |
|---|---|---|
| `token`* | string | Your API key |
| `sampler`* | string | The name of the chosen sampler |
| `prompt`* | string | A text prompt for generation |
| `negative_prompt` | string | Text prompt that the model shouldn't be drawn |
| `cfg_scale` | integer | How strongly the GIF should conform to the text (min: `0`, max: `20`, default: `10`) |
| `steps` | integer | How many times to iteratively improve the generated image (min: `1`, max: `50`, default: `30`) |

<sup>* Required parameters</sup>

**Request Example:**

```json
{
  "sampler": "Euler",
  "prompt": "Beautiful landscape",
  "negative_prompt": "canvas frame, cartoon, 3d, ...",
  "token": "your_api_key",
  "cfg_scale": 8,
  "steps": 30
}
```

<a name="code-examples"></a>
## Code Examples

<a name="llm-examples"></a>
### LLM Examples

<a name="python-add-image-to-request"></a>
#### Python (Add Image to Request)

```python
import base64
from openai import OpenAI

client = OpenAI(
    api_key="your_key",
    base_url="https://visioncraft.top/v1"
)

# Read and encode the image
with open("image.png", "rb") as image_file:
    base64_image = base64.b64encode(image_file.read()).decode('utf-8')

# Create a chat completion request with the image
chat_completion = client.chat.completions.create(
    stream=False, # Can be True
    model="llava-1.5-7b-hf",
    messages=[
        {
            "role": "user",
            "content": [
                {"type": "text", "text": "What’s in this image?"},
                {"type": "image_url", "image_url": {"url": f"data:image/jpeg;base64,{base64_image}"}}
            ]
        }
    ],
)
print(chat_completion)
```

<a name="javascript-node-js-add-image-to-request"></a>
#### JavaScript (Node.js) (Add Image to Request)

```javascript
const fetch = require('node-fetch');
const fs = require('fs');

async function generateTextWithImage() {
    const imageBuffer = fs.readFileSync('image.png');
    const base64Image = imageBuffer.toString('base64');

    const response = await fetch('https://visioncraft.top/v1/chat/completions', {
        method: 'POST',
        headers: {
            'Content-Type': 'application/json',
            'Authorization': 'Bearer your_api_key'
        },
        body: JSON.stringify({
            model: "llava-1.5-7b-hf",
            messages: [
                {
                    role: "user",
                    content: [
                        { type: "text", text: "What’s in this image?" },
                        { type: "image_url", "image_url": { url: `data:image/jpeg;base64,${base64Image}` } }
                    ]
                }
            ]
        })
    });
    
    const data = await response.json();
    console.log(data);
}

generateTextWithImage();
```

<a name="curl-add-image-to-request"></a>
#### cURL (Add Image to Request)

```sh
# Encode the image to base64
base64_image=$(base64 -w 0 image.png)

# Make the request
curl -X POST "https://visioncraft.top/v1/chat/completions" \
     -H "Content-Type: application/json" \
     -H "Authorization: Bearer your_api_key" \
     -d '{
            "model": "llava-1.5-7b-hf",
            "messages": [
                {
                    "role": "user",
                    "content": [
                        { "type": "text", "text": "What’s in this image?" },
                        { "type": "image_url", "image_url": { "url": "data:image/jpeg;base64,'"$base64_image"'" } }
                    ]
                }
            ]
         }'
```

<a name="python-available-models"></a>
#### Python (Available Models)

```python
import aiohttp
import asyncio

async def fetch_llm_models():
    """Get all available LLM models"""
    async with aiohttp.ClientSession() as session:
        async with session.get('https://visioncraft.top/models-llm') as response:
            return await response.json()

async def main():
    llm_models = await fetch_llm_models();
    print(llm_models)

if __name__ == '__main__':
    asyncio.run(main())
```

<a name="javascript-node-js-available-models"></a>
#### JavaScript (Node.js) (Available Models)

```javascript
const fetch = require('node-fetch');

async function fetchLLMModels() {
    const response = await fetch('https://visioncraft.top/models-llm');
    const data = await response.json();
    console.log(data);
}

fetchLLMModels();
```

<a name="curl-available-models"></a>
#### cURL (Available Models)

```sh
curl -X GET "https://visioncraft.top/models-llm"
```

<a name="python-text-generation"></a>
#### Python (Text Generation)

```python
from openai import OpenAI

client = OpenAI(
    api_key="your_api_key",
    base_url="https://visioncraft.top/v1"
)

chat_completion = client.chat.completions.create(
    stream=False, # Can be True
    model="Mixtral-8x7B-Instruct-v0.1",
    messages=[
        {
            "role": "user",
            "content": 'There are 50 books in a library. Sam decides to read 5 of the books. How many books are there now? If there are 45 books, say "1". Else, if there is the same amount of books, say "2".'
        },
    ],
)
print(chat_completion)
```

<a name="javascript-node-js-text-generation"></a>
#### JavaScript (Node.js) (Text Generation)

```javascript
const fetch = require('node-fetch');

async function generateText() {
    const response = await fetch('https://visioncraft.top/v1/chat/completions', {
        method: 'POST',
        headers: {
            'Content-Type': 'application/json',
            'Authorization': 'Bearer your_api_key'
        },
        body: JSON.stringify({
            model: "Mixtral-8x7B-Instruct-v0.1",
            messages: [
                {
                    role: "user",
                    content: 'There are 50 books in a library. Sam decides to read 5 of the books. How many books are there now? If there are 45 books, say "1". Else, if there is the same amount of books, say "2".'
                }
            ]
        })
    });
    const data = await response.json();
    console.log(data);
}

generateText();
```

<a name="curl-text-generation"></a>
#### cURL (Text Generation)

```sh
curl -X POST "https://visioncraft.top/v1/chat/completions" \
     -H "Content-Type: application/json" \
     -H "Authorization: Bearer your_api_key" \
     -d '{
            "model": "Mixtral-8x7B-Instruct-v0.1",
            "messages": [
                {
                    "role": "user",
                    "content": "There are 50 books in a library. Sam decides to read 5 of the books. How many books are there now? If there are 45 books, say \"1\". Else, if there is the same amount of books, say \"2\"."
                }
            ]
        }'
```

<a name="image-generation-examples"></a>
### Image Generation Examples

<a name="python-image-generation"></a>
#### Python

```python
import aiohttp
import asyncio

async def generate_image(api_url, data) -> bytes:
    timeout = aiohttp.ClientTimeout(total=None)  # Disable timeout
    async with aiohttp.ClientSession(timeout=timeout) as session:
        async with session.post(f"{api_url}/sd", json=data) as response:
            image = await response.read()
            return image

async def main():
    # Define the API endpoint
    api_url = "https://visioncraft.top"
    # Obtain your API key
    api_key = "your_api_key"

    # Generate image
    prompt = "Beautiful landscape"
    model = "sdxl-base"
    
    # Set up the data to send in the request
    data = {
        "model": model,
        "prompt": prompt,
        "token": api_key,
        "sampler": "Euler",
        "steps": 30,
        "width": 1024,
        "height": 1024,
        "cfg_scale": 7,
        "loras": {}
    }
    
    # Generate image asynchronously
    image = await generate_image(api_url, data)
    # Save the image locally
    with open(f"generated_image.png", "wb") as f:
        f.write(image)

if __name__ == "__main__":
    asyncio.run(main())
```

<a name="javascript-node-js-image-generation"></a>
#### JavaScript (Node.js)

```javascript
const fetch = require('node-fetch');
const fs = require('fs');

async function generateImage(apiUrl, data) {
    const response = await fetch(`${apiUrl}/sd`, {
        method: 'POST',
        headers: {
            'Content-Type': 'application/json'
        },
        body: JSON.stringify(data),
        timeout: 0  // Disable timeout
    });
    const buffer = await response.buffer();
    return buffer;
}

async function main() {
    const apiUrl = "https://visioncraft.top";
    const apiKey = "your_api_key";
    const prompt = "Beautiful landscape";
    const model = "sdxl-base";
    
    const data = {
        "model": model,
        "prompt": prompt,
        "token": apiKey,
        "sampler": "Euler",
        "steps": 30,
        "width": 1024,
        "height": 1024,
        "cfg_scale": 7,
        "loras": {}
    };
    
    const imageBuffer = await generateImage(apiUrl, data);
    fs.writeFileSync('generated_image.png', imageBuffer);
}

main();
```

<a name="curl-image-generation"></a>
#### cURL

```sh
curl -X POST "https://visioncraft.top/sd" \
     -H "Content-Type: application/json" \
     --max-time 0 \
     -d '{
            "model": "sdxl-base",
            "prompt": "Beautiful landscape",
            "negative_prompt": "bad quality",
            "token": "your_api_key",
            "sampler": "Euler",
            "steps": 30,
            "width": 1024,
            "height": 1024,
            "cfg_scale": 7,
            "loras": {}
        }'
```

<a name="text-to-gif-generation-examples"></a>
### Text-to-GIF Generation Examples

<a name="python-text-to-gif-generation"></a>
#### Python

```python
import aiohttp
import asyncio

async def generate_gif(api_url, data) -> bytes:
    timeout = aiohttp.ClientTimeout(total=None)  # Disable timeout
    async with aiohttp.ClientSession(timeout=timeout) as session:
        async with session.post(f"{api_url}/text2gif", json=data) as response:
            gif = await response.read()
            return gif

async def main():
    # Define the API endpoint
    api_url = "https://visioncraft.top"
    # Obtain your API key
    api_key = "your_api_key"

    # Generate GIF
    prompt = "A cat playing with a ball of yarn"
    
    # Set up the data to send in the request
    data = {
        "token": api_key,
        "prompt": prompt
    }
    
    # Generate GIF asynchronously
    gif = await generate_gif(api_url, data)
    # Save the GIF locally
    with open(f"generated_gif.gif", "wb") as f:
        f.write(gif)

if __name__ == "__main__":
    asyncio.run(main())
```

<a name="javascript-node-js-text-to-gif-generation"></a>
#### JavaScript (Node.js)

```javascript
const fetch = require('node-fetch');
const fs = require('fs');

async function generateGIF(apiUrl, data) {
    const response = await fetch(`${apiUrl}/text2gif`, {
        method: 'POST',
        headers: {
            'Content-Type': 'application/json'
        },
        body: JSON.stringify(data),
        timeout: 0  // Disable timeout
    });
    const buffer = await response.buffer();
    return buffer;
}

async function main() {
    const apiUrl = "https://visioncraft.top";
    const apiKey = "your_api_key";
    const prompt = "A cat playing with a ball of yarn";
    
    const data = {
        "token": apiKey,
        "prompt": prompt
    };
    
    const gifBuffer = await generateGIF(apiUrl, data);
    fs.writeFileSync('generated_gif.gif', gifBuffer);
}

main();
```

<a name="curl-text-to-gif-generation"></a>
#### cURL

```sh
curl -X POST "https://visioncraft.top/text2gif" \
     -H "Content-Type: application/json" \
     --max-time 0 \
     -d '{
            "token": "your_api_key",
            "prompt": "A cat playing with a ball of yarn"
        }'
```

<a name="gif-generation-examples"></a>
### GIF Generation Examples

<a name="python-gif-generation"></a>
#### Python

```python
import aiohttp
import asyncio

async def generate_gif(api_url, data):
    async with aiohttp.ClientSession() as session:
        async with session.post(f"{api_url}/generate-gif", json=data, verify_ssl=False) as response:
            return await response.json()

async def download_image(session, image_url, filename):
    async with session.get(image_url) as response:
        image_data = await response.read()
        with open(filename, "wb") as f:
            f.write(image_data)

async def main():
    # Define the API endpoint
    api_url = "https://visioncraft.top"
    # Obtain your API key
    api_key = "your_api_key"

    # Generate GIF using a specific model
    sampler = "Euler"
    prompt = "Beautiful landscape"
    cfg_scale = 8
    steps = 30

    # Set up the data to send in the request
    data = {
        "sampler": sampler,
        "prompt": prompt,
        "negative_prompt": "canvas frame, cartoon, 3d, ((disfigured)), ((bad art)), ((deformed)), ((extra limbs)), ((close up)), ((b&w)), weird colors, blurry, (((duplicate))), ((morbid)), ((mutilated)), [out of frame], extra fingers, mutated hands, ((poorly drawn hands)), ((poorly drawn face)), (((mutation))), ((ugly)), (((bad proportions))), (malformed limbs), ((missing arms)), ((missing legs)), (((extra arms))), (((extra legs))), (fused fingers), (too many fingers), (((long neck))), Photoshop, video game, tiling, poorly drawn feet, body out of frame",
        "token": api_key,
        "cfg_scale": cfg_scale,
        "steps": steps
    }

    # Generate GIF asynchronously
    response = await generate_gif(api_url, data)

    # Extract the image URL from the response
    image_url = response["images"][0]

    async with aiohttp.ClientSession() as session:
        await download_image(session, image_url, "generated_image.gif")

if __name__ == "__main__":
    asyncio.run(main())
```

<a name="javascript-node-js-gif-generation"></a>
#### JavaScript (Node.js)

```javascript
const fetch = require('node-fetch');
const fs = require('fs');

async function generateGif() {
    const response = await fetch('https://visioncraft.top/generate-gif', {
        method: 'POST',
        headers: {
            'Content-Type': 'application/json'
        },
        body: JSON.stringify({
            sampler: "Euler",
            prompt: "Beautiful landscape",
            negative_prompt: "canvas frame, cartoon, 3d, ((disfigured)), ((bad art)), ((deformed)), ((extra limbs)), ((close up)), ((b&w)), weird colors, blurry, (((duplicate))), ((morbid)), ((mutilated)), [out of frame], extra fingers, mutated hands, ((poorly drawn hands)), ((poorly drawn face)), (((mutation))), ((ugly)), (((bad proportions))), (malformed limbs), ((missing arms)), ((missing legs)), (((extra arms))), (((extra legs))), (fused fingers), (too many fingers), (((long neck))), Photoshop, video game, tiling, poorly drawn feet, body out of frame",
            token: "your_api_key",
            cfg_scale: 8,
            steps: 30
        })
    });
    
    const data = await response.json();
    const imageUrl = data.images[0];
    
    const imageResponse = await fetch(imageUrl);
    const buffer = await imageResponse.buffer();
    fs.writeFileSync('generated_image.gif', buffer);
}

generateGif();
```

<a name="curl-gif-generation"></a>
#### cURL

```sh
curl -X POST "https://visioncraft.top/generate-gif" \
     -H "Content-Type: application/json" \
     -d '{
            "sampler": "Euler",
            "prompt": "Beautiful landscape",
            "negative_prompt": "canvas frame, cartoon, 3d, ((disfigured)), ((bad art)), ((deformed)), ((extra limbs)), ((close up)), ((b&w)), weird colors, blurry, (((duplicate))), ((morbid)), ((mutilated)), [out of frame], extra fingers, mutated hands, ((poorly drawn hands)), ((poorly drawn face)), (((mutation))), ((ugly)), (((bad proportions))), (malformed limbs), ((missing arms)), ((missing legs)), (((extra arms))), (((extra legs))), (fused fingers), (too many fingers), (((long neck))), Photoshop, video game, tiling, poorly drawn feet, body out of frame",
            "token": "your_api_key",
            "cfg_scale": 8,
            "steps": 30
        }'
```

<a name="rate-limiting"></a>
## Rate Limiting

The VisionCraft API has rate limits in place to ensure fair usage and prevent abuse. The specific limits vary depending on the subscription tier. Please refer to the official API Limits documentation for the most up-to-date information: [https://api.visioncraft.top/limits](https://api.visioncraft.top/limits)

<a name="error-handling"></a>
## Error Handling

The API returns standard HTTP status codes to indicate the success or failure of a request. Common codes include:

* **200 OK:** The request was successful.
* **400 Bad Request:** The request was malformed or missing required parameters.
* **401 Unauthorized:** The API key is invalid or missing.
* **403 Forbidden:** You have exceeded your usage limits or are not subscribed to the required Telegram channel.
* **429 Too Many Requests:** You have exceeded the rate limit.
* **500 Internal Server Error:** An unexpected error occurred on the server.

The API may also return error messages in the response body to provide more details about the error.

<a name="links"></a>
## Links

* **GitHub Repository:** [https://github.com/Metimol1/VisionCraft](https://github.com/Metimol1/VisionCraft)
* **Telegram Bot:** [https://t.me/VisionCraft_bot](https://t.me/VisionCraft_bot)
* **API Limits:** [https://api.visioncraft.top/limits](https://api.visioncraft.top/limits)
* **Telegram Channel:** [https://t.me/visioncraft_channel](https://t.me/visioncraft_channel)

This comprehensive documentation provides a detailed overview of the VisionCraft API, its features, and how to use it effectively. If you have any further questions, please refer to the provided links or contact the VisionCraft team through their Telegram channels.
