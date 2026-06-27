# Frequently Asked Questions

## Is `alef run` the production path?

Yes. Public docs and examples should target the native runtime through:

```bash
alef run main.alef
```

## When should I use `--interp`?

Use `alef run --interp` for interpreter/dev surfaces that are not native-first.
Do not make it the default in production examples.

## When should I use maps instead of structs?

Use maps for JSON-heavy request, response, and UI state. Use structs when a
domain shape deserves a stable name and stronger documentation.

## Does Alef require AI credentials?

No. Docs and smoke tests should use the deterministic `stub` provider. Live
providers are optional and environment-gated.

## Is a UI example allowed to be server-rendered?

Yes. Server-rendered UI is a strong Alef demo when the point is native HTTP and
stateful workflow, not a frontend build chain.
