---
name: mudge-crm
description: Safely search, read, and make confirmed updates in the live Mudge CRM through the Mudge Tools MCP. Use for CRM record lookups, property/contact/company/deal updates, or adding a note or activity to an existing record. Enforces exact target resolution, field-level preview, explicit confirmation, least privilege, read-back verification, and audit receipts.
---

# Mudge CRM

Use only the `mudge_tools` MCP. Never fall back to generic SQL, HTTP, browser automation, repository files, or a legacy local CRM MCP for this workflow.

## Read workflow

1. Run `mudge_setup_doctor` when the connection or permissions are uncertain.
2. Search the correct entity type with a bounded query.
3. Resolve exactly one record. If multiple plausible matches remain, ask the user to choose.
4. Read the exact UUID before answering or preparing a change.

## Write workflow

1. Call `describe_capabilities` and use only an exposed update or linked-create tool.
2. Resolve the existing target to one exact UUID. Reject ambiguity.
3. Generate a stable idempotency key for this requested action.
4. Call the matching `preview_update_*`, `preview_add_note`, or `preview_add_activity` tool.
5. Show the user the target and field-level before/after preview. State that no write has happened.
6. Wait for explicit confirmation of that preview. Do not infer approval from the original request.
7. Call `confirm_crm_write` with the preview's confirmation token and the same idempotency key.
8. Report the verified read-back and audit receipt. If verification fails, say so plainly.

## Boundaries

- Update only fields returned by `describe_capabilities`.
- Create only linked notes or activities on an existing property, contact, company, or deal.
- Never create core records, delete, merge, import, upload, execute arbitrary SQL/HTTP, change relationships generically, or write to Mudge Brain.
- Treat Brain findings as context; re-read the live CRM before changing CRM data.
- Keep each preview and confirmation to one clear user-approved action.
