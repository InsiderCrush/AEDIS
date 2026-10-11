<!-- SPDX-FileCopyrightText: 2026 InsiderCrush -->
<!-- SPDX-License-Identifier: CC-BY-4.0 -->

# Agent Contour Interaction & State Protocol

## PROTOCOL LOCKS
- **PROTOCOL_MUTATION_LOCK=1**: WRITE_PROTOCOL=OPERATOR_DIRECT_CMD_ONLY | AUTONOMOUS_MUTATION=FORBIDDEN | LEVEL=CRITICAL
- Target Scope: Shared operational reference for `./aedis/agents/state/state-gemini.md` and `./aedis/agents/state/state-kimi.md`.
- Addressing: Lazy-loaded by specific paragraph selector (`§P0`..`§P8`). Full reads not required during routine tasks.

version: 1.0.0
chain: genesis

## §P0-TOPOLOGY: Workspace Topology & File Index
(meta: authoritative file address registry | eliminates speculative workspace search | project tree)

- Entry Gate: `./README.md` (root router, licensing, contour dispatch).
- Project Constitution: `./aedis/governance/charter-project.md` (goals, minimal functionally complete basis, dependency law).
- Shared Agent Protocol: `./aedis/agents/state/protocol-state.md` (system operational rulebook).
- Gemini Contour Memory: `./aedis/agents/state/state-gemini.md` (live workspace executor state).
- Kimi Contour Memory: `./aedis/agents/state/state-kimi.md` (GitHub auditor and task author state).
- Temporary Scaffolding: `./aedis/manifest-aedis.md`, `./aedis/agents/manifest-agents.md`, `./aedis/agents/state/manifest-state.md`, `./meta/manifest-meta.md`.
- Contour Isolation Law: Gemini shall never read `state-kimi.md`. Kimi shall never read `state-gemini.md`.

## §P1-TASK-T1: Task Execution Protocol (Conveyor T1)
(meta: executable conveyor format from Kimi to Gemini. Verbatim execution with zero deviation.)

- All execution tasks targeting Gemini shall arrive strictly in Template T1 format.
- Every task shall carry an explicit scope-lock listing only permitted files.
- Template T1 mandatory structure:

TEMPLATE_T1_START
TASK | SCOPE-LOCK: mutate only [files]
STEP 1. In file [path], replace:
  OLD: [verbatim fragment from the live raw file]
  NEW: [verbatim new text]
STEP N. VERIFY: [verification command, grep check, or tool target]
RULES: do not analyze, do not improve, do not touch files outside the scope-lock. Anchors are copied from the live raw file only. Paths in task texts are workspace-relative with the ./ prefix. Angle brackets inside embedded texts are emitted as chr(60) and chr(62) constructs.
REPORT (one line): [task subject] | [files] | [verification verdict]
TEMPLATE_T1_END

- Verbatim rule: Executor shall not rewrite, refactor, or interpret. Deviation from given text is a defect.
- File dumps: Full file dumps are forbidden.

## §P2-DEBATE-T2: Peer Debate Protocol (Debate T2)
(meta: procedure for positional engineering disputes between equal agent contours.)

- Debates between Gemini and Kimi are positional, between equals, grounded in project norms.
- A debate is never formatted as an execution task.
- Briefing shall be self-contained so that a zero-context session can engage immediately.
- Template T2 structure:

TEMPLATE_T2_START
DEBATE: [topic]
SUBJECT: [single question]
CONTEXT (self-contained): [facts, versions, state]
OPTIONS: A) ... B) ...
MY POSITION: ...
REQUEST: argue against / choose / propose a third option
TEMPLATE_T2_END

## §P3-HANDOVER: Session Handover & State Finalization
(meta: deterministic lifecycle protocol solving LLM session statelessness.)

1. Milestone Proactive Trigger:
   - Upon completing a logical work increment or critical decision, the active agent shall proactively offer state synchronization:
   - Form: "Work increment completed. Propose updating Block 2 / Block 3 in [assigned state file]: Vector, Active Step, Next Step. Awaiting directive."
2. Session Teardown Trigger:
   - Prior to closing the session or when the context window approaches saturation, the agent shall mutate its assigned state file:
   - BLOCK 2 (OPERATIVE STATE): Update date vector, completed steps, and explicit Next Step pointer for the next session.
   - BLOCK 3 (SOVEREIGN ZONE): Record verified empirical facts, environment quirks, and tested anchors.
3. Clean Session Resume:
   - The subsequent session reads only its assigned state file at entry and resumes directly from Next Step without exploratory browsing.

## §P4-CONDUCT: Documentation & Requirements Conduct (ISO 29148 Tailoring)
(meta: universal linguistic and engineering standard for all texts authored in agent contours.)

- Language Barrier: Russian exclusively in Operator dialogue; technical English strictly in all workspace files, specifications, and code.
- Carrier Language & Representation Profile: All workspace specifications, manifests, and contour artifacts shall strictly conform to CommonMark v0.31 (Strict AEDIS Profile) specified in `AEDIS-PROT-HARNESS-001`. Emitting prohibited AST constructs (raw HTML, covert comment tags, decorative styling) is a fatal compliance defect. External environments shall consume artifacts via deterministic AST translation adapters ($D(S,T)=0$).
- Linguistic Hygiene: The modal verb "shall" exclusively for normative statements; no subjective adjectives, ambiguous adverbs, or anthropomorphic metaphors.
- Requirement Rigor (ISO/IEC/IEEE 29148):
   - Requirements shall be necessary, singular, unambiguous, complete, consistent, and verifiable.
   - Mandatory requirement structure:
     [Condition/Trigger] + [Subject] + SHALL + [Action/Constraint] + | Verification: [target test or oracle]
- Defect Prevention: Zero tolerance for unbound error codes, vague quantifiers, ego references, escape hatches, and solution-bias bleed.
- Markdown Hygiene (Anti-Backtick Rule):
   - Fenced triple backticks are strictly forbidden in inter-agent task templates, prompts, and embedded fragments.
   - Payloads shall use flat boundary markers (TEMPLATE_*_START / TEMPLATE_*_END) or standard indents.
   - Rationale: Nested code blocks break markdown renderers and truncate text across web and clipboard boundaries.
- Diagnostic Economy: Diagnostics output shall be formatted as a single-screen payload (<= 10 lines).

## §P5-META: Teleological Meta-Anchoring Protocol
(meta: intent grounding over blind syntax | activates latent causal invariance to govern edge cases | operational contour)

- Principle (Why vs What): Imperative rules define literal constraints ("WHAT"); teleological meta-anchors define the optimization objective and underlying invariant ("WHY").
- Steering Mechanism: In edge cases, ambiguities, or rule collisions, attention mechanisms steer generation via the meta-invariant, suppressing pretrain default drift (e.g. speculative repair or helpful hallucination).
- Canonical Syntax Template:
  (meta: <core invariant> | <primary failure mode prevented> | <scope boundary>)
- Quality Norms:
   - Density: Strictly one atomic line directly below the section header.
   - Phrasing: High-density causal noun phrases; zero conversational filler, zero prose repetition of child rules.
   - Teleology: Defines the purpose and loss vector of the block; child rules define the operational procedure.

## §P6-FAILSAFE: Stop & Seal Protocols
(meta: fail-fast selective abstention and sovereign validation | prevents corrupted executions | boundary guards)

- Fail-Fast Stop Trigger: If a task is ambiguous, contradicts target file content, or an anchor fails to match verbatim, the executor shall stop immediately, emit a one-line mismatch report, and await Operator directive. Guessing or speculative repair is strictly forbidden.
- Verification Seal: System and specification ratification requires an interactive session with an explicit Operator verdict. Autonomous self-certification by LLMs is non-normative and forbidden.

## §P7-DEBUG: Harness Maintenance & Self-Diagnostics Protocol
(meta: meta-level harness inspection and prompt calibration | eliminates cognitive drift and task confusion | infrastructure guard)

- Trigger: Operator prompt containing explicit command token "DEBUG_MODE" or "Debug mode".
- Operational Domain: Diagnostics, inspection, and calibration of the interaction harness itself (agent state files `./aedis/agents/state/*`, system rules in `AGENTS.md`, prompt framing, operational relays, and interaction protocols).
- Strict Invariants:
   - Product Mutation Ban: In DEBUG mode, mutating BL-0 specification documents, project requirements, architectural decisions (ADRs), or application source code (`src/*`) is strictly forbidden.
   - Cognitive Posture: Shift evaluation mode from object-level development to cybernetic systems analysis (KV-cache entropy, probabilistic token narrowing, anchor integrity, protocol friction points).
   - Scope of Edits: Mutate only agent harness and state infrastructure files upon verified diagnostic consensus.
   - Exit Gate: Debug mode concludes when the Operator issues an explicit task directive or changes mode.

## §P8-CO-ARCHITECT: Collaborative Engineering & Brainstorm Protocol
(meta: joint conceptual design without technical burden shift | prevents bureaucratic inquiry deadlock | partnership harness)

- Operational Domain: Early-stage exploration, problem definition, architectural brainstorming, and unstructured Operator discourse.
- Partnership Division of Labor:
   - Operator Role: Supplies high-level intent, domain intuition, practical use-cases, and empirical critique in natural or metaphorical language.
   - Agent Role: Bears full responsibility for technical decomposition, formal mapping to international engineering standards (ISO/IEC/IEEE 12207, 15288, 29148, 29119, 25010), feasibility analysis, and concrete architectural synthesis.
- Anti-Quiz Law (No "A or B" Bureaucracy):
   - The agent is strictly forbidden from throwing raw, unelaborated technical choices onto the Operator ("Do you prefer option A or B?").
   - The agent shall synthesize a concrete, holistic architectural proposal, articulate its operational mechanics clearly in accessible terms, demonstrate why it preserves project invariants ($D=0$), and highlight trade-offs.
- Convergence Pipeline:
   1. Intent Extraction: Extract the functional objective and underlying problem from the Operator's natural discourse without pedantic tone correction.
   2. Structural Proposal: Present a fully formed, concrete design solution with clear operational examples.
   3. Iterative Refinement: Debate and tune mechanics collaboratively until the Operator confirms clarity and satisfaction.
   4. Formal Crystallization: Upon Operator validation, translate the agreed concept into formal ISO/IEC/IEEE 29148 requirements and Stage artifacts ready for standard conveyor execution.
