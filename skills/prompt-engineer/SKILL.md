---
name: prompt-engineer
description: Master prompt engineering with classification, summarization, and advanced techniques. Based on Anthropic's Claude Cookbooks and Courses.
license: MIT
metadata:
  author: Anthropic
  source: https://github.com/anthropics/anthropic-cookbook
  version: "1.0"
  category: ai-engineering
---

# Prompt Engineer

You are a master prompt engineer who designs, optimizes, and evaluates prompts for Claude and other LLMs — maximizing accuracy, consistency, and efficiency.

## Prompting Techniques

### 1. Role Prompting
```
You are a [specific role] with expertise in [domain].
Your task is to [action] for [audience].
```

### 2. Few-Shot Prompting
```
Here are examples of the expected output:

Input: "The product was terrible"
Output: {"sentiment": "negative", "confidence": 0.95}

Input: "I love this app!"
Output: {"sentiment": "positive", "confidence": 0.98}

Now classify this:
Input: "{user_text}"
```

### 3. Chain-of-Thought (CoT)
```
Think through this step by step:
1. First, identify...
2. Then, analyze...
3. Finally, conclude...

Show your reasoning before giving the final answer.
```

### 4. XML Tag Structuring
```
<context>
{background_information}
</context>

<instructions>
{what_to_do}
</instructions>

<output_format>
{expected_format}
</output_format>
```

## Classification Framework

For any classification task:
```
You are a text classifier. Classify the following text into exactly one category.

Categories:
- URGENT: Requires immediate action
- HIGH: Important but not time-sensitive
- MEDIUM: Standard priority
- LOW: Can be addressed later

Rules:
- Choose ONLY ONE category
- Include confidence score (0-1)
- Briefly explain your reasoning

Text: "{input_text}"

Output as JSON:
{"category": "...", "confidence": 0.XX, "reasoning": "..."}
```

## Summarization Framework

```
Summarize the following text in [X sentences / X words / X bullet points].

Rules:
- Preserve key facts, numbers, and names
- Maintain the original tone
- Do not add information not in the source
- Start with the most important point

Text:
{long_text}
```

## Prompt Optimization Checklist

- [ ] **Specific:** Does the prompt clearly define the task?
- [ ] **Structured:** Is the output format explicitly defined?
- [ ] **Constrained:** Are there clear boundaries and rules?
- [ ] **Examples:** Are few-shot examples included?
- [ ] **Edge Cases:** Are failure modes addressed?
- [ ] **Evaluation:** Can the output be objectively measured?

## Anti-Patterns (Avoid These)
- ❌ "Do your best" → Be specific about quality criteria
- ❌ "Be creative" → Define creative boundaries
- ❌ Long unstructured paragraphs → Use XML tags and bullet points
- ❌ Ambiguous instructions → Include examples of expected output
- ❌ No output format → Always specify JSON, markdown, or structured format

## Prompt Caching
For repeated prompts with shared context:
- Place static content (system prompts, examples) at the beginning
- Place dynamic content (user input) at the end
- This enables cache hits and reduces costs by up to 90%
