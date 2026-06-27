# Native Runtime

Alef's production docs and examples are native-first.

```bash
alef run main.alef
```

The native runtime supports the current backend-oriented path:

- CLI execution
- HTTP server routes
- HTTP client calls returning `Result`
- JSON encode/decode
- SQLite-backed examples through `std.db`
- `std.ai` provider surface
- package and smoke-test scripts

## Commands

```bash
alef run main.alef
alef --bytecode run main.alef
alef --strict-bytecode run main.alef
alef doctor
alef health
```

`--bytecode` tries bytecode first and can fall back for unsupported VM features.
`--strict-bytecode` keeps unsupported bytecode features visible during VM work.

## Native-First Rule

Use native examples for public docs unless a page is specifically about the
TypeScript interpreter or Go codegen path.

```bash
alef run examples/hello.alef
```

Use Go codegen only when the tutorial is explicitly about code generation:

```bash
alef build main.alef
```

