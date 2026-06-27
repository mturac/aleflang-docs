# 2. Installing And Running Alef

Alef users should not need the private Alef source repository.

Public usage is built around the `alef` command. Download the current macOS
arm64 binary from the public documentation release:

```bash
curl -L -o alef \
  https://github.com/mturac/aleflang-docs/releases/latest/download/alef-darwin-arm64
chmod +x ./alef
./alef --version
```

Move it somewhere on your `PATH` when you want to call it as `alef`:

```bash
mkdir -p ~/.local/bin
mv ./alef ~/.local/bin/alef
alef --version
```

Other platform binaries can be added to the same release without opening the
private Alef compiler or runtime source repository.

Verify that the command is available:

```bash
alef --version
```

If you receive a standalone native binary, place it on your `PATH` as `alef`:

```bash
chmod +x ./alef
./alef --version
```

Example repositories should also accept `ALEF_BIN` so they can run with either
an installed command or an explicitly provided binary:

```bash
ALEF_BIN=/path/to/alef bash scripts/smoke.sh
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

## Public Examples Without Source Access

Public examples should contain `.alef` programs, fixtures, smoke scripts, and
README instructions. They should not require access to the private Alef compiler
or runtime source tree.

This keeps the project shape simple: the language source can stay private while
docs, tutorials, and example applications remain useful to readers.
