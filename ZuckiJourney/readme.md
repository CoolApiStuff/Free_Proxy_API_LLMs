# Zukijourney API Documentation - V2.5

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
- [Code Examples](#code-examples)
- [Rate Limiting](#rate-limiting)
- [Error Handling](#error-handling)


<a name="overview"></a>

## Overview

The Zukijourney API is a powerful and versatile multi-AI API offering access to a wide range of models, including those from OpenAI, Anthropic, and others. Built with an open-source philosophy, it mirrors the OpenAI API for ease of use and boasts a vibrant community contributing wrappers for various programming languages. The API operates on a donation-based tier system, providing different access levels and benefits based on contribution levels.


<a name="free-vs-premium-features"></a>

## Free vs. Premium Features

| Feature               | Free Version                                     | Premium Version                                   |
|------------------------|---------------------------------------------------|--------------------------------------------------|
| API Access             | Yes                                              | Yes                                             |
| Daily Tokens          | 22,500                                          | Up to 4,000,000                                 |
| Messages/Day          | ~126                                            | Up to ~10,000                                   |
| Key Type              | IP-Locked                                        | IP-Locked or IP-Free (depending on the tier)      |
| Support Priority       | Low                                             | Medium to Highest (depending on the tier)         |
| Model Access          | All models                                        | All models                                       |
| Rate Limits           | Same as premium                                  | Same as free                                     |
| Daily Token Grant      | Yes                                              | Yes                                             |
| IP Reset              | Yes                                              | Yes                                             |
| Gamble Credits         | Yes                                              | Yes                                             |
| Community Support      | Yes                                              | Yes                                             |
| Open Source Code       | Yes                                              | Yes                                             |


<a name="pricing"></a>

## Pricing

| Tier             | Price                | Mode        | Benefits                                               |
|------------------|----------------------|-------------|---------------------------------------------------------|
| `@Member`        | Free                 | N/A         | Access to the API with limited daily tokens.            |
| `@Booster`       | Free                 | N/A         | Increased daily tokens for boosting the Discord server. |
| `@Donator`        | One-time donation > $5 | One-Time    | Increased daily tokens.                               |
| `@Early Supporter` | N/A                  | N/A         | Increased daily tokens (no longer available).          |
| `@Subscriber`    | ~$10/month           | Subscription | Significantly increased daily tokens and IP-Free key.  |
| `@Enterprise`   | $100/month           | Subscription | Highest daily tokens and IP-Free key.                  |


<a name="api-capacities-and-limits"></a>

## API Capacities and Limits

| Category               | Limit                                            |
|------------------------|-------------------------------------------------|
| Daily Tokens (Free)    | 22,500                                          |
| Daily Tokens (Premium)  | Up to 4,000,000                                 |
| Requests/Minute (/unf/) | 4                                               |
| Requests/Minute (/v1/)  | 12                                              |
| IP Addresses per Key   | 1 (unless IP-Free key)                           |
| Accounts per User      | 1                                               |


<a name="free-version-features"></a>

## Free Version Features

The free version of the Zukijourney API offers a generous daily token allowance of 22,500, allowing for substantial experimentation and development. Users can access all available AI models and benefit from the open-source nature of the API. While the free tier comes with an IP-locked key and lower support priority, it provides a valuable entry point for exploring the API's capabilities.


<a name="premium-version-features"></a>

## Premium Version Features

Premium tiers of the Zukijourney API unlock significantly higher daily token allowances, ranging from 200,000 to 4,000,000, depending on the chosen tier. These tiers also offer higher support priority and, at the highest levels, IP-free keys for enhanced flexibility.


<a name="authentication-methods"></a>

## Authentication Methods

The Zukijourney API uses API keys for authentication. These keys are generated through the `/key` command on the ZukiJourney Discord bot.


<a name="endpoints"></a>

## Endpoints

The Zukijourney API mirrors the OpenAI API structure. Therefore, you can refer to the OpenAI API documentation for detailed information on available endpoints and their parameters. However, remember to use the Zukijourney API base URL: `https://zukijourney.xyzbot.net/v1`.


<a name="code-examples"></a>

## Code Examples

Refer to the `zukijourney-tests` repository for code examples in various programming languages: [https://github.com/zukijourney/api-tests](https://github.com/zukijourney/api-tests)


<a name="rate-limiting"></a>

## Rate Limiting

The Zukijourney API enforces rate limits to ensure fair usage and prevent abuse. The limits are as follows:

- `/unf/` endpoints: 4 requests per minute per key per IP
- `/v1/` endpoints: 12 requests per minute per key per IP


<a name="error-handling"></a>

## Error Handling

The Zukijourney API returns standard HTTP error codes to indicate issues with requests. Refer to the OpenAI API documentation for a comprehensive list of potential error codes and their meanings.

<a name="models-and-limits"></a>

## Models and Limits

The Zukijourney API offers a wide array of models, each with its own cost multiplier and capabilities.  

### Chat Models & Cost Multipliers

| Multiplier | Models/Categories                                  |
|------------|---------------------------------------------------|
| 1.5x       | gpt-4-1106-preview and later, claude-3-opus and later, gpt-4-vision-preview |
| 1.25x      | gpt-4 and later, claude-3-sonnet                   |
| 1x         | gpt-4o-mini + all non-4 gpt models, claude-3-haiku and before, All Gemini/Mistral-Series models |
| 0.5x       | all other models not developed by zukijourney        |
| 0.25x      | caramelldansen-1 & caramelldansen-1-plus            |

### Image Models & Cost per Request

| Cost per Request | Models                                             |
|-----------------|----------------------------------------------------|
| 42,000           | Midjourney                                          |
| 2,500            | DALLE-2 and later + Stable-Diffusion-3-large + Stable-Image-Ultra/Core and later |
| 250             | Stable-Diffusion-3-Medium & the Flux model series.    |
| 100             | All models provided by Prodia.                      |

### Other Endpoints & Costs

| Endpoint Category         | Cost per Request |
|--------------------------|-----------------|
| Audio, Embeddings, Image-Upscaling | 100 tokens       |
| Moderations, Text-Translations   | 10 tokens        |

**Note:** Model availability and pricing are subject to change. Refer to the official API documentation and the ZukiJourney Discord server for the most up-to-date information.


<a name="token-system"></a>

## Token System

The Zukijourney API utilizes a token-based system for usage tracking and billing. 

- **Daily Token Grant:** Users can request a token grant every 24 hours if their balance is below 6969 tokens using the `/daily` command on the Discord server.
- **Token Equivalence:** 1 OpenAI token is equivalent to 1 Zukijourney token.
- **Cost Multipliers:** Different models have different cost multipliers, as outlined in the tables above.
- **Daily Token Allowances:** Daily token allowances vary based on the user's donation tier.


<a name="community-and-support"></a>

## Community and Support

The Zukijourney API boasts a vibrant and active community, providing support and resources for developers.

- **Discord Server:** The primary hub for community interaction, support requests, and announcements. Join here: [https://discord.gg/zukijourney](https://discord.gg/zukijourney)
- **GitHub Repository:** The API's codebase is publicly available on GitHub: [https://github.com/zukijourney/api-docs](https://github.com/zukijourney/api-docs)
- **Community-Contributed Wrappers:** Various community members have developed wrappers for different programming languages, simplifying integration with the API.


<a name="additional-information"></a>

## Additional Information

- **API Quirks and Considerations:** Be aware of specific quirks and considerations when using the API, such as request reuse, simple request handling, IP-locked keys, and key suspension policies. Details can be found in the `readme.md` file.
- **Administrative Rights:** The API administrator reserves the right to modify access and features as needed.
- **OpenAI Compatibility:** The API is designed to be compatible with the OpenAI API, allowing developers to use the OpenAI client with a simple base URL change.

