# Alef Documentation

Alef is an AI-native programming language for backend services, tools, and
agent workflows. The native runtime gives you HTTP, JSON, database, AI, MCP,
media, and operational smoke-test surfaces without starting from a framework
stack.

This repository is structured for GitBook:

- `README.md` is the landing page.
- `SUMMARY.md` is the GitBook table of contents.
- `docs/*.md` pages are plain Markdown.

## Quick Start

```alef
fn main() {
    println("Hello from Alef")
}
```

```bash
alef run main.alef
```

## What To Read First

1. [Syntax Guide](docs/syntax.md) for language basics.
2. [CLI and Project Setup](docs/cli-projects.md) for running files and example repos.
3. [Tutorial: TicketDesk UI](docs/tutorial-ticketdesk-ui.md) for a real multi-workspace app.
4. [HTTP and JSON](docs/http-json.md) for native backend work.
5. [Standard Library](docs/stdlib.md) for the built-in surfaces.

## Local Preview

Any Markdown viewer works. For GitBook, import the repository and use
`SUMMARY.md` as the table of contents.
