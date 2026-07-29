# Security Policy

This is a public repository.

## Never commit

- HubSpot private-app tokens
- MCP credentials
- API keys
- passwords or cookies
- `.env` files
- private CRM records or exports
- real customer/contact data
- confidential portal identifiers
- unsanitised screenshots
- private Notion content

## Test evidence

Use clearly labelled test records. Redact or omit unnecessary internal IDs. Screenshots must be checked before publication.

## Secrets

Store secrets only in approved environment-variable or credential-management systems. If a secret is committed, rotate it immediately and remove it from repository history.
