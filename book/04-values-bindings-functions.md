# 4. Values, Bindings, And Functions

Alef uses `let` for local bindings.

```alef
let name = "Ada"
let count = 3
let ready = true
```

Bindings can be reassigned when a program needs to move state forward:

```alef
let status = "triage"
status = "progress"
```

## Functions

```alef
fn add(a, b) {
    return a + b
}
```

Typed signatures are available when they clarify the program:

```alef
fn label(id: string, title: string) -> string {
    return "{id}: {title}"
}
```

## Early Returns

```alef
fn priority(plan, blocked) {
    if plan == "enterprise" and blocked {
        return "P0"
    }
    return "P2"
}
```

Alef code should read like a direct description of the case being handled.
