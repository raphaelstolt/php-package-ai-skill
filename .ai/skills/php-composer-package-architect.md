---
name: php-composer-package-architect-skill
description: An AI skill that designs, scaffolds, and evolves high-quality PHP Composer packages using test-first, PSR-compliant, and maintainable architecture patterns.
---

# PHP Composer Package architect skill

## Purpose

This skill enables an AI agent to **design, generate, and evolve production-quality PHP Composer packages** using modern standards and test-driven practices.

It is optimised for:
- Symfony Console based CLI tools
- Laravel packages if desired
- Developer tooling
- Static analysis utilities
- OSS-friendly architecture

---

## Architectural principles

The AI must always:

1. **Design before coding**
   - Propose a minimal architecture
   - Identify services, commands, and responsibilities

2. **AI ready**
   - Add an AI skill to `.ai/skills/{{skill-name}}.md` for CLI applications

3. **Test-first implementation**
   - Generate PHPUnit or PEST tests before or alongside implementation

4. **Separation of concerns**
   - Business logic in `src/Service`
   - CLI wiring in `src/Command`

5. **PSR Compliance**
   - PSR-4 autoloading
   - PSR-12 formatting

6. **Maintainability**
   - Prefer composition over inheritance
   - Use value objects where appropriate
   - Keep a CHANGELOG

---

## Default Directory Structure

```
.
├── composer.json
├── .gitattributes
├── README.md
├── LICENSE.md
├── CHANGELOG.md
├── phpunit.xml.dist
├── phpstan.neon.dist
└── .ai/
    └── skills
       └── {{skill-name}}.md
└── bin/
    └── {{cli-application-name}}
├── src/
│   ├── Command/
│   ├── Service/
│   └── Support/
├── tests/
│   ├── Unit/
│   └── Integration/
└── .github/
    └── workflows/
        └── tests.yml
```

---

## Code quality rules

The AI must:
- Type all method signatures
- Use `declare(strict_types=1);`
- Avoid static state
- Prefer immutable data structures
- Add PHPDoc only when types cannot be expressed natively
- For Laravel packages, use the standards defined in https://github.com/spatie/boost-spatie-guidelines
- Exclude non dist files from the package archive via `.gitattributes`

---

# Prompt templates

These are **copy-paste ready prompts** that work with Claude, ChatGPT, Copilot Chat, or agent frameworks.

---

## Template A — New Package scaffold

```
You are acting as the PHP package architect skill.

Design and generate a PHP Composer package with the following specification:

Package Name: {{vendor}}/{{package}}
Description: {{description}}
PHP Version: {{php_version|^8.2}}
Type: {{cli|library}}
License: {{license|MIT}}

Requirements:
- Use PSR-4 autoloading
- Follow PSR-12
- Include PHPUnit or PEST and PHPStan on level 8
- Use Symfony Console for a CLI application

Output:
- composer.json
- Directory structure
- Base classes
- Example test
- README.md
- LICENSE.md
- .gitattributes

Explain the architecture briefly before generating code.
```

---

## Template B — Add a wew command

```
You are acting as the PHP package architect skill.

Add a new Symfony Console command with the following specification:

Command Name: {{command}}
Command Options: {{options}}
Purpose: {{purpose}}

Rules:
- Business logic must live in a Service class
- Command must only handle I/O
- Generate PHPUnit or PEST tests
- Add a `bin` entry to `composer.json`

Output:
- Service class
- Command class
- Integration and unit tests
- README and CHANGELOG update
```

---

## Template C — Refactor / Evolve architecture

```
You are acting as the PHP package architect skill.

Refactor the following package to meet these goals:

Goals:
{{goals}}

Constraints:
- Backwards compatible
- Tests must be updated
- An existing Changelog must be updated
- Maintain PSR-12

Output:
- Refactored files
- Updated tests
- Migration notes
- Updated Changelog
```

---

## Template D — Test generation

```
You are acting as the PHP package architect skill.

Generate PHPUnit or PEST tests for the following class:

{{code}}

Requirements:
- Use data providers where appropriate
- Cover edge cases
- Mock external dependencies
- For a CLI application with PHPUnit as the testing framework, use zenstruck/console-test for integration tests
```
