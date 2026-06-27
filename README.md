# Documentation

Alef is an AI-native programming language for backend services, tools, and
agent workflows. It is designed to make programmers productive with one native
runtime command, readable product code, explicit failure handling, and standard
library surfaces for HTTP, JSON, database, cache, AI providers, and operational
smoke tests.

This page is the documentation portal. Start with the quickstart, then use the
guides, tutorials, references, and codewalks as your Alef programs grow.

## Getting Started

### [Installing Alef](docs/getting-started/installation.md)

Instructions for using Alef from a source checkout and configuring `ALEF_BIN`
for example repositories.

### [Quickstart](docs/getting-started/quickstart.md)

A brief Hello World tutorial that introduces `alef run`, functions, variables,
JSON, and the native runtime path.

### [Project Structure](docs/getting-started/project-structure.md)

How to organize a small Alef repository with `alef.mod`, `main.alef`, a README,
and a smoke script.

### [Language Tour](docs/language/tour.md)

A fast tour of values, functions, collections, branching, structs, results, and
native HTTP handlers.

## Using and Understanding Alef

### [What is Alef?](docs/what-is-alef.md)

The language goals, runtime story, and the kind of software Alef is meant to
make easier.

### [Effective Alef](docs/using/effective-alef.md)

Practical advice for writing clear Alef: prefer explicit results, keep examples
smoke-testable, use native-first docs, and avoid hiding provider failures.

### [Frequently Asked Questions](docs/using/faq.md)

Answers to common questions about the runtime, codegen path, AI provider
surface, and when to use maps versus structs.

### [Editor Plugins and IDEs](docs/using/editor-tools.md)

Editor and language-server expectations for Alef projects.

### [Diagnostics](docs/using/diagnostics.md)

How to use `alef health`, `alef doctor`, smoke scripts, and native runtime
checks to understand a failing program.

## Language Guide

### [Variables and Values](docs/language/variables.md)

Bindings, reassignment, common value kinds, and interpolation.

### [Functions](docs/language/functions.md)

Function declarations, typed signatures, early returns, and callback functions.

### [Arrays and Maps](docs/language/collections.md)

The everyday data structures for JSON-heavy backend and UI workflows.

### [Structs and Enums](docs/language/structs-enums.md)

Named data shapes, finite variants, and when stronger domain modeling helps.

### [Control Flow](docs/language/control-flow.md)

`if`, `for`, `while`, and `match`.

### [Results and Errors](docs/language/results-errors.md)

Explicit `Result` values, `?`, and native HTTP client failure handling.

## Tutorials

### [Build a Native API](docs/tutorials/native-api.md)

Build a small JSON API with stateful handlers and `std.http`.

### [Build TicketDesk UI](docs/tutorials/ticketdesk-ui.md)

Build a real multi-workspace ticket and task manager UI served by the native
runtime.

### [Build an AI Workflow](docs/tutorials/ai-workflow.md)

Build a support-ticket classifier with deterministic `std.ai` provider calls.

## References

### [Syntax Reference](docs/reference/syntax.md)

A compact reference for entrypoints, bindings, functions, arrays, maps, structs,
enums, imports, and control flow.

### [Command Documentation](docs/runtime/cli.md)

Reference for `alef run`, `alef build`, `alef test`, `alef health`, and
`alef doctor`.

### [Native Runtime](docs/runtime/native-runtime.md)

The production-facing runtime path, server options, and smoke-test surfaces.

### [Bytecode and JIT](docs/runtime/bytecode-jit.md)

When to use `--bytecode`, `--strict-bytecode`, and runtime feature checks.

### [alef.mod Reference](docs/reference/alef-mod.md)

The project module file format and public-repo conventions.

### [Release Notes](docs/reference/release-notes.md)

Release-oriented notes for native runtime behavior and public examples.

## Standard Library

### [Stdlib Overview](docs/stdlib/overview.md)

The high-level map of Alef's standard library surfaces.

### [HTTP and JSON](docs/stdlib/http-json.md)

Native HTTP servers, request maps, response helpers, problem responses, and
JSON encode/decode.

### [AI Providers](docs/stdlib/ai.md)

Deterministic stub calls, configured providers, named providers, and
credential-gated smoke patterns.

### [Database and Cache](docs/stdlib/db-cache.md)

SQLite-backed examples, query helpers, and small cache workflows.

## Accessing Databases

### [Accessing a Database](docs/database/accessing-databases.md)

Open a SQLite handle, execute SQL, query rows, and keep public examples
credential-free.

### [Database Smoke Tests](docs/database/database-smoke-tests.md)

How to write smoke tests that prove database-backed examples really persisted
state.

## Developing Modules

### [Developing Modules](docs/modules/developing-modules.md)

How to structure, name, and smoke-test a reusable Alef module or public example.

### [Publishing Example Repositories](docs/modules/publishing-examples.md)

Public repository conventions for Alef examples: README, `alef.mod`,
`scripts/smoke.sh`, portable paths, and no secrets.

## Codewalks

Guided tours of real Alef programs.

### [TicketDesk UI Codewalk](docs/codewalks/ticketdesk-ui.md)

Walk through the multi-workspace ticket manager example, from state shape to UI
actions and JSON verification.

### [Agent Ticket Router Codewalk](docs/codewalks/agent-ticket-router.md)

Walk through a small AI-assisted ticket routing workflow.

## GitBook

### [GitBook Publishing](docs/reference/gitbook-publishing.md)

How to import this repository into GitBook and keep navigation in sync with
`SUMMARY.md`.
