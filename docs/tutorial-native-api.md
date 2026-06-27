# Tutorial: Build a Native API

This tutorial builds a tiny CRM API with Alef's native HTTP runtime.

## 1. Create `main.alef`

```alef
import std.http { json_response, problem_response }

fn with_state(response, state) {
    return { "response" => response, "state" => state }
}

fn initial_state() {
    return {
        "accounts" => [
            { "id" => "acct_ada", "name" => "Ada AI Studio", "stage" => "trial" },
            { "id" => "acct_turing", "name" => "Turing Logistics", "stage" => "active" }
        ]
    }
}
```

The state is just structured data. No framework setup is needed.

## 2. Add Handlers

```alef
fn health(request, state) {
    return with_state(json_response(json_encode({
        "ok" => true,
        "service" => "mini-crm",
        "accounts" => len(state["accounts"])
    })), state)
}

fn list_accounts(request, state) {
    return with_state(json_response(json_encode({
        "data" => state["accounts"]
    })), state)
}
```

Each handler receives `request` and `state`, then returns the next response and
state.

## 3. Add Route Params

```alef
fn find_account(accounts, id) {
    for account in accounts {
        if account["id"] == id {
            return account
        }
    }
    return null
}

fn get_account(request, state) {
    let account = find_account(state["accounts"], request["params"]["id"])
    if account == null {
        return with_state(problem_response(404, "not_found", "account not found", "crm"), state)
    }
    return with_state(json_response(json_encode({ "data" => account })), state)
}
```

Route params are exposed as `request["params"]`.

## 4. Build the App

```alef
fn app() {
    let app = std.http.with_state(std.http.app(), initial_state())
    let app = std.http.route(app, "GET", "/health", health)
    let app = std.http.route(app, "GET", "/api/accounts", list_accounts)
    return std.http.route(app, "GET", "/api/accounts/:id", get_account)
}
```

## 5. Listen

```alef
fn main() {
    std.http.listen_options("127.0.0.1:8097", app(), {
        "timeout_ms" => 30000,
        "max_body_bytes" => 4096,
        "shutdown_path" => "/__shutdown"
    })
}
```

Run:

```bash
alef run main.alef
```

Try:

```bash
curl http://127.0.0.1:8097/health
curl http://127.0.0.1:8097/api/accounts/acct_ada
curl http://127.0.0.1:8097/__shutdown
```

## What You Built

You now have:

- a native HTTP server
- JSON responses
- route params
- structured problem responses
- stateful request handling

That is enough to start a real API repo.

