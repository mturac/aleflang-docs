# 2. Installing And Running Alef

During early public development, Alef can be used from a source checkout.

```bash
git clone https://github.com/mturac/aleflang
cd aleflang
npm install
npm run build
```

Run a program through the CLI wrapper:

```bash
node dist/cli.js run examples/hello.alef
```

If you have the native binary:

```bash
native_runtime/target/release/alef run examples/hello.alef
```

## Running A File

The normal command is:

```bash
alef run main.alef
```

This book uses that form in examples.

## Useful Diagnostics

```bash
alef health
alef doctor
```

Use these before guessing about provider, runtime, or feature availability.

## Example Repositories

Public example repositories should accept `ALEF_BIN`:

```bash
ALEF_BIN=/path/to/alef bash scripts/smoke.sh
```

This keeps examples portable. A README should never require a machine-local
path.
