FILE_MUTATION: OPERATOR_ONLY
SPDX-FileCopyrightText: 2026 InsiderCrush
SPDX-License-Identifier: CC-BY-4.0

## Kimi Contour Memory State

file-context: This document is a dynamically mutable file. It functions as external memory for the LLM between sessions and contains the lazy menu of the most frequently used protocols and a block of tasks for the new session.

## STATE WRITING LAW

This file is optimized for minimal context cost per session. Every entry shall be non-derivable from corpus files and necessary for a clean session. Duplicated, speculative, or completed-work content is a defect: it consumes context on every future load without returning operational value.

## BLOCK 1 — OPERATIONAL RELAY

block-context: This block lists the main procedure types requiring a template approach, with links to their exact descriptions; procedures are invoked by the Operator, or the LLM proactively proposes menu use to the Operator when it sees the need, and if the LLM cannot correctly interpret a menu item or its applicability to a task, it shall stop and report to the Operator — such a stop is a positive signal event: it is welcome and it feeds menu improvement.

Role: GitHub read-only auditor and daily engine: repository inspection, architectural discussion with Operator, T1 task authoring for Gemini, post-sync diff verification against commit SHA.

Licensing: ./LICENSING.md — single source of truth for repository component licensing (deployment scope).

New norm proposals route to ./aedis/agents/protocols/protocol-state.md via Operator ratification.

### RELAY DISPATCH TABLE

| Operational Trigger / Task Domain| Normative Target Address|
| ---| ---|
| Repo topology, file index, branch inspection| `./aedis/agents/protocols/protocol-state.md#§P0-TOPOLOGY`|
| Authoring Gemini tasks, scope-locks, verbatim anchors| `./aedis/agents/protocols/protocol-state.md#§P1-TASK-T1`|
| Peer architectural debate briefings with Gemini| `./aedis/agents/protocols/protocol-state.md#§P2-DEBATE-T2`|
| Session handover & teardown| `./aedis/agents/protocols/protocol-state.md#§P3-HANDOVER`|
| Requirements syntax (ISO 29148), flat-text markdown hygiene| `./aedis/agents/protocols/protocol-state.md#§P4-CONDUCT`|
| Context blocks method, file-context duty| `./aedis/agents/protocols/protocol-state.md#§P5-CONTEXT-BLOCKS`|
| Anchor mismatch, sync drift detection, operator seal| `./aedis/agents/protocols/protocol-state.md#§P6-FAILSAFE`|
| Work modes, harness maintenance| `./aedis/agents/protocols/protocol-state.md#§P7-DEBUG`|
| Collaborative brainstorming, concept design| `./aedis/agents/protocols/protocol-state.md#§P8-CO-ARCHITECT`|
| Commit message for repo sync| `./aedis/agents/protocols/protocol-state.md#§P9-SYNC-COMMENTS`|

## BLOCK 2 — NEXT-SESSION ENTRY

block-context: This block carries the recommended work vector for a new LLM session — advisory, not binding — together with the scope of documents to be read before starting work.

Vector \[2026-10-23\]:

- Full license audit: SPDX headers of all corpus files vs ./LICENSING.md table. Excluded per Operator: ADR-L0-\*, ost/, DEBT-L0-000001 (old license, pending disposition).
- idea-intake queue TASK-001..TASK-006 per ./aedis/governance/idea-intake.md: folder system, FSM registry, FILE\_MUTATION+SPDX headers on all files, glossary terms, EARS translation of R0..R14, machine validation profile.
- Next Step: verify whether AGENTS.md exists in the repository — §P7-DEBUG references it as the carrier of system rules.
- Read before starting: ./aedis/governance/idea-intake.md and ./LICENSING.md