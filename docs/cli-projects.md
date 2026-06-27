# CLI and Project Setup

Alef projects are deliberately small. A useful repo can start with:

```text
my-alef-app/
├── alef.mod
├── main.alef
├── README.md
└── scripts/
    └── smoke.sh
```

## Module File

```text
module my-alef-app

version 0.1.0
```

## Run A File

```bash
alef run main.alef
```

`alef run` uses the native runtime by default in production-facing docs and
examples.

## Bytecode Modes

```bash
alef --bytecode run main.alef
alef --strict-bytecode run main.alef
```

Use `--bytecode` when fallback is acceptable. Use `--strict-bytecode` when you
are testing the VM and want unsupported bytecode features to fail visibly.

## Health And Diagnostics

```bash
alef health
alef doctor
```

These commands report runtime capability, provider readiness, and feature
status without leaking secrets.

## Smoke Test Pattern

Public examples should include a smoke script:

```bash
#!/usr/bin/env bash
set -euo pipefail

ALEF_BIN="${ALEF_BIN:-alef}"
"$ALEF_BIN" run main.alef
```

For server examples, bind localhost on a random port, make real HTTP requests,
verify state, then call the shutdown endpoint.

