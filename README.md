
---
title: "Lesson Notes: Prompt Engineering by John Berryman"
---

## Introduction to Language Models

### What is a Language Model?

- Language models are algorithms that predict the next word in a sequence of words.
- Historically, Recurrent Neural Networks (RNNs) were the top language models until the introduction of the Attention mechanism in 2014.
- The Transformer architecture, introduced in 2017, replaced RNNs by allowing better handling of context.
- GPT (Generative Pre-trained Transformer) models use the decoder side of the Transformer architecture.

### GPT Evolution

- **GPT-1:** Introduced the use of the decoder side of the Transformer.
- **GPT-2:** Trained on 10x the data of GPT-1, leading to significantly better performance.
- **GPT-3 and beyond:** Continued scaling up in terms of parameters and training data, enhancing capabilities further.

### Capabilities and Responsibilities

- GPT-2 and similar models can outperform task-specific models in various NLP tasks (e.g., summarization, translation).
- With great power comes great responsibility: potential misuse includes generating misleading news, impersonating others, and creating spam.

## Prompt Crafting Techniques

### Few-shot Prompting

- Provide a few examples to set a pattern for the model to follow.
- Effective for simple tasks and quick adjustments.
- Example: Translation prompts.

```text
> How are you doing today?
< ¿Cómo estás hoy?

> My name is John.
< Mi nombre es John.
```

### Chain-of-Thought Reasoning

- Encourage the model to break down the reasoning process step-by-step.
- Useful for complex problems requiring logical steps.
- Example: Solving age-related problems.

```text
Q: Jim is twice as old as Steve. Jim is 12 years old. How old is Steve?
A: Jim is 12 years old, which is twice as old as Steve. Therefore, Steve is 6 years old.
```

### Document Mimicry

- Structure the prompt in a way that mimics a specific document type (e.g., transcripts, emails).
- Helps in conditioning the model to generate responses in a particular style.
- Example: IT support transcript.

```text
# IT Support Assistant
The following is a transcript between an award-winning IT support rep and a customer.

## Customer:
My cable is out! And I'm going to miss the Superbowl!

## Support Assistant:
Let's figure out how to diagnose your problem…
```

## Building LLM Applications

### Creating Effective Prompts

- Collect context from various sources (e.g., current documents, open tabs, prior messages).
- Rank and trim context to fit the most relevant information into the prompt.
- Assemble the prompt ensuring clarity and relevance for the task at hand.

```go
// Example for code completion
package searchskill

import (
    "context"
    "encoding/json"
    "fmt"
    "strings"
    "time"
)

type Skill struct {
    // Skill implementation
}

type params struct {
    // Parameters definition
}
```

### Introduction of Chat and Tools

- **Chat:** Models can simulate conversations with predefined roles and responses.
- **Tools:** Models can call functions to interact with real-world APIs, enhancing their capabilities.

```json
{
  "type": "function",
  "function": {
    "name": "get_weather",
    "description": "Get the weather",
    "parameters": {
      "type": "object",
      "properties": {
        "location": {
          "type": "string",
          "description": "The city and state"
        },
        "unit": {
          "type": "string",
          "description": "degrees Fahrenheit or Celsius",
          "enum": ["celsius", "fahrenheit"]
        }
      },
      "required": ["location"]
    }
  }
}

// Usage example
Input: {"role": "user", "content": "What's the weather like in Miami?"}
Function Call: {"role": "assistant", "function": {"name": "get_weather", "arguments": '{"location": "Miami, FL"}'}}
```

## Key Tips

### Understand the Model's Limitations

- LLMs are not psychic; they require clear and relevant prompts.
- Avoid overloading the prompt with unnecessary information.
- Use familiar language and clear constructs to improve the model's understanding.

### Safety and Ethical Considerations

- Ensure prompts and applications do not facilitate harmful or unethical use.
- Regularly evaluate the model's output for safety and accuracy.

## Conclusion

Prompt engineering is a critical skill in harnessing the power of large language models. By understanding different prompting techniques and the nuances of crafting effective prompts, one can significantly enhance the performance and reliability of these models in various applications. Always consider the ethical implications and responsibilities when deploying these powerful tools.
