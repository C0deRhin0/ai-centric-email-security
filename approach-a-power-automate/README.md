# Power Automate email-review reference

This directory contains a portable workflow example and HTML reply templates. It is a starting point for a separately reviewed test deployment, rather than a ready-to-activate security service.

## Included artifacts

- [flow-definition.json](flow-definition.json) — workflow reference to inspect in the target platform.
- [templates/](templates/) — response layouts for the supported verdicts.
- [Shared response schema](../shared/ai-response-schema.json) — assessment fields and accepted values.

## Adaptation

1. Read the [architecture and implementation limits](../docs/architecture.md).
2. Import or reconstruct the example in a test workspace with fictional messages.
3. Supply connection references, mailbox selection, provider settings, and credentials using the platform's private configuration facilities.
4. Validate response parsing, error handling, template rendering, and all delivery paths.
5. Implement and verify operator approval before enabling user-affecting actions.

The n8n export currently routes verdicts to send nodes without a confidence/human-approval gate. Do not assume the older design narrative is enforced by the exported graph. Email content is included in AI requests; review that data boundary before using any real message.

For Microsoft OAuth context, see [OAuth setup](../docs/oauth-setup.md). Provider plans, connector licensing, model names, and tenant consent are environment-specific; this repository does not guarantee free hosting, service availability, or a fixed setup time.
