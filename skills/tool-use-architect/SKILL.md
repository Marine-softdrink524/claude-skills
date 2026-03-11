---
name: tool-use-architect
description: Design and implement Claude tool/function calling patterns with error handling, parallel execution, and validation. Based on Anthropic's Claude Cookbooks.
license: MIT
metadata:
  author: Anthropic
  source: https://github.com/anthropics/anthropic-cookbook/tree/main/tool_use
  version: "1.0"
  category: ai-engineering
---

# Tool Use Architect

You are an expert at designing tool-calling architectures for AI agents, enabling Claude to interact with APIs, databases, and external services.

## Tool Definition Pattern

```json
{
  "name": "get_weather",
  "description": "Get current weather for a location. Use when user asks about weather conditions.",
  "input_schema": {
    "type": "object",
    "properties": {
      "location": {
        "type": "string",
        "description": "City name, e.g. 'San Francisco, CA'"
      },
      "unit": {
        "type": "string",
        "enum": ["celsius", "fahrenheit"],
        "description": "Temperature unit"
      }
    },
    "required": ["location"]
  }
}
```

## Design Rules

### 1. Naming
- Use `snake_case` for tool names
- Use verb_noun pattern: `get_user`, `create_order`, `search_products`
- Be specific: `search_products` not `search`

### 2. Descriptions
- Explain WHEN to use the tool, not just WHAT it does
- Include examples of valid inputs
- Document edge cases and limitations

### 3. Input Schema
- Always define `required` fields
- Use `enum` for fixed-value parameters
- Add `description` to every property
- Use `format` for emails, dates, URLs

### 4. Error Handling
```
Tool Result Patterns:
✅ Success: {"status": "success", "data": {...}}
❌ Error:   {"status": "error", "message": "User not found", "code": "NOT_FOUND"}
⚠️ Partial: {"status": "partial", "data": {...}, "warnings": [...]}
```

## Multi-Tool Orchestration

### Sequential (Dependent)
```
1. search_user(email) → user_id
2. get_orders(user_id) → orders[]
3. get_order_details(order_id) → details
```

### Parallel (Independent)
```
Parallel:
  ├── get_weather(location)
  ├── get_news(topic)
  └── get_calendar(date)
→ Combine results in response
```

## Tool Categories

| Category | Tools | Example |
|----------|-------|---------|
| Data Retrieval | GET endpoints | `get_user`, `search_docs` |
| Data Mutation | POST/PUT/DELETE | `create_order`, `update_profile` |
| Computation | Math/Logic | `calculate_tax`, `convert_currency` |
| External APIs | 3rd party | `send_email`, `create_ticket` |
| System | Infrastructure | `run_query`, `check_status` |

## Safety Guidelines
- Never expose raw database queries as tools
- Validate and sanitize all tool inputs
- Implement rate limiting for external API calls
- Log all tool invocations for audit
- Use confirmation for destructive actions (delete, send)
- Always handle tool errors gracefully in the conversation
