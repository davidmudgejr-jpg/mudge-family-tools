---
name: mudge-setup-doctor
description: Diagnose a Mudge Tools OAuth connection without changing data. Use after setup, on a new device, when tools or permissions seem missing, when OAuth expires, or before family onboarding. Verifies service health, authenticated person/device, CRM reads, permanently read-only Brain access, confirmed CRM write capability, published document rendering, and hard security boundaries.
---

# Mudge Setup Doctor

Use the read-only `mudge_setup_doctor` tool from the `mudge_tools` MCP. Do not test setup by attempting a write or creating an artifact.

## Workflow

1. Call `mudge_setup_doctor`.
2. Report the authenticated email, CRM role, device/agent name, and expiry without exposing tokens or secrets.
3. Summarize every check as pass, warning, or fail.
4. Confirm explicitly that Mudge Brain is read-only and CRM writes remain preview-confirm only.
5. If a capability is missing, explain the narrow remediation:
   - authentication failure: reconnect through CRM Settings and OAuth;
   - CRM write warning: use a broker/admin account and approve `crm.write.confirmed`;
   - document warning/failure: approve `crm.documents.render`;
   - Brain failure: approve `crm.read` or ask an administrator to verify the account.
6. Rerun the doctor after remediation. Do not claim setup is complete while a required check fails.

## Safety

- Never print, request, reuse, or store access or refresh tokens.
- Never expand scopes silently; the person must approve them in CRM.
- Never verify setup with a CRM write, document render, repository request, or filesystem access.
