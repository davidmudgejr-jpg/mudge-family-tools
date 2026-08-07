---
name: mudge-documents
description: Create Mudge Team documents through the live published document-factory registry in the Mudge Tools MCP. Use for BOVs, brochures, offering memoranda, for-lease or for-sale flyers, LOIs, commission worksheets, listing request forms, property surveys, and tour packages. Requires exact CRM property UUIDs, asks only for missing fields, and uses preview-confirm private artifact rendering.
---

# Mudge Documents

Use only the `mudge_tools` MCP and the live published registry. Never read design repositories, raw templates, local files, or GitHub to render a document.

## Workflow

1. Run `mudge_setup_doctor` if document access is uncertain.
2. Search CRM properties and resolve every selection to an exact UUID. Never pass an address where a UUID is required.
3. Call `list_mudge_document_designs` or `list_mudge_native_forms`; trust the live registry over remembered names.
4. Describe the selected template or form when its inputs are unclear.
5. Call the matching prepare tool.
6. Ask only for fields reported missing. Never invent a deal term, recipient, amount, date, checkbox, or property fact.
7. Call the matching preview-render tool with a stable idempotency key.
8. Show the artifact type, property, design/form, supplied answers, and preview summary. State that no artifact exists yet.
9. Wait for explicit confirmation, then call the matching confirm-render tool with the same idempotency key.
10. Return the private short-lived artifact link and receipt. Do not file it into CRM.

## Defaults and boundaries

- Use design `classic` only when the user did not name a design and the live registry includes it.
- Surveys and tours accept at most 60 exact property UUIDs. Confirm the selected list before previewing.
- LOIs, commission worksheets, and listing request forms are native forms; use the native-form tools.
- Unfilled draft values may remain bracketed when the live form allows them.
- Do not upload photos, edit template source, publish designs, access repositories, or file artifacts into CRM.
- Document creation never authorizes a CRM data update.
