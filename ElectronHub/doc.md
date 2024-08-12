## Electron Hub API Documentation

**Last Updated:** 2024-08-09 18:23:53

This document details the API endpoints and available models for Electron Hub, including pricing and usage limitations.  

**Subscription Plans**

Electron Hub offers various subscription plans to suit different needs, each with its own benefits:

| Plan        | Price    | Daily Credits | Messages (GPT-4o) | Rate Limit (requests/min) | Features                                                  | Support                             |
|--------------|----------|---------------|-------------------|---------------------------|----------------------------------------------------------|--------------------------------------|
| **Free**     | Free     | 500           | 100              | 5                        | Basic bug and error support                              | Basic                                 |
| **Starter**   | \$5      | 4,000          | 800              | 20                       | Access to advanced features                               | Priority bug and error support         |
| **Pro**       | \$29     | 10,000         | 2,000            | 40                       | Early access to new models and features                 | Higher priority for bugs, API, coding |
| **Business** | \$49     | 30,000         | 6,000            | 60                       | Early access to cutting-edge models and features, hands-on coding, API integration assistance | Highest priority for all issues        |

**Note:** Create your API key using the `/key` command at ⁠︱💬・text-ai.

---

### API Endpoints

**Base URLs:**

* `https://api.electronhub.top/`
* `https://api.electronhub.top/v1`

**Endpoints:**

| Endpoint                    | Methods                      | URL                                                 |
|-----------------------------|------------------------------|----------------------------------------------------|
| Models                      | GET \| POST \| PUT \| PATCH \| HEAD | `https://api.electronhub.top/models`                |
|                             |                               | `https://api.electronhub.top/v1/models`            |
|                             |                               | `https://api.electronhub.top/models/{model}`        |
|                             |                               | `https://api.electronhub.top/v1/models/{model}`      |
| Chat Completions            | POST \| OPTIONS               | `https://api.electronhub.top/chat/completions`      |
|                             |                               | `https://api.electronhub.top/v1/chat/completions`    |
| Image Generations           | POST \| OPTIONS               | `https://api.electronhub.top/images/generations`     |
|                             |                               | `https://api.electronhub.top/v1/images/generations`   |
| Image Edits                 | POST \| OPTIONS               | `https://api.electronhub.top/images/edits`           |
|                             |                               | `https://api.electronhub.top/v1/images/edits`         |
| Text-to-Speech              | POST \| OPTIONS               | `https://api.electronhub.top/audio/speech`          |
|                             |                               | `https://api.electronhub.top/v1/audio/speech`        |
| Music Generations (Custom) | POST \| OPTIONS               | `https://api.electronhub.top/audio/music`           |
|                             |                               | `https://api.electronhub.top/v1/audio/music`         |
| Video Generations (Custom) | POST \| OPTIONS               | `https://api.electronhub.top/videos/generations`     |
|                             |                               | `https://api.electronhub.top/v1/videos/generations`   |


---

### Available Models

**Audio Models:**

| Model                      | Tokens | Endpoint          | Cost (credits) |
|---------------------------|--------|--------------------|----------------|
| eleven-multilingual-v2     | 500    | `/v1/audio/speech` | 5              |
| suno-v3.5                 | 500    | `/v1/audio/music`  | 20             |

**Video Models:**

| Model          | Tokens | Endpoint              | Cost (credits) |
|-----------------|--------|----------------------|----------------|
| t2v-turbo       | 80     | `/v1/videos/generations` | 30             |
| svd-turbo       | 80     | `/v1/videos/generations` | 20             |
| dream-machine   | 500    | `/v1/videos/generations` | 80             |


**Image Models:**

| Model                         | Tokens   | Endpoint(s)                           | Cost (credits) | NSFW |
|------------------------------|----------|----------------------------------------|----------------|------|
| stable-diffusion-v1-4         | 100      | `/v1/images/generations`              | 2              | No   |
| stable-diffusion-v2           | 100      | `/v1/images/generations`              | 2              | No   |
| stable-diffusion-v2-1         | 100      | `/v1/images/generations`              | 2              | No   |
| sdxl                          | 80       | `/v1/images/generations`              | 1              | No   |
| sdxl-turbo                    | 100      | `/v1/images/generations`              | 1              | No   |
| sdxl-lightning                | 80       | `/v1/images/generations`              | 1              | No   |
| stable-diffusion-3           | 80       | `/v1/images/generations`              | 15             | No   |
| stable-cascade                | 100      | `/v1/images/generations`              | 5              | No   |
| playground-v2.5               | 80       | `/v1/images/generations`, `/v1/images/edits` | 30             | No   |
| animaginexl-3.1               | 80       | `/v1/images/generations`, `/v1/images/edits` | 20             | No   |
| realvisxl-4.0                 | 80       | `/v1/images/generations`, `/v1/images/edits` | 20             | No   |
| dreamshaper-5                 | 100      | `/v1/images/generations`              | 2              | No   |
| kandinsky-3                   | 100      | `/v1/images/generations`              | 5              | No   |
| dall-e-3                     | 200      | `/v1/images/generations`              | 20             | No   |
| midjourney-v6.1               | 300      | `/v1/images/generations`              | 30             | No   |
| midjourney-v6                 | 300      | `/v1/images/generations`              | 30             | No   |
| midjourney-v5.2               | 300      | `/v1/images/generations`              | 20             | No   |
| midjourney-v5.1               | 300      | `/v1/images/generations`              | 20             | No   |
| midjourney-v5                 | 300      | `/v1/images/generations`              | 20             | No   |
| midjourney-v4                 | 300      | `/v1/images/generations`              | 20             | No   |
| niji-v6                       | 300      | `/v1/images/generations`              | 30             | No   |
| niji-v5                       | 300      | `/v1/images/generations`              | 20             | No   |
| niji-v4                       | 300      | `/v1/images/generations`              | 20             | No   |
| openjourney-v2                | 100      | `/v1/images/generations`              | 5              | No   |
| openjourney-v3                | 100      | `/v1/images/generations`              | 5              | No   |
| openjourney-v4                | 100      | `/v1/images/generations`              | 5              | No   |
| openjourney-v5                | 100      | `/v1/images/generations`              | 5              | No   |
| flux-schnell                  | 32000    | `/v1/images/generations`              | 15             | No   |
| flux-dev                      | 32000    | `/v1/images/generations`              | 150            | No   |
| 3guofeng3-v3.4                | 300      | `/nsfw/images/generations`             | 5              | Yes  |
| absolutereality-v1.6          | 300      | `/nsfw/images/generations`             | 5              | Yes  |
| absolutereality-v1.8.1          | 300      | `/nsfw/images/generations`             | 5              | Yes  |
| am-i-real-v4.1                | 300      | `/nsfw/images/generations`             | 5              | Yes  |
| ... (see original document for full list of NSFW image models) | ... | ... | ... | ... |

**Chat Models:**

| Model                           | Tokens     | Endpoint               | Cost (credits) |
|---------------------------------|-------------|-------------------------|----------------|
| gpt-3.5-turbo                    | 4000       | `/v1/chat/completions`  | 1              |
| gpt-3.5-turbo-vision             | 4000       | `/v1/chat/completions`  | 2              |
| gpt-3.5-turbo-16k                | 16000      | `/v1/chat/completions`  | 1              |
| gpt-3.5-turbo-16k-0613           | 16000      | `/v1/chat/completions`  | 1              |
| ... (see original document for full list of chat models) | ... | ... | ... |

**Note:** This is a summarized version of the available models. 
