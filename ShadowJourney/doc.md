[Dashboard](https://shadowjourney.us.to/docs#) [Docs](https://shadowjourney.us.to/docs#) [API reference](https://shadowjourney.us.to/docs#)

## Introduction

You can interact with the API through HTTP requests from any language, via our official Python bindings, or with official Node.js code, or a [interface](https://shadowjourney.us.to/).

To send requests to our API in Python install this library:

```
pip install requests
```

To use our API in JS do the following:

```
npm install axios
```

## Authentication

### API keys

Before sending requests to our API, you need API keys. you can get them from [dashboard](https://shadowjourney.us.to/dashboard)

Then go login and click "generate a new key":

```
Generate a new key
```

To show your key do:

```
Click the form and input your old api key to view info
```

To delete a key do:

```
Input your current key, Click Delete key button
```

### Using the key

To use the key and put it in headers, do this:

```

                            {
                                "Authorization": "Bearer YOUR_KEY_HERE"
                            }
                        
```

Thats it for this section.

## Making Requests

### Code Snippets

In this section we will be showing code snippets and telling how to use them for each endpoint.

### OpenAI and Other Models

To use these models you need to go to [https://shadowjourney.us.to/v1/chat/completions](https://shadowjourney.us.to/v1/chat/completions) . This is the base endpoint for our api.

Code snippet to use it:

```
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

In this snippet we can choose different models, you can find them at [https://shadowjourney.us.to/v1/models](https://shadowjourney.us.to/v1/models)

### Anthropic Models

They are the same format as the OpenAI and other models. you have to just change the url to [https://shadowjourney.us.to/v1/messages](https://shadowjourney.us.to/claude) and do this:

```
"model": 'claude-3-opus'
```

You can find claude models at [https://shadowjourney.us.to/v1/models](https://shadowjourney.us.to/v1/models)

### Image Generation Dalle-3

To use Image Generation with Dalle-3 , use the following snippet:

```
                        import requests

                        # Define the URL of the Flask application
                        FLASK_APP_URL = "https://shadowjourney.us.to/v1/images/generations"
                        
                        # Define the payload for the image generation request
                        payload = {
                            "prompt": "llama 3d cartoon style standing in green grass ",
                            "model": "dalle-3",
                            "n": 1,
                            "size": "1024x1024"
                        }
                        
                        # Define the headers, including the Authorization header
                        headers = {
                            'Authorization':
                            'Bearer YOUR_KEY_HERE',  # Replace with your actual API key
                            'Content-Type': 'application/json'
                        }
                        
                        # Send a POST request to the Flask application
                        response = requests.post(FLASK_APP_URL, json=payload, headers=headers)
                        
                        # Check if the request was successful
                        if response.status_code == 200:
                            response_data = response.json()
                            print("Image generation request was successful.")
                            print("Response: https:", response_data)
                        else:
                            print(f"Failed to generate image. Status code: {response.status_code}")
                            print("Response content:", response.content)
                        
```

Replace your key in "YOUR\_KEY\_HERE" and you are good to go. it will return a cdn link.

### Text To Speech

To use text to speech just include this in the json body:

```
                   {
                        "text": "Hello, world!",
                        "model": "modelname"
                    }
```

In the headers put your Auth key and you are good to go. You can also change the model to different things. It will return a cdn link.

## HuggingFace

### HPT-2

HPT-2 is our new model finetuned from GPT-2. It is very good in typing random strings and playing games with the user.

To use the model you can use this snippet:

```
# Load model directly
                            from transformers import AutoTokenizer, AutoModelForCausalLM
                            
                            tokenizer = AutoTokenizer.from_pretrained("Ichate/HTP2")
                            model = AutoModelForCausalLM.from_pretrained("Ichate/HTP2")
```

```
With this code you can use HPT-2 directly. It has 124 parameters.
```

### adolpha-z

coming soon

### codehecker-7b

You can use it in HeckerAI

### Synth

coming very soon

### Endpoints

### Audio

Currently Audio endpoint:

```
https://shadowjourney.us.to/v1/audio
```

has only 1 feature, TextToSpeech

```
https://shadowjourney.us.to/v1/audio/texttospeech
```

Currently That also has 2 available models

```
"male", "female"
```

Thats it for this Section

### Chat Endpoints

## OpenAI and Other Models

For this the endpoint is:

```
https://shadowjourney.us.to/v1/chat/completions
```

## Pro

Currently the endpoint is:

```
https://shadowjourney.us.to/pro
```

## Anthropic Models

For this the endpoint is:

```
https://shadowjourney.us.to/claude
```

## Google Models

For this the endpoint is:

```
https://shadowjourney.us.to/api/gemini
```

```
import requests
import json

# Define the API endpoint
url = 'https://shadowjourney.us.to/api/gemini'  # Replace with your actual API URL

# Define the headers
headers = {'Content-Type': 'application/json', "Authorization": 'Bearer yourkey'}

# Define the data
data = {
    'input': 'Your input goes here',
    'model': 'gemini-1.5-flash'
}

# Send the POST request
response = requests.post(url, headers=headers, data=json.dumps(data))

# Print the response
print(response.json())
```

### Image Diffusion

## Endpoint

Current Endpoint is:

```
https://shadowjourney.us.to/v1/images/generations
```

### Vision

## Endpoint

The endpoint for using it is

```
https://shadowjourney.us.to/v1/chat/completions
```

For now only gpt-4-vision-preview is available (notfixed):

```
https://shadowjourney.us.to/v1/chat/completions
```

### End of Documentation

If you still aren't clear about how to use the API you can join our [Discord](https://discord.gg/PvMpnaDSET)

## Our Website

[https://shadowjourney.us.to/](https://shadowjourney.us.to/)

## Terms of Service

[https://shadowjourney.us.to/tos](https://shadowjourney.us.to/tos)

© 2024 ShadowJourney