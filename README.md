# Alef Documentation

Alef is an AI-native programming language for backend services, tools, and
agent workflows. It keeps the first production slice small: one language, one
runtime command, built-in HTTP, JSON, database, cache, AI provider calls, and
smoke-testable examples.

```alef
fn main() {
    println("Hello from Alef")
}
```

```bash
alef run main.alef
```

## Why Alef Exists

Modern backend work rarely stops at request handling. A real product quickly
needs structured JSON, state, background work, provider calls, internal tools,
AI workflows, and smoke tests. Alef puts those surfaces in the language and
standard library instead of asking every repo to assemble them from scratch.

Alef aims to feel familiar:

- Go-style project and CLI simplicity
- Rust-style explicit `Result` values for operations that can fail
- TypeScript/Python-like readability for product code
- native HTTP and AI surfaces as first-class standard library modules

## Read First

1. [Quickstart](docs/getting-started/quickstart.md)
2. [Language Tour](docs/language/tour.md)
3. [Build TicketDesk UI](docs/tutorials/ticketdesk-ui.md)
4. [HTTP and JSON](docs/stdlib/http-json.md)
5. [AI Providers](docs/stdlib/ai.md)

## Documentation Shape

This repository is structured for GitBook:

- `README.md` is the landing page.
- `SUMMARY.md` defines the navigation.
- `docs/**.md` contains the guide, tutorials, cookbook, and reference pages.

Every page is plain Markdown, so the docs are readable in GitHub and ready to
sync into GitBook.
