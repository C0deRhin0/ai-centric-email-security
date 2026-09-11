# AI-assisted Email Security

This repository contains adaptable examples for an email-security review workflow. It is a template, not a description of a deployed security operation.

## Safe adaptation

Configure the following privately for each environment:

- mailbox and activation convention;
- AI provider, model, credentials, and request limits;
- confidence/risk routing rules;
- review, escalation, and any containment actions.

The examples are deliberately provider-neutral. Keep real trigger text, operational thresholds, domain-blocking policy, recipient addresses, and production workflow exports in private configuration or internal documentation. Require human review for any automated action that could affect users, mail delivery, or infrastructure.

## Repository contents

- `approach-a-power-automate/` — workflow example for a managed automation platform.
- `approach-b-n8n/` — workflow example for a self-hosted automation platform.
- `shared/` — schemas and prompt templates.
- `docs/` — implementation notes and troubleshooting guidance.

Never commit API keys, production mailbox addresses, or organization-specific operating procedures.
