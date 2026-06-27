# Examples

These public example repos are designed to be small enough to inspect and real
enough to smoke test. The bar is: a real workflow, state changes, and a smoke
test that proves the behavior.

## TicketDesk UI

Multi-workspace ticket and task manager:

```bash
git clone <repo-url>/alef-ticketdesk-ui
cd alef-ticketdesk-ui
ALEF_BIN=/path/to/alef bash scripts/smoke.sh
```

Shows:

- server-rendered UI
- multiple workspaces
- ticket columns
- assign and move actions
- activity feed
- JSON API state verification

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
