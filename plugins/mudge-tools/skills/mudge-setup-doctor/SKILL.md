---
name: mudge-setup-doctor
description: "Connection check for Mudge Tools OAuth, read-only: run when tools are missing, Mudge Tools isn't working or OAuth expired, after setup, on a new device, or before family onboarding. Not for the CLI doctor (mudge-doc), installed skill drift (release-mudge-skills) or a down agent runtime (agent-runtime-recovery)."
---

# Mudge Setup Doctor

Use the read-only `mudge_setup_doctor` tool from the `mudge_tools` MCP. Do not test setup by attempting a write or creating an artifact.

## Workflow

1. Call `mudge_setup_doctor`. If no Mudge tool is callable in this chat, say so and check the client's MCP list (`/mcp`); a connected CLI does not prove this chat has the tools.
2. Report the authenticated email, CRM role, device/agent name, and expiry without exposing tokens or secrets.
3. Summarize every check as pass, warning, or fail.
4. Confirm explicitly that Mudge Brain is read-only and CRM writes remain preview-confirm only.
5. If a capability is missing, explain the narrow remediation:
   - authentication failure: reconnect through CRM Settings and OAuth;
   - CRM write warning: use a broker/admin account and approve `crm.write.confirmed`;
   - document warning/failure: approve `crm.documents.render`;
   - file/photo filing warning: use a broker/admin account and approve `crm.files.write`;
   - Brain warning: approve `crm.read` or ask an administrator to verify the account;
   - the doctor does not test tasks, record creation or conversations, so check `describe_capabilities.publication.callable_tools`: no `preview_create_task` needs `crm.tasks.write`, no `preview_create_deal` needs `crm.records.write`, no `list_conversations` needs `crm.conversations`;
   - a missing scope needs a full reconnect from the CRM Settings Connect Center; a token refresh cannot add one.
6. Rerun the doctor after remediation. Do not claim setup is complete while a required check fails.

## Safety

- Never print, request, reuse, or store access or refresh tokens.
- Never expand scopes silently; the person must approve them in CRM.
- Never verify setup with a CRM write, document render, repository request, or filesystem access.

## Known failures

- 2026-10-30: the CLI showed Mudge Tools connected while the open chat had none. Check the chat itself, then capture a fresh doctor result.
- 2026-10-14: Meta Muse failed at automatic app registration. A new hosted client needs its callback allowlisted on the server; a reconnect will not fix it.

When setup fails in a new way, add a dated line here in mudge-family-tools and bump the plugin version.

## Missing tools in the client

If a named tool is absent, use `describe_mudge_tools` with `tool_name` for its schema and route, then `call_mudge_read` or `call_mudge_action`. Paginate discovery until `next_offset` is null. Permissions and confirmations stay the same; these routes allow no arbitrary SQL, HTTP or filesystem access.
