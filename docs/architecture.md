# Email review workflow architecture

The repository contains two portable workflow references: a Power Automate flow definition and an n8n export. They share a JSON assessment schema and response templates. Neither is evidence of a live deployment.

## Boundaries

1. A configured mailbox trigger selects messages for review.
2. The automation sends message content to the configured AI provider. Hosting n8n locally does not make this provider request local.
3. The assessment contains a verdict, threat classification, indicators, recommendation, operator text, and confidence score; see [the schema](../shared/ai-response-schema.json).
4. A response template formats those fields. Template checks are separate from validating model content and authorization to send mail.

## Current export behavior

The n8n export parses the model response, switches on `verdict`, and connects verdict branches to Outlook send nodes. It does **not** enforce a confidence threshold or human approval before delivery. Its parse fallback uses `Unknown` as a threat classification even though that value is not in the shared schema. Treat the export as a reference requiring adaptation and validation before activation.

The Power Automate reference and platform walkthrough are also configuration examples. Review actual connection references, expressions, response parsing, error paths, and permissions in the destination tenant. A documented review policy is not an implemented gate.

## Adaptation sequence

- Import into a test workspace with fictional messages and delivery disabled.
- Supply mailbox, provider, model, credentials, and trigger conventions privately.
- Validate provider output against the shared schema and handle invalid/unavailable responses explicitly.
- Implement and test operator review before any user-affecting delivery or containment action.
- Inspect all outbound mail nodes and error paths before enabling the workflow.

Do not export production credentials, real mailbox contents, routing policy, or organization-specific thresholds back into this repository. The [template validator](../scripts/validate-templates.sh) checks local template artifacts; it does not certify a provider integration or live mail flow.
