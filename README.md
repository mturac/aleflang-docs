# The Alef Programming Language

Alef is a programming language for writing small tools, services, workflow
code, and AI-aware backend programs with one command:

```bash
alef run main.alef
```

This book is written for someone learning Alef from zero. You do not need the
private Alef source repository. You only need the public docs, a downloadable
`alef` binary, and a text editor.

## Start Here

If you are new to programming languages, use this path:

1. Install the `alef` command.
2. Create one file named `main.alef`.
3. Run it with `alef run main.alef`.
4. Learn values, functions, `if`, loops, arrays, maps, structs, enums, and
   explicit errors.
5. Build one small program before reading the advanced chapters.

The first hour should feel like this:

```alef
fn priority(plan, blocked) {
    if plan == "enterprise" and blocked {
        return "P0"
    }
    return "P2"
}

fn main() {
    let ticket = {
        "id" => "TD-101",
        "plan" => "enterprise",
        "blocked" => true
    }

    println(priority(ticket["plan"], ticket["blocked"]))
}
```

Run it:

```bash
alef run main.alef
```

Expected output:

```text
P0
```

## Published Site

Read the public GitHub Pages site:

```text
https://mturac.github.io/aleflang-docs/
```

Download the current macOS arm64 binary:

```text
https://github.com/mturac/aleflang-docs/releases/latest/download/alef-darwin-arm64
```

## What You Learn First

Alef has:

- `fn` for functions
- `let` for local values
- strings, numbers, booleans, arrays, and maps
- `if`, `for`, `while`, and `match`
- structs and enums for named data
- `Result` and `Option` style error handling
- a native runtime and command-line tool
- standard-library surfaces for JSON, HTTP, database, cache, AI, and tests

## Public Surface

Alef's language documentation, examples, tutorials, release binaries, and
example repositories can be public. The Alef compiler, native runtime
implementation, and private source repository are not part of the public
surface.

This book teaches the language contract:

- how `.alef` programs are written
- how the `alef` command is used
- how standard-library modules behave
- how public example repositories should be structured

It does not require readers to clone or inspect the private Alef source tree.

## How To Read This Book

Read Part I in order. It gets you from no setup to a working program.

Read Part II as the language course. Each chapter teaches one part of the
syntax and shows runnable examples.

Read Part III when you are ready to use the runtime and standard library.

Read Part IV when you want full program walkthroughs: API, TicketDesk UI, and
AI ticket routing.
