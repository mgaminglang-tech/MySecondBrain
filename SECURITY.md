# Security Policy

## Scope

MySecondBrain is a public, AI-assisted personal knowledge system. Because knowledge bases can contain sensitive information and AI agents can interact with repository content, security and privacy are treated as first-class concerns.

## Do not commit secrets

Never commit or paste any of the following into this public repository:

- passwords
- API keys
- access or authentication tokens
- private keys
- webhook secrets
- database credentials
- personal or client credentials
- unredacted sensitive personal or client data

Use placeholders such as `YOUR_API_KEY`, `YOUR_ACCESS_TOKEN`, and `YOUR_DATABASE_URL` in documentation and examples.

## AI-agent security boundaries

AI-assisted changes should follow `AGENTS.md`. In particular:

- Do not invent credentials, approvals, test results, or execution evidence.
- Do not expose secrets if they are discovered.
- Do not modify protected paths without explicit authorization.
- Do not perform external writes, sends, workflow activation, production changes, or destructive operations without explicit authorization.
- Prefer narrow retrieval and focused edits over broad vault-wide changes.
- Treat journal and personal knowledge as potentially sensitive data.

## Reporting a vulnerability

If you discover a security issue, please do not publish credentials, exploit details, or sensitive data in a public issue.

Instead, contact the repository owner privately through an appropriate GitHub private communication channel and provide:

1. A short description of the issue.
2. The affected file, workflow, or component.
3. Reproduction steps when safe to provide.
4. The potential impact.
5. A suggested mitigation, if known.

If the issue involves an exposed secret, do not copy the secret into the report. Identify the location and rotate/revoke the credential through the appropriate secure mechanism.

## Public repository warning

This repository is public. A file being present in the repository does not make its contents private. Sensitive personal information, credentials, and client data should remain outside the public repository or be sanitized before publication.
