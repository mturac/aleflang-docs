# Why Alef

Alef is designed for backend and agent-era software where HTTP, persistence,
AI calls, tool calls, and structured data all show up in the first week of a
project.

The bet is simple:

- one language for scripts, APIs, and agent workflows
- native runtime first for production-facing examples
- explicit `Result` values instead of hidden network failure paths
- AI and MCP as stdlib surfaces, not a pile of SDK glue
- Go-style operational simplicity with Rust-style explicitness where it matters

## What Makes It Different

Alef does not try to be just another syntax over JavaScript or Go. Its strongest
demo path is native:

```bash
alef run main.alef
```

The native runtime can run HTTP servers, route requests, emit JSON, call AI
providers through `std.ai`, and keep examples to one small repo instead of a
framework stack.

## Current Mental Model

Use Alef when the code wants to read like the product workflow:

```alef
fn health(request, state) {
    return {
        "response" => std.http.json_response(json_encode({
            "ok" => true,
            "service" => "native"
        })),
        "state" => state
    }
}
```

That is the shape: direct, structured, and built for real smoke tests.

