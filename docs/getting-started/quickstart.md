# Quickstart

Create `main.alef`:

```alef
fn main() {
    let name = "Alef"
    println("Hello, {name}")
}
```

Run it:

```bash
alef run main.alef
```

Expected output:

```text
Hello, Alef
```

## Add JSON

```alef
fn main() {
    let task = {
        "id" => "task_1",
        "title" => "Write docs",
        "done" => false
    }
    println(json_encode(task))
}
```

## Add A Function

```alef
fn priority(plan, blocked) {
    if plan == "enterprise" and blocked {
        return "P0"
    }
    return "P2"
}

fn main() {
    println(priority("enterprise", true))
}
```

## Next Steps

- Learn the [Language Tour](../language/tour.md).
- Build a real UI with [TicketDesk](../tutorials/ticketdesk-ui.md).
- Learn native [HTTP and JSON](../stdlib/http-json.md).
