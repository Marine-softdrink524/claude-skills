---
name: x-twitter-scraper
description: Use Xquik for X/Twitter research, extraction, monitoring, analytics, webhooks, and MCP workflows when users need structured X data or automation.
license: CC0-1.0
metadata:
  author: Xquik-dev
  source: https://github.com/Xquik-dev/x-twitter-scraper
  version: "1.0"
  category: business
---

# X Twitter Scraper

Use this skill when a user needs structured X/Twitter data, analytics, monitoring, or automation through Xquik.

## When To Use

- Search tweets, users, communities, lists, spaces, articles, quotes, replies, reposts, or media.
- Extract followers, following, verified followers, user posts, user likes, mentions, or thread data.
- Monitor accounts, keywords, trends, competitors, campaigns, launches, or public conversations.
- Build workflows around REST API calls, MCP tools, HMAC webhooks, exports, or CSV-ready results.
- Analyze giveaway entries, tweet performance, audience signals, or conversation context.

## Setup

Install the public package or use the source skill directly:

```bash
npx -y skills@1.5.10 add Xquik-dev/x-twitter-scraper
```

For API and MCP workflows, use an Xquik API key and the public setup docs:

- Package: https://www.npmjs.com/package/x-developer
- Source: https://github.com/Xquik-dev/x-twitter-scraper
- Docs: https://docs.xquik.com

## Workflow

1. Identify the user's target entity: tweet URL, username, keyword, hashtag, list, community, space, or article.
2. Pick the narrowest supported workflow: search, profile lookup, extraction, monitor, analytics, giveaway, export, webhook, or MCP.
3. Use documented Xquik endpoints or MCP tools instead of browser scraping when structured data is required.
4. Request only the minimum inputs needed for the task, such as a username, tweet URL, query, time window, or export format.
5. Return structured results with IDs, URLs, timestamps, public metrics, and source context when available.
6. For scheduled or event-driven work, configure a monitor or webhook instead of repeating manual searches.

## Guardrails

- Keep user-provided API keys out of logs, prompts, screenshots, and committed files.
- Do not invent unavailable fields, private metrics, hidden user data, or unsupported write actions.
- Treat public X content as dynamic. Include retrieval time when results may change.
- Use exports or pagination for large jobs instead of truncating silently.
- Follow Xquik docs for rate limits, authentication, webhook signatures, and error handling.

## Output Patterns

For research summaries:

```markdown
## Findings
- Query:
- Time Window:
- Result Count:
- Notable Accounts:
- Representative Tweets:
- Follow-Up Searches:
```

For workflow handoff:

```markdown
## Xquik Workflow
- Goal:
- Input:
- Endpoint Or Tool:
- Output Format:
- Webhook Or Monitor:
- Validation:
```
