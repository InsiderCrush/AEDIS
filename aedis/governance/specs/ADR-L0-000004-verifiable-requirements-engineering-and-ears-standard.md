---
id: ADR-L0-000004
title: Verifiable Requirements Engineering and EARS Standard
status: accepted
date: 2026-09-29
version: 1.0.0
supersedes: null
superseded-by: null
related: [ADR-L0-000001, ADR-L0-000002, ADR-L0-000003, ADR-L0-000005, ADR-L0-000006, ADR-L0-000007, ADR-L0-000008, ADR-L0-000009, ADR-L0-000010, ADR-L0-000011, ADR-L0-000012]
allocated-ranges:
  REQ: REQ-L0-000004-001..REQ-L0-000004-099
  ERR: ERR-L0-000004-1..ERR-L0-000004-99
---
<!-- SPDX-FileCopyrightText: 2026 InsiderCrush -->
<!-- SPDX-License-Identifier: CC-BY-NC-4.0 -->

# ADR-L0-000004. Verifiable Requirements Engineering and EARS Standard

## Status
Accepted

## Context
In collaborative software engineering systems where human developers and autonomous AI agents interact, unstructured natural language requirements introduce critical points of failure across the engineering lifecycle:
1. **Ambiguity and Interpretive Divergence ("Vibe-Coding"):** Informal user stories and conversational prompts permit multiple incompatible interpretations. Autonomous models synthesize code matching speculative assumptions rather than deterministic architectural constraints.
2. **Untestable Qualitative Vagueness:** Subjective qualifiers (e.g., "fast", "scalable", "reliable", "intuitive", "robust") cannot be compiled into deterministic unit tests, benchmark assertions, or automated test fixtures.
3. **Compound and Monolithic Statements:** Combining multiple functional triggers and side effects into single narrative paragraphs obscures error handling, prevents modular test coverage, and obscures fault domains.
4. **Omission of Unwanted Behavior and Boundary Conditions:** Happy-path requirements frequently omit negative condition handling, timeouts, resource exhaustion, and circuit-breaker behavior, creating unhandled runtime crashes.
5. **Implementation Leakage:** Conflating required external behavior with internal implementation choices (e.g., specifying concrete database brands or cache technologies in requirements) couples requirements prematurely to transient technical details.
6. **Linguistic and Taxonomic Inconsistency:** Alternating between informal synonyms for actors, systems, and states causes semantic fragmentation, corrupting automated traceability graphs and static verification gates.

The **Easy Approach to Requirements Syntax (EARS)**, originally formulated in 2009 by Alistair Mavin et al. at Rolls-Royce plc (IEEE RE'09) and proven across safety-critical domains (NASA, Airbus, medical and automotive systems), provides a constrained natural language grammar designed to eliminate these failure modes. 

However, classical requirements engineering was designed for manual human review. In modern AI-native engineering, requirements must function as **deterministic, executable behavioral contracts** for Spec-Driven Development (SDD), autonomous code synthesis, and continuous CI governance.

To bridge this divide, this standard establishes the **MyEARS** profile: an open, verifiable requirements engineering standard that integrates Rolls-Royce EARS grammar with mandatory test-case binding (`| Verification: test_target_name()`), quantitative Service Level Agreements (SLAs), an immutable closed catalog of 8 requirement anti-patterns, and automated gatekeeper validation.

## Decision

### R1. Syntactic Baseline & Public Open Standard (MyEARS Profile)
1. **Syntactic Foundation:** The repository adopts the open standard **EARS (Rolls-Royce / IEEE RE'09)** as its exclusive grammar for functional and non-functional requirements.
2. **The MyEARS Profile:** This standard augments baseline EARS with four mandatory AI-native engineering invariants:
   - **Deterministic Identifier Allocation:** Every requirement must declare an immutable, document-scoped identifier (`REQ-L<Layer>-<DocIndex>-<ItemIndex>`) pursuant to ADR-L0-000002.
   - **Quantitative SLA Invariant:** Every non-functional attribute, performance constraint, capacity limit, or retry ceiling must be declared as a quantitative, measurable metric (e.g., milliseconds, bytes, requests-per-second, retry count). Qualitative adjectives trigger immediate rejection (`ERR-L0-000004-5`).
   - **Mandatory Verification-Metadata Binding:** Every requirement must conclude with an explicit test-binding trailer designating the automated verification target:
     ```
     | Verification: test_target_name()
     ```
     A requirement lacking a verifiable test binding or containing an ungrounded placeholder is non-compliant and triggers gatekeeper rejection (`ERR-L0-000004-7`).
   - **One-to-One Acceptance Criteria Mapping:** In all Software Design Documents (SDD), acceptance criteria `AC-X.Y` must map 1-to-1 to formal `REQ-L<Layer>-<DocIndex>-<ItemIndex>` items.
3. **Canonical Upstream Repository:** The canonical upstream reference for the standard is established at `<vcs_repository_url>`. Downstream projects adopt MyEARS as an external baseline profile.
4. **Semantic Versioning:** The MyEARS standard is governed by Semantic Versioning (`vMAJOR.MINOR.PATCH`). Any breaking change to syntactic parsing rules, clause sequence, or mandatory keywords requires a major version increment.

### R2. The Six Canonical EARS Patterns

All system requirements across all specifications, design documents, and decision records shall strictly conform to one of the six canonical EARS patterns:

#### Pattern 1: Ubiquitous
- **Syntax:** `The <system> shall <action>.`
- **Semantics:** Active continuously and unconditionally across the entire lifecycle of the system. Represents fundamental system invariants, architectural boundaries, or ubiquitous operational constraints.
- **Verification Type:** Baseline invariant test, executed on every build and CI cycle.
- **Example:**
  ```
  The state storage ledger shall calculate a SHA-256 digest over every appended record block.
  | Verification: test_ledger_append_sha256_digest()
  ```

#### Pattern 2: Event-driven
- **Syntax:** `When <trigger>, the <system> shall <action>.`
- **Semantics:** Triggered immediately upon the occurrence of a discrete external stimulus, system event, or message arrival.
- **Verification Type:** Event-listener test: stimulate event $\rightarrow$ assert expected response.
- **Pairing Obligation:** For every event-driven requirement, the author must evaluate and declare corresponding unwanted behavior requirements (Pattern 4) governing event timeouts, corrupt payloads, and boundary failures.
- **Example:**
  ```
  When a signed state mutation transaction is submitted, the verification engine shall validate its cryptographic signature within 15 ms.
  | Verification: test_transaction_signature_verification_latency()
  ```

#### Pattern 3: State-driven
- **Syntax:** `While <state>, the <system> shall <action>.`
- **Semantics:** Active continuously throughout the entire duration that the system occupies a specified operating state or lifecycle mode, terminating immediately when the state transitions.
- **Verification Type:** State fixture test: enter state $\rightarrow$ assert behavior $\rightarrow$ exit state $\rightarrow$ assert behavior ceases.
- **Example:**
  ```
  While in STATE_STANDBY, the ingress gateway shall reject inbound user mutation commands with an error code.
  | Verification: test_standby_mutation_rejection()
  ```

#### Pattern 4: Unwanted behaviour
- **Syntax:** `If <condition>, then the <system> shall <action>.`
- **Semantics:** Dictates system response to unexpected events, runtime errors, invalid inputs, resource exhaustion, or security violations.
- **Verification Type:** Fault-injection test: simulate failure condition $\rightarrow$ assert recovery, isolation, and error code.
- **Example:**
  ```
  If the disk persistence layer fails to acknowledge a write within 250 ms, then the storage supervisor shall transition to STATE_CIRCUIT_OPEN and emit a high-priority diagnostic alert.
  | Verification: test_disk_timeout_circuit_breaker()
  ```

#### Pattern 5: Optional feature
- **Syntax:** `Where <feature>, the <system> shall <action>.`
- **Semantics:** Active only in product configurations, environments, or deployment tiers where a specific feature flag, hardware peripheral, or optional subsystem is enabled.
- **Verification Type:** Configuration matrix test: feature enabled $\rightarrow$ assert active; feature disabled $\rightarrow$ assert inert.
- **Example:**
  ```
  Where telemetry compression is enabled, the export engine shall compress outbound audit frames using zstandard level 3.
  | Verification: test_telemetry_compression_zstd()
  ```

#### Pattern 6: Complex
- **Syntax:** `While <state>, When <trigger>, [Where <feature>], [If <condition>], then the <system> shall <action>.`
- **Semantics:** Combines multiple preconditions, state contexts, triggers, and contingency branches within a single deterministic sentence.
- **Canonical Clause Ordering Rule:** Clause keywords must follow the exact, unalterable canonical sequence:
  1. `While` (State precondition)
  2. `When` (Discrete trigger)
  3. `Where` (Optional feature gate, if applicable)
  4. `If` (Negative condition or error branch, if applicable)
  5. `then the <system> shall` (Mandatory system response)
- **Verification Type:** Multi-condition integration test validating state, trigger, and branch paths.
- **Example:**
  ```
  While in STATE_OPERATIONAL, When an unverified schema modification is detected, If automatic remediation is disabled, then the governance linter shall abort execution and emit an alert.
  | Verification: test_unverified_schema_manual_remediation_abort()
  ```

#### Pattern Selection Matrix

| Question to Ask | Canonical Pattern | Primary Keyword |
| :--- | :--- | :--- |
| Is this an invariant active unconditionally across system lifecycle? | **1. Ubiquitous** | `The <system> shall` |
| Is this an action initiated immediately by an external or internal stimulus? | **2. Event-driven** | `When <trigger>, the <system> shall` |
| Is this behavior active throughout the duration of a defined state? | **3. State-driven** | `While <state>, the <system> shall` |
| Is this an exception flow, error recovery, or boundary defense? | **4. Unwanted behaviour** | `If <condition>, then the <system> shall` |
| Is this functionality gated by a feature flag, license, or config? | **5. Optional feature** | `Where <feature>, the <system> shall` |
| Does the requirement combine multiple states, triggers, or conditions? | **6. Complex** | `While ..., When ..., then the <system> shall` |

### R3. Closed Register of Eight Requirements Anti-Patterns

Static linters and CI verification gates shall enforce complete zero-tolerance rejection against the eight canonical requirement anti-patterns:

```mermaid
flowchart TD
    Req[Requirements Input] --> P1{Modal verb == 'shall'?}
    P1 -- No --> E1[ERR-L0-000004-1: Weak Modality]
    P1 -- Yes --> P2{Contains escape clause?}
    P2 -- Yes --> E2[ERR-L0-000004-2: Escape Clause]
    P2 -- No --> P3{Contains coordinate 'and'?}
    P3 -- Yes --> E3[ERR-L0-000004-3: Compound Requirement]
    P3 -- No --> P4{Specifies internal implementation?}
    P4 -- Yes --> E4[ERR-L0-000004-4: Implementation Leakage]
    P4 -- No --> P5{Contains unquantified adjective?}
    P5 -- Yes --> E5[ERR-L0-000004-5: Qualitative Vagueness]
    P5 -- No --> P6{Follows canonical EARS order?}
    P6 -- No --> E6[ERR-L0-000004-6: Clause Order Violation]
    P6 -- Yes --> P7{Has '| Verification:' trailer?}
    P7 -- No --> E7[ERR-L0-000004-7: Missing Test Binding]
    P7 -- Yes --> Pass[Valid EARS Contract]
```

#### 1. Weak Modalities
- **Prohibited Forms:** "should", "could", "might", "preferably", "ideally", "may", "try to", "aims to".
- **Rule:** The word **"shall"** is the exclusive permitted modal verb for system obligations. System requirements are binary and non-negotiable.

#### 2. Escape Clauses
- **Prohibited Forms:** "if possible", "as appropriate", "at system discretion", "generally", "normally", "periodically", "as necessary", "to the extent feasible".
- **Rule:** If a condition cannot be deterministically evaluated by code, state machine, or boolean logic, it is an unverified assumption and must be rejected.

#### 3. Compound Requirements
- **Prohibited Forms:** Multiple system actions conjoined by "and", "as well as", or comma-separated lists of distinct side effects.
- **Rule:** Exactly one atomic action per requirement. A compound statement must be decomposed into separate atomic requirements with unique identifiers.

#### 4. Implementation Leakage
- **Prohibited Forms:** Mandating concrete internal classes, commercial software libraries, concrete SQL tables, or specific storage technologies inside functional requirement sentences.
- **Rule:** Requirements govern observable external black-box behavior, contracts, and SLAs. Concrete architectural decisions belong in Architecture Decision Records (ADRs).

#### 5. Subjective Qualifiers Without Measurable Thresholds
- **Prohibited Forms:** "fast", "scalable", "reliable", "intuitive", "user-friendly", "seamless", "high-performance", "secure", "lightweight".
- **Rule:** Every qualitative claim must be replaced with an explicit numerical Service Level Agreement (SLA): latency percentiles (p99 $\le$ X ms), throughput ($\ge$ Y RPS), memory ceilings ($\le$ Z MB), or availability nines.

#### 6. Omission of Unwanted Behaviour
- **Prohibited Forms:** Defining happy-path triggers without defining system handling for edge cases, failures, timeouts, corrupt inputs, or unauthorized access.
- **Rule:** Every event-driven requirement must have corresponding unwanted behavior requirements (Pattern 4) covering failure and boundary branches.

#### 7. Synonymy and Taxonomic Drift
- **Prohibited Forms:** Alternating between synonyms for the same entity (e.g., mixing "user", "operator", "client", "agent", "consumer").
- **Rule:** Every core domain concept must map 1-to-1 to the canonical term defined in the project glossary (`./specs/glossary.md`) pursuant to ADR-L0-000003.

#### 8. Wordiness and Preamble Noise
- **Prohibited Forms:** Introductory narratives, conversational explanations, speculative rationale, or background essays embedded within requirement lines.
- **Rule:** Requirement clauses must begin strictly with the canonical EARS keyword without introductory fluff.

#### Comparative Anti-Pattern Reference Matrix

| Anti-Pattern Defect | Non-Compliant Formulation (Prohibited) | Compliant EARS Contract (Mandatory) |
| :--- | :--- | :--- |
| **1. Weak Modality** | The system should try to refresh authentication tokens. | When an authentication token reaches within 60 seconds of expiration, the security engine shall refresh the token. |
| **2. Escape Clause** | The engine shall flush cache records periodically as appropriate. | When cache memory utilization exceeds 85%, the cache supervisor shall evict the least recently used records until utilization drops below 70%. |
| **3. Compound Action** | The gateway shall validate headers and parse payload and store to DB. | 1. When a request is received, the gateway shall validate headers.<br>2. When headers are valid, the gateway shall parse the payload.<br>3. When payload is parsed, the gateway shall persist the record. |
| **4. Implementation Leak** | The system shall use Redis cluster for session token storage. | The session manager shall retrieve stored session tokens with p99 latency $\le$ 5 ms. |
| **5. Qualitative Vagueness** | The search engine shall return query results quickly. | When a query is submitted, the search engine shall return matching results within 200 ms for datasets up to 1,000,000 items. |
| **6. Omission of Negative Path** | When valid credentials are provided, the system shall issue a session token. | *Required Negative Pair:* If submitted credentials do not match stored credentials, then the authentication engine shall reject the request with HTTP 401 within 100 ms. |
| **7. Synonymy Drift** | The system shall notify the user, client, and operator. | The notification engine shall dispatch the alert event to the Operator. *(Term bound to ./specs/glossary.md)* |
| **8. Preamble Noise** | Since operators need fast feedback during deployment, the tool shall show status. | When deployment initiates, the deployment supervisor shall emit status updates every 1,000 ms. |

### R4. Boundaries of the EARS Standard
EARS is a specialized behavioral specification standard. It does not supersede or replace other architectural artifacts:
1. **Architectural Rationale & Invariants:** Governed exclusively by Architecture Decision Records (ADRs).
2. **System Structural Topology:** Governed by C4 Architecture Models (Levels 1–4) and UML/Mermaid state diagrams.
3. **Data Schemas & Protocols:** Governed by typed schema contracts (Protobuf, JSON Schema, OpenAPI, Pydantic).
4. **Implementation Workflows:** Governed by SDD implementation plans (`plan.md`) and task breakdown checklists (`tasks.md`).

## Requirements (EARS)

- **REQ-L0-000004-001 (Ubiquitous):**
  The requirements specification system shall enforce the adoption of the six canonical EARS patterns for all functional requirements across all specification documents under error `ERR-L0-000004-9`.
  | Verification: test_ears_canonical_patterns_enforcement()

- **REQ-L0-000004-002 (Unwanted behaviour):**
  If a functional requirement contains a modal verb other than "shall" (including "should", "could", "might", "may", "preferably"), then the governance linter shall reject the document under error `ERR-L0-000004-1`.
  | Verification: test_weak_modality_linter_rejection()

- **REQ-L0-000004-003 (Unwanted behaviour):**
  If a requirement contains an escape clause or ambiguous conditional ("if possible", "as appropriate", "generally", "normally", "at discretion"), then the governance linter shall reject the document under error `ERR-L0-000004-2`.
  | Verification: test_escape_clause_linter_rejection()

- **REQ-L0-000004-004 (Unwanted behaviour):**
  If a requirement combines multiple distinct system responses using coordinate conjunctions ("and", "as well as"), then the governance linter shall reject the requirement under error `ERR-L0-000004-3`.
  | Verification: test_compound_requirement_linter_rejection()

- **REQ-L0-000004-005 (Unwanted behaviour):**
  If a requirement specifies concrete implementation mechanisms (internal class names, commercial brand identifiers, or concrete database engines) instead of observable external behavior and SLAs, then the governance linter shall reject the specification under error `ERR-L0-000004-4`.
  | Verification: test_implementation_leakage_rejection()

- **REQ-L0-000004-006 (Unwanted behaviour):**
  If a non-functional requirement specifies qualitative subjective adjectives ("fast", "scalable", "reliable", "intuitive", "robust") without explicit numeric thresholds, then the governance linter shall reject the document under error `ERR-L0-000004-5`.
  | Verification: test_qualitative_vagueness_rejection()

- **REQ-L0-000004-007 (Event-driven):**
  When an event-driven requirement is declared (Pattern 2), the specification author shall pair it with at least one corresponding unwanted behavior requirement (Pattern 4) governing failure or boundary violations under error `ERR-L0-000004-10`.
  | Verification: test_unwanted_behavior_pairing_audit()

- **REQ-L0-000004-008 (State-driven):**
  While evaluating a Complex EARS requirement (Pattern 6), the parser shall enforce the strict clause ordering `While` -> `When` -> `Where` -> `If` -> `then the <system> shall` under error `ERR-L0-000004-6`.
  | Verification: test_complex_pattern_clause_order()

- **REQ-L0-000004-009 (Ubiquitous):**
  The requirements specification system shall bind every functional requirement to an explicit test case via the metadata trailer syntax `| Verification: test_target_name()` under error `ERR-L0-000004-7`.
  | Verification: test_requirement_verification_trailer_presence()

- **REQ-L0-000004-010 (Unwanted behaviour):**
  If a functional requirement lacks a valid verification metadata trailer or references a non-existent test case, then the traceability gate shall fail verification under error `ERR-L0-000004-7`.
  | Verification: test_missing_test_binding_failure()

- **REQ-L0-000004-012 (Unwanted behaviour):**
  If a breaking change is made to the syntactic parsing rules or clause ordering of the EARS standard, then the specification release engine shall increment the major semantic version (SemVer) under error `ERR-L0-000004-8`.
  | Verification: test_semver_major_bump_on_syntax_break()

## Checks & Verification Matrix

| Check Name | Target Artifact | Verification Gate | Error Code | Failure Condition |
| :--- | :--- | :--- | :--- | :--- |
| Modal Imperative Guard | `./specs/**/*.md` | pre-commit / CI | `ERR-L0-000004-1` | Requirement uses modal verb other than "shall". |
| Escape Clause Filter | `./specs/**/*.md` | pre-commit / CI | `ERR-L0-000004-2` | Requirement contains subjective escape clause. |
| Atomicity Linter | `./specs/**/*.md` | pre-commit / CI | `ERR-L0-000004-3` | Requirement contains coordinate conjunctions joining multiple actions. |
| Implementation Leak Gate | `./specs/**/*.md` | pre-commit / CI | `ERR-L0-000004-4` | Functional requirement specifies internal implementation or brand names. |
| Quantitative NFR Filter | `./specs/**/*.md` | pre-commit / CI | `ERR-L0-000004-5` | Subjective qualitative adjective used without numeric threshold. |
| Complex Clause Order Linter | `./specs/**/*.md` | pre-commit / CI | `ERR-L0-000004-6` | Complex pattern violates `While` -> `When` -> `Where` -> `If` sequence. |
| Test Verification Trailer Gate | `./specs/**/*.md` | pre-commit / CI | `ERR-L0-000004-7` | Requirement missing `\| Verification: test_target_name()` trailer. |
| Semantic Versioning Guard | Standard releases | CI Release Step | `ERR-L0-000004-8` | Breaking grammar change released without SemVer major bump. |
| EARS Pattern Adherence Gate | `./specs/**/*.md` | pre-commit / CI | `ERR-L0-000004-9` | Requirement does not conform to one of the six canonical EARS patterns. |
| Event Unwanted Pairing Gate | `./specs/**/*.md` | pre-commit / CI | `ERR-L0-000004-10` | Event-driven requirement lacks corresponding unwanted behavior requirement. |

## Error Catalog & Machine Remediation

- **`ERR-L0-000004-1` (WEAK-MODALITY-REJECTION):**
  - *Trigger:* A requirement contains non-binding modal verbs ("should", "could", "might", "preferably", "may").
  - *Remediation:* Substitute the weak modal verb with the binary imperative "shall". If the capability is conditional, restructure using Pattern 5 (`Where <feature>, the <system> shall...`).
- **`ERR-L0-000004-2` (ESCAPE-CLAUSE-DETECTED):**
  - *Trigger:* A requirement contains non-deterministic hedging ("if possible", "as appropriate", "generally", "normally").
  - *Remediation:* Replace vague conditional clauses with concrete boolean predicates or quantitative boundary triggers.
- **`ERR-L0-000004-3` (COMPOUND-REQUIREMENT-DETECTED):**
  - *Trigger:* A requirement statement combines multiple distinct actions using "and", "as well as", or complex sentence structures.
  - *Remediation:* Decompose the compound statement into individual atomic requirements, assigning each a unique `REQ-L<Layer>-<DocIndex>-<ItemIndex>` identifier.
- **`ERR-L0-000004-4` (IMPLEMENTATION-LEAKAGE-DETECTED):**
  - *Trigger:* Functional requirement prescribes concrete internal technologies, libraries, or database engines.
  - *Remediation:* Refactor the requirement into black-box observable behaviors and SLAs. Migrate concrete technology decisions into an Architecture Decision Record (ADR).
- **`ERR-L0-000004-5` (UNQUANTIFIED-NFR-DETECTED):**
  - *Trigger:* Subjective qualitative terms ("fast", "scalable", "reliable", "intuitive", "robust") detected without numeric metrics.
  - *Remediation:* Specify explicit numeric metrics (latency p99 $\le$ X ms, throughput $\ge$ Y RPS, memory $\le$ Z MB, retry count $\le$ N).
- **`ERR-L0-000004-6` (COMPLEX-CLAUSE-ORDER-VIOLATION):**
  - *Trigger:* Complex pattern keywords appear out of the canonical order (`While` $\rightarrow$ `When` $\rightarrow$ `Where` $\rightarrow$ `If` $\rightarrow$ `then`).
  - *Remediation:* Reorder the clauses to follow the strict canonical sequence.
- **`ERR-L0-000004-7` (MISSING-TEST-VERIFICATION-TRAILER):**
  - *Trigger:* Requirement is missing `| Verification: test_target_name()` or references an unmapped test placeholder.
  - *Remediation:* Append the explicit test binding trailer specifying the corresponding automated test function.
- **`ERR-L0-000004-8` (SEMVER-SYNTAX-BREAK-UNBUMPED):**
  - *Trigger:* Syntax rules or keyword ordering altered without incrementing the major version in metadata frontmatter.
  - *Remediation:* Increment the major version number (`vX.0.0`) in document frontmatter and changelog.

- **`ERR-L0-000004-9` (NON-CANONICAL-EARS-PATTERN):**
  - *Trigger:* A requirement statement fails to match any of the six recognized EARS pattern structures.
  - *Remediation:* Reformat the requirement into one of the 6 canonical patterns (Ubiquitous, Event-driven, State-driven, Unwanted behaviour, Optional feature, Complex).

- **`ERR-L0-000004-10` (UNPAIRED-UNWANTED-BEHAVIOR):**
  - *Trigger:* An event-driven requirement lacks an associated failure-handling or boundary violation requirement.
  - *Remediation:* Formulate and link an unwanted behavior requirement (`Pattern 4: If <condition>, then the <system> shall...`) covering exception paths.

## Consequences

### Positive
- Converts natural language requirements into deterministic, machine-parsable specifications suitable for autonomous AI code synthesis and automated validation.
- Eliminates vibe-coding by establishing an unambiguous 6-pattern syntactic standard and automated gatekeeper rejection.
- Guarantees complete test traceability by mandating that every requirement declare a concrete verification binding (`| Verification: test_target_name()`).
- Replaces subjective qualitative debates with measurable, verifiable Service Level Agreements (SLAs).

### Negative
- Requires strict authoring discipline; developers cannot paste informal conversational user stories into specification documents.
- Demands upfront analysis of negative conditions and failure modes (Pattern 4) before code fabrication begins.

## Alternatives Considered
- **Unconstrained Agile User Stories ("As a user, I want... so that..."):** Rejected. While intuitive for human product backlogs, user stories lack deterministic trigger/state semantics, regularly omit error handling, and produce severe specification drift when parsed by autonomous LLM agents.
- **Formal Mathematical Verification (TLA+, Z notation, Alloy):** Rejected for general-purpose requirement specifications. Formal mathematical methods impose extreme authoring overhead and steep learning curves, making them impractical for standard web, systems, and enterprise development.
- **Unstructured Given-When-Then (Gherkin):** Rejected as a primary requirements grammar. While effective for acceptance test execution, Gherkin often encourages overly detailed UI-level step-by-step descriptions rather than high-level architectural behavioral invariants.
