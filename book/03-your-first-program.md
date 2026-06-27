# 3. Your First Alef Program

Create `main.alef`:

```alef
fn main() {
    println("hello, Alef")
}
```

Run it:

```bash
alef run main.alef
```

Expected output:

```text
hello, Alef
```

## Add A Function

```alef
fn greet(name) {
    return "hello, {name}"
}

fn main() {
    println(greet("Ada"))
}
```

Functions use `fn`. String interpolation uses `{name}` inside a string.

## Add Data

```alef
fn main() {
    let ticket = {
        "id" => "TD-101",
        "title" => "Checkout timeout",
        "status" => "triage"
    }

    println(ticket["title"])
}
```

Maps use `=>` for key/value pairs. Access a value with brackets.

## Add JSON

```alef
fn main() {
    let ticket = {
        "id" => "TD-101",
        "status" => "triage"
    }

    println(json_encode(ticket))
}
```

Alef programs can print structured output without adding a JSON package.
