## Purpose
This folder documents a deterministic invoice processing workflow execution path with explicit authority boundaries and audit artifacts.

## What this documents
- Single execution path: inbound invoice → ERP-safe draft.
- 7-stage execution path with SLA and ownership.
- Authority boundaries (Allowed / Not Allowed) for AI, rules engine, and humans.
- Audit artifacts, retention, and access surfaces.

## What this does NOT do
This documentation does not define policy or certify compliance.
Authority assignment remains with policy owners.
Implementation responsibility remains with the deploying organization.

## Why this matters for review
Deterministic execution paths are used to avoid hidden branches, undocumented assumptions, and silent overrides.
Authority boundaries and audit artifacts are surfaced so review can evaluate behavior without assumptions.

## Status
Converted into Markdown from “Review-Ready Workflow Documentation — Deterministic Workflow Decomposition for SaaS & AI”.
