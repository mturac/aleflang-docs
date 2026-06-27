# Control Flow

## `if`

```alef
if priority == "P0" {
    return "incident-lead"
}
return "support"
```

Boolean operators:

```alef
if queue == "platform" and text.contains("timeout") {
    return "incident"
}
```

## `for`

```alef
for ticket in tickets {
    println(ticket["id"])
}
```

## `while`

```alef
let i = 0
while i < 10 {
    println(i)
    i = i + 1
}
```

## `match`

```alef
match result {
    Ok(value) => println(value),
    Err(error) => println("failed: {error}"),
}
```
