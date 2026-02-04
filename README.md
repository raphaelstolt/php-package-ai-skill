## php-package-ai-skill

The `php-package-ai-skill` is a **structured AI skill** that teaches coding agents how to design and generate professional PHP Composer packages using modern PHP standards, test-driven workflows, and clean architecture.


It provides:
- A machine-readable **skill manifest**
- A human-readable **architecture and ruleset**
- **Prompt templates** for scaffolding and evolving packages
- A ready-to-use **Claude agent skill**


## Works With

- Claude (Custom Instructions / Agents)
- ChatGPT (System Prompts / Projects)
- GitHub Copilot Chat
- AI agent frameworks that support skills or system instructions

## Repository Structure

```bash
.ai/skills/ 
├── skill.json # Machine-readable manifest 
├── php-composer-package-architect.md # Human-readable skill spec + prompts
└── claude-php-package-architect.md # Claude system instruction skill
```

## How to use it

### Claude

1. Open Claude → Custom Instructions / Agent Settings
2. Paste the contents of `.ai/skills/claude-php-package-architect.md`
3. Start prompting using the templates in `.ai/skills/php-composer-package-architect.md`

## Example Prompt

You are a PHP package architect.

Create a CLI package called `stolt/env-sync-lint` that:

- Compares `.env` files

- Preserves comments and blank lines

- Has `diff`, `validate`, and `clean` commands

- Includes full PHPUnit test coverage

## License

This skill is licensed under the MIT license. Please see [LICENSE.md](LICENSE.md) for more details.