# ShadowJourney API Documentation

## Table of Contents
- [Introduction](#introduction)
  - [Free vs. Premium Features](#free-vs-premium-features)
  - [Pricing](#pricing)
  - [API Capacities and Limits](#api-capacities-and-limits)
- [Authentication Methods](#authentication-methods)
- [Making Requests](#making-requests)
  - [Code Snippets](#code-snippets)
  - [OpenAI and Other Models](#openai-and-other-models-1)
  - [Anthropic Models](#anthropic-models-1)
  - [Image Generation Dalle-3](#image-generation-dalle-3-1)
  - [Text To Speech](#text-to-speech-1)
- [HuggingFace Models](#huggingface-models)
  - [HPT-2](#hpt-2)
  - [adolpha-z](#adolpha-z)
  - [codehecker-7b](#codehecker-7b)
  - [Synth](#synth)
- [Endpoints](#endpoints)
  - [Audio](#audio)
  - [Chat Endpoints](#chat-endpoints)
    - [OpenAI and Other Models](#openai-and-other-models-2)
    - [Pro](#pro)
    - [Anthropic Models](#anthropic-models-2)
    - [Google Models](#google-models)
  - [Image Diffusion](#image-diffusion)
  - [Vision](#vision)
- [Error Handling](#error-handling)
- [Rate Limiting](#rate-limiting)
- [Additional Resources](#additional-resources)
  - [Discord](#discord)
  - [Website](#website)
  - [Terms of Service](#terms-of-service)


<a name="introduction"></a>

## Introduction
The ShadowJourney API provides access to a diverse collection of large language models (LLMs) for various applications, including chatbots, text generation, image generation, and text-to-speech. Interact with the API using HTTP requests from any programming language, or through the provided Python and Node.js code examples.

### Key Features
* **Extensive Model Selection:** Offers models from leading providers like OpenAI, Anthropic, Google, and Meta, alongside open-source and custom-trained options.
* **Flexible Integration:** Supports interaction through HTTP requests, Python bindings, Node.js code, and a user interface.
* **Image Generation:** Enables image creation using DALL-E 3 and Stable Diffusion.
* **Text-to-Speech:** Provides text-to-speech functionality with a variety of voices.
* **Freemium Model:** Offers a free tier with daily credit limits and premium options for extended usage and access to exclusive models.

### <a name="free-vs-premium-features"></a>Free vs. Premium Features

| Feature | Free Version | Premium Version |
|---|---|---|
| Daily Credits | 2500 | Unlimited |
| Request Limit | 15 requests per minute | No Limit |
| Model Access | Access to most models | Access to all models, including premium ones like Claude-3-opus and advanced text-to-speech voices |
| Roleplay | Restricted | Allowed |
| Rate Limit | 4 credits per request | No credit deduction per request |


### <a name="pricing"></a>Pricing

ShadowJourney operates on a freemium model. The free tier provides access to a wide range of models with a daily credit limit. Premium models and usage beyond the daily limit require payment. Specific pricing details for premium offerings are not explicitly mentioned in the documentation.

### <a name="api-capacities-and-limits"></a>API Capacities and Limits

While the documentation doesn't explicitly state request/token limits for individual models, it mentions a daily limit of 2500 free credits. This likely translates to a certain number of tokens, but the exact conversion rate is unclear.  The rate limit for free users is 15 requests per minute, and each request consumes 4 credits. Premium users have no rate limits and no credit deductions per request.


<a name="authentication-methods"></a>

## Authentication Methods

### API Keys
To access the ShadowJourney API, you need an API key. Obtain your API key by following these steps:

1. Visit the [ShadowJourney Dashboard](https://shadowjourney.us.to/dashboard).
2. Log in to your account.
3. Click "Generate a new key."

To view your API key:

1. Click the designated form.
2. Input your old API key.

To delete an API key:

1. Input your current API key.
2. Click the "Delete key" button.

### Using Your API Key

Include your API key in the `Authorization` header of your HTTP requests:

```
{
  "Authorization": "Bearer YOUR_KEY_HERE"
}
```

<a name="making-requests"></a>

## Making Requests

### <a name="code-snippets"></a>Code Snippets

This section provides code examples for interacting with different endpoints and models.

### <a name="openai-and-other-models-1"></a>OpenAI and Other Models

Use the following code snippet to interact with OpenAI and other models through the `/v1/chat/completions` endpoint:

```python
import requests

api_key = "YOUR_KEY_HERE"

url = 'https://shadowjourney.us.to/v1/chat/completions'
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
      "content": "You are an Helpful Assistant"
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

Refer to the [models endpoint](https://shadowjourney.us.to/v1/models) for a list of available models.


### <a name="anthropic-models-1"></a>Anthropic Models

Use the same format as OpenAI models, but change the URL to `https://shadowjourney.us.to/v1/messages` and specify the desired Claude model:

```json
{
  "model": "claude-3-opus" 
}
```

### <a name="image-generation-dalle-3-1"></a>Image Generation Dalle-3

Use the following code snippet to generate images with DALL-E 3 through the `/v1/images/generations` endpoint:

```python
import requests

FLASK_APP_URL = "https://shadowjourney.us.to/v1/images/generations"

payload = {
  "prompt": "llama 3d cartoon style standing in green grass ",
  "model": "dalle-3",
  "n": 1,
  "size": "1024x1024"
}

headers = {
  'Authorization': 'Bearer YOUR_KEY_HERE',
  'Content-Type': 'application/json'
}

response = requests.post(FLASK_APP_URL, json=payload, headers=headers)

if response.status_code == 200:
  response_data = response.json()
  print("Image generation request was successful.")
  print("Response: https:", response_data)
else:
  print(f"Failed to generate image. Status code: {response.status_code}")
  print("Response content:", response.content)
```

This request will return a CDN link to the generated image.

### <a name="text-to-speech-1"></a>Text To Speech

Include the following JSON in the request body to use the text-to-speech functionality:

```json
{
  "text": "Hello, world!",
  "model": "modelname" 
}
```

Remember to include your API key in the `Authorization` header. This request will return a CDN link to the generated audio file.

<a name="huggingface-models"></a>

## HuggingFace Models

### <a name="hpt-2"></a>HPT-2

HPT-2, a fine-tuned GPT-2 model, excels at generating random strings and playing games. Use the following code to access it directly:

```python
from transformers import AutoTokenizer, AutoModelForCausalLM

tokenizer = AutoTokenizer.from_pretrained("Ichate/HTP2")
model = AutoModelForCausalLM.from_pretrained("Ichate/HTP2")
```

### <a name="adolpha-z"></a>adolpha-z

This model is currently unavailable.

### <a name="codehecker-7b"></a>codehecker-7b

Access this model through HeckerAI.

### <a name="synth"></a>Synth

This model is coming soon.

<a name="endpoints"></a>

## Endpoints

### <a name="audio"></a>Audio

The audio endpoint (`https://shadowjourney.us.to/v1/audio`) currently offers the TextToSpeech feature (`https://shadowjourney.us.to/v1/audio/texttospeech`) with two available models: "male" and "female."

### <a name="chat-endpoints"></a>Chat Endpoints

#### <a name="openai-and-other-models-2"></a>OpenAI and Other Models

Endpoint: `https://shadowjourney.us.to/v1/chat/completions`

#### <a name="pro"></a>Pro

Endpoint: `https://shadowjourney.us.to/pro`

#### <a name="anthropic-models-2"></a>Anthropic Models

Endpoint: `https://shadowjourney.us.to/v1/messages`

#### <a name="google-models"></a>Google Models

Endpoint: `https://shadowjourney.us.to/api/gemini`

Use the following code snippet to interact with Google models:

```python
import requests
import json

url = 'https://shadowjourney.us.to/api/gemini'
headers = {'Content-Type': 'application/json', "Authorization": 'Bearer yourkey'}

data = {
  'input': 'Your input goes here',
  'model': 'gemini-1.5-flash'
}

response = requests.post(url, headers=headers, data=json.dumps(data))
print(response.json())
```

### <a name="image-diffusion"></a>Image Diffusion

Endpoint: `https://shadowjourney.us.to/v1/images/generations`

### <a name="vision"></a>Vision

Endpoint: `https://shadowjourney.us.to/v1/chat/completions`

Currently, only `gpt-4-vision-preview` is available for vision tasks.

<a name="error-handling"></a>

## Error Handling

The documentation does not provide specific error handling guidelines. However, based on the provided information, here are some potential error scenarios and how to address them:

* **400 Error:** This error may indicate invalid input, insufficient credits, or exceeding the rate limit. Review your request parameters, ensure you have enough credits, and adhere to the rate limits.
* **500 Error:** This error may indicate a server-side issue or exhausted image generation credits. If related to image generation, wait for an hour for your credits to regenerate. For other 500 errors, try again later or contact ShadowJourney support.
* **Service Suspended Error:** This error indicates that the hosting service has suspended the API. The issue is usually temporary and resolves automatically within a few hours.


<a name="rate-limiting"></a>

## Rate Limiting

Free users are limited to 15 requests per minute. Each request consumes 4 credits. Premium users have no rate limits and no credit deductions per request.

<a name="additional-resources"></a>

## Additional Resources

### <a name="discord"></a>Discord

Join the ShadowJourney Discord server for support and updates: [https://discord.gg/PvMpnaDSET](https://discord.gg/PvMpnaDSET)

### <a name="website"></a>Website

Visit the ShadowJourney website: [https://shadowjourney.us.to/](https://shadowjourney.us.to/)

### <a name="terms-of-service"></a>Terms of Service

Review the ShadowJourney terms of service: [https://shadowjourney.us.to/tos](https://shadowjourney.us.to/tos)
