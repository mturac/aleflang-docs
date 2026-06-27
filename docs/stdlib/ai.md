# AI Providers

Alef treats AI provider calls as a standard-library surface.

## Deterministic Stub

Use `stub` in docs and tests:

```alef
fn main() {
    let r = std.ai.response_with("stub", "Summarize this ticket")
    println(r.provider)
    println(r.text)
}
```

The stub provider makes examples runnable without credentials.

## Configured Provider

```alef
let r = std.ai.response("Summarize this ticket")
```

Use environment variables to configure live providers.

## Named Providers

```alef
let r = std.ai.response_with("ollama", "hello")
let r = std.ai.response_with("minimax", "hello")
let r = std.ai.response_with("mimo", "hello")
```

Provider availability is environment-gated. A skipped live provider check is
not a failure unless the task explicitly requires that provider.
