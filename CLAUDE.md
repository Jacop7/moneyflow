# CLAUDE.md

This file provides guidance for AI assistants working on the MoneyFlow repository.

## Project Overview

MoneyFlow is a newly initialized project. The repository is in its earliest stage with no application code, build system, or dependencies configured yet.

## Repository Structure

```
moneyflow/
├── CLAUDE.md          # AI assistant guidance (this file)
└── README.md          # Project README
```

## Current State

- **Status**: Greenfield project — no source code, dependencies, or configuration exist yet.
- **Branch**: `master` is the default branch.
- **History**: Single initial commit.

## Development Guidelines

Since this project is starting from scratch, the following guidelines should be applied as the codebase grows:

### General Conventions

- Keep commits focused and atomic with clear, descriptive messages.
- Prefer simple, minimal implementations over over-engineered solutions.
- Do not introduce dependencies without a clear need.
- Follow the principle of least surprise in API and interface design.

### When Adding Code

- Establish and follow a consistent directory structure from the first files onward.
- Add a `.gitignore` appropriate for the chosen tech stack before committing generated or environment files.
- Include a `.env.example` if environment variables are used — never commit `.env` files or secrets.
- Set up linting and formatting configuration early to enforce consistency.
- Add tests alongside new functionality.

### When Making Changes

- Read existing code before modifying it.
- Do not refactor or "improve" code beyond what the task requires.
- Do not add comments, docstrings, or type annotations to code you did not change.
- Avoid backwards-compatibility shims — if something is unused, remove it.

## Commands

No build, test, or lint commands are configured yet. Update this section as tooling is added.

<!-- Example (update when applicable):
```
npm install          # Install dependencies
npm run dev          # Start development server
npm run build        # Production build
npm test             # Run test suite
npm run lint         # Run linter
```
-->
