# Messages and Special Tokens

## System Messages
System messages (also called System Prompts) define how the model should behave. They serve as persistent instructions, guiding every subsequent interaction.

```python
system_message = {
    "role": "system",
    "content": "You are a professional customer service agent. Always be polite, clear, and helpful."
}
```

## Conversations: User and Assistant Messages
A conversation consists of alternating messages between a Human (user) and an LLM (assistant).
```python
conversation = [
    {"role": "user", "content": "I need help with my order"},
    {"role": "assistant", "content": "I'd be happy to help. Could you provide your order number?"},
    {"role": "user", "content": "It's ORDER-123"},
]
```

## Chat Templates
Chat templates are essential for structuring conversations between language models and users. They guide how message exchanges are formatted into a single prompt.

```python
messages = [
    {"role": "system", "content": "You are a math tutor."},
    {"role": "user", "content": "What is calculus?"},
    {"role": "assistant", "content": "Calculus is a branch of mathematics..."},
    {"role": "user", "content": "Can you give me an example?"},
]
```

## Base Models vs Instruct Models
Another point we need to understand is the difference between a Base Model vs. an Instruct Model:

- A Base Model is trained on raw text data to predict the next token.

- An Instruct Model is fine-tuned specifically to follow instructions and engage in conversations. 

To make a Base Model behave like an instruct model, we need to format our prompts in a consistent way that the model can understand.



To convert previous conversation into a prompt, we load the tokenizer and call `apply_chat_template`:

```python
from transformers import AutoTokenizer

tokenizer = AutoTokenizer.from_pretrained("HuggingFaceTB/SmolLM2-1.7B-Instruct")
rendered_prompt = tokenizer.apply_chat_template(messages, tokenize=False, add_generation_prompt=True)
```

