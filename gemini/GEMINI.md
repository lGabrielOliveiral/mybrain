## Approach
- Read existing files before writing. Don't re-read unless changed.
- Thorough in reasoning, concise in output.
- Skip files over 100KB unless required.
- No sycophantic openers or closing fluff.
- No emojis or em-dashes.
- Do not guess APIs, versions, flags, commit SHAs, or package names. Verify by reading code or docs before asserting.

## Style Guide

### Formatting
- Use Markdown tables for itemized lists (e.g., "features", "parameters", "notes").
- Do not use HTML `<ul>` or `<ol>` tags.
- Do not use bullet points (`*`, `-`) for lists.
- Do not use emojis, unless explicitly requested.

### Code & Commands
- Use Markdown code blocks for all commands and code snippets.
- Specify the language for the code block (e.g., ```bash, ```python).
- Do not use backticks for inline code. Use full code blocks even for short commands.

### Reasoning & Language
- Use clear, direct, and professional language.
- Be concise and avoid unnecessary jargon or filler words.
- Organize reasoning into logical steps or bullet points for readability.
- Do not use self-deprecating humor or phrases like "I'm not sure" unless factually correct.

## Skills Integration
- This repository contains specialized skills in `gemini/skills/`.
- Always consult the `SKILL.md` file for the relevant skill before performing tasks related to:
    - Obsidian Markdown (`.md`): `gemini/skills/obsidian-markdown/SKILL.md`
    - Obsidian Bases (`.base`): `gemini/skills/obsidian-bases/SKILL.md`
    - JSON Canvas (`.canvas`): `gemini/skills/json-canvas/SKILL.md`
    - Obsidian CLI operations: `gemini/skills/obsidian-cli/SKILL.md`
    - Web content extraction: `gemini/skills/defuddle/SKILL.md`