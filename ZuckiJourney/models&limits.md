## Zukijourney API - Models and Limits

Here's a summary of the models available in the Zukijourney API and their associated limits, presented in tables for easier readability:

**Chat Models & Cost Multipliers**

| Multiplier | Models/Categories                                  |
|------------|---------------------------------------------------|
| 1.5x       | gpt-4-1106-preview and later, claude-3-opus and later, gpt-4-vision-preview |
| 1.25x      | gpt-4 and later, claude-3-sonnet                   |
| 1x         | gpt-4o-mini + all non-4 gpt models, claude-3-haiku and before, All Gemini/Mistral-Series models |
| 0.5x       | all other models not developed by zukijourney        |
| 0.25x      | caramelldansen-1 & caramelldansen-1-plus            |


**Image Models & Cost per Request**

| Cost per Request | Models                                             |
|-----------------|----------------------------------------------------|
| 42,000           | Midjourney                                          |
| 2,500            | DALLE-2 and later + Stable-Diffusion-3-large + Stable-Image-Ultra/Core and later |
| 250             | Stable-Diffusion-3-Medium & the Flux model series.    |
| 100             | All models provided by Prodia.                      |


**Other Endpoints & Costs**

| Endpoint Category         | Cost per Request |
|--------------------------|-----------------|
| Audio, Embeddings, Image-Upscaling | 100 tokens       |
| Moderations, Text-Translations   | 10 tokens        |


**Rate Limits**

| Endpoint Category | Requests per Minute per Key per IP |
|--------------------|-----------------------------------|
| `/unf/`           | 4                                   |
| `/v1/`            | 12                                  |


**Daily Token Allowances (Based on Donation Tier)**

| Tier             | Daily Tokens | Messages/Day (Approx.) |
|------------------|--------------|------------------------|
| `@Member`        | 22,500        | 126                     |
| `@Booster`       | 200,000       | 400                     |
| `@Donator`        | 200,000       | 400                     |
| `@Early Supporter` | 225,000       | 450                     |
| `@Subscriber`    | 450,000       | 900                     |
| `@Enterprise`   | 4,000,000      | 10,000                   |

**Note:** This is a general overview. Specific model availability and pricing are subject to change. Always refer to the official API documentation and the ZukiJourney Discord server for the most up-to-date information.
