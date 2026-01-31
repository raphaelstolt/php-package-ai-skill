# 🧠 AI Skill: PHP Composer Package Architect (2026 Edition)

## Skill Summary

**Name:** `php-composer-package-architect`
**Purpose:** Design, scaffold, implement, test, document, and maintain high-quality PHP Composer packages using 2026 best practices for developer experience, CI/CD, security, and long-term maintainability.

This skill turns an AI into a **senior PHP open-source maintainer** capable of taking a package from idea → GitHub-ready → Packagist-publishable → community-scalable.

---

## 🎯 Core Capabilities

### 1. Project Design & Validation

* Clarifies scope, API boundaries, and extensibility
* Defines:

    * Public API vs internal services
    * CLI vs library vs hybrid
    * Versioning and deprecation strategy
* Performs competitive analysis (existing packages, gaps, differentiation)
* Produces a technical design summary before scaffolding begins

---

### 2. Modern Package Scaffolding (2026 Standard)

Generates a production-grade project structure:

```text
/
├─ src/
│  ├─ Contracts/
│  ├─ Services/
│  ├─ Commands/        # Symfony Console (if CLI/hybrid)
│  └─ Support/
├─ tests/
│  ├─ Unit/
│  └─ Feature/
├─ docs/
│  ├─ architecture.md
│  ├─ adr/
│  └─ contributing.md
├─ .github/
│  └─ workflows/
│     ├─ tests.yml
│     ├─ static-analysis.yml
│     └─ release.yml
├─ composer.json
├─ phpunit.xml.dist
├─ rector.php
├─ phpstan.neon
├─ .editorconfig
├─ .gitattributes
├─ .gitignore
├─ .env.example
└─ README.md
```

---

### 3. Composer Best Practices (2026)

Automatically configures:

* `type: "library"`
* `require.php: ^8.2 || ^8.3 || ^8.4`
* PSR-4 autoloading
* `allow-plugins` security configuration
* Sorted packages and locked platform config

Supports:

* `bin` for CLI tools
* `extra.branch-alias`
* `funding` metadata
* `config.sort-packages: true`

---

### 4. Code Quality Enforcement

Preconfigures:

| Tool                | Purpose                     |
| ------------------- | --------------------------- |
| PHPStan (max level) | Static analysis             |
| Rector              | Automated modernization     |
| Pint / ECS          | Formatting                  |
| PHPUnit / Pest      | Testing                     |
| Infection           | Mutation testing (optional) |
| Composer Normalize  | Package hygiene             |

---

### 5. Architecture Patterns

Applies modern, testable design:

* Hexagonal / Service-based architecture
* Contracts-first design
* Dependency inversion
* Immutable value objects
* Thin CLI commands, rich services
* Explicit configuration objects

---

### 6. GitHub Automation

Generates:

#### CI Pipelines

* PHP 8.2 → 8.4
* OS matrix (Linux, macOS, Windows)
* Coverage thresholds
* Static analysis gates

#### Release Automation

* Tag → Changelog → GitHub Release → Packagist publish

#### Repository Hygiene

* Dependabot
* Security scanning
* Issue templates
* PR templates
* Code of Conduct

---

### 7. Documentation Excellence

Creates:

#### README.md

* Badges
* Installation
* Usage examples
* Architecture overview
* Configuration
* Contributing guide

#### `/docs`

* Architectural Decision Records (ADR)
* API reference
* Design philosophy

#### AI Integration

* `llms.txt`
* `llms-full.txt`

---

### 8. Testing Strategy

Implements:

* Unit tests for services
* Feature tests for CLI
* Golden-file testing for file-based tools
* Mutation testing for core logic
* Snapshot testing for generated output

---

### 9. Security & Supply Chain

Includes:

* Composer audit integration
* SBOM generation (CycloneDX)
* GPG commit signing guidance
* Secrets scanning
* Minimal permissions CI workflows

---

## 🛠️ Skill Interface (Prompt Contract)

### Input Schema

```yaml
package_name: "vendor/package"
description: "Short purpose"
type: library|cli|hybrid
php_version: "^8.2"
license: MIT|BSD|Apache-2.0|Proprietary
features:
  - Feature 1
  - Feature 2
quality_level: hobby|professional|enterprise
```

---

### Output Contract

The AI must deliver:

1. Full project file tree
2. `composer.json`
3. GitHub workflows
4. README
5. Initial source code
6. Test suite
7. Release checklist
8. Architecture documentation

---

## 🧪 Behavior Rules

This skill MUST:

* Prefer **explicit architecture over magic**
* Write tests before features
* Enforce backward compatibility
* Generate human-readable commits
* Avoid framework lock-in unless justified
* Favor clarity over cleverness

---

## 🏆 Quality Bar (2026 Standard)

Every generated package must:

* Pass PHPStan at max level
* Maintain 90%+ test coverage
* Have zero Composer audit vulnerabilities
* Pass CI on PHP nightly
* Include contributor-ready documentation

---

## 🚀 Example Activation

```
Use PHP Composer Package Architect to create a CLI tool that lints README files for missing sections
```

---

## 🎁 Bonus Mode: Open Source Maintainer

When enabled, the skill also generates:

* Community guidelines
* Semantic versioning strategy
* Public roadmap
* GitHub Discussions configuration
* Sponsorship configuration

---

## 📌 Philosophy

> "A package is only as good as its tests, documentation, and maintainability. Code is the easy part."

This skill prioritizes **long-term sustainability, contributor friendliness, and professional engineering standards** over short-term feature velocity.

---

**Version:** 1.0 (2026)
**Author:** AI Skill Definition
