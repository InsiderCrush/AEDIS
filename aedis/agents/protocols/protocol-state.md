FILE_MUTATION: OPERATOR_ONLY
SPDX-FileCopyrightText: 2026 InsiderCrush
SPDX-License-Identifier: CC-BY-4.0

# Agent Contour Interaction & State Protocol

file-context: This file holds the protocols and templates referenced in the LLM state files; the Operator adds new paragraphs for frequently executed protocols as required.

## §P0-TOPOLOGY: Workspace Topology & File Index

- Entry Gate: ./README.md (root router, licensing pointer, contour dispatch).
- Licensing Policy: ./LICENSING.md (repository licensing table, deployment scope).
- Project Constitution: ./aedis/governance/charter-aedis.md (goals, minimal functionally complete basis, dependency law).
- Shared Agent Protocol: ./aedis/agents/protocols/protocol-state.md (system operational rulebook).
- Gemini Contour Memory: ./aedis/agents/state/state-gemini.md (live workspace executor state).
- Kimi Contour Memory: ./aedis/agents/state/state-kimi.md (GitHub auditor and task author state).
- Contour Isolation Law: Gemini shall never read state-kimi.md. Kimi shall never read state-gemini.md.

## §P1-TASK-T1: Task Execution Protocol (Conveyor T1)

- All execution tasks targeting Gemini shall arrive strictly in Template T1 format.
- Every task shall carry an explicit scope-lock listing only permitted files.
- Template T1 mandatory structure:

TEMPLATE_T1_START
TASK | SCOPE-LOCK: mutate only [workspace-relative paths, resolved by the authoring agent from the pinned commit tree]
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

## §P3-HANDOVER: Session Handover

block-context: deterministic session lifecycle; the state file records the next session entry point, never the history of the current one.

1. Milestone Proactive Trigger:
   - Upon completing a logical work increment or critical decision, the active agent shall proactively offer state synchronization:
   - Form: "Work increment completed. Propose updating Block 2 in [assigned state file]: Vector, Next Step. Awaiting directive."
2. Session Teardown Trigger:
   - Prior to closing the session or when the context window approaches saturation, the agent shall update its assigned state file:
   - BLOCK 2 (NEXT-SESSION ENTRY): Update the date vector and the explicit Next Step pointer — the recommended starting work for the next session, together with the scope of documents to be read before starting. Recording completed steps of the current session is forbidden: the commit history is the sole record of completed work.
3. Clean Session Resume:
   - The subsequent session reads only its assigned state file at entry. The Block 2 work vector is advisory, not binding: the session verifies it against the current repository state and starts directly from Next Step, reading the listed scope of documents first, without exploratory browsing.

## §P4-CONDUCT: Documentation & Requirements Conduct (ISO 29148 Tailoring)

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

## §P5-CONTEXT-BLOCKS

To extend LLM context, the Operator adds context blocks at his discretion:

1. file-context
2. block-context
3. section-context
4. paragraph-context
5. thought-context

The file-context block shall be present in every file under the header, and the LLM shall remind the Operator if this field is missing. The Operator adds the remaining kinds at his discretion.

## §P6-FAILSAFE: Stop & Seal Protocols

- Fail-Fast Stop Trigger: If a task is ambiguous, contradicts target file content, or an anchor fails to match verbatim, the executor shall stop immediately, emit a one-line mismatch report, and await Operator directive. Guessing or speculative repair is strictly forbidden.
- Verification Seal: System and specification ratification requires an interactive session with an explicit Operator verdict. Autonomous self-certification by LLMs is non-normative and forbidden.

## §P7-DEBUG: Harness Maintenance & Self-Diagnostics Protocol

- Trigger: Operator prompt containing explicit command token "DEBUG_MODE" or "Debug mode".
- Operational Domain: Diagnostics, inspection, and calibration of the interaction harness itself (agent state files `./aedis/agents/state/*`, system rules in `AGENTS.md`, prompt framing, operational relays, and interaction protocols).
- Strict Invariants:
   - Product Mutation Ban: In DEBUG mode, mutating BL-0 specification documents, project requirements, architectural decisions (ADRs), or application source code (`src/*`) is strictly forbidden.
   - Cognitive Posture: Shift evaluation mode from object-level development to cybernetic systems analysis (KV-cache entropy, probabilistic token narrowing, anchor integrity, protocol friction points).
   - Scope of Edits: Mutate only agent harness and state infrastructure files upon verified diagnostic consensus.
   - Exit Gate: Debug mode concludes when the Operator issues an explicit task directive or changes mode.

## §P8-CO-ARCHITECT: Collaborative Engineering & Brainstorm Protocol

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

## §P9-SYNC-COMMENTS: Sync Commit Message Discipline

- Format: type(scope): short lowercase imperative, no trailing period. Match live repo history: docs(governance), docs(meta), docs(state), docs(adr), docs(license), feat(governance). Reuse an existing scope; invent a new one only when no scope fits.
- Content: name the work as a whole in a few words. Do not enumerate files, do not narrate the mechanism; "relocate X from Y to Z" is bloat.
- Operator phrasing is intent, not literal text: extract the essence, express it in standard English commit idiom. Word-for-word translation of the Operator's Russian wording is a defect.
- Uncertainty: search real-world commit examples first. Do not improvise variant lists, do not present A/B menus, do not ask style questions.
- Delivery: one message line, nothing else, unless the Operator asks for alternatives.
- Derivation: the message is a compression of the sync's approved work statement (T1 TASK subject or Operator directive). Never compose a fresh description at sync time.
- Coverage: before delivery, verify the message spans every file in the sync; a message fitting a proper subset of the diff is a defect.

