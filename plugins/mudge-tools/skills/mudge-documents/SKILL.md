---
name: mudge-documents
description: "MCP documents: BOVs, flyers, brochures, OMs, LOIs, commission worksheets, listing forms, surveys and tours from the live Mudge registry over Mudge Tools OAuth, in one pass when asked. Use when the mudge-doc CLI is absent or the user picks the MCP route; otherwise use mudge-doc. Comp sets: mudge-comp-pull. Lease vs buy: mudge-lvb."
---

# Mudge Documents through OAuth MCP

This skill governs only the `mudge_tools` MCP transport. When the user or applicable instructions select the shared Mudge CLI, follow `mudge-doc` instead. Do not blend command contracts or switch routes to evade a tool boundary or failed approval. For this MCP workflow, use the live published registry; do not read repositories, raw templates, local files, or GitHub to render a document.

1. Run `mudge_setup_doctor` if document access is uncertain.
2. Search properties and resolve each selection to its exact CRM UUID. Never pass an address as a UUID.
3. Call `list_mudge_document_designs` or `list_mudge_native_forms` and describe inputs when unclear. Trust the live registry.
4. Call the matching prepare tool. Reuse supplied answers and ask only missing required fields. Never invent deal terms, recipient details, numbers, dates, checkboxes, or property facts. For a BOV, get the user's explicit ruling on comps and value before filling the valuation; this route has no valuation receipt, so say the BOV is unreceipted.
5. Call the matching preview-render tool with a stable idempotency key. Show the property/design/form, supplied inputs, and preview summary. This preview has not created an artifact.
6. When the user asked for the document, confirm-render with that same idempotency key in the same pass and return the link; do not ask for a second approval. Stop and ask only if a required field is missing, the preview reports a warning, conflict or substitution, or it shows something the user did not ask for.
7. Return the private short-lived artifact link and receipt. This workflow does not file into CRM. A receipt is not client-ready proof: say so until the rendered pages have been inspected.

For a normal sale or lease brochure use the registry's `preferred_brochure_design`. Otherwise default to `classic` only if not otherwise specified and present in the live registry. Surveys/tours accept at most 60 exact UUIDs; confirm the selected list using any already-settled selection. Native LOI, commission, and listing forms use native-form tools. Intentional bracketed draft fields are valid where the live form permits them.

Do not upload photos, edit/publish templates, access repositories, or file artifacts through this workflow. A later filing request requires an authorized supported filing capability; it does not permit bypassing these MCP boundaries. Creation does not authorize a CRM data update or an external send.

## Known failures

- 2026-10-21: a brochure returned a success receipt with template residue and empty photo frames. Inspect the pages.
- 2026-10-14: agents asked for a second approval after the preview. One pass is the rule when the user asked.

When a render fails in a new way, add a dated line here in mudge-family-tools and bump the plugin version.

## Missing tools in the client

If a named tool is absent, use `describe_mudge_tools` with `tool_name` for its schema and route, then `call_mudge_read` or `call_mudge_action`. Paginate discovery until `next_offset` is null. Permissions and confirmations stay the same; these routes allow no arbitrary SQL, HTTP or filesystem access.
