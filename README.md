# no-inline-comment

> Install "no inline comment" coding rules for AI code editors and agents.

A CLI tool to quickly add strict comment policy rules to your project for various AI-powered code editors and assistants.

## What This Does

This package enforces a clean comment policy:

- **No inline/line-by-line comments** (e.g., `// do X`, `// set y`)
- **Use JSDoc** for documentation of functions, classes, and methods
- **No emojis** in comments or JSDoc
- **Comments only for truly complex logic** (rare cases)

## Installation

Run directly with npx (no install required):

```bash
npx no-inline-comment
```

Or install globally:

```bash
npm install -g no-inline-comment
```

## Usage

### Interactive Mode (Arrow Key Navigation)

```bash
npx no-inline-comment
```

Features:

- Use **Up/Down arrows** to navigate
- Press **Space** to toggle selection
- Press **A** to select all, **N** to select none
- Press **Enter** to confirm

### Install for Specific Editor (Project)

```bash
# Cursor (installs to current directory)
npx no-inline-comment cursor

# GitHub Copilot
npx no-inline-comment copilot

# Windsurf
npx no-inline-comment windsurf

# Claude Code
npx no-inline-comment claude

# And 30+ more editors...
```

### Install Globally (Home Directory)

Use `--global` or `-g` flag to install rules to your home directory:

```bash
# Cursor (installs to ~/)
npx no-inline-comment cursor --global

# All editors globally
npx no-inline-comment --all -g
```

### Install for All Editors

```bash
# Project scope (current directory)
npx no-inline-comment --all

# Global scope (home directory)
npx no-inline-comment --all --global
```

### List Supported Editors

```bash
npx no-inline-comment --list
```

### Options

| Option         | Description                                            |
| -------------- | ------------------------------------------------------ |
| `-g, --global` | Install to home directory instead of current directory |
| `-a, --all`    | Install for all supported editors                      |
| `-l, --list`   | List all supported editors                             |
| `-h, --help`   | Show help message                                      |

## Supported Editors/Agents (30+)

| Editor         | Config File                               |
| -------------- | ----------------------------------------- |
| Aider          | `CONVENTIONS.md`                          |
| Antigravity    | `.agent/skills/no-inline-comment.md`      |
| Claude Code    | `CLAUDE.md`                               |
| Cline          | `.clinerules`                             |
| CodeBuddy      | `.codebuddy/rules/no-inline-comment.md`   |
| Codex          | `AGENTS.md`                               |
| Command Code   | `.commandcode/rules/no-inline-comment.md` |
| Continue       | `.continue/rules/no-inline-comment.md`    |
| Crush          | `.crush/rules/no-inline-comment.md`       |
| Cursor         | `.cursor/rules/no-inline-comment.mdc`     |
| Droid          | `.droid/rules/no-inline-comment.md`       |
| Gemini CLI     | `GEMINI.md`                               |
| GitHub Copilot | `.github/copilot-instructions.md`         |
| Goose          | `.goose/rules/no-inline-comment.md`       |
| Junie          | `.junie/rules/no-inline-comment.md`       |
| Kilo Code      | `.kilocode/rules/no-inline-comment.md`    |
| Kiro CLI       | `.kiro/rules/no-inline-comment.md`        |
| Kode           | `.kode/rules/no-inline-comment.md`        |
| MCPJam         | `.mcpjam/rules/no-inline-comment.md`      |
| Moltbot        | `.moltbot/rules/no-inline-comment.md`     |
| Mux            | `.mux/rules/no-inline-comment.md`         |
| Neovate        | `.neovate/rules/no-inline-comment.md`     |
| OpenCode       | `.opencode/rules/no-inline-comment.md`    |
| OpenHands      | `.openhands/rules/no-inline-comment.md`   |
| Pi             | `.pi/rules/no-inline-comment.md`          |
| Pochi          | `.pochi/rules/no-inline-comment.md`       |
| Qoder          | `.qoder/rules/no-inline-comment.md`       |
| Qwen Code      | `.qwencode/rules/no-inline-comment.md`    |
| Roo Code       | `.roo/rules/no-inline-comment.md`         |
| Trae           | `.trae/rules/no-inline-comment.md`        |
| Windsurf       | `.windsurfrules`                          |
| Zed            | `.zed/rules/no-inline-comment.md`         |
| Zencoder       | `.zencoder/rules/no-inline-comment.md`    |

## The Rule

### Absolute Rules

- DO NOT add inline or line-by-line comments
- Prefer clear naming + small functions over comments
- Write JSDoc for exported functions/classes and public methods

### JSDoc Requirements

- Purpose (1 sentence)
- `@param` for each parameter
- `@returns` (or void)
- Important constraints

### Good Example

```ts
/**
 * Normalizes a user-provided phone number into E.164-like format.
 * @param input - Raw phone number string from UI.
 * @param defaultCountry - ISO country code used when input has no prefix.
 * @returns Normalized string or null if invalid.
 */
export function normalizePhone(
  input: string,
  defaultCountry: string
): string | null {
  // implementation...
}
```

### Bad Example

```ts
// get user
const user = await getUser(id);
// update user
user.name = name;
// save user
await saveUser(user);
```

## Contributing

Pull requests welcome! If you want to add support for a new editor, edit `bin/cli.js` and add the editor config to the `EDITORS` object.

## License

MIT
