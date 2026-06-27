# What is Alef?

Alef is a programming language for production-facing backend and agent software.
Its default story is:

```bash
alef run main.alef
```

That command runs the native runtime. Public examples should target this path
unless they are specifically documenting the TypeScript interpreter or Go
codegen.

## Design Goals

Alef optimizes for a few concrete outcomes:

- a new developer can read the program top to bottom
- HTTP, JSON, database, cache, and AI provider code are standard-library work
- network and provider failures are visible as values
- examples are smoke-testable from the command line
- small teams can ship useful internal tools without scaffolding a framework

## A Tiny Backend

```alef
import std.http { json_response }

fn with_state(response, state) {
    return { "response" => response, "state" => state }
}

fn health(request, state) {
    return with_state(json_response(json_encode({
        "ok" => true,
        "runtime" => "native"
    })), state)
}

fn app() {
    let app = std.http.with_state(std.http.app(), {})
    return std.http.route(app, "GET", "/health", health)
}

fn main() {
    std.http.listen_options("127.0.0.1:8090", app(), {
        "shutdown_path" => "/__shutdown"
    })
}
```

## What Alef Is Not

Alef is not trying to be a thin syntax layer over an existing web framework.
The native runtime and standard library are part of the product.

Alef is also not a promise that every mature Go, Rust, Python, or .NET library
already has an equivalent. The current strength is a compact, integrated path
for backend services, AI workflows, and operational examples.
