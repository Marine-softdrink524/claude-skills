# 🤝 Contributing to Claude Skills

Thank you for your interest in contributing! This repository follows the official [Agent Skills Standard](https://agentskills.io/specification).

---

## 📋 Before You Start

### ✅ Acceptance Criteria

| # | Rule | Required |
|---|---|---|
| 1 | Must follow the [Agent Skills Standard](https://agentskills.io/specification) (SKILL.md format) | ✅ Yes |
| 2 | Skill must be a **folder** in `skills/` with a `SKILL.md` file inside | ✅ Yes |
| 3 | `name` field must match folder name (lowercase, hyphens only, 1-64 chars) | ✅ Yes |
| 4 | `description` must be under 1024 characters and explain WHAT + WHEN | ✅ Yes |
| 5 | Skill must be unique (not a duplicate) | ✅ Yes |
| 6 | Must be tested and working with Claude | ✅ Yes |
| 7 | Your GitHub username in `metadata.author` | ✅ Yes |

### ❌ Auto-Reject Rules

Your PR will be **immediately closed** if:

- ❌ No `SKILL.md` file in the folder
- ❌ Missing YAML frontmatter (`name`, `description`)
- ❌ `name` doesn't match folder name
- ❌ `name` contains uppercase or invalid characters
- ❌ Multiple skills in one PR (1 skill per PR!)
- ❌ Duplicate of existing skill
- ❌ Spam or promotional content

---

## 🚀 How to Add Your Skill

### Step 1: Fork this Repository
Click the "Fork" button at the top right.

### Step 2: Create Your Skill Folder

```bash
# Create skill folder (lowercase, hyphens for spaces)
mkdir skills/your-skill-name

# Create the SKILL.md file
touch skills/your-skill-name/SKILL.md
```

### Step 3: Write Your SKILL.md

Use the [template](./template/SKILL.md) as a starting point:

```markdown
---
name: your-skill-name
description: Clear description of what this skill does and when Claude should use it. Include specific keywords and scenarios.
license: CC0-1.0
metadata:
  author: your-github-username
  version: "1.0"
  category: coding
---

# Your Skill Name

[Detailed instructions that Claude will follow when this skill is active]

## When to Use
- Scenario 1
- Scenario 2

## Guidelines
- Guideline 1
- Guideline 2

## Examples
- Example of good output
- Example of what to avoid
```

### Step 4: Optional — Add Supporting Files

```
your-skill-name/
├── SKILL.md              # Required
├── scripts/              # Optional: helper scripts
├── references/           # Optional: reference documentation
└── assets/               # Optional: templates, images
```

### Step 5: Submit a Pull Request
- PR Title: `Add: [your-skill-name]`
- Fill out the PR template
- Wait for review (usually within 48 hours)

---

## 📐 Naming Rules (from agentskills.io)

| Rule | Valid | Invalid |
|---|---|---|
| Lowercase only | `seo-blog-writer` | ~~`SEO-Blog-Writer`~~ |
| Hyphens for spaces | `senior-python-dev` | ~~`senior_python_dev`~~ |
| 1-64 characters | `code-reviewer` | ~~(empty)~~ |
| No start/end hyphen | `my-skill` | ~~`-my-skill-`~~ |
| No consecutive hyphens | `my-skill` | ~~`my--skill`~~ |
| Match folder name | folder: `my-skill/` → name: `my-skill` | ~~mismatch~~ |

## 🏷️ Categories

Use one of these in your `metadata.category`:

| Category | Examples |
|---|---|
| `coding` | Python, JavaScript, debugging, testing |
| `web-development` | React, Next.js, CSS, frontend |
| `writing` | Blog posts, docs, copywriting |
| `business` | Strategy, analysis, planning |
| `design` | UI/UX, branding, creative |
| `devops` | Docker, CI/CD, cloud infrastructure |
| `security` | Auditing, vulnerability scanning |
| `education` | Tutorials, teaching |
| `productivity` | Email, scheduling, automation |

---

## 💡 Tips for Great Skills

1. **Be specific** — "Senior Python Developer" > "Coding Helper"
2. **Include examples** — Show what great output looks like
3. **Explain what to avoid** — Help Claude know what NOT to do
4. **Keep instructions under 5000 tokens** — As recommended by the spec
5. **Test with Claude** — Make sure it actually works!

---

## 🌐 Get More Visibility

List your skill on [AiAgentBase.app](https://aiagentbase.app) for wider reach and potential monetization!

---

## 📜 Code of Conduct

By contributing, you agree to follow our [Code of Conduct](CODE_OF_CONDUCT.md).

---

Thank you for contributing! 🎉
