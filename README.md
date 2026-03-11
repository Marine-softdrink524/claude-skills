<p align="center">
  <img src="https://img.shields.io/badge/Agent_Skills-Standard-blueviolet?style=for-the-badge" alt="Agent Skills" />
  <img src="https://img.shields.io/badge/Format-SKILL.md-00B4D8?style=for-the-badge" alt="SKILL.md" />
  <img src="https://img.shields.io/badge/Maintained-Active-brightgreen?style=for-the-badge" alt="Maintained" />
  <img src="https://img.shields.io/badge/PRs-Welcome-orange?style=for-the-badge" alt="PRs Welcome" />
  <img src="https://img.shields.io/badge/License-CC0%201.0-lightgrey?style=for-the-badge" alt="License" />
</p>

<h1 align="center">🤖 Claude Skills</h1>

<p align="center">
  <strong>A community-curated collection of Agent Skills for Claude AI</strong>
  <br />
  <em>Following the official <a href="https://agentskills.io/specification">Agent Skills Standard</a> (SKILL.md format)</em>
</p>

<p align="center">
  <a href="https://aiagentbase.app/skills">🌐 Browse & Deploy on AiAgentBase</a> •
  <a href="#-how-to-contribute">🤝 Contribute</a> •
  <a href="#-skill-catalog">📂 Catalog</a> •
  <a href="https://agentskills.io">📋 Agent Skills Spec</a>
</p>

---

> 🚀 **Want 1-Click Deploy & Premium Skills?** Visit [AiAgentBase.app/skills](https://aiagentbase.app/skills) — The Community-Driven AI Skills Marketplace

---

## 📖 What Are Agent Skills?

**Agent Skills** are folders containing a `SKILL.md` file with instructions and metadata that teach Claude how to perform specialized tasks. Skills follow the open [Agent Skills Standard](https://agentskills.io/specification) by Anthropic.

```
Without Skill:  Generic AI → Average output
With Skill:     Expert Python Developer → Production-grade code ✨
```

### Skill Format

Each skill is a folder with a `SKILL.md` file:

```
skill-name/
├── SKILL.md          # Required: YAML frontmatter + instructions
├── scripts/          # Optional: executable code
├── references/       # Optional: documentation
└── assets/           # Optional: templates, resources
```

```markdown
---
name: skill-name
description: What it does and when to use it
license: CC0-1.0
metadata:
  author: github-username
  version: "1.0"
---

# Instructions for Claude go here
```

---

## 📂 Skill Catalog

### 💻 Coding & Development

| Skill | Description | Author |
|---|---|---|
| [senior-python-developer](./skills/senior-python-developer/) | Expert Python coding with type hints, async, testing & clean architecture | [skillsdirectory](https://github.com/skillsdirectory) |
| [nextjs-expert](./skills/nextjs-expert/) | Next.js 14+ App Router, RSC, Server Actions, TypeScript | [skillsdirectory](https://github.com/skillsdirectory) |
| [code-reviewer](./skills/code-reviewer/) | Thorough code reviews for bugs, security & performance | [skillsdirectory](https://github.com/skillsdirectory) |

### ✍️ Writing & Content

| Skill | Description | Author |
|---|---|---|
| [seo-blog-writer](./skills/seo-blog-writer/) | SEO-optimized blog posts with keyword strategy & structure | [skillsdirectory](https://github.com/skillsdirectory) |
| [technical-writer](./skills/technical-writer/) | Clear technical docs with API references & tutorials | [skillsdirectory](https://github.com/skillsdirectory) |

### 📊 Business & Strategy

| Skill | Description | Author |
|---|---|---|
| [business-plan-writer](./skills/business-plan-writer/) | Investor-ready business plans with financial projections | [skillsdirectory](https://github.com/skillsdirectory) |
| [market-research-analyst](./skills/market-research-analyst/) | Deep market analysis with competitor insights & TAM sizing | [skillsdirectory](https://github.com/skillsdirectory) |

### 🎨 Design & UX

| Skill | Description | Author |
|---|---|---|
| [ui-ux-advisor](./skills/ui-ux-advisor/) | Design feedback with accessibility, usability & modern patterns | [skillsdirectory](https://github.com/skillsdirectory) |

### 🛡️ DevOps & Security

| Skill | Description | Author |
|---|---|---|
| [devops-engineer](./skills/devops-engineer/) | Docker, K8s, CI/CD pipelines & cloud infrastructure | [skillsdirectory](https://github.com/skillsdirectory) |
| [security-auditor](./skills/security-auditor/) | OWASP Top 10 analysis, vulnerability scanning & remediation | [skillsdirectory](https://github.com/skillsdirectory) |

---

## 🔧 How to Use These Skills

### In Claude Code
```bash
# Clone this repo locally
git clone https://github.com/skillsdirectory/claude-skills.git

# Reference a skill in your project
# Claude will automatically detect SKILL.md files in your project
cp -r claude-skills/skills/senior-python-developer ./skills/
```

### In Claude.ai
1. Go to **Project Settings** → **Skills**
2. Upload the `SKILL.md` file from any skill folder
3. Claude will now follow those instructions

### In Claude API
Use the Skills API to attach skills to your conversations programmatically.

---

## 📈 Stats

| Metric | Count |
|---|---|
| Total Skills | 10 |
| Categories | 5 |
| Format | Agent Skills Standard (SKILL.md) |
| Spec | [agentskills.io](https://agentskills.io) |

---

## 🤝 How to Contribute

We welcome community skills! Follow the official [Agent Skills Standard](https://agentskills.io/specification).

### Quick Steps

1. ⭐ **Star this repo** (helps others find it!)
2. 🍴 **Fork** this repository
3. 📁 **Create a folder** in `skills/` with your skill name (lowercase, hyphens)
4. 📝 **Add a `SKILL.md`** file following the [template](./template/SKILL.md)
5. 📤 **Submit a Pull Request**

👉 **Full guidelines:** [CONTRIBUTING.md](CONTRIBUTING.md)

### SKILL.md Template

```markdown
---
name: your-skill-name
description: Clear description of what this skill does and when to use it
license: CC0-1.0
metadata:
  author: your-github-username
  version: "1.0"
  category: coding
---

# Your Skill Name

[Detailed instructions for Claude]
```

### Naming Rules (from agentskills.io spec)
- ✅ Lowercase only: `senior-python-developer`
- ✅ Hyphens for spaces: `seo-blog-writer`
- ✅ 1-64 characters
- ❌ No uppercase: ~~`Senior-Python`~~
- ❌ No consecutive hyphens: ~~`seo--blog`~~
- ❌ Can't start/end with hyphen: ~~`-python-`~~

---

## 🔗 Related Projects

| Project | Description |
|---|---|
| [anthropics/skills](https://github.com/anthropics/skills) | Official Anthropic skills repository |
| [agentskills.io](https://agentskills.io) | Agent Skills specification |
| [awesome-ai-skills](https://github.com/skillsdirectory/awesome-ai-skills) | Skills for all AI tools (Cursor, Windsurf, Copilot) |
| [mcp-servers-hub](https://github.com/skillsdirectory/mcp-servers-hub) | MCP servers directory |

---

## 📄 License

All community skills in this repository are licensed under [CC0 1.0 Universal](LICENSE) — free to use, modify, and share.

---

## ⚖️ Disclaimer

> **This is an independent, community-maintained project.**
>
> - This repository is **NOT** affiliated with, endorsed by, sponsored by, or associated with **Anthropic, PBC** or any of its products, including Claude, Claude Code, or Claude API.
> - **"Claude"** and **"Anthropic"** are trademarks of **Anthropic, PBC**. Use of these names in this repository is solely for the purpose of describing compatibility and is considered nominative fair use.
> - The **Agent Skills Standard** and **agentskills.io** specification is an open standard. This repository implements that standard independently.
> - All skills in this repository are **original community contributions** licensed under CC0 1.0. They are not derived from or copies of Anthropic's proprietary or official skills.
> - References to any third-party products, services, or companies (including but not limited to Anthropic, OpenAI, Google, Microsoft, Cursor, Windsurf, GitHub Copilot, VS Code) are for **informational and compatibility purposes only** and do not imply any affiliation, endorsement, or sponsorship.
> - This repository and its maintainers make **no warranties** regarding the quality, accuracy, or fitness of any skills listed herein. Use at your own risk.
> - **Individual contributors** are responsible for the content they submit. Maintainers review submissions but do not guarantee their correctness.

---

<p align="center">
  <strong>🌟 Found this useful? Give us a ⭐ Star!</strong>
  <br /><br />
  <a href="https://aiagentbase.app/skills">
    <img src="https://img.shields.io/badge/🚀_Explore_Skills_Marketplace-AiAgentBase.app-FF6B35?style=for-the-badge" alt="AiAgentBase" />
  </a>
</p>
