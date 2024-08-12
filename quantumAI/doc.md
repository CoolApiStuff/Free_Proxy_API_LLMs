# QuantumAI Documentation

Welcome to the QuantumAI documentation. This guide will help you understand the features, pricing, and API usage for QuantumAI and QuantumAI Pro.

## QuantumAI Pro Features

Upgrade to QuantumAI Pro and unlock exclusive benefits:

- **Early Access to Models**: Be the first to try new and advanced models.
- **7500 Requests per Day**: Access any model, including Claude 3 Opus, CMDR+, and more.
- **30 Requests per Minute**: Boost your efficiency with rapid requests.
- **Custom Plans Available**: Need more usage? Contact us for tailored solutions.

### Pricing

- **Monthly Plan**: $10/month
- **Lifetime Plan**: $50 one-time payment
- **Yearly Plan**: $120/year


## API Limits

### Free Plan

- **Requests per Day**: 850
- **Requests per Minute**: 10

### Paid Plan

- **Requests per Day**: 8500
- **Requests per Minute**: 20

## API Documentation

### Base URL

Access the API using the following base URL:
```
https://api.qtm-ai.com/v1
```

### Endpoints

#### Models List

Retrieve the list of available models using this endpoint:
```
https://api.qtm-ai.com/v1/models
```

#### Chat Completions

Send requests to the models using this endpoint:
```
https://api.qtm-ai.com/v1/chat/completions
```

### API Key Management

Manage your API key using the `/manage-key` command in the Discord bot.

## Available Models

Here is a list of some of the models available through QuantumAI:

- **text-embedding-ada-002**
- **gpt-4o**
- **gemma2-9b-it**
- **llama3-70b-8192**
- **dall-e-3**
- **whisper-large-v3**

For a full list, please refer to the models endpoint.


---

Models : 
{"object":"list","data":[{"id":"text-embedding-ada-002","object":"model","created":1686935002,"owned_by":"QTMAI"},{"id":"text-embedding-3-small","object":"model","created":1686935002,"owned_by":"QTMAI"},{"id":"text-embedding-3-large","object":"model","created":1686935002,"owned_by":"QTMAI"},{"id":"gpt-4o","object":"model","created":1686935002,"owned_by":"QTMAI"},{"id":"gpt-4o-2024-05-13","object":"model","created":1686935002,"owned_by":"QTMAI"},{"id":"gpt-4o-mini","object":"model","created":1686935002,"owned_by":"QTMAI"},{"id":"gpt-4o-mini-2024-07-18","object":"model","created":1686935002,"owned_by":"QTMAI"},{"id":"gemma2-9b-it","object":"model","created":1686935002,"owned_by":"QTMAI"},{"id":"gemma-7b-it","object":"model","created":1686935002,"owned_by":"QTMAI"},{"id":"llama3-70b-8192","object":"model","created":1686935002,"owned_by":"QTMAI"},{"id":"llama3-8b-8192","object":"model","created":1686935002,"owned_by":"QTMAI"},{"id":"llama3-groq-70b-8192-tool-use-preview","object":"model","created":1686935002,"owned_by":"QTMAI"},{"id":"llama3-groq-8b-8192-tool-use-preview","object":"model","created":1686935002,"owned_by":"QTMAI"},{"id":"mixtral-8x7b-32768","object":"model","created":1686935002,"owned_by":"QTMAI"},{"id":"whisper-large-v3","object":"model","created":1686935002,"owned_by":"QTMAI"},{"id":"dall-e-3","object":"model","created":1686935002,"owned_by":"QTMAI"},{"id":"whisper-1","object":"model","created":1686935002,"owned_by":"QTMAI"},{"id":"gpt-4-turbo-2024-04-09","object":"model","created":1686935002,"owned_by":"QTMAI"},{"id":"gpt-4-1106-preview","object":"model","created":1686935002,"owned_by":"QTMAI"},{"id":"dall-e-2","object":"model","created":1686935002,"owned_by":"QTMAI"},{"id":"gpt-4-turbo","object":"model","created":1686935002,"owned_by":"QTMAI"},{"id":"tts-1-hd-1106","object":"model","created":1686935002,"owned_by":"QTMAI"},{"id":"tts-1-hd","object":"model","created":1686935002,"owned_by":"QTMAI"},{"id":"gpt-4-turbo-preview","object":"model","created":1686935002,"owned_by":"QTMAI"},{"id":"babbage-002","object":"model","created":1686935002,"owned_by":"QTMAI"},{"id":"gpt-4-0125-preview","object":"model","created":1686935002,"owned_by":"QTMAI"},{"id":"tts-1-1106","object":"model","created":1686935002,"owned_by":"QTMAI"},{"id":"gpt-3.5-turbo-instruct","object":"model","created":1686935002,"owned_by":"QTMAI"},{"id":"gpt-3.5-turbo-instruct-0914","object":"model","created":1686935002,"owned_by":"QTMAI"},{"id":"davinci-002","object":"model","created":1686935002,"owned_by":"QTMAI"},{"id":"tts-1","object":"model","created":1686935002,"owned_by":"QTMAI"},{"id":"BasicLLM","object":"model","created":1686935002,"owned_by":"QTMAI"},{"id":"ERNIE-3.5-8K","object":"model","created":1686935002,"owned_by":"QTMAI"},{"id":"llama2-7b-2048","object":"model","created":1686935002,"owned_by":"QTMAI"},{"id":"llama2-70b-4096","object":"model","created":1686935002,"owned_by":"QTMAI"},{"id":"deepseek-chat","object":"model","created":1686935002,"owned_by":"QTMAI"},{"id":"deepseek-coder","object":"model","created":1686935002,"owned_by":"QTMAI"},{"id":"gpt-4-vision-preview","object":"model","created":1686935002,"owned_by":"QTMAI"},{"id":"gpt-4-1106-vision-preview","object":"model","created":1686935002,"owned_by":"QTMAI"},{"id":"yi-large","object":"model","created":1686935002,"owned_by":"QTMAI"},{"id":"yi-large-rag","object":"model","created":1686935002,"owned_by":"QTMAI"},{"id":"yi-large-turbo","object":"model","created":1686935002,"owned_by":"QTMAI"},{"id":"yi-medium","object":"model","created":1686935002,"owned_by":"QTMAI"},{"id":"yi-vision","object":"model","created":1686935002,"owned_by":"QTMAI"},{"id":"yi-medium-200k","object":"model","created":1686935002,"owned_by":"QTMAI"},{"id":"yi-spark","object":"model","created":1686935002,"owned_by":"QTMAI"},{"id":"yi-large-preview","object":"model","created":1686935002,"owned_by":"QTMAI"},{"id":"yi-large-fc","object":"model","created":1686935002,"owned_by":"QTMAI"},{"id":"gpt-3.5-turbo","object":"model","created":1686935002,"owned_by":"QTMAI"},{"id":"gpt-3.5-turbo-1106","object":"model","created":1686935002,"owned_by":"QTMAI"},{"id":"gpt-3.5-turbo-16k","object":"model","created":1686935002,"owned_by":"QTMAI"},{"id":"gpt-3.5-turbo-16k-0613","object":"model","created":1686935002,"owned_by":"QTMAI"},{"id":"gpt-3.5-turbo-0301","object":"model","created":1686935002,"owned_by":"QTMAI"},{"id":"gpt-4","object":"model","created":1686935002,"owned_by":"QTMAI"},{"id":"llama-3.1-70b-versatile","object":"model","created":1686935002,"owned_by":"QTMAI"},{"id":"llama-3.1-8b-instant","object":"model","created":1686935002,"owned_by":"QTMAI"},{"id":"Llama3-70b-8192","object":"model","created":1686935002,"owned_by":"QTMAI"},{"id":"meta-llama-3.1-405b-instruct","object":"model","created":1686935002,"owned_by":"QTMAI"},{"id":"text-embedding-ada-002-online","object":"model","created":1686935002,"owned_by":"QTMAI"},{"id":"text-embedding-3-small-online","object":"model","created":1686935002,"owned_by":"QTMAI"},{"id":"text-embedding-3-large-online","object":"model","created":1686935002,"owned_by":"QTMAI"},{"id":"gpt-4o-online","object":"model","created":1686935002,"owned_by":"QTMAI"},{"id":"gpt-4o-2024-05-13-online","object":"model","created":1686935002,"owned_by":"QTMAI"},{"id":"gpt-4o-mini-online","object":"model","created":1686935002,"owned_by":"QTMAI"},{"id":"gpt-4o-mini-2024-07-18-online","object":"model","created":1686935002,"owned_by":"QTMAI"},{"id":"gemma2-9b-it-online","object":"model","created":1686935002,"owned_by":"QTMAI"},{"id":"gemma-7b-it-online","object":"model","created":1686935002,"owned_by":"QTMAI"},{"id":"llama3-70b-8192-online","object":"model","created":1686935002,"owned_by":"QTMAI"},{"id":"llama3-8b-8192-online","object":"model","created":1686935002,"owned_by":"QTMAI"},{"id":"llama3-groq-70b-8192-tool-use-preview-online","object":"model","created":1686935002,"owned_by":"QTMAI"},{"id":"llama3-groq-8b-8192-tool-use-preview-online","object":"model","created":1686935002,"owned_by":"QTMAI"},{"id":"mixtral-8x7b-32768-online","object":"model","created":1686935002,"owned_by":"QTMAI"},{"id":"whisper-large-v3-online","object":"model","created":1686935002,"owned_by":"QTMAI"},{"id":"dall-e-3-online","object":"model","created":1686935002,"owned_by":"QTMAI"},{"id":"whisper-1-online","object":"model","created":1686935002,"owned_by":"QTMAI"},{"id":"gpt-4-turbo-2024-04-09-online","object":"model","created":1686935002,"owned_by":"QTMAI"},{"id":"gpt-4-1106-preview-online","object":"model","created":1686935002,"owned_by":"QTMAI"},{"id":"dall-e-2-online","object":"model","created":1686935002,"owned_by":"QTMAI"},{"id":"gpt-4-turbo-online","object":"model","created":1686935002,"owned_by":"QTMAI"},{"id":"tts-1-hd-1106-online","object":"model","created":1686935002,"owned_by":"QTMAI"},{"id":"tts-1-hd-online","object":"model","created":1686935002,"owned_by":"QTMAI"},{"id":"gpt-4-turbo-preview-online","object":"model","created":1686935002,"owned_by":"QTMAI"},{"id":"babbage-002-online","object":"model","created":1686935002,"owned_by":"QTMAI"},{"id":"gpt-4-0125-preview-online","object":"model","created":1686935002,"owned_by":"QTMAI"},{"id":"tts-1-1106-online","object":"model","created":1686935002,"owned_by":"QTMAI"},{"id":"gpt-3.5-turbo-instruct-online","object":"model","created":1686935002,"owned_by":"QTMAI"},{"id":"gpt-3.5-turbo-instruct-0914-online","object":"model","created":1686935002,"owned_by":"QTMAI"},{"id":"davinci-002-online","object":"model","created":1686935002,"owned_by":"QTMAI"},{"id":"tts-1-online","object":"model","created":1686935002,"owned_by":"QTMAI"},{"id":"BasicLLM-online","object":"model","created":1686935002,"owned_by":"QTMAI"},{"id":"ERNIE-3.5-8K-online","object":"model","created":1686935002,"owned_by":"QTMAI"},{"id":"llama2-7b-2048-online","object":"model","created":1686935002,"owned_by":"QTMAI"},{"id":"llama2-70b-4096-online","object":"model","created":1686935002,"owned_by":"QTMAI"},{"id":"deepseek-chat-online","object":"model","created":1686935002,"owned_by":"QTMAI"},{"id":"deepseek-coder-online","object":"model","created":1686935002,"owned_by":"QTMAI"},{"id":"gpt-4-vision-preview-online","object":"model","created":1686935002,"owned_by":"QTMAI"},{"id":"gpt-4-1106-vision-preview-online","object":"model","created":1686935002,"owned_by":"QTMAI"},{"id":"yi-large-online","object":"model","created":1686935002,"owned_by":"QTMAI"},{"id":"yi-large-rag-online","object":"model","created":1686935002,"owned_by":"QTMAI"},{"id":"yi-large-turbo-online","object":"model","created":1686935002,"owned_by":"QTMAI"},{"id":"yi-medium-online","object":"model","created":1686935002,"owned_by":"QTMAI"},{"id":"yi-vision-online","object":"model","created":1686935002,"owned_by":"QTMAI"},{"id":"yi-medium-200k-online","object":"model","created":1686935002,"owned_by":"QTMAI"},{"id":"yi-spark-online","object":"model","created":1686935002,"owned_by":"QTMAI"},{"id":"yi-large-preview-online","object":"model","created":1686935002,"owned_by":"QTMAI"},{"id":"yi-large-fc-online","object":"model","created":1686935002,"owned_by":"QTMAI"},{"id":"gpt-3.5-turbo-online","object":"model","created":1686935002,"owned_by":"QTMAI"},{"id":"gpt-3.5-turbo-1106-online","object":"model","created":1686935002,"owned_by":"QTMAI"},{"id":"gpt-3.5-turbo-16k-online","object":"model","created":1686935002,"owned_by":"QTMAI"},{"id":"gpt-3.5-turbo-16k-0613-online","object":"model","created":1686935002,"owned_by":"QTMAI"},{"id":"gpt-3.5-turbo-0301-online","object":"model","created":1686935002,"owned_by":"QTMAI"},{"id":"gpt-4-online","object":"model","created":1686935002,"owned_by":"QTMAI"},{"id":"llama-3.1-70b-versatile-online","object":"model","created":1686935002,"owned_by":"QTMAI"},{"id":"llama-3.1-8b-instant-online","object":"model","created":1686935002,"owned_by":"QTMAI"},{"id":"Llama3-70b-8192-online","object":"model","created":1686935002,"owned_by":"QTMAI"},{"id":"meta-llama-3.1-405b-instruct-online","object":"model","created":1686935002,"owned_by":"QTMAI"},{"id":"claude-3.5-sonnet","object":"model","created":1686935002,"owned_by":"Anthropic"},{"id":"claude-3.5-sonnet-online","object":"model","created":1686935002,"owned_by":"Anthropic"},{"id":"claude-3-opus","object":"model","created":1686935002,"owned_by":"Anthropic"},{"id":"claude-3-opus-online","object":"model","created":1686935002,"owned_by":"Anthropic"},{"id":"command-r-plus","object":"model","created":1686935002,"owned_by":"QTMAI"},{"id":"command-r-plus-online","object":"model","created":1686935002,"owned_by":"QTMAI"}]}