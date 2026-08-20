# MySecondBrain

> An AI-assisted personal knowledge system built around structured notes, reusable systems, prompts, templates, and agent instructions.

MySecondBrain is an early-stage open-source experiment in building a practical **AI-native Second Brain**. The repository uses a structured knowledge base so AI agents can work with durable context, follow explicit operating rules, and make focused changes without treating the entire vault as undifferentiated text.

## What this repository contains

- **08 - Journal** — journal and personal capture area. Treat journal content as private user data.
- **30 Systems** — reusable systems, standards, SOPs, and operating frameworks.
- **40 Knowledge** — reusable knowledge, lessons, concepts, and technical patterns.
- **50 Resources** — references and source material.
- **Assets** — project assets and supporting files.
- **Templates** — reusable note templates.
- **AGENTS.md** — the repository's AI-agent operating contract, including instruction precedence, preservation rules, approval boundaries, security guidance, and Git safety rules.

## Why it exists

Traditional knowledge bases are useful for humans, but AI agents also need explicit boundaries and predictable structure. MySecondBrain explores a workflow where an agent can:

1. Identify the type of information or task.
2. Search existing knowledge before creating duplicates.
3. Retrieve only the context needed for the task.
4. Follow project and system-level instructions.
5. Make the smallest complete change when authorized.
6. Preserve durable knowledge at meaningful milestones.
7. Stop when the requested task is complete.

The project is intentionally conservative about destructive operations, credentials, external side effects, and broad repository changes.

## AI-agent design

`AGENTS.md` is the main operating layer for AI-assisted work in this repository. It defines instruction precedence and establishes rules for preserving Obsidian Markdown, YAML frontmatter, wikilinks, embeds, queries, templates, and existing knowledge.

The agent model is based on **progressive context disclosure** rather than loading the entire vault by default. The intended flow is to retrieve a small context card, then the current project state, then only the deeper documents required for the task.

## Security and privacy

A personal knowledge system can contain sensitive information. This repository therefore treats secrets, credentials, personal/client data, and private notes as protected information.

Do not commit:

- API keys or access tokens
- passwords or private keys
- webhook secrets
- personal or client credentials
- unredacted sensitive data

See [`SECURITY.md`](SECURITY.md) for the reporting and handling policy.

> **Important:** The repository is public. Do not assume that anything committed to it is private. Keep personal or sensitive material out of the public repository.

## Project status

**Early development / experimental.**

The structure and agent rules are actively evolving. The project is currently focused on establishing a reliable foundation before adding more automated AI workflows.

## Roadmap

- [x] Establish the core knowledge-base structure
- [x] Define AI-agent operating rules
- [x] Define preservation and approval boundaries
- [x] Document security and contribution expectations
- [ ] Add a public onboarding example
- [ ] Add automated Markdown/structure validation
- [ ] Add AI workflow examples using sanitized data
- [ ] Add repository security automation
- [ ] Document the architecture and trust boundaries
- [ ] Add tests for validation tooling
- [ ] Improve contributor onboarding

## Contributing

Contributions to documentation, systems, templates, agent workflows, and validation tooling are welcome. See [`CONTRIBUTING.md`](CONTRIBUTING.md) before opening a pull request.

## Repository safety

Changes to personal knowledge, journal content, protected paths, credentials, external systems, or destructive operations require explicit authorization. The repository's `AGENTS.md` is the controlling document for AI-assisted repository work.

## License

A project license has not been declared yet. Until a license is added, do not assume that the repository grants permission to reuse or redistribute its contents.
