# Pricing 

**Tier 1 (5$/month)**

Balance 20$/month Access to premium models Lower limits

**Tier 2 (8$/month)**

Balance 40$/month Access to premium models Lower limits

**Tier 3 (12$/month)**

Unlimited balance Lower limits

Access to premium models

**Tier 4 (16$/month)**

Unlimited balance Lower limits Access to premium models

**Tier 5 (20$/month)**

Unlimited balance Lower limits Access to premium models

**Tier 6 (24$/month)**

Unlimited balance Lower limits Access to premium models

---

## Limits

When you sign up, you will have free access to 4 *dollars* per month. You can spend them when using GPT 4, GPT 3.5 and other models.

But the prices for the models will be much lower than OpenAI and Anthropic. In the future there may be changes in price and starting balance, follow the news in our telegram channel.

You can also buy tariffs, with which you will have access to limited models, as well as will be increased balance per month.

## 

Rate Limits (Requests)

| **Endpoint**              | **Free**     | **Tier 1**   | **Tier 2**    | **Tier 3** | **Tier 4** | **Tier 5** | **Tier 6** |
|---------------------------|--------------|--------------|---------------|------------|------------|------------|------------|
| **/v1/chat/completions**  | *15/m 200/d* | *50/m 800/d* | 8*0/m 1300/d* | *2500/ d*  | *4200/ d*  | *7500/ d*  | *12000/ d* |
| **/v1/image/generations** | *8/m 60/d*   | *30/m 120/d* | *60/m 160/d*  | *350/d*    | *350/d*    | *350/d*    | *350/d*    |



These limits are also subject to change

Last updated 1 month ago

---

## 🤖Models

Some of the patterns may be less stable without a marker!

## 

OpenAI

*   gpt-4o / gpt-4o-2024-05-13 (premium)
    
*   gpt-4o-mini / gpt-4o-mini-2024-07-18 (premium)
    
*   gpt-4-turbo / gpt-4-turbo-2024-04-09 (premium)
    
*   gpt-4-0125-preview (premium)
    
*   gpt-4-1106-preview
    
*   gpt-4-32k
    
*   gpt-4
    
*   gpt-3.5-turbo-16k
    
*   gpt-3.5-turbo
    
*   dall-e-3
    

## 

Open Source

*   gemma-7b-it
    
*   mixtral-8x7b
    
*   llama-3-70b
    
*   llama-3-8b
    
*   llama-3.1-405b
    
*   llama-3.1-70b
    
*   wizardlm-2-8x22b
    
*   mixtral-8x22b
    
*   sdxl
    

Some models may not be available or may only be available for paid plans

Last updated 14 days ago

---

## 💲Pricing

## 

Price per 1K tokens (LLMs)

*   gpt-4o - 0.005$ input / 0.015$ output
    
*   gpt-4o-mini - 0.00015$ input / 0.0006 output
    
*   gpt-4-turbo - 0.01$ input / 0.03$ output
    
*   gpt-4-0125-preview - 0.01$ input / 0.02$ output
    
*   gpt-4-1106-preview - 0.01$ input / 0.03$ output
    
*   gpt-4-32k - 0.06$ input / 0.10$ output
    
*   gpt-4 - 0.03$ input / 0.04$ output
    
*   gpt-3.5-turbo-16k - 0.003$ input / 0.004$ output
    
*   gpt-3.5-turbo - 0.0005$ input / 0.0014$ output
    
*   llama3-70b - 0.0012$ input / 0.0014$ output
    
*   llama3-8b - 0.0008$ input / 0.0009$ output
    
*   llama-3.1-405b - 0.004$ input / 0.005$ output
    
*   llama-3.1-70b - 0.0012$ input / 0.002$ output
    
*   mixtral-8x7b - 0.001$ input / 0.002$ output
    
*   gemma-7b-it - 0.0004$ input / 0.0005$ output
    
*   wizardlm-2-8x22B - 0.002$ input / 0.004$ output
    
*   mixtral-8x22b - 0.0015$ input / 0.0017$ output
    

## 

Price per generation (Image generators models)

The size of the image as well as the quality does not matter!

*   dall-e-3 - 0.04$
    
*   sdxl - 0.02$
    

Last updated 14 days ago

---

## 🛠️Receiving a API token

To get a token, go to our [Telegram bot](https://t.me/gpt4all_robot), and enter the command /token. In it you can also check your statistic (/stats)

[PreviousPricing](https://docs.gpt4-all.xyz/information/pricing)[NextAPI Endpoint](https://docs.gpt4-all.xyz/main/api-endpoint)

Last updated 4 months ago

---
```
from openai import OpenAI

client = OpenAI(api_key="YOUR_TOKEN", base_url="https://api.gpt4-all.xyz/v1")

response = client.chat.completions.create(
    model="gpt-4o-mini",
    messages=[{"role": "user", "content": "hi"}],
    stream=False,
)

print(response.choices[0].message.content)
```