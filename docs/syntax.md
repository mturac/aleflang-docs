# Syntax Guide

This page is a practical Alef syntax tour. It is written for people who want to
open a file and ship something, not memorize a grammar.

## Hello World

```alef
fn main() {
    println("Merhaba Alef")
}
```

Run:

```bash
alef run main.alef
```

## Variables

```alef
fn main() {
    let name = "Ada"
    let count = 3
    let ready = true

    println("{name} has {count} tasks")
}
```

Alef uses `let` for local bindings. Existing runtime examples also reassign
locals when a workflow needs it:

```alef
let status = "open"
status = "done"
```

## Functions

```alef
fn add(a, b) {
    return a + b
}

fn main() {
    println(add(2, 3))
}
```

Typed signatures are supported where the program benefits from them:

```alef
fn divide(a: f64, b: f64) -> Result<f64, string> {
    if b == 0.0 {
        return Err("division by zero")
    }
    return Ok(a / b)
}
```

## Strings

Alef supports interpolation in strings:

```alef
fn main() {
    let service = "mini-crm"
    println("{service} is live")
}
```

Useful methods:

```alef
let text = "API timeout".to_lower()
let urgent = text.contains("timeout")
let parts = "a,b,c".split(",")
```

## Arrays

```alef
fn main() {
    let items = ["alpha", "beta"]
    items.push("gamma")

    for item in items {
        println(item)
    }
}
```

Common helpers:

```alef
len(items)
items.len()
items[0]
items.map(fn(x) { return x.to_upper() })
```

## Maps

Maps use `=>` for key/value pairs:

```alef
let account = {
    "id" => "acct_ada",
    "name" => "Ada AI Studio",
    "stage" => "trial"
}

println(account["name"])
```

Maps are the most common shape for JSON and HTTP payloads.

## Structs

```alef
struct Task {
    id: string,
    title: string,
    done: bool
}

fn main() {
    let task = Task {
        id: "task_1",
        title: "Ship docs",
        done: false
    }
    println(task.title)
}
```

## Enums and Match

```alef
enum Shape {
    Circle(f64),
    Rect(f64, f64),
    Point,
}

fn area(s: Shape) -> f64 = match s {
    Circle(r) => 3.14159 * r * r,
    Rect(w, h) => w * h,
    Point => 0.0,
}
```

Use `match` when variants matter. Use `if` chains for simple string routing.

## Conditionals

```alef
fn priority(plan, queue) {
    if plan == "enterprise" {
        return "p1"
    }
    if queue == "platform" {
        return "p2"
    }
    return "p3"
}
```

Boolean operators:

```alef
if queue == "platform" and text.contains("timeout") {
    return "incident"
}
```

## Loops

```alef
for ticket in tickets {
    println(ticket["id"])
}

let i = 0
while i < 10 {
    println(i)
    i = i + 1
}
```

## Result and Option

Alef uses explicit success/failure values:

```alef
fn divide(a: f64, b: f64) -> Result<f64, string> {
    if b == 0.0 {
        return Err("division by zero")
    }
    return Ok(a / b)
}
```

The `?` operator unwraps `Ok(value)` or early-returns on `Err(error)`:

```alef
let x = divide(20.0, 4.0)?
let y = divide(x, 2.0)?
```

For native HTTP client calls, unwrap or match the result:

```alef
match std.http.get("https://example.com") {
    Ok(r) => println(r.body),
    Err(e) => println("request failed: {e}"),
}
```

## Imports

```alef
import std.http { json_response, problem_response }
import std.ai { complete_with }
```

You can also use qualified names:

```alef
std.http.listen_options(address, app(), options)
```

## JSON

```alef
let payload = {
    "ok" => true,
    "items" => [1, 2, 3]
}

let body = json_encode(payload)
let decoded = json_decode(body)
println(decoded["items"][0])
```

## HTTP Server Shape

Handlers return a map with `response` and `state`:

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
    std.http.listen_options("127.0.0.1:8097", app(), {
        "shutdown_path" => "/__shutdown"
    })
}
```

## AI Provider Shape

```alef
fn main() {
    let r = std.ai.response_with("stub", "Summarize this ticket")
    println(r.provider)
    println(r.text)
}
```

The `stub` provider is deterministic and useful for docs, tests, and CI.

