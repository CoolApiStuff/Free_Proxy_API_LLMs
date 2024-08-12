# VisionCraft API Documentation

Welcome to the VisionCraft API documentation! This guide provides comprehensive information on how to use the VisionCraft API for various tasks, including text generation, image generation, and GIF generation.

## Table of Contents

* [Tier](#tier)
* [Obtaining an API Key](#obtaining-an-api-key)
* [Subscriptions and Limits](#subscriptions-and-limits)
* [LLM](#llm)
    * [Add Image to Request](#add-image-to-request)
    * [Available Models](#available-models)
    * [Text Generation](#text-generation)
* [Image Generation](#image-generation)
    * [Available Samplers](#available-samplers)
    * [Available Models](#available-models-1)
    * [Available Loras](#available-loras)
* [Text-to-GIF Generation](#text-to-gif-generation)
* [Error Handling](#error-handling)
* [Links](#links)

## Tier

The VisionCraft API offers four subscription tiers: Free, Tier 1 ($10/month), Tier 2 ($20/month), and a special tier available once every 30 days.

### Free Tier

* Access to all models
* Limited number of requests per second (see [Limits](https://api.visioncraft.top/limits))

### Tier 1 ($10 per month)

* Access to all models
* Increased number of requests per second (see [Limits](https://api.visioncraft.top/limits))

### Tier 2 ($20 per month)

* Access to all models
* Unlimited usage

### Free Tier 1 for 24 hours

* Available once every 7 days

## Obtaining an API Key

To use the VisionCraft API, you need to obtain an API key. Follow these steps:

1. **Subscribe to the VisionCraft Telegram channel:** [https://t.me/visioncraft_channel](https://t.me/visioncraft_channel)
2. **Send the `/key` command to the VisionCraft bot:** [https://t.me/VisionCraft_bot](https://t.me/VisionCraft_bot)
3. **Secure your key:** Do not share your API key publicly.

**Note:** Your API key is linked to your subscription to the VisionCraft Telegram channel. Unsubscribing will deactivate your key. Resubscribing will reactivate it.

## Subscriptions and Limits

To purchase a premium subscription, use the `/premium` command in the VisionCraft Telegram bot.

Check the limits for all tiers: [https://api.visioncraft.top/limits](https://api.visioncraft.top/limits)

## LLM

### Add Image to Request

The LLaVA model allows you to interact with images. Only the LLaVA model supports images!

**Examples:**

See the [LLM Examples](#llm-examples) section for examples in Python, JavaScript, and cURL.

### Available Models

Retrieve a list of available LLM models:

```
GET https://visioncraft.top/models-llm
```

**Response:**

```json
["lzlv_70b_fp16_hf", "CodeLlama-34b-Instruct-hf", ...]
```

**Examples:**

See the [LLM Examples](#llm-examples) section for examples in Python, JavaScript, and cURL.

### Text Generation

Generate text using the chosen LLM model:

```
POST https://visioncraft.top/v1/chat/completions
```

**Parameters:**

| Parameter          | Type    | Description                                                                                               |
|--------------------|---------|-----------------------------------------------------------------------------------------------------------|
| `model`*           | string  | The name of the chosen LLM model                                                                          |
| `max_tokens`       | integer | Maximum length of the generated text (min: `128`, max: `100000`, default: `512`)                          |
| `temperature`      | float   | Sampling temperature. 0 means deterministic output, values >1 encourage diversity (min: `0`, max: `100`, default: `0.7`)  |
| `top_p`            | float   | Probability threshold for token sampling (min: `0`, max: `1`, default: `0.9`)                             |
| `top_k`            | integer | Number of top tokens to sample from (min: `0`, max: `99999`, default: `0`)                                |
| `repetition_penalty`| float   | Penalty for token repetition (min: `0.01`, max: `5`, default: `1`)                                        |
| `presence_penalty` | float   | Positive values penalize new tokens based on their presence in the text so far (min: `-2`, max: `2`, default: `0`) |
| `frequency_penalty`| float   | Positive values penalize new tokens based on their frequency in the text so far (min: `-2`, max: `2`, default: `0`) |
| `messages`*        | list    | Messages to the LLM                                                                                       |

<sup>* Required parameters</sup>

**Request Example:**

```
Authorization: Bearer your_api_key
```

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

**Examples:**

See the [LLM Examples](#llm-examples) section for examples in Python, JavaScript, and cURL.


## Image Generation

Generate images using Stable Diffusion models:

```
POST https://visioncraft.top/sd
```

**Parameters:**

| Parameter        | Type    | Description                                                                                                   |
|------------------|---------|---------------------------------------------------------------------------------------------------------------|
| `token`*         | string  | Your API key                                                                                                   |
| `model`*         | string  | One of the available SD models                                                                                 |
| `prompt`*        | string  | A text prompt for generation                                                                                   |
| `negative_prompt`| string  | Text prompt that the model shouldn't be drawn on the picture                                                   |
| `sampler`       | string  | One of the available SD samplers                                                                               |
| `steps`         | integer | How many times to iteratively improve the image (min: `1`, max: `35`, default: `35`)                           |
| `width`         | integer | Generated image width (min: `64`, max: `1024`, default: `1024`)                                                |
| `height`        | integer | Generated image height (min: `64`, max: `1024`, default: `1024`)                                               |
| `cfg_scale`      | integer | How strongly the image should conform to the text (min: `1`, max: `30`, default: `7`)                          |
| `loras`          | dict    | Dictionary of available loras (max `5` in dict)                                                                |

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

**Loras Usage:**

```json
{
  "lora_name_1": priority,
  "lora_name_2": priority,
  "lora_name_3": priority
}
```

**Examples:**

See the [Image Generation Examples](#image-generation-examples) section for examples in Python, JavaScript, and cURL.


### Available Samplers

Retrieve a list of available samplers for image generation:

```
GET https://visioncraft.top/sd/samplers
```

**Response:**

```json
["Euler a", "Euler", "LMS", ...]
```

**Examples:**

See the [Image Generation Examples](#image-generation-examples) section for examples in Python, JavaScript, and cURL.

### Available Models

Retrieve a list of available models for image generation:

```
GET https://visioncraft.top/sd/models
```

**Response:**

```json
["sdxl-base", "sdxl-refiner", "deliberate_v2", ...]
```

**Examples:**

See the [Image Generation Examples](#image-generation-examples) section for examples in Python, JavaScript, and cURL.


### Available Loras

Retrieve a list of available Loras for image generation:

```
GET https://visioncraft.top/sd/loras
```

**Response:**

```json
["add_detail", "analog_diffusion_1.0", "anireality_mix", ...]
```

**Examples:**

See the [Image Generation Examples](#image-generation-examples) section for examples in Python, JavaScript, and cURL.


## Text-to-GIF Generation

Generate GIFs from text prompts:

```
POST https://visioncraft.top/text2gif
```

**Parameters:**

| Parameter | Type   | Description                                                                                 |
|-----------|--------|---------------------------------------------------------------------------------------------|
| `token`*  | string | Your API key                                                                                 |
| `prompt`* | string | A text prompt to generate a GIF from                                                        |

<sup>* Required parameters</sup>

**Request Example:**

```json
{
  "token": "your_api_key",
  "prompt": "A cat playing with a ball of yarn"
}
```

**Examples:**

See the [Text-to-GIF Generation Examples](#text-to-gif-generation-examples) section for examples in Python, JavaScript, and cURL.


## Error Handling

The API returns standard HTTP status codes. Common codes include:

* **200 OK:** The request was successful.
* **400 Bad Request:** The request was malformed or missing required parameters.
* **401 Unauthorized:** The API key is invalid or missing.
* **403 Forbidden:** You have exceeded your usage limits or are not subscribed to the required Telegram channel.
* **429 Too Many Requests:** You have exceeded the rate limit.
* **500 Internal Server Error:** An unexpected error occurred on the server.

The API may also return error messages in the response body.

## Links

* **GitHub Repository:** [https://github.com/Metimol1/VisionCraft](https://github.com/Metimol1/VisionCraft)
* **Telegram Bot:** [https://t.me/VisionCraft_bot](https://t.me/VisionCraft_bot)
* **API Limits:** [https://visioncraft.top/limits](https://visioncraft.top/limits)
* **Telegram Channel:** [https://t.me/visioncraft_channel](https://t.me/visioncraft_channel)

---

This concludes the main documentation. Please refer to the following sections for code examples.

## LLM Examples

### Python (Add Image to Request)

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

### JavaScript (Node.js) (Add Image to Request)

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

### cURL (Add Image to Request)

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

### Python (Available Models)

```python
import aiohttp
import asyncio

async def fetch_llm_models():
    """Get all available LLM models"""
    async with aiohttp.ClientSession() as session:
        async with session.get('https://visioncraft.top/models-llm') as response:
            return await response.json()

async def main():
    llm_models = await fetch_llm_models()
    print(llm_models)

if __name__ == '__main__':
    asyncio.run(main())
```

### JavaScript (Node.js) (Available Models)

```javascript
const fetch = require('node-fetch');

async function fetchLLMModels() {
    const response = await fetch('https://visioncraft.top/models-llm');
    const data = await response.json();
    console.log(data);
}

fetchLLMModels();
```

### cURL (Available Models)

```sh
curl -X GET "https://visioncraft.top/models-llm"
```

### Python (Text Generation)

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

### JavaScript (Node.js) (Text Generation)

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

### cURL (Text Generation)

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


## Image Generation Examples

### Python

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

### JavaScript (Node.js)

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

### cURL

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

## Text-to-GIF Generation Examples

### Python

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

### JavaScript (Node.js)

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

### cURL

```sh
curl -X POST "https://visioncraft.top/text2gif" \
     -H "Content-Type: application/json" \
     --max-time 0 \
     -d '{
            "token": "your_api_key",
            "prompt": "A cat playing with a ball of yarn"
        }'
```

---

#Models

* airoboros-70b
* dolphin-2.6-mixtral-8x7b
* openchat-3.6-8b
* Mixtral-8x22B-Instruct-v0.1
* codegemma-7b-it
* WizardLM-2-8x22B
* zephyr-orpo-141b-A35b-v0.1
* dbrx-instruct
* Mistral-7B-Instruct-v0.3
* Llama-2-70b-chat-hf
* Mixtral-8x7B-Instruct-v0.1
* Llama-3-8B-Instruct
* Mixtral-8x22B-v0.1
* Yi-34B-Chat
* Llama-2-7b-chat-hf
* Llama-2-13b-chat-hf
* gemma-1.1-7b-it
* Qwen2-72B-Instruct
* Phi-3-medium-4k-instruct
* L3-70B-Euryale-v2.1
* dolphin-2.9.1-llama-3-70b
* Llama-3-70B-Instruct
* lzlv_70b_fp16_hf
* WizardLM-2-7B
* llava-1.5-7b-hf
* gemma-2-9b-it
* gemma-2-27b-it
* Llama-3.1-8B-Instruct
* Llama-3.1-70B-Instruct
* Llama-3.1-405B-Instruct
* Nemotron-4-340B-Instruct
