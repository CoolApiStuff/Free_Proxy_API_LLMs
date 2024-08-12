# Top links : 
- https://github.com/xtekky/gpt4free/tree/main
- https://github.com/zukixa/cool-ai-stuff?tab=readme-ov-file#overview-of-apis
- https://rentry.co/revvapis
- https://github.com/LiLittleCat/awesome-free-chatgpt/blob/main/README_en.md
- https://github.com/PawanOsman/ChatGPT



# ShuttleAI Free Tier 

## Overview

ShuttleAI offers a generous free tier allowing developers to explore and experiment with their platform. You get 500 free requests per day across a wide range of models with no hidden fees. 

## Features

Here's a breakdown of what's included in the free tier:

**Models:**

* **ShuttleAI Models:**
    * **Shuttle-2-Turbo (64k):** ShuttleAI's largest LLM, comparable to GPT-4 in performance.
    * **Shuttle-Turbo (32k):**  A powerful turbo chat completion model with image recognition and web access.
    * **Shuttle Diffusion:**  High-quality image generation, surpassing SDXL, Playground v2.5, and Dall-E 3 in speed and quality according to ShuttleAI. 
* **OpenAI Models:**  
    * `gpt-4-0613`
    * `gpt-4-bing`
* **Anthropic Models:**
    * `claude-instant-1.0`
* **Meta Models:**
    * `meta-llama-3-70b-instruct`
    * `meta-llama-3-8b-instruct`
* **Other Models:**
    * Many open-source models like `wizardlm-2-70b`, `dolphin-2.6-mixtral-8x7b`,  and `Nous Hermes 2 - Mixtral 8x7b`.
    * Tools like web search, text-to-speech (`tts-1`), and joke/insult generation.

**Limitations:**

* **Requests:** 500 requests per day, 5 requests per minute.
* **Max Tokens:** Varies per model, refer to [Model List](https://docs.shuttleai.app/getting-started/models) for specifics.
* **No access to premium models:**  `gpt-4`, `claude-3`, `Mistral-Large`, `Gemini-1.5/Ultra` are not included in the free tier.


## Links

* **Website:** [https://shuttleai.app/](https://shuttleai.app/)
* **Model List:** [https://docs.shuttleai.app/getting-started/models](https://docs.shuttleai.app/getting-started/models)
* **Discord:** [https://discord.gg/shuttleai](https://discord.gg/shuttleai)
* **Documentation:** [https://docs.shuttleai.app](https://docs.shuttleai.app)
* **Status:** [https://status.shuttleai.app/](https://status.shuttleai.app/)

## Getting Started

To start using ShuttleAI's free tier:

1. Create an account on their website.
2. Obtain your free API key from the dashboard.
3. Refer to the documentation for API usage examples and integration instructions.

---

# GPT4ALL API - Free Tier Details

This document outlines the features and limitations of the free tier of the GPT4ALL API. This tier allows users to explore the API's capabilities and experiment with different models without any upfront cost.

## Key Features of the Free Tier

* **Access to Multiple Models:** The free tier provides access to a selection of LLMs and image generation models, including GPT-3.5-Turbo and several open-source models.
* **Limited Free Usage:** Users receive a starting balance of $4 per month, which can be used to experiment with various models and features.
* **Request Limits:** The free tier has usage limits to ensure fair access for all users. These limits are outlined below.

## Request Limits (Free Tier)

| Endpoint                      | Limit          |
|-------------------------------|-----------------|
| `/v1/chat/completions`        | 15/minute, 200/day |
| `/v1/image/generations`       | 8/minute, 60/day   |

## Available Models (Free Tier)

While the exact models available on the free tier may vary, the documentation suggests access to the following:

* **OpenAI Models:**
    * GPT-3.5-Turbo
* **Open Source Models:**
    * gemma-7b-it
    * mixtral-8x7b
    * llama-3-70b
    * llama-3-8b
    * llama-3.1-405b
    * llama-3.1-70b
    * wizardlm-2-8x22b
    * mixtral-8x22b
    * sdxl (Image generation)

**Note:** The availability of specific models on the free tier is subject to change.

## Usage Costs

While the free tier provides a starting balance, usage is ultimately metered based on the number of tokens processed. The cost per 1,000 tokens varies depending on the model used.

**Example:**

* Using GPT-3.5-Turbo might cost $0.0005 for input and $0.0014 for output per 1,000 tokens.

## Benefits of the Free Tier

* **Exploration and Experimentation:** Try out different models and functionalities without financial commitment.
* **Learning and Development:** Familiarize yourself with the API and its capabilities before upgrading to a paid plan.
* **Prototyping:** Develop and test proof-of-concept applications before scaling up.

## Limitations of the Free Tier

* **Limited Usage:** The free tier has usage limits that may restrict extensive usage or large-scale projects.
* **Model Availability:** Not all models, especially premium models like GPT-4, are available on the free tier.
* **Potential for Rate Limiting:** Exceeding the request limits may result in rate limiting, temporarily restricting access to the API.

## Upgrading to a Paid Tier

If you require higher usage limits, access to premium models, or more features, consider upgrading to a paid tier. Paid tiers offer a variety of benefits, including increased request limits, access to a wider range of models, and a dedicated balance for usage.

## Conclusion

The free tier of the GPT4ALL API offers a valuable opportunity to explore the platform and experiment with various models. By understanding the limitations and benefits, users can effectively leverage the free tier for learning, development, and prototyping.

**Remember to consult the official documentation for the most up-to-date information on the free tier and its features.**

---

## Fresed API - Free Tier Overview

This document outlines the features and limitations of the Fresed API's free tier, providing a clear understanding of what users can access without any financial commitment.

**Key Features:**

* **Daily Token Limit:** 80,000 tokens per day.
* **Model Access:** Access to various AI models, including GPT-4 and Claude (subject to availability and limitations).
* **Functionality:** Utilize the API for chat completions, image generation, speech generation, and temporary email services.
* **GPT-4 Requests:** Approximately 1000 or 125 free requests per day. **Further clarification is needed on the exact number.**
* **Two Usage Modes:**
    * **Token Mode:** Utilize the full 80,000 token limit with no restrictions on the number of requests.
    * **Request Mode:** Limited to 100 requests per day, with each request consuming 800 tokens.
* **Community Support:** Access to the FresedGPT Discord and Telegram communities for support and updates.

**Limitations:**

* **Daily Token Cap:** The 80,000 token limit resets daily.
* **Potential Queues:** Access to popular models like GPT-4 might involve queueing due to high demand.
* **Limited Model-Specific Information:** Details regarding specific daily/monthly request or token limits for individual models like Claude are not readily available.
* **No Guaranteed Uptime:** The free tier does not come with a guaranteed uptime or support SLA.

**Use Cases (Free Tier):**

* **Experimentation:** Explore the API's capabilities and test different models for various tasks.
* **Small-Scale Projects:** Develop and deploy small-scale applications that utilize AI functionalities within the token limit.
* **Learning and Development:** Utilize the free tier for educational purposes and to learn how to integrate the API into projects.
* **Community Engagement:** Participate in the FresedGPT community to learn from other users and contribute to the platform's development.

**Who Should Consider the Free Tier?**

* **Individuals exploring AI capabilities.**
* **Developers testing and prototyping applications.**
* **Students and educators seeking learning resources.**
* **Users with limited or occasional API usage requirements.**

**Conclusion:**

The Fresed API's free tier offers a valuable opportunity to experience and utilize powerful AI models without any financial investment. While limitations exist, the free tier provides ample resources for exploration, learning, and development. Users with more demanding requirements can consider the donation-based tiers or the unlimited access plan for enhanced capabilities and support.


This document aims to provide a comprehensive overview of the Fresed API's free tier. For the most up-to-date information and further clarification on specific details, it's recommended to visit the official FresedGPT platform and community channels.

---

# QuantumAI Free Plan: A Quick Overview

This document outlines the key features and limitations of the QuantumAI Free Plan, designed to help you explore its capabilities and determine its suitability for your needs.

## Free Plan Features

The QuantumAI Free Plan offers a generous entry point into the world of AI models, providing:

* **Access to a Wide Range of Models:** Experiment with diverse models, including GPT-3.5-turbo, text-embedding-ada-002, and more (refer to the complete models list in the main documentation).
* **Daily Request Limit:**  Perform up to 850 requests per day, allowing for substantial experimentation and testing.
* **Rate Limit:** Execute up to 10 requests per minute, ensuring a smooth and responsive experience.
* **API Access:** Utilize the API to integrate QuantumAI's capabilities into your applications and workflows.

## Limitations

While the Free Plan provides significant access, it's essential to be aware of its limitations:

* **Request Limits:** The daily and per-minute request limits may restrict usage for high-volume applications.
* **Potential Queueing:**  During peak hours, you might experience queueing delays due to high demand.
* **No Access to QuantumAI Pro Features:** The Free Plan doesn't include the benefits of QuantumAI Pro, such as early access to new models or custom plans.

## Use Cases for the Free Plan

The Free Plan is well-suited for various use cases, including:

* **Exploration and Learning:**  Familiarize yourself with different AI models and their functionalities.
* **Prototyping and Testing:** Develop and test proof-of-concept applications before committing to a paid plan.
* **Small-Scale Projects:** Implement AI capabilities in projects with limited usage requirements.
* **Educational Purposes:**  Utilize the Free Plan for learning and experimenting with AI technologies in academic settings.

## Conclusion

The QuantumAI Free Plan provides a valuable opportunity to explore the potential of AI models without any financial commitment. By understanding its features and limitations, you can effectively leverage this plan for learning, experimentation, and small-scale projects.  If your needs exceed the Free Plan's limitations, consider upgrading to the Paid or QuantumAI Pro plans for enhanced capabilities and higher usage limits.

---

## AnyAI API Free Tier: Access Powerful AI for Free

This document outlines the features and limitations of the AnyAI API's free tier, allowing developers to explore and experiment with various AI capabilities without any cost.

**Key Features:**

* **Access to Open-Source LLMs:** Utilize a variety of powerful open-source LLMs, including those from the Llama 2 family, Mistral, and more, for various tasks like chatbots, content generation, and question answering.
* **Limited Access to Closed-Source LLMs:** Experiment with industry-leading closed-source models like GPT-4 and Claude models with a limited number of daily requests.
* **Image Generation with DALL-E 3:** Generate unique images based on text prompts using the powerful DALL-E 3 model, albeit with daily request limitations.
* **GlobalAsk for Knowledge Retrieval:** Access the GlobalAsk endpoint to retrieve information and answers from diverse online sources with daily usage limits.
* **Vision Endpoint for Image Analysis:** Utilize the Vision endpoint to describe and analyze image content, within the free tier's usage constraints.

**Request Limits:**

The free tier provides generous daily request limits for various functionalities:

* **Open-Source LLMs:** 2000 requests per day, 10 requests per minute.
* **Closed-Source LLMs:** 100 requests per day, 25 requests per hour.
* **DALL-E 3:** 750 requests per day, 120 requests per minute.
* **GlobalAsk & Vision Endpoint:** Limited to a combined total of 100 requests per day and 25 requests per hour.

**Note:** The maximum characters per message is limited to 1000 in the free tier.

**Use Cases:**

Despite the limitations, the free tier enables various use cases:

* **Prototyping and Experimentation:** Explore different models and functionalities to determine the best fit for your project before committing to a paid plan.
* **Low-Volume Applications:** Build applications with relatively low usage requirements, such as personal projects or small-scale chatbots.
* **Educational Purposes:** Learn and experiment with AI concepts and techniques without incurring any financial costs.

**Ideal for:**

* **Hobbyists & Individual Developers:** Experiment with AI and build personal projects without financial barriers.
* **Students & Researchers:** Learn and explore AI concepts and models for educational purposes.
* **Startups & Small Businesses:** Test and validate AI capabilities for potential future integration.

**Limitations:**

* **Request Limits:** Daily and per-minute request limits may restrict usage for high-volume applications.
* **Limited Access to Closed-Source Models:** The limited access to powerful models like GPT-4 may require careful planning and utilization.
* **Character Limit:** The 1000 character limit per message may restrict the complexity of interactions and outputs.

**Conclusion:**

The AnyAI API's free tier offers a valuable opportunity to explore and experiment with the capabilities of various AI models and functionalities. While limitations exist, it provides a powerful platform for learning, prototyping, and building low-volume applications without any financial commitment. It's an ideal starting point for anyone interested in harnessing the power of AI.

---

## ShadowJourney API: Exploring the Free Tier

This document focuses specifically on the free offerings of the ShadowJourney API, highlighting the available models and their capabilities.

### Introduction

The ShadowJourney API operates on a freemium model, providing access to a wide range of powerful AI models and functionalities without any upfront cost. This free tier allows users to experiment with various LLMs, image generation, and even text-to-speech capabilities, within a daily usage limit.

### Free Credits and Limitations

ShadowJourney provides **2500 free credits per day.** These credits can be used to access a selection of free models, enabling users to explore their potential and build applications without incurring immediate expenses. However, it's important to note that the specific conversion rate between credits and tokens remains unclear, and further clarification on usage limitations beyond the daily credits is needed.

### Free Model Availability

The ShadowJourney API offers an impressive array of free models, including:

**Large Language Models (LLMs):**

* **GPT-3.5-turbo (various versions):** A powerful and versatile model suitable for conversation, text generation, and various other tasks.
* **GPT-4 (various versions):** A highly advanced model with enhanced reasoning and creative writing capabilities.
* **Claude-3-haiku, Claude-3-sonnet:** Specialized models for generating haiku and sonnet poems.
* **Claude-3.5-sonnet (freemium):** A freemium version of Claude 3.5, capable of generating sonnets.
* **Gemini (various versions):** Google's latest family of LLMs, offering strong performance across various tasks.
* **Meta-Llama/Llama-2-70b-chat-hf:** Open-source chatbot model from Meta.
* **Mixtral-8x7B-Instruct-v0.1:** Open-source model with strong performance in following instructions.
* **Many other open-source and proprietary models:** A diverse range of models with specialized capabilities.

**Image Generation:**

* **DALL-E 3:** Advanced image generation model capable of creating realistic and creative images.
* **Stable Diffusion v2-1:** Powerful open-source image generation model.

**Use Cases within the Free Tier:**

The free tier of the ShadowJourney API enables a wide range of use cases, including:

* **Experimentation and Prototyping:** Explore different models and functionalities to determine the best fit for your project.
* **Low-Volume Applications:** Build and deploy applications with limited usage requirements, staying within the daily credit limit.
* **Educational Purposes:** Learn about and experiment with various AI models and techniques.
* **Personal Projects:** Develop personal projects and explore creative applications of AI.

### Examples of Free Tier Usage:**

* **Build a simple chatbot:** Utilize GPT-3.5-turbo to create a chatbot for answering basic questions or providing information.
* **Generate creative content:** Experiment with Claude-3-haiku or Claude-3-sonnet to explore different poetic forms.
* **Create images from text prompts:** Use DALL-E 3 or Stable Diffusion to generate unique visuals for your projects.
* **Test different LLMs for specific tasks:** Compare the performance of various free models for tasks like summarization or translation.

### Conclusion

The free tier of the ShadowJourney API provides a valuable opportunity to explore the potential of various AI models and functionalities without any financial commitment. While limitations exist in terms of daily credits and access to premium models, the diverse range of free offerings makes it an attractive platform for experimentation, learning, and developing low-volume applications. Remember to review the API documentation and usage guidelines to maximize your experience within the free tier.

---

## Oxygen API: Free Tier Overview

**Introduction:**

The Oxygen API offers a generous free tier, allowing developers to explore and experiment with over 150 advanced Large Language Models (LLMs) without any cost. This document provides a comprehensive overview of the free tier's features, limitations, and potential use cases.

**Free Tier Features:**

* **Access to 150+ LLMs:**  Explore a vast library of LLMs, including popular models like GPT-3.5-Turbo and Claude 3.5.
* **Generous Request Limits:**  Utilize a substantial amount of free requests per month for various models.
* **All API Endpoints:** Access all API endpoints, including chat completions, image generation, audio speech, and embeddings.
* **Community Support:** Benefit from a vibrant community of developers and users for assistance and collaboration.

**Request/Token Limits (Free Tier):**

| Model           | Max Tokens | Max Context Tokens | Free Requests |
|-----------------|------------|-------------------|---------------|
| GPT-4           | 4096       | 128000            | 0             |
| GPT-3.5-Turbo   | 4096       | 128000            | 300           |
| Claude 3.5      | 4096       | 200000            | 0             |
| DALL-E 2       | N/A        | N/A               | 50            |
| Stable Diffusion| N/A        | N/A               | 300           |
| ElevenLabs Models| N/A        | N/A               | 50            |

**Note:** These limits are subject to change. Refer to the official [Oxygen API documentation](https://docs.oxyapi.uk/) for the most up-to-date information.

**Use Cases (Free Tier):**

The free tier is ideal for:

* **Experimentation and Learning:** Explore different LLMs and their capabilities.
* **Prototyping and Development:** Build and test proof-of-concept applications.
* **Small-Scale Projects:** Deploy applications with limited usage requirements.
* **Educational Purposes:** Learn about AI and LLM integration in a practical setting.

**Examples:**

* **Build a simple chatbot:**  Develop a basic chatbot using GPT-3.5-Turbo with limited interactions.
* **Generate short-form content:** Create short pieces of text, such as social media captions or product descriptions.
* **Experiment with image generation:** Explore the creative potential of DALL-E 2 and Stable Diffusion.
* **Test audio speech synthesis:** Generate short audio clips using ElevenLabs models.

**Limitations:**

* **Request Limits:**  The free tier has limitations on the number of requests per month for each model.
* **No Access to GPT-4 and Claude 3.5:** These models are not available in the free tier.

**Conclusion:**

The Oxygen API's free tier provides a valuable opportunity for developers to explore the world of LLMs and build AI-powered applications without any financial commitment. With its generous request limits and access to a wide range of models, the free tier is an excellent starting point for anyone interested in leveraging the power of AI. Remember to review the usage limitations and consider upgrading to a paid tier for more demanding projects.

---

# Free API Access Documentation

This document details the specifications for accessing and utilizing the free version of our API, specifically highlighting the available models and their respective endpoints.

## Free Model: CosmosRP (CosmosRP-V2)

The CosmosRP model is a powerful and versatile roleplay model available for free and unlimited use.  No API key is required to access this model.

**Key Features:**

* **Excellent Quality:** Designed to provide high-quality responses tailored for roleplaying scenarios.
* **Context Size:** 8k Tokens. This allows for extended conversations and interactions within a given context.
* **Unlimited Usage:**  Enjoy unrestricted access without limitations on the number of requests.
* **Uncensored:**  Experience a free and open environment for creative expression and exploration.

**Base URL & Endpoints:**

* **Base URL:** https://api.pawan.krd/cosmosrp/v1
* **Full URL (Chat Completions):** https://api.pawan.krd/cosmosrp/v1/chat/completions

**Instructed Version (CosmosRP-IT):**

For more natural and nuanced responses, we offer an instructed version of the CosmosRP model, also available for free and unlimited use.

* **Instructed Version:** https://api.pawan.krd/cosmosrp-it/v1
* **Instructed URL (Chat Completions):** https://api.pawan.krd/cosmosrp-it/v1/chat/completions


## Important Considerations

While the free version offers unrestricted access, please be mindful of the global rate limit, which applies to all users:

* **Global Rate Limit:** 100 requests per 10 seconds

Exceeding this limit will result in a temporary block of 10 seconds.  After the block, you can resume using the API.

## Conclusion

The CosmosRP model provides a fantastic opportunity to explore the capabilities of our API and engage in creative roleplaying experiences without any cost or usage restrictions.  Leverage the power of this free model to bring your ideas to life and enjoy unlimited access to a dynamic and engaging roleplaying environment.

We encourage you to explore the capabilities of the free CosmosRP model and its instructed counterpart.  If you require enhanced features or higher rate limits, consider exploring our supporter plans for access to premium models and functionalities.

---

# Zukijourney API - Free Tier Information

This document outlines the features and limitations specifically for the free tier of the Zukijourney API, accessible to all members of the ZukiJourney Discord server.

## Key Features (Free Tier)

* **Access to a wide range of AI models:** Experiment with various models, including those from OpenAI, Anthropic, and custom-developed models like Caramelldansen-1.
* **OpenAI compatibility:** Utilize the OpenAI client with a simple base URL change.
* **Daily token allowance:**  Receive 22,500 tokens every 24 hours, allowing for approximately 126 messages per day.
* **Community support:** Benefit from the active Zukijourney community and access to community-contributed wrappers for different programming languages.

## Limitations (Free Tier)

* **Rate limits:** Restricted to 4 requests per minute per key per IP for `/unf/` endpoints and 12 requests per minute per key per IP for `/v1/` endpoints.
* **IP-locked key:** Your API key is tied to a single IP address. Use the `/resetip` command on the ZukiJourney Discord bot to change it.
* **Lower priority support:**  Receive lower priority support compared to paid tiers.


## Token System (Free Tier)

* **Daily Token Grant:** Use the `/daily` command to claim your 22,500 token grant every 24 hours if your balance is below 6969 tokens.
* **Token Costs:** Token costs vary based on the model used (see the main documentation for detailed cost multipliers).


## How to Get Started (Free Tier)

1. Join the ZukiJourney Discord server: [https://discord.gg/zukijourney](https://discord.gg/zukijourney)
2. Use the `/key` command with the `zuki.api` bot to generate your free API key.
3. Start using the API with the OpenAI client, modifying the base URL as follows:

```python
OpenAI(base_url="https://zukijourney.xyzbot.net/v1", api_key='zu-...')
```

## Upgrading to Paid Tiers

Consider upgrading to a paid tier for increased benefits, such as higher daily token allowances, IP-free keys, and priority support.  See the main documentation for details on donation tiers and their benefits.

## Conclusion

The free tier of the Zukijourney API provides a great opportunity to explore the capabilities of various AI models. By understanding the limitations and token system, you can effectively utilize this powerful tool for your projects and experiments. Remember to consult the main documentation for comprehensive information and always stay updated through the ZukiJourney Discord server.

---

# Webraft Free API: Unleash the Power of AI for Free

Webraft offers a powerful and versatile Free API that gives you access to a vast array of cutting-edge AI models for various tasks, including chat completion, image generation, image analysis, and more. With 500 free credits replenished every 24 hours, you have ample opportunity to experiment, learn, and build amazing applications without any financial commitment.

## What You Get

- **500 Free Credits:** 
    - Each request consumes 1 credit.
    - Credits are replenished daily, allowing for consistent usage.
- **Extensive Model Library:** Choose from over 200 diverse models for:
    - Chat Completion: Interact with advanced language models for conversation, text generation, question answering, and more.
    - Image Generation: Create stunning images from text prompts using Stable Diffusion, DALL-E, Midjourney, and other state-of-the-art models.
    - Image Analysis: Analyze images for object detection, captioning, image-to-text conversion, and classification.
- **Easy Integration:**  
    - Follow the simple instructions in the OpenAI documentation and set the API endpoint to `https://api.webraft.in/freeapi`.
    - Utilize familiar libraries like `curl` and `requests` in Python.
    - Refer to our detailed code examples for guidance.

##  Key Features

- **Free and accessible:** Explore the potential of AI without any financial barriers.
- **Diverse models:** Experiment with a wide range of models to find the perfect fit for your project.
- **Regular credit replenishment:** Enjoy continuous access to the API with daily credit replenishment.
- **User-friendly documentation:**  Our comprehensive documentation provides clear instructions and examples.

##  Usage Limits

- **Rate Limit:** To ensure fair usage, the following rate limits apply:
    - 5 requests per second.
    - 60 requests per minute.

##  Getting Started

1. **Obtain Your Free API Key:**
   - Go to the `🔧・ᴄᴏᴍᴍᴀɴᴅs` section.
   - Run the `!key` command to generate your unique API key.
2. **Set the Endpoint URL:**
   -  Follow the OpenAI documentation ([https://platform.openai.com/docs/api-reference/introduction](https://platform.openai.com/docs/api-reference/introduction)) for setting up your environment.
   - Set the `api_base` to `https://api.webraft.in/freeapi` 

## Explore the Possibilities

Webraft's Free API empowers you to build a wide range of AI-powered applications, including:

- **Chatbots:** Create engaging and interactive chatbots for customer support, entertainment, and more.
- **Text Generators:** Generate creative stories, articles, marketing copy, and other textual content.
- **Image Creation Tools:** Design unique visuals, graphics, and artwork for various purposes.
- **AI-Powered Assistants:** Develop intelligent assistants that can answer questions, provide summaries, and automate tasks.

---

## Naga API Free Tier: Exploring AI Capabilities Without Cost

The Naga API offers a generous free tier, allowing users to explore its diverse AI capabilities without any financial commitment. This free access provides an excellent opportunity to experiment with various models and discover the potential of AI for different applications.

### Free Model Access

The free tier grants access to a wide range of powerful models, including:

**Text Models:**

* **GPT-3.5-TURBO-1106:** Ideal for conversational AI, text generation, and code generation.
* **Claude-3-HAIKU-20240307:**  Suitable for concise text generation and summarization.
* **LLAMA-2-70B-CHAT, LLAMA-2-13B-CHAT, LLAMA-2-7B-CHAT:** Powerful open-source models for various text-based tasks.
* **MISTRAL-7B-INSTRUCT, MIXTRAL-8X7B-INSTRUCT:** Efficient models for instruction-based tasks.
* **GEMINI-PRO:** Google's versatile text model for various applications.

**Image Models:**

* **PLAYGROUND-V2.5:**  Explore image generation capabilities with this model.
* **SDXL, KANDINSKY-3.1, KANDINSKY-3, KANDINSKY-2.2, KANDINSKY-2:** Diverse models for generating creative visuals from text prompts.

**Embedding Models:**

* **TEXT-EMBEDDING-ADA-002, TEXT-EMBEDDING-3-SMALL, TEXT-EMBEDDING-3-LARGE, BGE-LARGE-EN-V1.5:** Create vector representations of text for semantic search, clustering, and other tasks.

**Moderation Models:**

* **TEXT-MODERATION-LATEST, TEXT-MODERATION-STABLE:**  Assess the safety and appropriateness of text content.

**Audio Models:**

* **WHISPER-LARGE, M2M100-1.2B:** Experiment with speech-to-text and translation capabilities.

### Request Limits

The free tier comes with specific request limits for each model, typically allowing for a few requests per minute and a limited number of requests per day. For instance:

* **GPT-3.5-TURBO-1106:** 3 requests per minute, 200 requests per day.
* **Claude-3-HAIKU-20240307:** 1 request per minute, 50 requests per day.
* **PLAYGROUND-V2.5:** 3 requests per minute, 100 requests per day.

These limits ensure fair usage and allow a wide range of users to explore the API's capabilities.

### Use Cases for the Free Tier

The free tier is perfect for:

* **Experimentation and Learning:** Explore different models and understand their strengths and limitations.
* **Prototyping and Development:** Build and test proof-of-concept applications before scaling up.
* **Small-scale Projects:**  Implement AI features in personal projects or small-scale applications.
* **Educational Purposes:** Learn about AI and its practical applications through hands-on experience.

### Getting Started

To start using the Naga API's free tier, simply sign up for an account and obtain your API key. You can then integrate the API into your applications using the provided documentation and code examples.

The Naga API free tier provides a valuable resource for anyone interested in exploring the power of AI. Its diverse selection of models and generous request limits allow for experimentation, learning, and development without any financial barriers.

---

## VisionCraft API: Free Tier Options

The VisionCraft API offers a generous Free Tier, allowing you to explore and experiment with our powerful AI models without any cost. Here's a quick overview of what's included:

**Access to All Models:**

* **LLM (Large Language Models):** Experiment with a wide range of text generation models, including:
    * `airoboros-70b`
    * `dolphin-2.6-mixtral-8x7b`
    * `openchat-3.6-8b`
    * `Mixtral-8x22B-Instruct-v0.1`
    * ...and many more! (See full list in documentation)
* **Stable Diffusion:** Generate stunning images using popular Stable Diffusion models like:
    * `sdxl-base`
    * `sdxl-refiner`
    * `deliberate_v2`
    * ...and more!
* **Text-to-GIF:** Create engaging GIFs from text prompts.

**Usage Limits:**

While the Free Tier provides access to all models, it does have usage limitations to ensure fair access for all users. These limits apply to the number of requests you can make per second/day.  

**Key Highlights:**

* **Explore and Experiment:**  Test out various models and functionalities to find the perfect fit for your needs.
* **No Cost:** Start using the API without any financial commitment.
* **Easy Access:** Obtain your API key quickly through our Telegram bot.

**Ready to Get Started?**

1. Subscribe to our Telegram channel: [https://t.me/visioncraft_channel](https://t.me/visioncraft_channel)
2. Get your API key from our Telegram bot: [https://t.me/VisionCraft_bot](https://t.me/VisionCraft_bot)
3. Check out our full documentation for details and examples: [Link to Your GitHub Documentation]

**Upgrade for More Power:**

If you need higher usage limits and more features, consider upgrading to one of our premium subscription tiers.

We encourage you to try out the VisionCraft API's Free Tier and unlock the potential of AI for your projects!

