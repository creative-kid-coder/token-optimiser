# GitHub Copilot Instructions
# ============================================================
# FILE: .github/copilot-instructions.md
#
# This file is sent with EVERY Copilot request in this repo.
# Keep it SHORT and SPECIFIC. Every word here costs tokens.
# Target: under 300 tokens total.
#
# DELETE THIS COMMENT BLOCK before committing.
# ============================================================

## Project
<!-- One or two sentences. What does this repo do? -->
[PROJECT_NAME] is a [brief description, e.g. "Node.js REST API for order management"].

## Stack
<!-- List only. No prose. -->
- Language: [e.g. TypeScript 5.x]
- Runtime / Framework: [e.g. Node 20, Express 4]
- Database: [e.g. PostgreSQL via Prisma]
- Test runner: [e.g. Vitest]
- CI: [e.g. GitHub Actions]

## Code Conventions
<!-- Only rules that differ from language defaults. -->
- Use `async/await`; never raw `.then()` chains
- Named exports only; no default exports
- Errors: throw typed error classes, never plain strings
- No `any` in TypeScript — use `unknown` and narrow
- File naming: `kebab-case.ts`
- Function naming: `camelCase`
- Max function length: 40 lines — extract if longer

## Folder Structure
<!-- One line per key folder. Only include non-obvious ones. -->
- `src/` — application source
- `src/domain/` — pure business logic, no framework imports
- `src/infra/` — DB, HTTP, external service adapters
- `src/api/` — route handlers only
- `tests/` — mirrors src/ structure

## Testing
- Unit tests live next to source files as `*.test.ts`
- Integration tests in `tests/integration/`
- Mocks go in `tests/__mocks__/`
- Always test happy path + one error path minimum

## What Copilot Should NOT Do
- Do not suggest `console.log` in production code; use the `logger` service
- Do not use `var`; always `const` or `let`
- Do not import from `../../../`; use path aliases (`@domain/`, `@infra/`)
- Do not generate migration files; those are written manually
