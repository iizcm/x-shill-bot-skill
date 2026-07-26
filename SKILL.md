---
name: x-shill-bot
description: "Automate posting or shilling to multiple X (Twitter) accounts on a schedule. Critical hard-won facts about X Free API being read-only and browser-cookie auth being required. Use when the user has several X accounts and wants scheduled shill posts, e.g. every 6 hours."
version: 1.0.0
author: Community
license: MIT
platforms: [linux, macos, windows]
tags: [general]
---

# X Shill Bot — Skill

Automate posting or shilling to multiple X (Twitter) accounts on a schedule. Critical hard-won facts about X Free API being read-only and browser-cookie auth being required. Use when the user has several X accounts and wants scheduled shill posts, e.g. every 6 hours.

## Install

```bash
cp -r <skill-name> ~/.hermes/skills/<skill-path>/
```

Or clone this repository:

```bash
git clone https://github.com/iizcm/x-shill-bot-skill.git ~/.hermes/skills/<skill-path>/
```

## Usage

Invoke your AI agent with a clear instruction matching this skill's purpose. The agent will route tasks to this skill when the instruction matches its description or trigger keywords.

Refer to `README.md` in this repository for:
- Detailed step-by-step installation guide
- Bilingual documentation (English + Indonesian)
- Troubleshooting table
- Security best practices
- Customization tips

## Safety rules

- Never commit private keys, seed phrases, API tokens, or personal data to version control
- Use placeholders (`<YOUR_...>`) in all examples and code snippets
- Validate all outputs before acting on them
- Keep real credentials in your runtime's secure credential store only
