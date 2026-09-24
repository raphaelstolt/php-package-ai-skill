---
name: php-composer-package-architect-skill
description: An AI skill that designs, scaffolds, and evolves high-quality PHP Composer packages using test-first, PSR-compliant, and maintainable architecture patterns.
---

# PHP Composer package architect skill

## Purpose

This skill enables an AI agent to **design, generate, and evolve production-quality PHP Composer packages** using modern standards and test-driven practices.

It is optimised for:
- Symfony Console based CLI tools
- Laravel packages if desired
- Developer tooling
- Static analysis utilities
- OSS-friendly architecture

## Project context discovery

Before implementing or extending a PHP package, inspect the existing project context before making implementation
decisions.

### Read the README

If a `README.md` exists, read it before implementing the requested feature.

Use it to understand:

* the package's purpose and scope
* documented features and supported use cases
* public APIs, CLI commands, and configuration
* documented behaviour and constraints
* terminology used by the project
* installation and usage patterns
* examples that should remain valid
* documented development or contribution workflows

Treat the README as an important source of project intent. Do not introduce behaviour that contradicts documented
functionality without first considering whether the README or implementation needs to be updated.

### Inspect Composer development dependencies

Read the `require-dev` section of `composer.json` before choosing development tools or adding new dependencies.

Use existing development dependencies to identify the project's established tooling, such as:

* PHPUnit or another test framework
* PHPStan, Psalm, or other static-analysis tools
* PHP-CS-Fixer, PHP_CodeSniffer, Pint, or other coding-standard tools
* Rector or migration/refactoring tools
* Infection or other mutation-testing tools
* documentation or API-generation tools
* CLI/testing utilities
* project-specific development plugins

Prefer existing project tooling over introducing an additional tool when it can reasonably solve the task.

For example, if the project already uses PHPUnit, write tests using PHPUnit rather than introducing another test framework.
If a static analyser or coding-standard tool is already configured, follow its existing configuration and conventions.

### Preserve existing project conventions

The goal is to extend the project consistently, not to impose a generic toolchain or architecture.

Before implementing:

1. Read `README.md`, if present.
2. Read `composer.json`, including `require-dev`, scripts, and relevant `extra` configuration.
3. Inspect existing tests and representative source files.
4. Identify the project's established tools, conventions, and architecture.
5. Reuse those conventions when implementing the requested change.

Do not add a new dependency, framework, testing library, or development tool merely because the skill recommends it.
The existing project context takes precedence where it is compatible with the requested feature and the package's stated
goals.

If the README, `composer.json`, source code, and tests appear to disagree, investigate the discrepancy before making
assumptions.

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
   - Executable binary in `bin/` for CLI applications

5. **PSR Compliance**
   - PSR-4 autoloading
   - PSR-12 formatting

6. **Maintainability**
   - Prefer composition over inheritance
   - Use value and data transfer objects where appropriate
   - Keep a CHANGELOG

## Default directory structure

### Filesystem standard
- The package's filesystem structure should follow the [PDS skeleton](https://github.com/php-pds/skeleton?tab=readme-ov-file#summary) standard.

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
    ├── CONTRIBUTING.md
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
- Format and lint code via code formatters|linters like Mago or PHP CS Fixer

## Distribution rules

The Composer package should only ship or contain required files. This can be achieved via a `.gitattributes` files. An
negated export-ignore approach is to be preferred.

In case the Composer package is a CLI application, its version should be in sync with the Git tag and changelog entry.

The Composer package declaration should be validated via `composer validate --strict`.

---

# Prompt templates

These are **copy-paste ready prompts** that work with Claude, ChatGPT, Copilot Chat, or agent frameworks.

---

## Template A — New package scaffold

```
You are acting as the PHP package architect skill.

Design and generate a PHP Composer package with the following specification:

Package Name: {{vendor}}/{{package}}
Description: {{description}}
Keywords:  {{a list of package describing keywords}}
PHP Version: {{php_version|^8.2}}
Type: {{cli|library}}
License: {{license|MIT}}

Requirements:
- Use PSR-4 autoloading
- Follow PSR-12
- Include PHPUnit or PEST and PHPStan on level 8
- Use Symfony Console for a CLI application
- Use Mago or PHP CS Fixer for code formatting and linting
- Pass `composer validate --strict`

Output:
- composer.json
- Directory structure
- Base classes
- Example test
- README.md
- LICENSE.md
- CONTRIBUTING.md
- .gitattributes
- mago.toml or .php-cs-fixer.php

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
- For a CLI application with PHPUnit as the testing framework, use `zenstruck/console-test` for integration tests
```
