# Standard Library

Alef's standard library is designed around real backend and agent workflows.

## HTTP

Use `std.http` for native servers and clients.

```alef
import std.http { html, json_response, problem_response }
```

Common server helpers:

- `std.http.app()`
- `std.http.with_state(app, state)`
- `std.http.route(app, method, path, handler)`
- `std.http.listen_options(address, app, options)`
- `html(body)`
- `json_response(body)`
- `problem_response(status, code, message, request_id)`

## JSON

```alef
let body = json_encode({ "ok" => true })
let value = json_decode(body)
```

## AI

```alef
let r = std.ai.response_with("stub", "Summarize this ticket")
println(r.provider)
println(r.text)
```

Use `stub` for deterministic tests. Use configured providers for live runs.

## Database

Alef native examples use `std.db` for SQLite-backed flows:

```alef
import std.db { connect, exec, query }
```

## Cache

```alef
import std.cache { make, get, set }
```

## View And HTML

For full template rendering, use `std.view`. For compact public examples,
server-rendered strings plus `std.http.html` keep the repo small and runnable.

