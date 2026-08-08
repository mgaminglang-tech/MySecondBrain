---
type: system-standard
system: Merv's AI OS
status: draft
version: 1.0
---

# Backup and Recovery Standard

## Purpose

Define reusable controls for recoverable, secret-free backups before risky automation changes and during incidents.

## Required Backup Events

Create or verify an applicable backup:

- before first production activation
- before every production change
- before credential rotation that can affect a workflow
- before restoring or replacing workflow configuration
- after an approved production release
- before client handover

## Backup Contents

Include when applicable:

- exported workflow definition without embedded secrets
- workflow name or reference, environment, version, export timestamp, and operator
- node and connection inventory
- required credential names, never credential values
- non-secret environment references, dependencies, deployment notes, and known limitations
- rollback and restore requirements
- relevant test and release evidence references

## Storage and Retention

- Store backups only in the approved project or recovery location with appropriate access restrictions.
- Exclude secrets and unredacted sensitive client data.
- Record restricted storage as a reference rather than exposing a public link.
- Define retention and deletion according to the client agreement or applicable policy; do not assume one universal period.

## Ownership

- The project owner defines the approved location and retention requirement.
- The operator creates the export and records a checksum or other integrity evidence when available.
- A reviewer confirms that the backup opens, contains the intended workflow, and excludes prohibited data.
- The production approver confirms rollback readiness before deployment.

## Recovery Readiness

A backup is recovery-ready only when:

- the workflow and environment are correctly identified
- the file is readable and structurally complete
- the version and timestamp are recorded
- restore requirements and required credential names are documented
- integrity evidence is available when practical
- the only recoverable copy will not be overwritten
- production restoration has separate explicit approval

After an approved restore, validate configuration, connections, credential references, triggers, and downstream side effects before reactivation.

## Related Standards

- [[30 Systems/Standard Automation Project Workflow|Standard Automation Project Workflow]]
- [[Client Data Handling Standard]]
- [[Credential and Secrets Management Standard]]
