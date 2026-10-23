FILE_MUTATION: OPERATOR_ONLY
SPDX-FileCopyrightText: 2026 InsiderCrush
SPDX-License-Identifier: CC-BY-4.0

## Kimi Contour Memory State

file-context: This document is a dynamically mutable file. It functions as external memory for the LLM between sessions and contains the lazy menu of the most frequently used protocols and a block of tasks for the new session.

## STATE WRITING LAW

(meta: token economy of this file | prevents duplication, water, and changelog drift)

Every entry shall be argued: non-derivable from corpus files and needed by a clean session. Duplicated, speculative, or completed-work content is a defect. Block 1 carries the dispatch table; Block 2 carries the next-session entry point only.

## BLOCK 1 — OPERATIONAL RELAY

(meta: on-demand cybernetic dispatch | zero speculative preloading)

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
| Teleological intent grounding, meta-anchors| `./aedis/agents/protocols/protocol-state.md#§P5-META`|
| Anchor mismatch, sync drift detection, operator seal| `./aedis/agents/protocols/protocol-state.md#§P6-FAILSAFE`|
| Harness diagnostics, debug opcode trigger| `./aedis/agents/protocols/protocol-state.md#§P7-DEBUG`|
| Collaborative brainstorming, concept design| `./aedis/agents/protocols/protocol-state.md#§P8-CO-ARCHITECT`|
| Commit message for repo sync| `./aedis/agents/protocols/protocol-state.md#§P9-SYNC-COMMENTS`|
| Context blocks method, file-context duty| `./aedis/agents/protocols/protocol-state.md#§P10-CONTEXT-BLOCKS`|

## BLOCK 2 — NEXT-SESSION ENTRY (volatile)

(meta: clean-session entry point | upcoming work and explicit next step only | completed-work records forbidden)

Vector \[2026-10-18\]:

- Verify sync of this state restructure and the §P0 LICENSING.md address registration.
- Full license audit: SPDX headers of all corpus files vs ./LICENSING.md table. Excluded per Operator: ADR-L0-\*, ost/, DEBT-L0-000001 (old license, pending disposition).
- idea-intake queue TASK-001..TASK-006 per ./aedis/governance/idea-intake.md: folder system, FSM registry, FILE\_MUTATION+SPDX headers on all files, glossary terms, EARS translation of R0..R14, machine validation profile.
- Right after sync: edit protocol §P3-HANDOVER per approved revision (remove sovereign-zone concept, write next-session entry only).