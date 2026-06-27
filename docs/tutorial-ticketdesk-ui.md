# Tutorial: TicketDesk UI

This tutorial shows the shape of a real Alef app: a multi-workspace ticket and
task manager with a browser UI and JSON API.

The full example lives in the `alef-ticketdesk-ui` style repo. The important
idea is that the UI is served by Alef itself: no React build, no backend
framework, no second process.

## 1. Model Workspaces

```alef
fn workspace_seed() {
    return [
        { "id" => "ops", "name" => "Ops Desk", "lead" => "Ada", "sla" => "4h" },
        { "id" => "product", "name" => "Product Bugs", "lead" => "Grace", "sla" => "1d" },
        { "id" => "success", "name" => "Customer Success", "lead" => "Leyla", "sla" => "8h" }
    ]
}
```

## 2. Model Tickets

```alef
fn ticket_seed() {
    return [
        {
            "id" => "TD-101",
            "workspace" => "ops",
            "title" => "Checkout API timeout",
            "customer" => "Northwind",
            "status" => "triage",
            "priority" => "P0",
            "assignee" => "ada"
        }
    ]
}
```

## 3. Keep State In The Server

```alef
fn initial_state() {
    return {
        "workspaces" => workspace_seed(),
        "tickets" => ticket_seed(),
        "events" => ["TD-101 opened by support intake"],
        "selected" => "ops"
    }
}
```

Alef handlers return both `response` and the next `state`.

```alef
fn with_state(response, state) {
    return { "response" => response, "state" => state }
}
```

## 4. Render A UI

```alef
import std.http { html }

fn page(request, state) {
    let body = "<!doctype html><html><body><h1>Alef TicketDesk</h1></body></html>"
    return with_state(html(body), state)
}
```

The real example builds columns, cards, workspace navigation, actions, and an
activity feed with the same pattern.

## 5. Add Actions

```alef
fn move_ticket(request, state) {
    let id = request["params"]["id"]
    let status = request["params"]["status"]
    let tickets = []

    for ticket in state["tickets"] {
        if ticket["id"] == id {
            tickets.push({
                "id" => ticket["id"],
                "workspace" => ticket["workspace"],
                "title" => ticket["title"],
                "status" => status,
                "priority" => ticket["priority"],
                "assignee" => ticket["assignee"]
            })
        } else {
            tickets.push(ticket)
        }
    }

    let next = {
        "workspaces" => state["workspaces"],
        "tickets" => tickets,
        "events" => state["events"],
        "selected" => state["selected"]
    }
    return with_state(html("<p>updated</p>"), next)
}
```

Route params come from `request["params"]`.

## 6. Wire Routes

```alef
fn app() {
    let app = std.http.with_state(std.http.app(), initial_state())
    let app = std.http.route(app, "GET", "/", page)
    let app = std.http.route(app, "GET", "/workspace/:id", workspace_page)
    let app = std.http.route(app, "GET", "/move/:id/:status", move_ticket)
    return std.http.route(app, "GET", "/api/tickets", tickets_json)
}
```

## 7. Listen

```alef
fn main() {
    std.http.listen_options("127.0.0.1:8097", app(), {
        "timeout_ms" => 30000,
        "shutdown_path" => "/__shutdown"
    })
}
```

## What This Proves

The example is a real UI slice:

- multiple workspaces
- multiple ticket statuses
- assignment actions
- state mutation
- activity feed
- JSON API verification
- localhost smoke test

That is the public-example bar for Alef: not a fake screenshot, a runnable
workflow.

