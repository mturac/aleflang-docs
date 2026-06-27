# Examples

These public example repos are designed to be small enough to inspect and real
enough to smoke test.

## Agent Ticket Router

AI-assisted support triage:

```bash
git clone <repo-url>/alef-agent-ticket-router
cd alef-agent-ticket-router
ALEF_BIN=/path/to/alef bash scripts/smoke.sh
```

Shows:

- business routing
- `std.ai.response_with`
- deterministic stub provider
- JSON output contract

## Mini CRM API

Native HTTP API:

```bash
git clone <repo-url>/alef-mini-crm-api
cd alef-mini-crm-api
ALEF_BIN=/path/to/alef bash scripts/smoke.sh
```

Shows:

- `std.http` server
- route params
- JSON responses
- problem responses
- stateful handlers

