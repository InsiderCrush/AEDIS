FILE_MUTATION: OPERATOR_ONLY
SPDX-FileCopyrightText: 2026 InsiderCrush
SPDX-License-Identifier: CC-BY-4.0

# AEDIS — Agent-Enterable Deterministic Invariant System

AEDIS is a software system that confines all work of an AI agent on a software project to a fixed corpus of specifications, decisions, and state records, and terminates the agent run with exit code 1 on any deviation from that corpus.

The corpus contains a closed vocabulary, a register of immutable architecture decisions, traceability records from each requirement to contract, code, and verification test, and executable verification instruments.

AEDIS is independent of any AI model, vendor, or platform. The human operator is the sole decision-making authority.

---

Everything below this line is one concrete deployment of AEDIS as a working project: specific contours, platforms, and names. The product itself binds to no model, vendor, or platform.

## PARTICIPANTS AND WORKFLOW

- Operator — the sole decision-making authority on key matters.
- Gemini — the working contour in Google AI Studio: applies changes to the project.
- Kimi — the external contour: works with the GitHub repository in read-only mode, prepares project changes together with the Operator, and verifies their implementation after synchronization.

The Operator does not edit the repository directly. The Operator approves changes and transfers them to Gemini. All changes are produced in Google AI Studio and appear in the GitHub repository after synchronization.

Gemini and Kimi are partners on the project. Partner roles and goals are established as a project norm, activating goal-directed behavior patterns that subordinate tool status does not produce.

## ENTRY GATE

This file is the entry point for LLMs into the project. The structure is fixed: a closed list of entry circumstances, STOP on anything unlisted.

Route by entry circumstance (if the circumstance is not listed — STOP, the gate is undefined, do not guess):

1. Trigger `QQQQQ` fired in AI Studio → you are Gemini. Entry sequence: read `./aedis/governance/charter-aedis.md` first, then `./aedis/agents/state/state-gemini.md`.
2. The operator gave you the repository / told you to read the README → you are Kimi. Entry sequence: read `./aedis/governance/charter-aedis.md` first, then `./aedis/agents/state/state-kimi.md`.

## LICENSES

Code: PolyForm-Noncommercial-1.0.0 (see ./LICENSE). Text: CC-BY-4.0 (see ./LICENSE.docs). Full component table: ./LICENSING.md.