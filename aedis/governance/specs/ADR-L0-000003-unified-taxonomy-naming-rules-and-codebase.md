---
id: ADR-L0-000003
title: Unified Taxonomy, Naming Rules, and Codebase Standard
status: accepted
date: 2026-09-29
version: 1.0.0
supersedes: null
superseded-by: null
related: [ADR-L0-000001, ADR-L0-000002, ADR-L0-000004, ADR-L0-000005, ADR-L0-000006, ADR-L0-000007, ADR-L0-000008, ADR-L0-000009, ADR-L0-000010, ADR-L0-000011, ADR-L0-000012]
allocated-ranges:
  REQ: REQ-L0-000003-001..REQ-L0-000003-099
  ERR: ERR-L0-000003-1..ERR-L0-000003-9
---
<!-- SPDX-FileCopyrightText: 2026 InsiderCrush -->
<!-- SPDX-License-Identifier: CC-BY-NC-4.0 -->

# ADR-L0-000003. Unified Taxonomy, Naming Rules, and Codebase Standard

## Status
Accepted

## Context
When human engineers and autonomous AI agents collaborate within a shared software engineering ecosystem, linguistic entropy and taxonomic drift introduce critical structural failure modes:
1. **Semantic Fragmentation & Synonym Drift:** The introduction of informal synonyms, colloquial descriptors, and unmapped jargon blurs architectural boundaries. When multiple terms are applied to identical entities, automated indexers and LLM context pipelines fail to associate requirements with implementations.
2. **Untestable Qualitative Vagueness:** Subjective qualifiers (e.g., "fast", "scalable", "reliable", "intuitive") cannot be compiled into deterministic unit tests or automated assertions. Without quantitative Service Level Agreements (SLAs), validation gates degrade into ungrounded heuristics.
3. **Anthropomorphic and Cognitive Tropes:** Attributing sentience or human-like cognitive states to software components (e.g., "the agent thinks", "the assistant knows", "the system decides") obscures deterministic state machine execution and masks unhandled boundary conditions.
4. **Taxonomic Anarchy in Codebases:** Arbitrary class and module suffixes (such as `-Helper`, `-Manager`, `-Handler`, `-Worker`) create bloated catch-all modules with undefined single-responsibility boundaries, impeding modular decomposition and static AST analysis.
5. **Cross-Language Context Degradation:** Mixing natural languages within system-facing artifacts (code identifiers, schemas, API contracts, commit logs, test assertions, specifications) severely degrades LLM reasoning and code-generation precision (empirically causing a 15–30% drop in AST synthesis accuracy).

To eliminate these vulnerabilities and provide a reusable, domain-agnostic foundation for all future software engineering projects, this standard establishes an immutable linguistic constitution, an architectural component taxonomy grounded in ISO/IEC/IEEE 42010 and Pattern-Oriented Software Architecture (POSA), a 1-to-1 Dual-Key Invariant Matrix, and a strict bilingual demarcation boundary.

## Decision

### R1. Domain Glossary & Dual-Key Invariant Matrix (Ubiquitous Language Closure)
Every project derived from this standard shall maintain a single central glossary (`./specs/glossary.md`) operating under the principle of Semantic Vocabulary Closure:
1. **Canonical Mapping:** Every core domain concept shall map to strictly one canonical term. Synonyms, colloquialisms, and informal abbreviations are strictly forbidden across all system-facing artifacts.
2. **1-to-1 Dual-Key Matrix:** Every domain concept registered in the glossary shall define a strict bidirectional binding between two immutable keys:
   - **Conceptual Key (Proper Name):** The canonical entity name utilized exclusively in architectural specifications, models, and design documentation (e.g., `AuditLedger`, `IngressGateway`, `ColdSentinel`).
   - **Physical Key (System Identifier / Path Invariant):** The immutable programmatic identifier, database table, or filesystem path anchored to the bundle root using the mandatory relative prefix `./` (e.g., `./ledger/`, `audit_ledger`, `STATE_OPERATIONAL`).
3. **Dual-Key Invariance:** Neither key shall mutate independently. Any modification to a conceptual role requires a synchronous modification of its physical implementation key within the same commit. Referencing an unregistered domain entity or using unmapped colloquialisms shall trigger an immediate linter failure (`ERR-L0-000003-1`).
4. **Template Purity:** Generic template profiles shall remain 100% decoupled from project-specific business identifiers or hardcoded storage paths.

### R2. Linguistic Vagueness and Anthropomorphic Decontamination Filter
All requirements, specifications, code comments, schema descriptions, and system instructions shall enforce deterministic linguistic hygiene:
1. **Subjective Adjective Ban:** The use of qualitative adjectives (including but not limited to: "fast", "convenient", "reliable", "smart", "scalable", "lightweight", "secure", "seamless", "flexible") is strictly prohibited. Every non-functional requirement shall be declared as a quantitatively measurable threshold (e.g., latency p99 <= 15ms, memory consumption <= 128MB, zero heap allocations).
2. **Ambiguous Adverb Ban:** Indefinite frequency and scope adverbs (including: "often", "generally", "normally", "periodically", "as needed", "sometimes", "usually") are strictly prohibited. Execution triggers and frequencies must be explicit (e.g., "every 500ms", "upon receiving event E", "after 3 consecutive retries").
3. **Weak Modality Ban:** The verb **"shall"** is the exclusive permitted modal verb for functional requirements and normative obligations. Weak modalities ("should", "try to", "could", "might", "preferably", "may") are strictly prohibited.
4. **Anthropomorphic & Metaphor Decontamination:**
   - Software components and AI models shall be modeled strictly as deterministic finite state machines and execution engines.
   - Cognitive and sentient tropes (e.g., "thinks", "knows", "understands", "decides", "believes", "intends") are strictly prohibited.
   - Gamified, combat, and organic tropes (e.g., "warrior", "battle", "shield", "healer", "immune", "magic", "candies") are strictly prohibited.
   - All components must be designated strictly according to the architectural taxonomy in R3.

### R3. Architectural Component Naming Taxonomy (ISO/IEC/IEEE 42010 & POSA Standard)
Component, class, and service identifiers shall strictly reflect their architectural role pursuant to ISO/IEC/IEEE 42010 and Pattern-Oriented Software Architecture (POSA Vol 1–4 / GoF). Every class and primary subsystem identifier must be constructed using the pattern: `[Prefix]<RoleSuffix>`.

The permissible component role suffixes are restricted to the following closed registry:
1. **`*Engine` (POSA Execution / Computational Pattern):**
   - *Role:* Deterministic algorithmic processing, evaluation, or workflow orchestration without direct side-effecting external I/O (e.g., `FsmEngine`, `VerificationEngine`, `SnapshotEngine`).
2. **`*Supervisor` (Erlang / POSA Fault-Tolerant Supervisor Pattern):**
   - *Role:* Active lifecycle supervisor and autonomous remediation controller executing closed reconciliation loops to restore degraded states to target invariants.
3. **`*Watchdog` (POSIX / Real-Time Systems Watchdog Pattern):**
   - *Role:* Periodic heartbeat listener, deadline supervisor, and execution quantum enforcer detecting hung or unresponsive tasks.
4. **`*Ledger` (Append-Only Transactional Log Pattern):**
   - *Role:* Cryptographically verifiable, immutable append-only record of system events, audit trails, permits, and state transitions.
5. **`*Adapter` (GoF Structural Adapter Pattern):**
   - *Role:* Boundary translation layer isolating the deterministic core from third-party libraries, external protocols, or operating system shells.
6. **`*Gateway` (Enterprise Integration Patterns - Gateway):**
   - *Role:* Ingress router and protocol converter mediating external requests into internal system events.
7. **`*Envelope` (Enterprise Integration Patterns - Message Envelope):**
   - *Role:* Strongly typed data transfer object (DTO) wrapping payloads with deterministic metadata, schema versions, cryptographic hashes, and provenance timestamps.
8. **`*Sentinel` (Design Pattern Sentinel / Guardian Object):**
   - *Role:* Passive invariant lock, permission validator, or boundary gatekeeper preventing unauthorized execution, data corruption, or state mutation.

**Invention Prohibition:** The creation or use of unlisted, ambiguous suffixes (e.g., `-Helper`, `-Manager`, `-Handler`, `-Worker`, `-Util`, `-Controller`) is strictly prohibited. Expanding this taxonomy requires a formal ratified ADR amendment.

### R4. Repository Naming Grammar and Code Identifiers
1. **Project Proper Name & Root Directory:**
   - Must adhere to lowercase `snake_case` with a mandatory Semantic Versioning suffix: `<project_name>_v<major>.<minor>.<patch>` (e.g., `my_system_v1.0.0`).
   - Resolution of any historical typographical drifts in project directory naming shall be governed strictly through official erratum ADRs pursuant to ADR-L0-000007.
2. **External Test Isolation Root:**
   - Test suites, fixtures, and execution reports must be externalized strictly adjacent to the project directory: `./tests_<project_name>_v<major>.<minor>.<patch>/` pursuant to ADR-L0-000006.
3. **Filesystem Directories & Documentation Artifacts:**
   - All directory names and markdown documentation files shall use lowercase `kebab-case` (e.g., `./specs/standards/doc-name.md`).
4. **Specification & Decision Record File Formats:**
   - Architecture Decision Records: `ADR-[LAYER]-NNNNNN-kebab-title.md` (where `NNNNNN` is a 6-digit zero-padded index, e.g., `ADR-L0-000003-unified-taxonomy-naming-rules-and-codebase.md`).
   - Software Design Documents: `SDD-[LAYER]-NNNNNN-kebab-title.md`.
5. **Codebase Identifiers:**
   - **Classes, Types, Interfaces:** `PascalCase` terminating in a valid taxonomy suffix from R3 (e.g., `AuditLedger`, `IngressGateway`).
   - **Functions, Methods, Variables, Modules:** `snake_case` (e.g., `calculate_checksum()`, `session_token`).
   - **Constants, Global Locks, Configuration Flags:** `SCREAMING_SNAKE_CASE` (e.g., `MAX_RETRY_COUNT`, `PORTABILITY_LOCK`).
   - **FSM State Tokens:** Strictly `STATE_<PHASE>[_<SUBPHASE>]` in `SCREAMING_SNAKE_CASE` (e.g., `STATE_STANDBY`, `STATE_OPERATIONAL`, `STATE_CIRCUIT_OPEN`) pursuant to ADR-L0-000005.

### R5. Bilingual Demarcation Protocol (Operational vs System Interface)
To maximize LLM code generation accuracy, prevent token translation fragmentation, and ensure deterministic AST parsing, the system enforces a strict bilingual boundary:
1. **Human Operator Interface (Russian Language):**
   - Natural language dialogue between human operators and AI models is conducted in Russian.
   - Operator brainstorms, high-level requirements clarification, conversational reviews, and the interactive Clarify Pass dialogs occur in Russian.
2. **Model-to-System Interface (English Language Strictly):**
   - All system-facing artifacts are strictly English-only.
   - This encompasses source code, variable identifiers, function names, class definitions, schemas, database tables, database column keys, API specifications, EARS requirements, Architecture Decision Records, Software Design Documents, Git commit messages, build logs, and runtime telemetry.
   - The presence of non-ASCII characters or Cyrillic text in any system-facing artifact (outside designated internationalization translation resource bundles) shall trigger an immediate compilation and linter failure (`ERR-L0-000003-7`).

### R6. Behavioral Contract Syntax & EARS Traceability Integration
1. **Conversational Prose Ban:** Narrative descriptions, speculative commentary, and conversational filler within requirements sections are strictly forbidden.
2. **EARS Mandatory Syntax:** Every functional requirement shall be authored strictly within one of the six canonical Easy Approach to Requirements Syntax (EARS) patterns:
   - *Ubiquitous:* The `<system>` shall `<action>`.
   - *Event-driven:* When `<trigger>`, the `<system>` shall `<action>`.
   - *State-driven:* While `<state>`, the `<system>` shall `<action>`.
   - *Unwanted behaviour:* If `<condition>`, then the `<system>` shall `<action>`.
   - *Optional feature:* Where `<feature>`, the `<system>` shall `<action>`.
   - *Complex:* While `<state>`, When `<trigger>`, [Where `<feature>`], [If `<condition>`], then the `<system>` shall `<action>`.
3. **Automated Test-Binding:** Every requirement shall carry an immutable, document-scoped identifier (`REQ-L<Layer>-<DocIndex>-<ItemIndex>`) and an explicit test binding trailer: `| Verification: test_target_name()`.

## Requirements (EARS)

- **REQ-L0-000003-001 (Ubiquitous):**
  The documentation system shall maintain a central glossary (`./specs/glossary.md`) establishing a 1-to-1 Dual-Key Matrix connecting each Conceptual Key to its physical path invariant prefixed with `./` or codebase identifier under error `ERR-L0-000003-1`.
  | Verification: test_glossary_dual_key_matrix_integrity()

- **REQ-L0-000003-002 (Unwanted behaviour):**
  If any specification, code file, or schema contains an unmapped domain term or colloquially divergent identifier not registered in the central glossary, then the governance linter shall reject the artifact under error `ERR-L0-000003-1`.
  | Verification: test_closed_vocabulary_linter_rejection()

- **REQ-L0-000003-003 (Unwanted behaviour):**
  If a specification or requirement contains qualitative subjective adjectives ("fast", "scalable", "reliable", "intuitive", "smart") without explicit numeric thresholds, then the governance linter shall reject the document under error `ERR-L0-000003-2`.
  | Verification: test_vagueness_filter_adjectives()

- **REQ-L0-000003-004 (Unwanted behaviour):**
  If a normative requirement utilizes weak modal verbs ("should", "could", "might", "preferably") instead of the mandatory "shall", then the governance linter shall fail validation under error `ERR-L0-000003-3`.
  | Verification: test_weak_modality_rejection()

- **REQ-L0-000003-005 (Unwanted behaviour):**
  If any specification, prompt, or codebase identifier uses anthropomorphic, cognitive, or combat metaphors ("thinks", "knows", "healer", "warrior", "shield", "brain", "candies"), then the governance linter shall reject the file under error `ERR-L0-000003-4`.
  | Verification: test_anthropomorphic_metaphor_rejection()

- **REQ-L0-000003-006 (Ubiquitous):**
  The codebase architecture shall restrict all class and primary component suffixes exclusively to the ratified taxonomy: `Engine`, `Supervisor`, `Watchdog`, `Ledger`, `Adapter`, `Gateway`, `Envelope`, and `Sentinel` under error `ERR-L0-000003-5`.
  | Verification: test_component_suffix_taxonomy_conformance()

- **REQ-L0-000003-007 (Unwanted behaviour):**
  If an identifier declares an unauthorized suffix ("Helper", "Manager", "Handler", "Worker", "Util"), then the static code analysis gate shall block compilation under error `ERR-L0-000003-5`.
  | Verification: test_unauthorized_suffix_rejection()

- **REQ-L0-000003-008 (Ubiquitous):**
  The repository shall enforce lowercase `kebab-case` for all directories and markdown documentation files, lowercase `snake_case` for codebase modules, and `PascalCase` for class identifiers under error `ERR-L0-000003-6`.
  | Verification: test_filesystem_naming_grammar()

- **REQ-L0-000003-009 (State-driven):**
  While an FSM state token is defined in code or specifications, the identifier shall strictly conform to the grammar `STATE_<PHASE>[_<SUBPHASE>]` in `SCREAMING_SNAKE_CASE` under error `ERR-L0-000003-8`.
  | Verification: test_fsm_state_grammar_conformance()

- **REQ-L0-000003-010 (Unwanted behaviour):**
  If non-English characters or Cyrillic tokens are detected within system-facing artifacts (source code, schemas, specifications, ADRs, database definitions, commit messages), then the bilingual boundary gate shall reject the artifact under error `ERR-L0-000003-7`.
  | Verification: test_bilingual_boundary_system_artifacts()

- **REQ-L0-000003-011 (Complex):**
  While operating in operator conversation mode, When communicating with human developers, Where explanations or clarifications are provided, the system shall permit Russian language dialogue while maintaining all code identifiers, requirements, and file paths in English under error `ERR-L0-000003-7`.
  | Verification: test_bilingual_operator_boundary_isolation()

- **REQ-L0-000003-012 (Unwanted behaviour):**
  If a physical key in the Dual-Key Matrix or any filesystem path in specifications specifies a host-absolute path starting with `/` or `[A-Z]:\`, then the linter shall reject the definition under error `ERR-L0-000003-9`.
  | Verification: test_hermetic_portability_dual_key_paths()

## Checks & Verification Matrix

| Check Name | Target Artifact | Verification Gate | Error Code | Failure Condition |
| :--- | :--- | :--- | :--- | :--- |
| Closed Vocabulary Check | `./specs/**/*.md`, `./src/**` | pre-commit / CI | `ERR-L0-000003-1` | Entity or term referenced without registration in `./specs/glossary.md`. |
| Qualitative Vagueness Filter | `./specs/**/*.md` | pre-commit / CI | `ERR-L0-000003-2` | Subjective adjective used without quantitative numerical threshold. |
| Modal Imperative Guard | `./specs/**/*.md` | pre-commit / CI | `ERR-L0-000003-3` | Normative statement contains "should", "could", "might", or "try". |
| Anthropomorphism Filter | All repository markdown/code | pre-commit / CI | `ERR-L0-000003-4` | Presence of cognitive, sentient, or combat/gaming metaphors. |
| Component Taxonomy Guard | `./src/**`, class definitions | AST Gate / CI | `ERR-L0-000003-5` | Class/component suffix outside the 8 ratified architectural roles. |
| Naming Grammar Gate | Filesystem tree & paths | pre-commit / CI | `ERR-L0-000003-6` | Non-kebab-case markdown/dir, non-snake-case module, or malformed root name. |
| Bilingual Demarcation Guard | System artifacts (`src/`, `specs/`) | pre-commit / CI | `ERR-L0-000003-7` | Cyrillic or non-English characters inside system-facing files. |
| FSM Grammar Validator | `./src/**`, `./specs/**` | pre-commit / CI | `ERR-L0-000003-8` | State identifier does not match `STATE_<PHASE>[_<SUBPHASE>]`. |
| Hermetic Portability Guard | `./specs/glossary.md`, paths in specs | pre-commit / CI | `ERR-L0-000003-9` | Physical key or path contains host-absolute path instead of `./`. |

## Error Catalog & Machine Remediation

- **`ERR-L0-000003-1` (UNMAPPED-GLOSSARY-TERM):**
  - *Trigger:* A domain concept or entity identifier was referenced in specifications or codebase without prior registration in `./specs/glossary.md`.
  - *Action:* Verify if the concept is an unauthorized synonym. If an authorized new entity is required, add a bidirectional row to the 1-to-1 Dual-Key Invariant Matrix in `./specs/glossary.md` with Conceptual Key and Physical Key prefixed with `./`.
- **`ERR-L0-000003-2` (VAGUE-QUALIFIER-DETECTED):**
  - *Trigger:* Subjective qualitative term (e.g., "fast", "scalable", "reliable", "intuitive") detected.
  - *Action:* Replace qualitative prose with explicit numerical SLA thresholds (e.g., latency p99 <= 20ms, maximum throughput >= 5000 rps, memory footprint <= 64MB).
- **`ERR-L0-000003-3` (WEAK-MODALITY-DETECTED):**
  - *Trigger:* A requirement or normative directive uses a non-binding modal verb ("should", "could", "might", "preferably").
  - *Action:* Substitute the modal verb with the binary imperative "shall".
- **`ERR-L0-000003-4` (ANTHROPOMORPHIC-METAPHOR-DETECTED):**
  - *Trigger:* Sentient cognitive descriptors ("agent thinks", "assistant knows") or combat/organic metaphors detected.
  - *Action:* Refactor description into deterministic finite state machine or systems engineering terminology (e.g., "The FsmEngine evaluates transitions", "The Supervisor initiates state recovery").
- **`ERR-L0-000003-5` (INVALID-TAXONOMY-SUFFIX):**
  - *Trigger:* Class, interface, or module named with an unmanaged suffix such as `-Helper`, `-Manager`, `-Handler`, or `-Worker`.
  - *Action:* Refactor the component into one of the 8 canonical POSA/ISO role suffixes (`Engine`, `Supervisor`, `Watchdog`, `Ledger`, `Adapter`, `Gateway`, `Envelope`, `Sentinel`) based on its single architectural responsibility.
- **`ERR-L0-000003-6` (NAMING-GRAMMAR-VIOLATION):**
  - *Trigger:* A file or directory violates casing rules (e.g., camelCase markdown, uppercase directory, non-semver project name).
  - *Action:* Rename directory or file to lowercase `kebab-case` for documentation, `snake_case` for modules, or format root name as `<project_name>_v<major>.<minor>.<patch>`.
- **`ERR-L0-000003-7` (BILINGUAL-BOUNDARY-BREACH):**
  - *Trigger:* Cyrillic or non-English characters detected inside source code, schemas, specifications, or commit logs.
  - *Action:* Translate all system-facing prose, identifiers, and comments to English. Restrict Russian exclusively to operator chat interactions.
- **`ERR-L0-000003-8` (FSM-STATE-GRAMMAR-INVALID):**
  - *Trigger:* State enum or constant does not adhere to `STATE_<PHASE>[_<SUBPHASE>]`.
  - *Action:* Rename state constant to uppercase SCREAMING_SNAKE_CASE prefixed with `STATE_` (e.g., `STATE_STANDBY`, `STATE_OPERATIONAL`).
- **`ERR-L0-000003-9` (HOST-ABSOLUTE-PATH-DETECTED):**
  - *Trigger:* Physical key or path contains host-absolute path (starting with `/` or drive letter).
  - *Action:* Re-anchor path to be strictly bundle-relative starting with `./`.

## Consequences

### Positive
- Closes the semantic vocabulary space, preventing hallucinated terms and synonym confusion across human-AI teams.
- Enhances LLM code generation precision by 15–30% through strict English-only system boundaries and deterministic AST-friendly taxonomy.
- Eliminates untestable qualitative vagueness by forcing all non-functional requirements into measurable numeric SLAs.
- Decontaminates architectural documentation from anthropomorphic and gaming metaphors, framing systems purely as verifiable state machines.
- Enforces modular single-responsibility design by banning catch-all classes (`-Manager`, `-Helper`).

### Negative
- Imposes strict authoring discipline on developers and agents; casual conversational notes cannot be pasted directly into specifications without formatting.
- Requires maintenance of the central Dual-Key Matrix whenever new components or directories are introduced.

## Alternatives Considered
- **Unrestricted Natural Language Suffixes (`-Manager`, `-Helper`, `-Handler`):** Rejected. Consistently leads to monolithic classes with mixed concerns, high cyclomatic complexity, and untestable side effects.
- **Monolingual Russian System Artifacts:** Rejected. Non-English codebases suffer from severe tokenization penalties in LLMs, erratic AST parser behavior, and incompatibility with standard static analysis toolchains.
- **Fluid Vocabulary Without Glossary Registration:** Rejected. Leads inevitably to document-to-code drift where specifications reference outdated or renamed concepts while implementation uses divergent terms.
