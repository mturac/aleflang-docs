# Syntax Reference

This page is a compact reference. Use the Language Guide for explanations.

## Program Entry

```alef
fn main() {
    println("hello")
}
```

## Binding

```alef
let name = "Ada"
name = "Grace"
```

## Function

```alef
fn add(a, b) {
    return a + b
}
```

## Typed Function

```alef
fn add(a: int, b: int) -> int {
    return a + b
}
```

## Array

```alef
let xs = [1, 2, 3]
xs.push(4)
```

## Map

```alef
let m = { "id" => "TD-101", "status" => "triage" }
```

## Struct

```alef
struct Ticket {
    id: string,
    title: string
}
```

## Enum

```alef
enum Status {
    Triage,
    Done,
}
```

## If

```alef
if ok {
    return "yes"
}
return "no"
```

## For

```alef
for item in items {
    println(item)
}
```

## Match

```alef
match value {
    Ok(v) => v,
    Err(e) => 0,
}
```

## Import

```alef
import std.http { json_response }
```
