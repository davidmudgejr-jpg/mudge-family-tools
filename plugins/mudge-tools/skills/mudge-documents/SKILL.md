---
name: mudge-documents
description: "Create Mudge Team documents using the Mudge Tools OAuth MCP live registry and prepare/preview/confirm protocol. Applies when that MCP workflow is selected; an explicit Mudge CLI request follows the separate mudge-doc skill."
---

# Mudge Documents through OAuth MCP

This skill governs only the `mudge_tools` MCP transport. When the user or applicable instructions select the shared Mudge CLI, follow `mudge-doc` instead. Do not blend command contracts or switch routes to evade a tool boundary or failed approval. For this MCP workflow, use the live published registry; do not read repositories, raw templates, local files, or GitHub to render a document.

1. Run `mudge_setup_doctor` if document access is uncertain.
2. Search properties and resolve each selection to its exact CRM UUID. Never pass an address as a UUID.
3. Discover current document designs/native forms and describe inputs when unclear. Trust the live registry.
4. Call the matching prepare tool. Reuse supplied answers and ask only missing required fields. Never invent deal terms, recipient details, numbers, dates, checkboxes, or property facts.
5. Call the matching preview-render tool with a stable idempotency key. Show the property/design/form, supplied inputs, and preview summary. This preview has not created an artifact.
6. Follow the MCP's explicit preview confirmation requirement, then confirm-render with that same idempotency key. General document intent does not replace this tool protocol. If the matching preview has already been explicitly confirmed, do not request a duplicate confirmation.
7. Return the private short-lived artifact link and receipt. This workflow does not file into CRM.

Default to `classic` only if not otherwise specified and present in the live registry. Surveys/tours accept at most 60 exact UUIDs; confirm the selected list using any already-settled selection. Native LOI, commission, and listing forms use native-form tools. Intentional bracketed draft fields are valid where the live form permits them.

Do not upload photos, edit/publish templates, access repositories, or file artifacts through this workflow. A later filing request requires an authorized supported filing capability; it does not permit bypassing these MCP boundaries. Creation does not authorize a CRM data update or an external send.

## Missing tools in the client

If a named tool is absent, use `describe_mudge_tools` with `tool_name` for its exact input schema and route, then `call_mudge_read` or `call_mudge_action` with that name and arguments. Paginate discovery until `next_offset` is null. These MCP routes preserve the same account permissions, typed validation, original handlers and confirmation requirements. They do not permit arbitrary SQL, HTTP or filesystem access.

