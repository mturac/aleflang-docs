# 6. Collections And Data Modeling

Arrays and maps are the common data structures for Alef programs.

## Arrays

```alef
let statuses = ["triage", "progress", "review", "done"]
statuses.push("archived")
```

Iterate with `for`:

```alef
for status in statuses {
    println(status)
}
```

## Maps

```alef
let ticket = {
    "id" => "TD-101",
    "title" => "Checkout timeout",
    "priority" => "P0"
}
```

Maps are useful for JSON, request state, response bodies, and examples.

## Structs

Use a struct when a shape deserves a name:

```alef
struct Task {
    id: string,
    title: string,
    done: bool
}
```

## Enums

Use an enum when the valid cases are finite:

```alef
enum Shape {
    Circle(f64),
    Rect(f64, f64),
    Point,
}
```

Maps make public examples easy to inspect. Structs and enums make library and
domain code more explicit.
