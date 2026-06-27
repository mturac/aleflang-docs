# HTTP and JSON

Alef's HTTP server API is small enough to remember.

## Minimal Server

```alef
import std.http { json_response }

fn with_state(response, state) {
    return { "response" => response, "state" => state }
}

fn health(request, state) {
    return with_state(json_response(json_encode({ "ok" => true })), state)
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

## Request Shape

Handlers receive a request map with useful fields:

```alef
request["method"]
request["path"]
request["headers"]
request["query"]
request["params"]
request["body"]
```

## JSON

```alef
let body = json_encode({ "ok" => true, "items" => [1, 2, 3] })
let value = json_decode(body)
println(value["items"][0])
```

## Problem Responses

```alef
import std.http { problem_response }

return with_state(
    problem_response(404, "not_found", "account not found", "req-1"),
    state
)
```

