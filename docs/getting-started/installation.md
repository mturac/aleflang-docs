# Installation

Alef can be used from a source checkout while the public package channel is
being prepared.

## From Source

```bash
git clone https://github.com/mturac/aleflang
cd aleflang
npm install
npm run build
```

Run an example:

```bash
node dist/cli.js run examples/hello.alef
```

If you have a native binary:

```bash
native_runtime/target/release/alef run examples/hello.alef
```

## Requirements

- Node.js for the TypeScript CLI wrapper and build scripts
- Rust for the native runtime build
- Go only when using the optional Go codegen path

## Recommended Developer Alias

For local examples, set `ALEF_BIN`:

```bash
export ALEF_BIN=/path/to/aleflang/native_runtime/target/release/alef
```

Public example repos use `ALEF_BIN` so they can be cloned next to Alef or run
with an installed `alef` command.
