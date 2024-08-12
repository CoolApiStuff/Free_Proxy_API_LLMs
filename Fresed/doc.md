## 🚀 Getting Started

To interact with the Fresed API, you need to generate an API key. Follow these steps to obtain your key:

1.  Go to the chat: ⁠🤖│commands.
    
2.  Use the command `/gen_key` to generate a new key.
    
3.  If you already have a key, use `/show_key` to view it.
    
4.  To recreate the key, use `/generate_key`.
    

[Previous🎉 Introduction](https://fresed-api.gitbook.io/fresed-api)[Next🌐 API Endpoints](https://fresed-api.gitbook.io/fresed-api/api-endpoints)

Last updated 22 days ago

---

## 🌐 API Endpoints

#### 

Basic URL API

*   Base URL: `https://fresedgpt.space/v1`
    

#### 

Chat Completions

*   Endpoint: `https://fresedgpt.space/v1/chat/completions`
    
*   Use this endpoint for generating better GPT responses.
    

#### 

Image Generation

*   Endpoint: `https://fresedgpt.space/v1/images/generations`
    
*   Use this endpoint to generate images based on text prompts.
    

#### 

Speech Generation

*   Endpoint: `https://fresedgpt.space/v1/audio/speech`
    
*   Use this endpoint to generate speech from text input.
    

#### 

Temporary Email Service

*   **Endpoint:** `https://fresedgpt.space/v1/temp_mail/generate` Use this endpoint to generate a temporary email address
    
*   **Endpoint:** `https://fresedgpt.space/v1/temp_mail/messages/{identifier}` Use this endpoint to retrieve messages for a specific temporary email address using the identifier.
    

Last updated 4 hours ago

---

*   **Supported Models List:**
    
    *   [View supported models](https://fresedgpt.space/v1/models)
        
    
*   **API Status:**
    
    *   [Monitor API status](https://stats.uptimerobot.com/UPZd5tBI9z/796838663)
        
    

To ensure that the model has access to the network, you need to add +web (gpt-4o+web) when requesting it.

---

The list of available domain names for generating temporary emails has been updated. Each domain has an associated coefficient that impacts the cost of creating a new temporary email. Below is the list of domains with their corresponding coefficients:

```
<span><span>"1secmail.com": 0.2,
"1secmail.net": 0.2,
"1secmail.org": 0.2,
"amik.pro": 0.2,
"blondmail.com": 0.2,
"chapsmail.com": 0.2,
"clowmail.com": 0.2,
"dispmail.org": 0.2,
"dpptd.com": 0.2,
"dropjar.com": 0.2,
"dygovil.com": 0.2,
"fivermail.com": 0.2,
"getairmail.com": 0.2,
"getmule.com": 0.2,
"getnada.com": 0.2,
"gimpmail.com": 0.2,
"givmail.com": 0.2,
"gmail.com": 2.0,
"gonetor.com": 0.2,
"guysmail.com": 0.2,
"inboxbear.com": 0.2,
"knmcadibav.com": 0.2,
"laafd.com": 0.2,
"mailaugust.com": 0.2,
"mailfebruary.com": 0.2,
"mailjanuary.com": 0.2,
"qacmjeq.com": 0.2,
"qejjyl.com": 0.2,
"eplyloop.com": 0.2,
"rfcdrive.com": 0.2,
"robot-mail.com": 0.2,
"rteet.com": 0.2,
"smykwb.com": 0.2,
"somelora.com": 0.2,
"spicysoda.com": 0.2,
"tafmail.com": 0.2,
"temptami.com": 0.2,
"tidissajiiu.com": 0.2,
"tippabble.com": 0.2,
"tupmail.com": 0.2,
"txcct.com": 0.2,
"vafyxh.com": 0.2,
"vjuum.com": 0.2,
"vomoto.com": 0.2,
"vvatxiy.com": 0.2,
"whatisakilowatt.com": 0.2,
"wywnxa.com": 0.2,
"zlorkun.com": 0.2,
```

*   **Email Creation Cost:** The cost of creating a new temporary email is calculated as `800 * coefficient`, where the coefficient corresponds to the selected domain from the list above.
    
*   **Message Retrieval:** Receiving messages is free and unlimited.
    

A new command has been added to the API that allows users to view usage statistics.

---

# Chat Completion Example
```
from openai import AsyncOpenAI

client = AsyncOpenAI(
    api_key='fresed-...',
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
Image Generation Example
Copy
from openai import OpenAI

client = OpenAI(base_url='https://fresedgpt.space/v1', api_key='fresed-...')

response = client.images.generate(
    model="midjourney",
    prompt="a white siamese cat",
    size="1024x1024"
)

print(response)
Speech Generation Example
Copy
from openai import OpenAI

client = OpenAI(
    api_key='fresed-...',
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

## Temporary Email Example

```
import httpx
import asyncio

BASE_URL = "https://fresedgpt.space/v1"
API_KEY = "fresed-..."

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

---

## 🔄 System of referrals and levels

#### 

Referral Exchange Rates

*   5 referrals: 85,000 tokens every day for a month (access to Claude)
    
*   10 referrals: 160,000 tokens every day for a month
    
*   20 referrals: 320,000 tokens every day for a month
    
*   40 referrals: 960,000 tokens every day for a month
    
*   60 referrals: 1,600,000 tokens every day for a month
    

#### 

How to Exchange Referrals

*   Message @fresed to exchange referrals for subscriptions.
    

#### 

Referral System Features

*   `/user_info` - Displays user information including their referral code.
    
*   Use a Referral Code: Command `/activate_referral` gives 160,000 tokens for 3 days and access to Claude. Each user can activate a code only once.
    
*   Referral Contest: The top users with the most activated codes will receive a one-month subscription.
    

Level System

*   Levels and rewards are available for activity in the chat channel:
    
    *   Level 1: 88,000 tokens
        
    *   Level 2: 128,000 tokens
        
    *   Level 3: 160,000 tokens
        
    
*   Levels are awarded monthly and calculated only in chat channels. Message @fresed to assign your role.
    

Last updated 22 days ago

---

## 🔢 Limit System

#### 

Default Limit

*   All users have a default limit of 80,000 tokens.
    

#### 

Token Mode 🎟️

*   Receive 80,000 tokens every day.
    
*   No limit on the number of requests per minute.
    

#### 

Request Mode 📋

*   Receive 100 requests every day.
    
*   Each request uses 800 tokens.
    

#### 

Switching Modes

*   Use the command `/set_limit_mode` to switch between modes.
    
*   Check all limit information using `/all_limits`.
    

Models have a token coefficient. Each model has its own coefficient. View the coefficients here: [Model Coefficients](https://fresedgpt.space/v1/models)

Last updated 22 days ago

---

## 💰 Donation Information

Support our service and get more tokens per month!

*   $5: 320,000 tokens
    
*   $10: 960,000 tokens
    
*   $15: 1,600,000 tokens
    

For other amounts, contact @fresed. Refunds are available if GPT models do not work.

#### 

Unlimited Access

*   Unlimited API access: $100 per month
    
*   Access to Claude: $3 (tokens not included)
    

Last updated 22 days ago