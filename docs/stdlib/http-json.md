# HTTP and JSON

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

Handlers receive a request map:

```alef
request["method"]
request["path"]
request["headers"]
request["query"]
request["params"]
request["body"]
```

## Responses

```alef
json_response(json_encode({ "ok" => true }))
problem_response(404, "not_found", "missing", "req-1")
html("<h1>Hello</h1>")
```

## JSON

```alef
let body = json_encode({ "items" => [1, 2, 3] })
let value = json_decode(body)
println(value["items"][0])
```
