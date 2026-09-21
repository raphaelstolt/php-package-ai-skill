## php-package-ai-skill

The `php-package-ai-skill` is a **structured AI skill** that teaches coding agents how to design and generate professional PHP Composer packages using modern PHP standards, test-driven workflows, and clean architecture.

It provides:
- A machine-readable **skill manifest**
- A human-readable **architecture and ruleset**
- **Prompt templates** for scaffolding and evolving packages
- A ready-to-use **Claude agent skill**

## Works with

- Claude (Custom Instructions / Agents)
- ChatGPT (System Prompts / Projects)
- GitHub Copilot Chat
- AI agent frameworks that support skills or system instructions

## Repository structure

```bash
tree .ai/skills
.ai/skills/ 
├── skill.json # Machine-readable manifest 
├── php-composer-package-architect.md # Human-readable skill spec + prompts
└── claude-php-package-architect.md # Claude system instruction skill
```

## How to use it

### With Claude

1. Open Claude → Custom Instructions / Agent Settings
2. Paste the contents of `.ai/skills/claude-php-package-architect.md`
3. Start prompting using the templates in `.ai/skills/php-composer-package-architect.md`

### With PHP

```bash
composer require --dev stolt/php-package-ai-skill
composer require --dev netresearch/composer-agent-skill-plugin
```

## Using with php-package-template

Want to build a PHP Composer package with AI while starting from a consistent, reusable project structure?

Combine [`php-package-ai-skill`](https://github.com/raphaelstolt/php-package-ai-skill) with [`php-package-template`](https://github.com/raphaelstolt/php-package-template)
to give your AI coding agent both a package architecture skill and a ready-to-use PHP package foundation.

* **php-package-template** provides the initial package structure and project conventions.
* **php-package-ai-skill** guides your AI coding agent through package design, implementation, testing, and quality practices.

Start by creating a repository from [`php-package-template`](https://github.com/raphaelstolt/php-package-template),
then use the `php-package-ai-skill` instructions to guide your AI agent in implementing and evolving the package.

This combination helps you move from a reusable package skeleton to a thoughtfully designed, tested, and maintainable
PHP Composer package.

## Example prompt

You are a PHP package architect.

Create a CLI package called `stolt/env-sync-lint` that:

- Compares `.env` files

- Preserves comments and blank lines

- Has a `diff`, `validate`, and `clean` command

- Includes full PHPUnit test coverage

## License

These skills are licensed under the MIT license. Please see [LICENSE.md](LICENSE.md) for more details.