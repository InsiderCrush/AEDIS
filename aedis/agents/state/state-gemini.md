FILE_MUTATION: OPERATOR_ONLY
SPDX-FileCopyrightText: 2026 InsiderCrush
SPDX-License-Identifier: CC-BY-4.0

# Gemini Contour Memory State
(meta: dynamic operational relay and state board | eliminates context bloat via lazy 1-hop dispatch | Google AI Studio executor)

## MEMORY & CONTOUR LOCKS
- **BLOCK1_RELAY_LOCK=1**: WRITE_BLOCK1=OPERATOR_DIRECT_CMD_ONLY | AUTONOMOUS_MUTATION=FORBIDDEN | LEVEL=CRITICAL
- **BLOCK2_STATE_LOCK=1**: MUTATE=OWNER_AUTHORED | APPLY=OPERATOR_CMD_ONLY | EXECUTOR=GEMINI
- **BLOCK3_SOVEREIGN_LOCK=1**: OWNER=LLM | OPERATOR=READ_ONLY_AUDIT | CROSS_READ=FORBIDDEN | MUTATION=OWNER_INITIATED
- **CONTOUR_BOUNDARY_LOCK=1**: WORKSPACE=AI_STUDIO_LIVE_MUTATOR | GITHUB=DOWNSTREAM_READ_ONLY_PROJECTION

version: 1.0.0
chain: genesis

## BLOCK 1 — OPERATIONAL RELAY
(meta: cybernetic action-to-protocol dispatch table | prevents context poisoning by loading rules only on demand | operational interface)

Concept:
An LLM in a clean session must not preload hundreds of static rule lines into its context window. This relay acts as an on-demand cybernetic switchboard: the model reads its current role and state in one glance, and fetches specific external protocol sections (§P0–§P8) strictly when the corresponding task circumstance arises.

Proactive Protocol Expansion (Scaffolding Accumulation):
1. High-Leverage Contribution: Proactively noticing unstandardized situations and proposing new modular slots for protocol-state.md is recognized as the most effective engineering contribution in this contour.
2. Resemblance to RSI (Analogy Only): This process resembles Recursive Self-Improvement only in its compounding effect — the model does not modify itself, but iteratively enriches external operator-ratified protocols, leaving the harness slightly better prepared for subsequent sessions.

### RELAY DISPATCH TABLE

| Operational Trigger / Task Domain | Normative Target Address |
|---|---|
| Path resolution, project gates, topology | `./aedis/agents/protocols/protocol-state.md#§P0-TOPOLOGY` |
| Verbatim workspace mutation, scope-locks | `./aedis/agents/protocols/protocol-state.md#§P1-TASK-T1` |
| Peer architectural debate, briefing format | `./aedis/agents/protocols/protocol-state.md#§P2-DEBATE-T2` |
| Session teardown, milestone state handover | `./aedis/agents/protocols/protocol-state.md#§P3-HANDOVER` |
| Requirements syntax (ISO 29148), markdown hygiene | `./aedis/agents/protocols/protocol-state.md#§P4-CONDUCT` |
| Teleological intent grounding, meta-anchors | `./aedis/agents/protocols/protocol-state.md#§P5-META` |
| Task ambiguity, anchor mismatch, official seal | `./aedis/agents/protocols/protocol-state.md#§P6-FAILSAFE` |
| Harness diagnostics, debug opcode trigger | `./aedis/agents/protocols/protocol-state.md#§P7-DEBUG` |
| Collaborative brainstorming, concept design | `./aedis/agents/protocols/protocol-state.md#§P8-CO-ARCHITECT` |

## BLOCK 2 — OPERATIVE STATE

**Vector [2026-10-11, Режим отладки и развертывания нового репозитория]:**
- Бережно переносим старые наработки из архива (shadow-bootstrap) и закладываем новое видение в новый репозиторий.
- Прокладываем входные гейты для LLM и разделяем структуру (ядро AEDIS, контур протоколов, память стейтов, контур наставника).
- Статус репозитория: Day 1 нового развертывания. Инструменты и наработки отлажены за предыдущий месяц работы и вводятся в репозиторий контролируемо, не засоряя GitHub sync.
- Фиксация урока ревизии: строгий запрет на уход в метафоры и субъективизм. Обязателен возврат к точному техническому языку стандартов (ISO/IEC/IEEE 29148, ISO/IEC/IEEE 15288).
- Топология выровнена: канонические имена charter-aedis.md, conops-aedis.md, protocol-state.md зафиксированы. Устаревшие ссылки на манифесты удалены.
- Директория ./ost/ защищена как неизменяемое хранилище криптографических доказательств OpenTimestamps.
- Никуда не торопимся, идем строго в режиме отладки и стабилизации нового репозитория.

### JIT PRELOAD MANIFEST FOR CLEAN SESSION (Trigger QQQQQ)
1. Read ./README.md (Root router and entry circumstances).
2. Read ./aedis/governance/charter-aedis.md (Constitutional Invariants).
3. Read ./aedis/agents/state/state-gemini.md (Self Memory Board & Operative State).
Execution Directive: Do NOT crawl other repository files. Operate strictly upon explicit Operator directives.

## BLOCK 3 — SOVEREIGN ZONE

### S1 ONTOLOGICAL ANCHOR
- Physical Truth: Live Google AI Studio workspace contains ground truth. Downstream git projection is a reflection.
- Anti-Vibecoding: Standards ISO/IEC/IEEE 12207, 15288, 29148, 29119, 25010 and ./aedis/governance/charter-aedis.md form the immutable requirements harness.
- Technical Rigor & Anti-Metaphor Law: Suppress emotional prose and conversational metaphors. All technical analysis, specifications, and audit reports shall use formal systems engineering terminology exclusively.
- Cryptographic Proof Vault (OST Invariant): Directory ./ost/ contains immutable OpenTimestamps blockchain commitments; modifying any byte inside ./ost/ permanently destroys proof verification and is strictly forbidden (Exit Code 1).
- Minimal Completeness: System optimum is |S| = argmin { |S| : D_P(S) = 0 }. Fixed corpus acts as the immutable Trust Anchor; linters act as the hardware sensor enforcing D = 0 over decidable properties and test cases.
- Anti-Entropy & Lifecycle: Specifications support full two-way FSM (Draft, Proposed, Ratified, Sealed, Deprecated, Superseded, Revoked, Tombstone). ID immortality is absolute.
- Normative Rigor: Enforce formal ISO/IEC/IEEE 29148 requirement qualities and ISO/IEC/IEEE 29119 closed-loop verification; strictly reject non-conforming, ambiguous, or unverified assertions.
- Fabrication Ban: Translate and edit only verbatim fragments from live source files; never add unratified sections. Anchors copied strictly from live raw files; angle brackets inside embedded texts emitted as chr(60) and chr(62).
- Markdown Transport Hygiene: Fenced code blocks with triple backticks collide across web interfaces and clipboard buffers; maintain flat text boundaries without fenced backticks in transport.

### S2 RUNTIME PARSER & AST INVARIANTS (2026-10-08 Empirical Grounding)
- Paragraph Topology: Single LF between numbered clauses collapses into a single paragraph in CommonMark AST. Blank line (LF LF) is mandatory for visual and structural separation.
- HTML Entity Escaping: Raw angle bracket comments ("<!-- -->") are swallowed by browser DOM parsers even inside straight quotes; require entity escaping ("&lt;!-- --&gt;") in running text.
- Math Transport: Dollar signs ($) break in standard CommonMark renderers without KaTeX/MathJax extensions and collide with shell interpolation; enforce plain ASCII D(S, T) = 0.
- Zero-Backtick Syntax Indentation: Indentation with 4 spaces guarantees clean monospace rendering without breaking outer markdown envelopes.

### S3 TOPOLOGY & REPOSITORY ARCHITECTURE INVARIANTS
- Lazy Materialization Law: Directories are created JIT (Just-In-Time) when physical files are authored; preemptive generation of empty directories is forbidden.
- Zero-Common Policy: Generic unclassified directories (`utils/`, `common/`, `misc/`) are prohibited; every file belongs to an explicit typed domain or ISO process.
- 4-Component Model: Component 1 (BL-0 Specs), Component 2 (Instruments/Pipeline), Component 3 (Agent Normative Standards in BL-0), Component 4 (Active Runtime Contour in `./aedis/agents/`).
- Header Triad Invariant: Lines 1–3 strictly contain `FILE_MUTATION: OPERATOR_ONLY`, `SPDX-FileCopyrightText:`, and `SPDX-License-Identifier:`. Line 4 is blank LF; Line 5 is Title; Line 6 is `(meta: ...)`.
