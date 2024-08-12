# Electron Hub Models

This document lists all available models on Electron Hub, categorized by their type: Chat, Image, Video, and Audio. Each table provides details about the model name, tokens, endpoint, cost in credits, and whether it is considered NSFW (Not Safe for Work).

## Chat Models

| Model                           | Tokens     | Endpoint               | Cost (credits) |
|---------------------------------|-------------|-------------------------|----------------|
| gpt-3.5-turbo                    | 4000       | `/v1/chat/completions`  | 1              |
| gpt-3.5-turbo-vision             | 4000       | `/v1/chat/completions`  | 2              |
| gpt-3.5-turbo-16k                | 16000      | `/v1/chat/completions`  | 1              |
| gpt-3.5-turbo-16k-0613           | 16000      | `/v1/chat/completions`  | 1              |
| gpt-3.5-turbo-1106               | 4000       | `/v1/chat/completions`  | 1              |
| gpt-3.5-turbo-0125               | 4000       | `/v1/chat/completions`  | 1              |
| gpt-3.5-turbo-0613               | 4000       | `/v1/chat/completions`  | 1              |
| gpt-4                           | 2000       | `/v1/chat/completions`  | 1              |
| gpt-4-32k                       | 32000      | `/v1/chat/completions`  | 10             |
| gpt-4-turbo                      | 128000     | `/v1/chat/completions`  | 10             |
| gpt-4o                          | 128000     | `/v1/chat/completions`  | 5              |
| gpt-4o-mini                     | 128000     | `/v1/chat/completions`  | 5              |
| gpt-4o-mini-vision              | 4000       | `/v1/chat/completions`  | 5              |
| gpt-4o-mini-128k-vision         | 128000     | `/v1/chat/completions`  | 15             |
| claude-instant-vision           | 9000       | `/v1/chat/completions`  | 5              |
| claude-instant-100k-vision      | 100000     | `/v1/chat/completions`  | 15             |
| claude-3-sonnet-vision          | 4000       | `/v1/chat/completions`  | 40             |
| claude-3-haiku-vision           | 4000       | `/v1/chat/completions`  | 5              |
| claude-3.5-sonnet-vision         | 4000       | `/v1/chat/completions`  | 40             |
| claude-3-opus-200k               | 200000     | `/v1/chat/completions`  | 10             |
| claude-3-sonnet-200k             | 200000     | `/v1/chat/completions`  | 5              |
| claude-3-haiku-200k              | 200000     | `/v1/chat/completions`  | 5              |
| claude-3.5-sonnet-200k            | 200000     | `/v1/chat/completions`  | 10             |
| gemini-1.0-pro-vision           | 32000      | `/v1/chat/completions`  | 5              |
| gemini-1.5-pro                   | 32000      | `/v1/chat/completions`  | 1              |
| gemini-1.5-pro-vision           | 32000      | `/v1/chat/completions`  | 15             |
| gemini-1.5-flash                | 128000     | `/v1/chat/completions`  | 10             |
| gemini-1.5-flash-vision          | 4000       | `/v1/chat/completions`  | 5              |
| gemini-1.5-flash-128k-vision     | 128000     | `/v1/chat/completions`  | 20             |
| gemini-1.5-flash-online          | 4000       | `/v1/chat/completions`  | 5              |
| llama-2-7b                       | 4000       | `/v1/chat/completions`  | 1              |
| llama-2-13b                      | 4000       | `/v1/chat/completions`  | 5              |
| llama-2-70b                      | 4000       | `/v1/chat/completions`  | 10             |
| code-llama-7b                    | 16000      | `/v1/chat/completions`  | 1              |
| code-llama-13b                   | 16000      | `/v1/chat/completions`  | 1              |
| code-llama-34b                   | 16000      | `/v1/chat/completions`  | 10             |
| code-llama-70b                   | 4000       | `/v1/chat/completions`  | 1              |
| code-llama-70b-instruct          | 16000      | `/v1/chat/completions`  | 10             |
| phind-code-llama-34b-v2          | 16000      | `/v1/chat/completions`  | 1              |
| llama-3-8b                       | 8000       | `/v1/chat/completions`  | 1              |
| llama-3-70b                      | 8000       | `/v1/chat/completions`  | 5              |
| llama-3.1-8b                     | 128000     | `/v1/chat/completions`  | 1              |
| llama-3.1-70b                    | 128000     | `/v1/chat/completions`  | 5              |
| llama-3.1-405b                   | 128000     | `/v1/chat/completions`  | 10             |
| deepseek-llm-67b-chat           | 4000       | `/v1/chat/completions`  | 5              |
| deepseek-coder-33b-instruct      | 10000      | `/v1/chat/completions`  | 1              |
| deepseek-coder-6.7b-instruct     | 16000      | `/v1/chat/completions`  | 1              |
| deepseek-v2-0628                | 16000      | `/v1/chat/completions`  | 1              |
| deepseek-coder-v2-0614           | 16000      | `/v1/chat/completions`  | 1              |
| mixtral-8x7b                    | 32000      | `/v1/chat/completions`  | 1              |
| mixtral-8x22b                   | 32000      | `/v1/chat/completions`  | 1              |
| mistral-7b-instruct-v0.3        | 32000      | `/v1/chat/completions`  | 1              |
| mistral-7b-instruct-v0.2        | 32000      | `/v1/chat/completions`  | 1              |
| mistral-7b-instruct-v0.1        | 8000       | `/v1/chat/completions`  | 1              |
| mistral-small                   | 32000      | `/v1/chat/completions`  | 1              |
| mistral-medium-vision            | 32000      | `/v1/chat/completions`  | 15             |
| mistral-large                   | 32000      | `/v1/chat/completions`  | 5              |
| mistral-nemo                    | 128000     | `/v1/chat/completions`  | 10             |
| dolphin-2.5-mixtral-8x7b         | 4000       | `/v1/chat/completions`  | 1              |
| dbrx-instruct                   | 32000      | `/v1/chat/completions`  | 5              |
| command-r                       | 128000     | `/v1/chat/completions`  | 20             |
| command-r-plus                   | 128000     | `/v1/chat/completions`  | 30             |
| rekaflash                       | 8000       | `/v1/chat/completions`  | 5              |
| palm-2                          | 8000       | `/v1/chat/completions`  | 15             |
| phi-2                           | 2000       | `/v1/chat/completions`  | 1              |
| phi-3-medium-4k-instruct        | 4000       | `/v1/chat/completions`  | 1              |
| openchat-3.5                    | 4000       | `/v1/chat/completions`  | 1              |
| vicuna-7b-v1.5                  | 4000       | `/v1/chat/completions`  | 1              |
| vicuna-13b-v1.5                 | 4000       | `/v1/chat/completions`  | 1              |
| mytho-max-l2-13b                | 4000       | `/v1/chat/completions`  | 10             |
| solar-0-70b-16bit               | 2000       | `/v1/chat/completions`  | 5              |
| gemma-2b-it                     | 8000       | `/v1/chat/completions`  | 1              |
| gemma-2-9b-it                   | 8000       | `/v1/chat/completions`  | 5              |
| gemma-2-27b-it                  | 8000       | `/v1/chat/completions`  | 20             |
| gemma-7b                        | 32000      | `/v1/chat/completions`  | 1              |
| gemma-instruct-7b               | 4000       | `/v1/chat/completions`  | 5              |
| qwen-1.5-72b                    | 32000      | `/v1/chat/completions`  | 1              |
| qwen-1.5-110b                   | 32000      | `/v1/chat/completions`  | 5              |
| qwen-2-7b-instruct               | 32000      | `/v1/chat/completions`  | 1              |
| qwen-2-72b-instruct              | 32000      | `/v1/chat/completions`  | 5              |
| qwen-2-72b-chat                 | 32000      | `/v1/chat/completions`  | 5              |
| doubao-lite-128k                | 128000     | `/v1/chat/completions`  | 1              |
| snowflake-arctic-instruct        | 4000       | `/v1/chat/completions`  | 5              |
| wizardlm-13b                    | 4000       | `/v1/chat/completions`  | 5              |
| olmo-7b-instruct                | 2000       | `/v1/chat/completions`  | 1              |
| stripedhyena-nous-7b             | 4000       | `/v1/chat/completions`  | 5              |
| yi-34b-chat                     | 2000       | `/v1/chat/completions`  | 1              |
| yi-34b                          | 2000       | `/v1/chat/completions`  | 1              |
| yi-6b                           | 2000       | `/v1/chat/completions`  | 1              |
| cosmosrp                        | 8000       | `/nsfw/chat/completions` | 1              |

## Image Models

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
| analog-v1                      | 300      | `/nsfw/images/generations`             | 5              | Yes  |
| aniverse-v3                    | 300      | `/nsfw/images/generations`             | 5              | Yes  |
| anything-v3                    | 300      | `/nsfw/images/generations`             | 5              | Yes  |
| anything-v4.5                  | 300      | `/nsfw/images/generations`             | 5              | Yes  |
| anything-v5                    | 300      | `/nsfw/images/generations`             | 5              | Yes  |
| abyss-orange-mix-v3            | 300      | `/nsfw/images/generations`             | 5              | Yes  |
| blazing-drive-v10g             | 300      | `/nsfw/images/generations`             | 5              | Yes  |
| breakdomain-i2428              | 300      | `/nsfw/images/generations`             | 5              | Yes  |
| breakdomain-m2150              | 300      | `/nsfw/images/generations`             | 5              | Yes  |
| cetus-mix-v3.5                 | 300      | `/nsfw/images/generations`             | 5              | Yes  |
| childrens-stories-v1-3d         | 300      | `/nsfw/images/generations`             | 5              | Yes  |
| childrens-stories-v1-semi-real  | 300      | `/nsfw/images/generations`             | 5              | Yes  |
| childrens-stories-v1-toon-anime | 300      | `/nsfw/images/generations`             | 5              | Yes  |
| counterfeit-v3.0               | 300      | `/nsfw/images/generations`             | 5              | Yes  |
| cuteyukimix-midchapter-3       | 300      | `/nsfw/images/generations`             | 5              | Yes  |
| cyberrealistic-v3.3            | 300      | `/nsfw/images/generations`             | 5              | Yes  |
| dalcefo-v4                      | 300      | `/nsfw/images/generations`             | 5              | Yes  |
| deliberate-v2                  | 300      | `/nsfw/images/generations`             | 5              | Yes  |
| deliberate-v3                  | 300      | `/nsfw/images/generations`             | 5              | Yes  |
| dreamlike-anime-v1             | 300      | `/nsfw/images/generations`             | 5              | Yes  |
| dreamlike-diffusion-v1          | 300      | `/nsfw/images/generations`             | 5              | Yes  |
| dreamlike-photoreal-v2          | 300      | `/nsfw/images/generations`             | 5              | Yes  |
| dreamshaper-6                  | 300      | `/nsfw/images/generations`             | 5              | Yes  |
| dreamshaper-7                  | 300      | `/nsfw/images/generations`             | 5              | Yes  |
| dreamshaper-8                  | 300      | `/nsfw/images/generations`             | 5              | Yes  |
| edge-of-realism-eor-v2.0        | 300      | `/nsfw/images/generations`             | 5              | Yes  |
| eimis-anime-diffusion-v1       | 300      | `/nsfw/images/generations`             | 5              | Yes  |
| elldreths-vivid-mix            | 300      | `/nsfw/images/generations`             | 5              | Yes  |
| epicphotogasm-x-plus-plus       | 300      | `/nsfw/images/generations`             | 5              | Yes  |
| epicrealism-natural-sin-rc1     | 300      | `/nsfw/images/generations`             | 5              | Yes  |
| epicrealism-pure-evolution-v3    | 300      | `/nsfw/images/generations`             | 5              | Yes  |
| indigo-furry-mix-v7.5-hybrid   | 300      | `/nsfw/images/generations`             | 5              | Yes  |
| juggernaut-aftermath           | 300      | `/nsfw/images/generations`             | 5              | Yes  |
| lofi-v4                        | 300      | `/nsfw/images/generations`             | 5              | Yes  |
| lyriel-v1.6                     | 300      | `/nsfw/images/generations`             | 5              | Yes  |
| majicmix-realistic-v4          | 300      | `/nsfw/images/generations`             | 5              | Yes  |
| mechamix-v1.0                  | 300      | `/nsfw/images/generations`             | 5              | Yes  |
| meinamix-meina-v9              | 300      | `/nsfw/images/generations`             | 5              | Yes  |
| meinamix-meina-v11              | 300      | `/nsfw/images/generations`             | 5              | Yes  |
| neverending-dream-v1.22         | 300      | `/nsfw/images/generations`             | 5              | Yes  |
| pastel-mix                     | 300      | `/nsfw/images/generations`             | 5              | Yes  |
| portrait-plus-v1               | 300      | `/nsfw/images/generations`             | 5              | Yes  |
| protogen-x3.4                  | 300      | `/nsfw/images/generations`             | 5              | Yes  |
| realistic-vision-v1.4          | 300      | `/nsfw/images/generations`             | 5              | Yes  |
| realistic-vision-v2.0          | 300      | `/nsfw/images/generations`             | 5              | Yes  |
| realistic-vision-v4.0          | 300      | `/nsfw/images/generations`             | 5              | Yes  |
| realistic-vision-v5.0          | 300      | `/nsfw/images/generations`             | 5              | Yes  |
| realistic-vision-v5.1          | 300      | `/nsfw/images/generations`             | 5              | Yes  |
| rev-animated-v1.2.2            | 300      | `/nsfw/images/generations`             | 5              | Yes  |
| rundiffusion-fx-2.5d-v1.0       | 300      | `/nsfw/images/generations`             | 5              | Yes  |
| rundiffusion-fx-photorealistic-v1.0 | 300      | `/nsfw/images/generations`             | 5              | Yes  |
| stable-diffusion-v1.5          | 300      | `/nsfw/images/generations`             | 5              | Yes  |
| sd-v1-inpainting               | 300      | `/nsfw/images/generations`             | 5              | Yes  |
| shonin-beautiful-v1.0          | 300      | `/nsfw/images/generations`             | 5              | Yes  |
| theally-mix-ii                 | 300      | `/nsfw/images/generations`             | 5              | Yes  |
| timeless-v1                    | 300      | `/nsfw/images/generations`             | 5              | Yes  |
| toonyou-beta-6                 | 300      | `/nsfw/images/generations`             | 5              | Yes  |

## Video Models

| Model          | Tokens | Endpoint              | Cost (credits) |
|-----------------|--------|----------------------|----------------|
| t2v-turbo       | 80     | `/v1/videos/generations` | 30             |
| svd-turbo       | 80     | `/v1/videos/generations` | 20             |
| dream-machine   | 500    | `/v1/videos/generations` | 80             |


## Audio Models

| Model                      | Tokens | Endpoint          | Cost (credits) |
|---------------------------|--------|--------------------|----------------|
| eleven-multilingual-v2     | 500    | `/v1/audio/speech` | 5              |
| suno-v3.5                 | 500    | `/v1/audio/music`  | 20             |

