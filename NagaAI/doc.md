# Documentation for PR Agent with Naga API Integration

This document explains how to run a PR Agent locally using the Naga API as a drop-in replacement for the OpenAI API. This allows you to leverage existing OpenAI-based code without modifications.

## Example Use Case: Running PR Agent Locally

The standard setup for PR Agent usually requires an OpenAI API key. However, due to the similar structure of OpenAI and Naga APIs, you can seamlessly integrate Naga without altering your existing PR Agent code.

## Leveraging Official OpenAI Packages

Official OpenAI packages available on PyPI utilize environment variables for configuration:

* **OPENAI_API_KEY:** Your API key.
* **OPENAI_BASE_URL:** The base URL of the API endpoint.

By setting these environment variables to your Naga API key and base URL, any application built with OpenAI packages will automatically use Naga. This offers a convenient way to migrate existing applications to the Naga API.

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

**Adding to Shell Startup Files (Unix only):**

For convenience, you can add these variables to your shell startup files like `.bashrc`:

```bash
curl https://raw.githubusercontent.com/segmentationf4u1t/NagaWeb/main/sourcemeUnix.txt >> ~/.bashrc
```

This script appends the necessary environment variables to your `.bashrc` file. Remember to replace the placeholders with your actual Naga API key and base URL.

## Example Codes & Implementations

This section provides code examples in Python and JavaScript demonstrating how to use both OpenAI and Naga APIs. These examples cover various functionalities, including chat completion, embeddings, image generation, and more.

**All Naga Endpoints:**

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

**Further Resources:**

* **Naga API Documentation:** <https://api.naga.ac/docs>
* **Mozilla Developer Network (MDN):** <https://developer.mozilla.org/en-US/>
* **OpenAI Platform Documentation:** <https://platform.openai.com/docs/introduction>
* **Python Fundamentals for Data Science:** <https://www.freecodecamp.org/news/python-fundamentals-for-data-science/>


# Code Examples

## Chat Completion

```python
import os
from openai import OpenAI

client = OpenAI(
    # This is the default and can be omitted
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

## Simple Embedding

```python
from openai import OpenAI

client = OpenAI()

def get_embedding(text, model="text-embedding-ada-002"):
   text = text.replace("\n", " ")
   return client.embeddings.create(input = [text], model=model).data[0].embedding

df['ada_embedding'] = df.combined.apply(lambda x: get_embedding(x, model='text-embedding-ada-002'))
df.to_csv('output/embedded_1k_reviews.csv', index=False)
```

## Simple Image Generation

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

## Simple Vision Generation

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

## Simple TTS

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