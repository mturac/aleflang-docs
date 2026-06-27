# 1. Why Alef Is A Language

Alef is a programming language. That matters.

A framework gives you conventions inside another language. A library gives you
functions inside another language. A template gives you a starting repository.
Alef gives you syntax, a runtime, a command-line tool, a standard library, and a
way to express programs directly.

The examples in this book include APIs, ticket boards, and AI workflows because
those are useful programs. They are not the identity of Alef. They are proof
that Alef can describe real software without immediately handing the problem to
a separate framework stack.

## The Core Bet

Most modern programs need the same things early:

- structured data
- control flow
- explicit error handling
- HTTP
- JSON
- persistence
- local state
- tests and smoke checks
- model or provider calls

Alef treats those as ordinary language work. It does not make you start with a
pile of SDK choices before the first useful program exists.

## A Language-Level Example

```alef
fn owner(priority) {
    if priority == "P0" {
        return "incident-lead"
    }
    return "support"
}

fn main() {
    println(owner("P0"))
}
```

There is no app framework here. This is just a program.

## A Standard-Library Example

```alef
import std.http { json_response }

fn with_state(response, state) {
    return { "response" => response, "state" => state }
}

fn health(request, state) {
    return with_state(json_response(json_encode({ "ok" => true })), state)
}
```

This is still language documentation. The `std.http` module is part of Alef's
standard library, just like `net/http` is part of Go's standard library.

## Native-First

Alef's public examples target:

```bash
alef run main.alef
```

That command runs an Alef program on the native runtime. Other paths can exist,
but the book teaches the native path first because it is the production-facing
story.
