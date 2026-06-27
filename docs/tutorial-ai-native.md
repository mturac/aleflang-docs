# Tutorial: AI-Native Workflow

This tutorial builds a ticket router that uses ordinary Alef functions for
business logic and `std.ai` for the provider boundary.

## 1. Classify Input

```alef
fn contains_any(text, words) {
    for word in words {
        if text.contains(word) {
            return true
        }
    }
    return false
}

fn classify_ticket(ticket) {
    let text = (ticket["title"] + " " + ticket["body"]).to_lower()
    if contains_any(text, ["invoice", "payment", "refund"]) {
        return "billing"
    }
    if contains_any(text, ["login", "password", "2fa"]) {
        return "identity"
    }
    if contains_any(text, ["timeout", "error", "500"]) {
        return "platform"
    }
    return "general"
}
```

## 2. Add AI Summary

```alef
fn ai_summary(ticket, queue, priority) {
    let prompt = "Summarize ticket " + ticket["id"] + " for " + queue
    let response = std.ai.response_with("stub", prompt)
    return {
        "provider" => response.provider,
        "model" => response.model,
        "finish_reason" => response.finish_reason,
        "text_len" => len(response.text)
    }
}
```

The `stub` provider is deterministic. Swap it for a live provider when the
environment is configured.

## 3. Return JSON

```alef
fn main() {
    let ticket = {
        "id" => "TCK-1001",
        "plan" => "startup",
        "title" => "Refund for duplicate invoice",
        "body" => "Customer was charged twice."
    }
    let queue = classify_ticket(ticket)
    let payload = {
        "id" => ticket["id"],
        "queue" => queue,
        "ai" => ai_summary(ticket, queue, "p2")
    }
    println(json_encode(payload))
}
```

Run:

```bash
ALEF_AI_PROVIDER=stub alef run main.alef
```

## Provider Pattern

Use stub for tests:

```alef
let r = std.ai.response_with("stub", "hello")
```

Use configured defaults for runtime environments:

```alef
let r = std.ai.response("hello")
```

Use named providers when credentials or local services exist:

```alef
let r = std.ai.response_with("ollama", "hello")
let r = std.ai.response_with("minimax", "hello")
let r = std.ai.response_with("mimo", "hello")
```

