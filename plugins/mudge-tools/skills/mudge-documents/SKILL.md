---
name: mudge-documents
description: "Create Mudge/Lee collateral through Mudge Tools using published Mudge Classic by default: brochures, flyers, BOV layouts, OMs, surveys and tours. Route LOIs, pitch letters, commission and listing forms through approved native templates. Preserve BOV receipt requirements; lease-versus-buy uses mudge-lvb."
---

# Mudge Documents through OAuth MCP

This is the default connected document workflow for Mudge/Lee collateral.
Explicitly select `classic` (Mudge Classic) unless David names another design
for this task. The registry describes availability, not permission to override
his design choice. Use the live published registry; do not read repositories,
raw templates or GitHub to recreate a document.

Design and transport are separate. For an operation this connection cannot
perform, disclose the exact current gap and follow `mudge-doc`'s supported CLI
route for the complete artifact. Do not switch mid-job to evade a tool boundary,
warning, permission or receipt gate. A blocked Classic artifact stops for a
task-specific decision; never substitute `crm-classic`, an unreceipted BOV or a
generic PDF/DOCX/PPTX/Canva/Express design. Generic tools may inspect, extract or
convert an existing artifact.

1. Run `mudge_setup_doctor` if document access is uncertain.
2. Search properties and resolve each selection to its exact CRM UUID. Never pass an address as a UUID.
3. Call `list_mudge_document_designs` or `list_mudge_native_forms` and describe inputs when unclear. Pass `design: "classic"` explicitly for collateral; a flyer maps to the matching sale/lease listing template. If Classic does not cover the request, disclose the gap rather than creating a substitute.
4. Call the matching prepare tool. Reuse supplied answers and ask only missing required fields. Never invent deal terms, recipient details, numbers, dates, checkboxes, or property facts. For a BOV, get the user's explicit ruling on comps and value before filling the valuation. This render route does not supply the receipt-bound BOV chain: preserve required receipts through the supported workflow, or stop. Never pass an unreceipted render off as a completed receipt-required BOV.
5. Call the matching preview-render tool with a stable idempotency key. Show the property/design/form, supplied inputs, and preview summary. This preview has not created an artifact.
6. When the user asked for the document, confirm-render with that same idempotency key in the same pass and return the link; do not ask for a second approval. Stop and ask only if a required field is missing, the preview reports a warning, conflict or substitution, or it shows something the user did not ask for.
7. Return the private short-lived artifact link and receipt. This workflow does not file into CRM. A receipt is not client-ready proof: say so until the rendered pages have been inspected.

The design default includes normal sale and lease brochures: use `classic`,
regardless of `preferred_brochure_design` or an older tool hint. `team-standard`
remains available only for a task-specific choice. Surveys/tours accept at most
60 exact UUIDs; confirm the selected list using any already-settled selection.
Native LOIs, pitch letters, commission/listing forms, LVB and AIR packages keep
their approved templates and formulas, not a marketing-design substitution.
Intentional bracketed draft fields are valid where the live form permits them.

Rendering does not authorize photo uploads, template publishing, CRM edits,
filing or sending. A separately authorized filing uses the supported typed
upload/complete/preview/confirm tools with exact-destination read-back. Discover
current capabilities and supported doc types; this render workflow's scope is
not a claim that the platform cannot file. Photo crops must remain real, without
AI alteration. Preserve required BOV evidence, the one-pager's orange styling,
and the approved LVB formulas.

## Known failures

- 2026-10-21: a brochure returned a success receipt with template residue and empty photo frames. Inspect the pages.
- 2026-10-14: agents asked for a second approval after the preview. One pass is the rule when the user asked.

When a render fails in a new way, add a dated line here in mudge-family-tools and bump the plugin version.

## Missing tools in the client

If a named tool is absent, use `describe_mudge_tools` with `tool_name` for its schema and route, then `call_mudge_read` or `call_mudge_action`. Paginate discovery until `next_offset` is null. Permissions and confirmations stay the same; these routes allow no arbitrary SQL, HTTP or filesystem access.
