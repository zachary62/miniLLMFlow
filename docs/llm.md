---
layout: default
title: "LLM Wrapper"
parent: "Preparation"
nav_order: 1
---

# LLM Wrappers  

We **don't** provide built-in LLM wrappers. Instead, please implement your own, for example by asking an assistant like ChatGPT or Claude. If you ask ChatGPT to "implement a `call_llm` function that takes a prompt and returns the LLM response," you shall get something like:

```python
def call_llm(prompt):
    from openai import OpenAI
    # Set the OpenAI API key (use environment variables, etc.)
    client = OpenAI(api_key="YOUR_API_KEY_HERE")
    r = client.chat.completions.create(
        model="gpt-4",
        messages=[{"role": "user", "content": prompt}]
    )
    return r.choices[0].message.content

# Example usage
call_llm("How are you?")
```

## Improvements
Feel free to enhance your `call_llm` function as needed. Here are examples:

- Handle chat history:

```python
def call_llm(messages):
    from openai import OpenAI
    client = OpenAI(api_key="YOUR_API_KEY_HERE")
    r = client.chat.completions.create(
        model="gpt-4",
        messages=messages
    )
    return r.choices[0].message.content
```

- Add in-memory caching:

```python
from functools import lru_cache

@lru_cache(maxsize=1000)
def call_llm(prompt):
    # Your implementation here
    pass
```

- Enable logging:

```python
def call_llm(prompt):
    import logging
    logging.info(f"Prompt: {prompt}")
    response = ... # Your implementation here
    logging.info(f"Response: {response}")
    return response
```

## Why Not Provide Built-in LLM Wrappers?
I believe it is a **bad practice** to provide LLM-specific implementations in a general framework:
- **LLM APIs change frequently**. Hardcoding them makes maintenance a nighmare.
- You may need **flexibility** to switch vendors, use fine-tuned models, or deploy local LLMs.
- You may need **optimizations** like prompt caching, request batching, or response streaming.