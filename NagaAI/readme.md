## Naga API Documentation

This documentation provides a comprehensive guide to the Naga API, a drop-in replacement for the OpenAI API. It details features, pricing, usage limits, and code examples.

### Table of Contents

- [Overview](#overview)
- [Free vs. Premium Comparison](#free-vs-premium-comparison)
- [Free Version Features](#free-version-features)
- [Premium Version Features](#premium-version-features)
- [Authentication Methods](#authentication-methods)
- [Endpoints](#endpoints)
    - [Chat Completions](#chat-completions)
    - [Embeddings](#embeddings)
    - [Image Generations](#image-generations)
    - [Vision Generations](#vision-generations)
    - [TTS](#tts)
    - [All Naga Endpoints](#all-naga-endpoints)
- [Code Examples](#code-examples)
    - [Chat Completion](#code-example-chat-completion)
    - [Simple Embedding](#code-example-simple-embedding)
    - [Simple Image Generation](#code-example-simple-image-generation)
    - [Simple Vision Generation](#code-example-simple-vision-generation)
    - [Simple TTS](#code-example-simple-tts)
- [Rate Limiting](#rate-limiting)
- [Error Handling](#error-handling)


<a name="overview"></a>
## Overview

The Naga API offers a variety of models for AI tasks such as text and image generation, embeddings, and audio processing. It's designed to be a seamless replacement for the OpenAI API, enabling users to utilize their existing OpenAI-based code without modifications.

<a name="free-vs-premium-comparison"></a>
## Free vs. Premium Comparison

### Feature Comparison Table

| Feature | Free Version | Premium Version |
|---|---|---|
| Access to Models | Limited Selection | All Models Available |
| Request Limits | Lower Limits (e.g., 3 requests/min for GPT-3.5-TURBO-1106) | Higher Limits (e.g., 10 requests/min for GPT-3.5-TURBO-1106 in Tier 1) |
| Daily Usage Limits | Lower Limits (e.g., 200 requests/day for GPT-3.5-TURBO-1106) | Higher Limits (e.g., 3000 requests/day for GPT-3.5-TURBO-1106 in Tier 1) |
| Cost | Free | Varies by Tier and Usage |

### Pricing Table

| Tier | Price | Request Limits | Daily Usage Limits |
|---|---|---|---|
| Free | Free | See Free Model Limits | See Free Model Limits |
| Tier 1 | Contact Naga | Increased Limits | Increased Limits |
| Tier 2 | Contact Naga | Further Increased Limits | Further Increased Limits |
| Tier 3 | Contact Naga | Significantly Increased Limits | Significantly Increased Limits |
| Tier 4 | Contact Naga | Highest Limits | Highest Limits |

### API Capacities and Limits Table

| Model | Free Limit | Tier-1 Limit | Tier-2 Limit | Tier-3 Limit | Tier-4 Limit |
|---|---|---|---|---|---|
| GPT-3.5-TURBO-1106 | 3/min, 200/day | 10/min, 3000/day | 15/min, 4500/day | 25/min, 7500/day | 40/min, 12000/day |
| GPT-4-0613 | Not available | 10/min, 2000/day | 15/min, 3000/day | 25/min, 5000/day | 40/min, 8000/day |
| CLAUDE-3.5-SONNET-20240620 | Not available | 3/min, 50/day | 3/min, 50/day | 3/min, 100/day | 5/min, 200/day |
| ... | ... | ... | ... | ... | ... |

**Note:** This table only includes a few examples. Refer to the `models.md` document for a complete list of models and their limits.

<a name="free-version-features"></a>
## Free Version Features

The free version of the Naga API provides access to a limited selection of models with lower request and daily usage limits. This allows users to experiment with the API and test its capabilities before committing to a paid tier. See the `models.md` document for a complete list of free models and their limitations.

<a name="premium-version-features"></a>
## Premium Version Features

The premium version of the Naga API offers access to all available models with significantly higher request and daily usage limits. Premium users also benefit from faster response times and priority support.

<a name="authentication-methods"></a>
## Authentication Methods

The Naga API utilizes the same authentication method as the OpenAI API. You need to set the `OPENAI_API_KEY` environment variable to your Naga API key.

**Setting Environment Variables:**

**Linux/macOS:**

```bash
export OPENAI_API_KEY=YourNagaKeyGoesHere
export OPENAI_BASE_URL=https://api.naga.ac/v1
```

**Windows:**

```powershell
$env:OPENAI_API_KEY=YourNagaKeyGoesHere
$env:OPENAI_BASE_URL=https://api.naga.ac/v1
```

<a name="endpoints"></a>
## Endpoints

The Naga API provides various endpoints mirroring the OpenAI API structure. Here are some key endpoints:

<a name="chat-completions"></a>
### Chat Completions

This endpoint allows you to generate conversational text using various models like GPT-3.5-TURBO and Claude.

**Parameters:**

* `model`: The ID of the model to use.
* `messages`: A list of messages comprising the conversation history.
* `max_tokens`: The maximum number of tokens to generate.
* `temperature`: Controls the randomness of the generated text.
* ...

**Response:**

* `id`: The ID of the completion.
* `object`: The type of object returned (e.g., "chat.completion").
* `created`: The timestamp of when the completion was created.
* `model`: The ID of the model used.
* `choices`: A list of completion choices, each with:
    * `message`: The generated message.
    * `finish_reason`: The reason the generation stopped (e.g., "stop", "length").
    * `index`: The index of the choice.
* `usage`: Token usage information.

<a name="embeddings"></a>
### Embeddings

This endpoint generates vector representations of text for tasks like semantic search and clustering.

**Parameters:**

* `model`: The ID of the embedding model to use.
* `input`: The text to embed.

**Response:**

* `object`: The type of object returned (e.g., "list").
* `data`: A list of embedding objects, each with:
    * `object`: The type of object (e.g., "embedding").
    * `embedding`: The embedding vector.
    * `index`: The index of the embedding.

<a name="image-generations"></a>
### Image Generations

This endpoint generates images from text prompts using models like DALL-E-3 and Stable Diffusion.

**Parameters:**

* `model`: The ID of the image generation model to use.
* `prompt`: The text prompt describing the desired image.
* `n`: The number of images to generate.
* `size`: The desired image size.

**Response:**

* `created`: The timestamp of when the image was created.
* `data`: A list of image objects, each with:
    * `url`: The URL of the generated image.

<a name="vision-generations"></a>
### Vision Generations

This endpoint allows you to analyze images and generate text descriptions or answers based on their content.

**Parameters:**

* `model`: The ID of the vision model to use (e.g., "gpt-4-vision-preview").
* `messages`: A list of messages, including image URLs and text prompts.

**Response:**

* Similar to the Chat Completions response, but the generated text is based on the provided image.

<a name="tts"></a>
### TTS

This endpoint converts text to speech using various voices and models.

**Parameters:**

* `model`: The ID of the TTS model to use.
* `voice`: The desired voice for the speech.
* `input`: The text to convert to speech.

**Response:**

* An audio stream that can be downloaded or streamed directly.

<a name="all-naga-endpoints"></a>
### All Naga Endpoints

* **Base URL:** <https://api.naga.ac/v1/>
* **Documentation:** <https://api.naga.ac/docs>
* **Models:** <https://api.naga.ac/v1/models>
* **Limits:** <https://api.naga.ac/v1/limits>
* **Embeddings:** <https://api.naga.ac/v1/embeddings>
* **Moderations:** <https://api.naga.ac/v1/moderations>
* **Chat Tokenizer:** <https://api.naga.ac/v1/chat/tokenizer>
* **Chat Completions:** <https://api.naga.ac/v1/chat/completions>
* **Image Generations:** <https://api.naga.ac/v1/image/generations>
* **Audio Translations:** <https://api.naga.ac/v1/audio/translations>
* **Audio TTS Generation:** <https://api.naga.ac/v1/audio/tts/generation>
* **Audio Transcriptions:** <https://api.naga.ac/v1/audio/transcriptions>

<a name="code-examples"></a>
## Code Examples

<a name="code-example-chat-completion"></a>
### Chat Completion

```python
import os
from openai import OpenAI

client = OpenAI(
    api_key=os.environ.get("OPENAI_API_KEY"),
)

chat_completion = client.chat.completions.create(
    messages=[
        {
            "role": "user",
            "content": "Say this is a test",
        }
    ],
    model="gpt-3.5-turbo",
)
```

<a name="code-example-simple-embedding"></a>
### Simple Embedding

```python
from openai import OpenAI

client = OpenAI()

def get_embedding(text, model="text-embedding-ada-002"):
   text = text.replace("\n", " ")
   return client.embeddings.create(input = [text], model=model).data[0].embedding

df['ada_embedding'] = df.combined.apply(lambda x: get_embedding(x, model='text-embedding-ada-002'))
df.to_csv('output/embedded_1k_reviews.csv', index=False)
```

<a name="code-example-simple-image-generation"></a>
### Simple Image Generation

```python
from openai import OpenAI

client = OpenAI()

response = client.images.generate(
  model="dall-e-3",
  prompt="a white siamese cat",
  size="1024x1024",
  quality="standard",
  n=1,
)

image_url = response.data[0].url
```

<a name="code-example-simple-vision-generation"></a>
### Simple Vision Generation

```python
from openai import OpenAI

client = OpenAI()

response = client.chat.completions.create(
  model="gpt-4-vision-preview",
  messages=[
    {
      "role": "user",
      "content": [
        {"type": "text", "text": "What’s in this image?"},
        {
          "type": "image_url",
          "image_url": {
            "url": "https://upload.wikimedia.org/wikipedia/commons/thumb/d/dd/Gfp-wisconsin-madison-the-nature-boardwalk.jpg/2560px-Gfp-wisconsin-madison-the-nature-boardwalk.jpg",
          },
        },
      ],
    }
  ],
  max_tokens=300,
)

print(response.choices[0])
```

<a name="code-example-simple-tts"></a>
### Simple TTS

```python
from pathlib import Path
from openai import OpenAI

client = OpenAI()

speech_file_path = Path(__file__).parent / "speech.mp3"
response = client.audio.speech.create(
  model="tts-1",
  voice="alloy",
  input="Today is a wonderful day to build something people love!"
)

response.stream_to_file(speech_file_path)
```


<a name="rate-limiting"></a>
## Rate Limiting

The Naga API implements rate limits to ensure fair usage and prevent abuse. These limits vary based on the model and the user's subscription tier. Refer to the `models.md` document for specific rate limits for each model and tier.

<a name="error-handling"></a>
## Error Handling

The Naga API returns standard HTTP error codes. Common errors include:

* **429 Too Many Requests:** Indicates you have exceeded the rate limit.
* **401 Unauthorized:** Indicates an invalid or missing API key.
* **400 Bad Request:** Indicates an invalid request format or parameters.

It is recommended to implement proper error handling in your application to gracefully handle these situations.

## Further Resources

* **Naga API Documentation:** <https://api.naga.ac/docs>
* **Mozilla Developer Network (MDN):** <https://developer.mozilla.org/en-US/>
* **OpenAI Platform Documentation:** <https://platform.openai.com/docs/introduction>
* **Python Fundamentals for Data Science:** <https://www.freecodecamp.org/news/python-fundamentals-for-data-science/>
