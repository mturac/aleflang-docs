# The Alef Programming Language

Alef is a programming language.

This book is the main documentation for Alef. It is written as a guided book,
not a collection of disconnected notes. Read it from the beginning if you are
new to Alef; use the appendices when you need a reference.

## Published Site

Read the public GitHub Pages site:

```text
https://mturac.github.io/aleflang-docs/
```

Download the current macOS arm64 binary:

```text
https://github.com/mturac/aleflang-docs/releases/latest/download/alef-darwin-arm64
```

Alef has:

- its own syntax
- modules
- functions
- values and collections
- structs and enums
- `Result` and `Option` style error handling
- a command-line tool
- a native runtime
- a standard library for HTTP, JSON, database, cache, AI, and operational code

AI-native means AI provider calls are part of the standard library story. It
does not mean Alef is an app template. Ticket boards, APIs, and agent workflows
are examples of programs written in Alef.

## Public Surface

Alef's language documentation, examples, tutorials, and release artifacts can be
public. The Alef compiler, native runtime implementation, and private source
repository are not part of the public surface.

That means this book teaches the language contract:

- how `.alef` programs are written
- how the `alef` command is used
- how standard-library modules behave
- how public example repositories should be structured

It does not require readers to clone or inspect the private Alef source tree.

## How To Read This Book

Start with Part I if you want the language model. It explains why Alef exists,
how programs run, and how to write your first useful program.

Read Part II to learn the language itself: values, functions, control flow,
data modeling, errors, and modules.

Read Part III to learn the runtime and standard library: the CLI, native
runtime, HTTP, JSON, database, cache, AI, and testing.

Read Part IV for complete program walkthroughs. These are not the definition of
Alef; they are proof that the language can build real programs.

## A First Alef Program

```alef
fn greet(name) {
    return "hello, {name}"
}

fn main() {
    println(greet("Alef"))
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

## The Shape Of Alef

Alef code is meant to read directly:

```alef
fn priority(plan, blocked) {
    if plan == "enterprise" and blocked {
        return "P0"
    }
    return "P2"
}
```

Data is structured:

```alef
let ticket = {
    "id" => "TD-101",
    "title" => "Checkout timeout",
    "status" => "triage"
}
```

Failures are visible:

```alef
match std.http.get("https://example.com") {
    Ok(r) => println(r.body),
    Err(e) => println("request failed: {e}"),
}
```

That is the center of the language: readable programs, explicit failure, and a
standard library that covers the modern backend and AI-native surfaces people
actually reach for.
