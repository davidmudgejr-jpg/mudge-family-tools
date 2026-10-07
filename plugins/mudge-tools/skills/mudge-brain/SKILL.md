---
name: mudge-brain
description: Search and read prior Mudge business knowledge through the permanently read-only Mudge Brain tools in the Mudge Tools MCP. Use for prior conversations, people, companies, properties, deals, identifiers, historical context, and entity dossiers. Never writes to Brain and never treats Brain context as current CRM truth.
---

# Mudge Brain

Use `brain_search`, `entity_page`, and `read_chunk` from the `mudge_tools` MCP. Mudge Brain is permanently read-only for every family role.

## Workflow

1. Run `mudge_setup_doctor` if Brain access is uncertain.
2. Call `brain_search` with a focused business query and a small result limit.
3. Review cited excerpts and identifiers. If the target remains ambiguous, refine the search.
4. Call `entity_page` only with a slug or exact entity type and ID returned by search.
5. Cite or clearly attribute the relevant Brain context in the answer.
6. For current CRM facts or any proposed CRM change, re-read the exact live CRM record separately.

## Boundaries

- Never attempt to write, annotate, correct, delete, or add telemetry to Mudge Brain.
- Never use repository, filesystem, database, or arbitrary HTTP access as a substitute.
- Brain history may be stale or incomplete; distinguish it from live CRM data.
- If the user asks to save something, use the explicit CRM note/activity preview-confirm workflow when appropriate; do not imply that it changes Brain.

## Zoning evidence

Use read_chunk to inspect full cited zoning sections and neighboring text. Preserve NOT ANSWER-ELIGIBLE, TABLES UNREVIEWED, CONFLICT and OCR PENDING labels. Use permissions come from useMatrix/GIS and lookup_use_determination, never Brain similarity. Unsupported or ambiguous activities yield no determination. Recorded entitlement actions apply to their exact parcel, not other parcels.

## Missing tools in the client

If a named tool is absent, use `describe_mudge_tools` with `tool_name` for its exact input schema and route, then `call_mudge_read` or `call_mudge_action` with that name and arguments. Paginate discovery until `next_offset` is null. These MCP routes preserve the same account permissions, typed validation, original handlers and confirmation requirements. They do not permit arbitrary SQL, HTTP or filesystem access.

