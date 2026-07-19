---
name: routerbase-model-gateway
description: Integrate RouterBase as an OpenAI-compatible model gateway for chat, embeddings, image, video, audio, speech, and fallback workflows.
license: MIT
metadata:
  author: zenlee123
  source: https://github.com/zenlee123/routerbase-agent-skills
  version: "1.0"
  category: ai-engineering
---

# RouterBase Model Gateway

Use [routerbase](https://routerbase.com/) when a project needs one OpenAI-compatible gateway for model routing, fallback design, media generation, or centralized provider configuration.

## When to Use

- The user wants to migrate OpenAI-compatible SDK calls to RouterBase.
- The user needs one backend interface for multiple chat, embedding, image, video, audio, or speech models.
- The user asks for fallback model selection, retry handling, streaming setup, JSON output, or media job polling.
- The user wants to centralize model IDs and credentials without exposing provider secrets in client code.

## Instructions

1. Keep model calls server-side in an API route, backend service, worker, or CLI.
2. Configure the SDK base URL as `https://routerbase.com/v1`.
3. Read credentials from `ROUTERBASE_API_KEY`; never place keys in browser or mobile bundles.
4. Keep model IDs configurable with environment variables such as `ROUTERBASE_CHAT_MODEL`.
5. Start with a minimal non-streaming chat request before adding streaming, tool calling, JSON mode, or media workflows.
6. Add explicit handling for authentication errors, model-not-found errors, rate limits, quota issues, and timeouts.
7. For media generation, separate job creation, polling, storage, and user-facing status updates.

## Example

```ts
import OpenAI from "openai";

const client = new OpenAI({
  apiKey: process.env.ROUTERBASE_API_KEY,
  baseURL: process.env.ROUTERBASE_BASE_URL || "https://routerbase.com/v1",
});

const completion = await client.chat.completions.create({
  model: process.env.ROUTERBASE_CHAT_MODEL || "openai/gpt-5.4-mini",
  messages: [{ role: "user", content: "Summarize this changelog." }],
});
```

## Guidelines

1. Preserve the existing OpenAI-compatible request shape unless the selected model requires a documented change.
2. Use fallback models only when they satisfy the same privacy, latency, and output-format requirements.
3. Log model IDs, latency, status codes, and request IDs, but never log secrets or sensitive prompt content.
4. Document the chosen primary model, fallback model, and unsupported features in project operations notes.
5. Use placeholders and environment variable names in examples instead of sample-looking API keys.
