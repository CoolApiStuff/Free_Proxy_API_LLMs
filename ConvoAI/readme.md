# <a name="convoai-api-documentation"></a>ConvoAI API Documentation

## <a name="table-of-contents"></a>Table of Contents

- [Overview](#overview)
    - [Free vs. Premium Features](#free-vs-premium-features)
    - [Pricing](#pricing)
    - [API Capacities and Limits](#api-capacities-and-limits)
- [Free Version Features](#free-version-features)
- [Premium Version Features](#premium-version-features)
- [Authentication Methods](#authentication-methods)
- [Endpoints](#endpoints)
    - [Function Calling](#function-calling)
    - [Streaming](#streaming)
    - [Error Codes](#error-codes)
- [Rate Limiting](#rate-limiting)
- [Error Handling](#error-handling)
- [Code Examples](#code-examples)
- [Models](#models)
    - [Text Generation Models](#text-generation-models)
    - [Image Generation Models](#image-generation-models)
    - [Audio Processing Models](#audio-processing-models)
    - [Embeddings Models](#embeddings-models)
    - [Complete Model List](#model-list)
- [Token Calculation](#token-calculation)
    - [Understanding Costs](#understanding-costs)
    - [How It Works](#how-it-works)
    - [Cost Calculation Example](#cost-calculation-example)
    - [Flat Rate Services](#flat-rate-services)
    - [Additional Examples](#additional-examples)
- [Quickstart](#quickstart)
    - [Registration](#registration)
    - [Using the Dashboard](#using-the-dashboard)
    - [Making Your First Request](#making-your-first-request)
    - [Example Request](#example-request)
- [Support and Resources](#support-and-resources) 

---

## <a name="overview"></a>Overview

The ConvoAI API provides access to a wide range of AI models, including text generation, image generation, audio processing, and embeddings, through a single, unified interface. It is designed to be developer-friendly, adhering to the OpenAI schema for seamless integration into your applications.

### <a name="free-vs-premium-features"></a>Free vs. Premium Features

| Feature | Free Trial | Premium | Professional | Enterprise |
|---|---|---|---|---|
| Access to Basic Models | ✓ | ✓ | ✓ | ✓ |
| Access to Premium Models | Limited | ✓ | ✓ | ✓ |
| Request Limits | Lower | Higher | Higher | Highest |
| Response Speed | Slower | Faster | Faster | Fastest |
| Response Quality | Lower | Higher | Higher | Highest |
| NSFW Content | ✗ | ✓ | ✓ | ✓ |
| Beta Models | ✗ | ✗ | ✗ | ✓ |
| Dedicated Servers | ✗ | ✗ | ✗ | ✓ |

### <a name="pricing"></a>Pricing

| Membership | Price |
|---|---|
| Free Trial | Free |
| Premium | $4.99 per month |
| Professional | $9.99 per month |
| Enterprise | $19.99 per month |

### <a name="api-capacities-and-limits"></a>API Capacities and Limits

| Membership | Credits | Request Limit per minute |
|---|---|---|
| Free Trial | 1,000 | 60 |
| Premium | 20,000 | 120 |
| Professional | 40,000 | 240 |
| Enterprise | 80,000 | 480 |

---

## <a name="free-version-features"></a>Free Version Features

The free version of the ConvoAI API provides:

- Access to a limited selection of basic AI models.
- Lower request limits.
- Slower response speeds and lower quality responses compared to premium memberships.

---

## <a name="premium-version-features"></a>Premium Version Features

Premium memberships offer:

- Access to a wider range of AI models, including premium and beta models.
- Increased request limits.
- Faster response speeds and higher quality responses.
- Access to NSFW content.
- Dedicated servers for Enterprise members.

---

## <a name="authentication-methods"></a>Authentication Methods

The ConvoAI API uses API keys for authentication. To obtain an API key:

1. Register for an account on the ConvoAI website.
2. Navigate to the API Keys page in your dashboard.
3. Generate a new API key.

**API Key Requirement:**

Every API request must include your API key in the `Authorization` HTTP header using the Bearer scheme:

```
Authorization: Bearer YOUR_API_KEY
```

**Important:**

- Secure your API key at all times and avoid sharing it.
- If you suspect your API key has been compromised, regenerate it immediately from your dashboard.

## <a name="endpoints"></a>Endpoints

The ConvoAI API provides various endpoints for different functionalities:

### <a name="function-calling"></a>Function Calling

**Endpoint:** `/v1/chat/completions`

Function calling allows you to reliably get structured data from the model. The Chat Completions API does not call the function itself; instead, the model generates JSON for use in your code.

**Common Use Cases:**

- Creating Assistants: Define functions that will call external APIs to answer user queries.
- Converting Natural Language to API Calls: Turn natural language phrases into API calls.
- Extracting Structured Data from Text: Define functions to extract structured data from text.

**Basic Sequence:**

1. **Initial Call:** Send the user query along with a set of predefined functions to the model.
2. **Function Detection:** The model may choose to call one or more functions, outputting a JSON object adhering to your schema.
3. **JSON Parsing and Function Call:** Parse the string into JSON in your code, then call your function with the provided arguments.
4. **Result Summarization:** Append the function response as a new message and let the model summarize the results back to the user.

**Function Calling Behavior:**

- **Default Behavior:** `tool_choice: "auto"` - lets the model decide whether and which functions to call.
- **Forced Function Call:** `tool_choice: "required"` - forces the model to call one or more functions.
- **Specific Function Call:** `tool_choice: {"type": "function", "function": {"name": "my_function"}}` - calls a specific function.
- **Disable Function Calls:** `tool_choice: "none"` - forces the model to generate only a user-facing message.

**Parallel Function Calling:**

Parallel function calling enables multiple function calls simultaneously, reducing API round trips, especially for long-running functions. To disable parallel function calls, pass `parallel_tool_calls: false` in the request.

### <a name="streaming"></a>Streaming

**Endpoint:** `/v1/chat/completions`

The ConvoAI API supports streaming responses, enabling the delivery of partial results for specific requests. This feature leverages the Server-sent events (SSE) standard to support real-time, interactive applications.

**Benefits:**

- Enhanced user experience by providing faster and more responsive applications.
- Timely updates and improved performance for chatbots, real-time analytics, and interactive services.

**Implementation:**

Set the `stream` parameter to `true` in the request. The response will be a stream of chunks, each containing a partial response.

**Parsing Server-sent events:**

Parsing Server-sent events is non-trivial and should be done with caution. Simple strategies like splitting by a new line may result in parsing errors. It is recommended to use existing client libraries when possible.

### <a name="error-codes"></a>Error Codes

The ConvoAI API uses standard HTTP status codes to indicate the success or failure of a request. Here is a table of common error codes:

| Error Code | Cause | Solution |
|---|---|---|
| 400 | The request body is invalid. | Ensure your request body conforms to the required format and includes all necessary fields. |
| 401 | Missing Authorization header. | Include an Authorization header using the Bearer scheme with your API key. |
| 402 | Attempting to access a premium model without a premium plan. | Upgrade your subscription plan to access premium models. |
| 403 | Your API key has been banned. | Contact ConvoAI support to resolve the issue. |
| 403 | Your IP address has been banned. | Contact ConvoAI support to resolve the issue. |
| 429 | Rate limit has been exceeded. | Wait until the next minute to continue using the API. Retry your request after a brief wait. If the issue persists, contact ConvoAI support and check the status page. |
| 500 | Server or provider issues. | Retry your request after a brief wait. If the issue persists, contact ConvoAI support and check the status page. |
| 503 | Servers are experiencing high traffic. | Retry your request after a brief wait. If the issue persists, contact ConvoAI support and check the status page. |

---

## <a name="rate-limiting"></a>Rate Limiting

The ConvoAI API implements rate limiting to prevent abuse and ensure fair usage for all users. Rate limits vary based on your membership plan:

| Membership | Requests per minute |
|---|---|
| Free Trial | 60 |
| Premium | 120 |
| Professional | 240 |
| Enterprise | 480 |

If you exceed the rate limit, you will receive a `429 Too Many Requests` error. You can check your current rate limit status and remaining requests in the response headers.

---

## <a name="error-handling"></a>Error Handling

It is essential to implement proper error handling in your applications to gracefully handle API errors. When making API requests, always check the HTTP status code and handle errors accordingly.

- Use `try-catch` blocks to catch exceptions and handle errors gracefully.
- Log errors for debugging and monitoring purposes.
- Provide informative error messages to users when appropriate.

---

## <a name="code-examples"></a>Code Examples

**Example: Parallel Function Calling with Python**

```python
from openai import OpenAI
import json

client = OpenAI(
    base_url="https://api.convoai.tech",
    api_key="sk-*********************"
)

# Example dummy function hard coded to return the same weather
# In production, this could be your backend API or an external API
def get_current_weather(location, unit="fahrenheit"):
    """Get the current weather in a given location"""
    if "tokyo" in location.lower():
        return json.dumps({"location": "Tokyo", "temperature": "10", "unit": unit})
    elif "san francisco" in location.lower():
        return json.dumps({"location": "San Francisco", "temperature": "72", "unit": unit})
    elif "paris" in location.lower():
        return json.dumps({"location": "Paris", "temperature": "22", "unit": unit})
    else:
        return json.dumps({"location": location, "temperature": "unknown"})

def run_conversation():
    # Step 1: send the conversation and available functions to the model
    messages = [{"role": "user", "content": "What's the weather like in San Francisco, Tokyo, and Paris?"}]
    tools = [
        {
            "type": "function",
            "function": {
                "name": "get_current_weather",
                "description": "Get the current weather in a given location",
                "parameters": {
                    "type": "object",
                    "properties": {
                        "location": {
                            "type": "string",
                            "description": "The city and state, e.g. San Francisco, CA",
                        },
                        "unit": {"type": "string", "enum": ["celsius", "fahrenheit"]},
                    },
                    "required": ["location"],
                },
            }
        }
    ]
    response = client.chat.completions.create(
        model="gpt-40",
        messages=messages,
        tools=tools,
        tool_choice="auto", # auto is default, but we'll be explicit
    )
    response_message = response.choices[0].message
    tool_calls = response_message.tool_calls
    # Step 2: check if the model wanted to call a function
    if tool_calls:
        # Step 3: call the function
        # Note: the JSON response may not always be valid; be sure to handle errors
        available_functions = {
            "get_current_weather": get_current_weather,
        } # only one function in this example, but you can have multiple
        messages.append(response_message) # extend conversation with assistant's reply
        # Step 4: send the info for each function call and function response to the model
        for tool_call in tool_calls:
            function_name = tool_call.function.name
            function_to_call = available_functions[function_name]
            function_args = json.loads(tool_call.function.arguments)
            function_response = function_to_call(
                location=function_args.get("location"),
                unit=function_args.get("unit"),
            )
            messages.append(
                {
                    "tool_call_id": tool_call.id,
                    "role": "tool",
                    "name": function_name,
                    "content": function_response,
                }
            ) # extend conversation with function response
        second_response = client.chat.completions.create(
            model="gpt-40",
            messages=messages,
        ) # get a new response from the model where it can see the function response
        return second_response
    print(run_conversation())

```

**Example: Streaming with Python**

```python
from openai import OpenAI

client = OpenAI(
    base_url="https://api.convoai.tech",
    api_key="sk-***
****"
)

stream = client.chat.completions.create(
    model="gpt-3.5-turbo",
    messages=[{"role": "user", "content": "Say this is a test"}],
    stream=True,
)

for chunk in stream:
    if chunk.choices[0].delta.content is not None:
        print(chunk.choices[0].delta.content, end="")

```

**More Examples:**

- You can find more code examples demonstrating function calling in the [OpenAI Function Calling Examples Cookbook](https://platform.openai.com/docs/guides/function-calling).
- For examples on other endpoints and functionalities, refer to the [ConvoAI API Reference](https://api.convoai.tech/docs).

---

## <a name="models"></a>Models

ConvoAI offers a wide range of AI models, covering various functionalities like text generation, image generation, audio processing, and embeddings. Each model has its own strengths and capabilities, catering to different use cases and requirements.

### <a name="text-generation-models"></a>Text Generation Models

These models are trained to understand and generate human-like text based on the provided prompts. They are versatile and can be used for various tasks, including:

- Content Generation: Create articles, stories, marketing copy, and more.
- Code Generation: Generate code in various programming languages.
- Summarization: Condense large amounts of text into concise summaries.
- Conversation: Build chatbots and conversational AI systems.
- Creative Writing: Generate poems, scripts, and other creative content.

**Key Considerations:**

- **Context Length:** The maximum number of tokens the model can handle in a single request.
- **Output Length:** The maximum number of tokens the model can generate in a single response.
- **Knowledge Cut-off Date:** The date up to which the model's knowledge is trained.

**Examples:**

| Model | Description | Membership |
|---|---|---|
| GPT-3.5 Turbo | Powerful and versatile text generation model. | All |
| GPT-4 | Advanced model with enhanced capabilities and longer context length. | Premium, Professional, Enterprise |
| Claude 3 | High-performance model known for its conversational abilities. | Premium, Professional, Enterprise |
| Alpaca 7B | Instruction-following language model fine-tuned from LLaMA 7B. | All |

### <a name="image-generation-models"></a>Image Generation Models

These models can generate images from textual descriptions, allowing you to visualize ideas and concepts. They are particularly useful for:

- Creating Illustrations: Generate unique and visually appealing illustrations.
- Generating Digital Art: Create artistic images based on textual prompts.
- Designing Visuals: Generate custom visuals for marketing, education, and other purposes.

**Key Considerations:**

- **Image Quality:** The resolution and detail level of the generated images.
- **Style Options:** The range of artistic styles the model can generate.
- **Customization:** The ability to control aspects like composition, color palette, and objects in the image.

**Examples:**

| Model | Description | Membership |
|---|---|---|
| DALL-E 2 | Generates high-quality images from textual descriptions. | All |
| DALL-E 3 | Advanced image generation model with enhanced realism and detail. | Premium, Professional, Enterprise |
| Stable Diffusion | Open-source model known for its creative and diverse image generation. | All |
| Midjourney | Model focused on creative storytelling and narrative generation. | All |

### <a name="audio-processing-models"></a>Audio Processing Models

ConvoAI offers audio models for tasks like speech-to-text, text-to-speech, and translation. These models facilitate accessibility and communication across different platforms and languages.

**Key Considerations:**

- **Accuracy:** The accuracy of speech recognition and translation.
- **Voice Quality:** The naturalness and clarity of the synthesized speech.
- **Language Support:** The range of languages supported by the model.

**Examples:**

| Model | Description | Membership |
|---|---|---|
| Whisper Large | Highly accurate speech-to-text model. | Premium, Professional, Enterprise |
| Eleven Multilingual V2 | Text-to-speech model with support for multiple languages. | Premium, Professional, Enterprise |
| Deep TTS | Text-to-speech model with natural and expressive voice quality. | All |

### <a name="embeddings-models"></a>Embeddings Models

Embeddings models convert text into numerical representations (vectors) that capture the meaning and semantic relationships between words. They are widely used for:

- Search: Find relevant documents and information based on semantic similarity.
- Clustering: Group similar data points together.
- Recommendations: Suggest items based on user preferences and item characteristics.
- Anomaly Detection: Identify unusual or outlier data points.
- Classification: Categorize text into predefined categories.

**Key Considerations:**

- **Dimensionality:** The size of the embedding vectors.
- **Accuracy:** The ability of the embeddings to capture semantic relationships.
- **Speed:** The time it takes to generate embeddings.

**Examples:**

| Model | Description | Membership |
|---|---|---|
| Text Embedding Ada 002 | Fast and efficient embedding model. | Premium, Professional, Enterprise |
| Text Embedding 3 Large | High-dimensional embedding model with enhanced accuracy. | Premium, Professional, Enterprise |

### <a name="model-list"></a>Complete Model List

For a detailed list of all available models, their costs, and specific parameters, refer to the [Models Page](model.md). This page provides comprehensive information about each model, including:

- Knowledge details like maximum context length, input/output token limits, and knowledge cut-off date.
- Cost information for input tokens, output tokens, and lump-sum costs for flat-rate services.
- Model ID, name, description, owner, supported memberships, scope, endpoint, and creation date.

This comprehensive list allows you to explore and choose the best models for your specific needs and budget.

---

## <a name="token-calculation"></a>Token Calculation

ConvoAI uses a token-based system to calculate the cost of API usage. Tokens are units that represent pieces of text, roughly equivalent to 1.5 words. Both input and output text are tokenized to determine the cost of each request.

### <a name="understanding-costs"></a>Understanding Costs

- **Token-Based Pricing:** Each request is charged based on the number of tokens consumed, both for input and output.
- **Model-Specific Costs:** Different models have different costs per 1,000 tokens.
- **Flat-Rate Services:** Some services, like image generation, use a flat-rate fee instead of token-based pricing.

### <a name="how-it-works"></a>How It Works

1. **Purchase Membership:** You purchase a membership to receive credits.
2. **Credit Deduction:** Credits are deducted for each request based on the model used and the number of tokens consumed.

### <a name="cost-calculation-example"></a>Cost Calculation Example

**Scenario:** A request with 10 tokens (8 input and 2 output) using the `gpt-40` model.

**Cost Calculation:**

- **Input:** 8 tokens * (5 credits per 1000 tokens) = 0.04 credits
- **Output:** 2 tokens * (15 credits per 1000 tokens) = 0.03 credits
- **Total Cost:** 0.04 + 0.03 = **0.07 credits deducted**

**Response Structure:**

The API response includes a `cost` object with details about the token usage and cost:

```json
{
  "cost": {
    "input_tokens": 5,
    "output_tokens": 15,
    "lump_sum": 0
  }
}
```

### <a name="flat-rate-services"></a>Flat Rate Services

For services with a flat-rate fee (e.g., image generation, audio embeddings), the `lump_sum` value in the `cost` object represents the cost in credits.

**Example:**

```json
{
  "cost": {
    "input_tokens": 0,
    "output_tokens": 0,
    "lump_sum": 200
  }
}
```

**Calculation:**

- **Lump Sum:** 200 credits / 1000 = **0.2 credits deducted**

### <a name="additional-examples"></a>Additional Examples

**Example 1: Text Processing**

- Input Tokens: 12
- Output Tokens: 6
- Model: `gpt-3`

```json
{
  "cost": {
    "input_tokens": 4,
    "output_tokens": 10,
    "lump_sum": 0
  }
}
```

**Calculation:**

- Input: 12 tokens * (4 credits per 1000 tokens) = 0.048 credits
- Output: 6 tokens * (10 credits per 1000 tokens) = 0.06 credits
- Total Cost: 0.048 + 0.06 = **0.108 credits deducted**

**Example 2: Image Generation**

- Service: Image generation
- Flat-rate Lump Sum: 500 credits

```json
{
  "cost": {
    "input_tokens": 0,
    "output_tokens": 0,
    "lump_sum": 500
  }
}
```

**Calculation:**

- Lump Sum: 500 credits / 1000 = **0.5 credits deducted**

For more details and examples of token calculation, refer to the [Token Calculation](https://api.convoai.tech/docs/token-calculation) documentation page.

---

## <a name="quickstart"></a>Quickstart

This guide provides a step-by-step walkthrough to get you started with the ConvoAI API.

### <a name="registration"></a>Registration

1. **Visit Registration Page:** Go to the [ConvoAI Registration](https://convoai.tech/register) page.
2. **Enter Details:** Fill in the registration form with your username, email address, and password.
    - **Important:** Remember your password, as it cannot be reset.
3. **OTP Verification:** You will receive a One-Time Password (OTP) via email. Enter the OTP to complete the registration.

### <a name="using-the-dashboard"></a>Using the Dashboard

Once registered, you can access your dashboard to:

- **Monitor API Requests:** Track your API usage, including credits consumed and requests made.
- **Manage API Keys:** Generate, view, and manage your API keys.
- **Upgrade Membership:** Upgrade to a premium membership for higher limits and faster responses.

### <a name="making-your-first-request"></a>Making Your First Request

1. **Choose a Model:** Select a model that suits your needs from the [Models Page](model.md).
2. **Obtain API Key:** Generate an API key from the API Keys page in your dashboard.
3. **Construct Request:** Use your preferred programming language and HTTP client library to construct an API request.
    - Include your API key in the `Authorization` header.
    - Specify the chosen model and other parameters as required.
4. **Send Request:** Send the API request to the appropriate endpoint.
5. **Handle Response:** Parse the API response and handle errors gracefully.

### <a name="example-request"></a>Example Request (Python)

```python
import openai

openai.api_key = "YOUR_API_KEY"

response = openai.ChatCompletion.create(
  model="gpt-3.5-turbo",
  messages=[
    {"role": "user", "content": "Hello, how are you?"}
  ]
)

print(response.choices[0].message.content)
```

This is a basic example of a chat completion request using the `gpt-3.5-turbo` model. You can customize the request with different models, parameters, and input messages.

For more detailed guides and examples, refer to the ConvoAI API documentation:

- [API Introduction](https://api.convoai.tech/docs/api-introduction)
- [Function Calling](https://api.convoai.tech/docs/function-calling)
- [Streaming](https://api.convoai.tech/docs/streaming)
- [Error Codes](https://api.convoai.tech/docs/error-codes)


---


## <a name="support-and-resources"></a>Support and Resources

- **Documentation:** The ConvoAI API documentation provides comprehensive information about the API, models, endpoints, and usage guidelines.
- **Status Page:** The [ConvoAI Status Page](https://status.convoai.tech/) provides updates on the API's availability and performance.
- **Support Team:** Contact the ConvoAI support team for assistance with any issues or questions.

