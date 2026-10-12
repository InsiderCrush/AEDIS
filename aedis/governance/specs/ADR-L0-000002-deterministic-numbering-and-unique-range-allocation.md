---
id: ADR-L0-000002
title: Deterministic Numbering and Unique Range Allocation
status: accepted
date: 2026-09-29
version: 1.0.0
supersedes: null
superseded-by: null
related: [ADR-L0-000001, ADR-L0-000003, ADR-L0-000004, ADR-L0-000007, ADR-L0-000009, ADR-L0-000010]
allocated-ranges:
  REQ: REQ-L0-000002-001..REQ-L0-000002-099
  ERR: ERR-L0-000002-1..ERR-L0-000002-9
---
<!-- SPDX-FileCopyrightText: 2026 InsiderCrush -->
<!-- SPDX-License-Identifier: CC-BY-NC-4.0 -->

# ADR-L0-000002. Deterministic Numbering and Unique Range Allocation

## Status
Accepted

## Context
In collaborative software engineering environments comprising human developers and autonomous AI agents, non-deterministic identifier allocation introduces severe structural vulnerabilities across the engineering lifecycle:
1. **Identifier Collisions (Document-to-Document Drift):** When requirement identifiers are allocated fluidly across broad architectural layers without document scoping, concurrent authors inevitably generate colliding IDs with incompatible semantics. Such collisions corrupt traceability graphs and invalidate test-to-requirement assertions.
2. **Loss of Deterministic Traceability (Document-to-Code Drift):** Fluid, non-deterministic numbering or volatile UUIDs prevent developers and static analyzers from inferring ownership, layer placement, or lifecycle boundaries from the identifier itself.
3. **Contextual Saturation and Hallucination (Vibe-Coding):** In the absence of strict, deterministic numbering schemas, AI models hallucinate requirement identifiers or silently renumber requirements during refactoring passes, obfuscating whether a functional requirement has been altered or omitted.

To guarantee deterministic, collision-free identification across all specification artifacts without administrative overhead, the repository requires an immutable standard governing:
- A flat 6-digit numbering formula (`L[Layer]-\d{6}`) encoding stratum and sequential increment.
- Permanent static reservation of the initial Layer 0 range (`000001`–`000100`) for foundational meta-standards and core template specifications.
- Document-scoped requirement identifier allocation (quantized pools declared per document).
- Explicit metadata declarations in document frontmatter.
- Protocols for pool exhaustion, overflow handling, and custom range delegation via Addendum ADRs.
- Automated pre-commit verification enforcing fail-closed collision prevention.

## Decision

### R1. Flat 6-Digit Numbering Formula (`L[Layer]-\d{6}`)
The repository shall enforce a universal, flat 6-digit numbering schema for all architectural records, design documents, and requirements:
```
Formula: L<Layer>-<6-Digit-Index>
```
1. **Layer Digit (`<Layer>`):**
   The first digit strictly denotes the architectural layer of the artifact:
   - `L0` (Stratum 0: `000001`–`099999`): Universal meta-architecture, governance standards, linguistic constitutions, and system invariants.
   - `L1` (Stratum 1: `100001`–`199999`): Domain kernel, state machines, core data models, and primary business logic.
   - `L2` (Stratum 2: `200001`–`299999`): Tooling, code fabricators, boundary adapters, linters, and verification runners.
   - `L3` (Stratum 3: `300001`–`399999`): Application entry points, UI presentation, deployment configurations, and peripheral integrations.
2. **Sequential Index (`<6-Digit-Index>`):**
   The 6-digit index consists of the layer digit followed by a 5-digit sequential increment. Arbitrary sub-block divisions within the numerical identifier are prohibited in favor of continuous, flat numbering (`+1`).

### R2. Canonical Layer 0 Baseline Reservation (`000001`–`000100`)
The first 100 positions of Layer 0 (`000001` through `000100`) are permanently reserved for the foundational, immutable Architecture Decision Records (ADRs) and master template specifications constituting the repository standard profile:
- `ADR-L0-000001`: Specifications Lifecycle, Bootstrap, and Bundle Architecture
- `ADR-L0-000002`: Deterministic Numbering and Unique Range Allocation
- `ADR-L0-000003`: Unified Taxonomy, Naming Rules, and Codebase Standard
- `ADR-L0-000004`: Verifiable Requirements Engineering and EARS Standard
- `ADR-L0-000005`: FSM Grammar, Syntax, and System Registry
- `ADR-L0-000006`: External Test Infrastructure and Sandbox Isolation
- `ADR-L0-000007`: Official Errata and Refactoring Protocols
- `ADR-L0-000008`: Module Dependency Topology and Interaction Map Standard
- `ADR-L0-000009`: Requirements Traceability Matrix and Closed-Loop Verification
- `ADR-L0-000010`: Norm Applicability Manifest and File Registration Gate
- `ADR-L0-000011`: Anti-Rationalization and Specification Mutation Prevention
- `ADR-L0-000012`: Context Economy and Machine-Readable Standards for LLM
- `ADR-L0-000013` through `ADR-L0-000100`: Reserved for foundational template standards, system invariants, and master governance specifications.

Any project-specific cross-cutting architectural decision, local extension, or downstream standard created for a specific application shall be allocated sequentially starting strictly from `ADR-L0-000101+` upwards.

### R3. Document-Scoped Requirement Identifier Allocation
1. **Hierarchical Syntactic Structure:**
   Every functional requirement identifier shall follow the deterministic structure:
   ```
   REQ-L<Layer>-<DocIndex>-<ItemIndex>
   ```
   - `L<Layer>`: Architectural layer identifier (`L0`, `L1`, `L2`, `L3`).
   - `<DocIndex>`: Exact 6-digit index of the parent specification document.
   - `<ItemIndex>`: 3-digit sequential index within the document pool (e.g., `001`, `002`, `099`).
2. **Prohibition of Fluid Allocation:**
   Allocating requirement identifiers dynamically across an entire architectural layer without binding to a physical owning document is strictly forbidden.
3. **Prohibition of UUID and Non-Deterministic Schemes:**
   The use of Universally Unique Identifiers (UUIDs), random hashes, or unstructured text labels for requirement identification is strictly prohibited.
4. **Mandatory Frontmatter Range Declaration:**
   Every specification file must explicitly declare its assigned requirement identifier range and diagnostic error range within its YAML frontmatter metadata block:
   ```yaml
   allocated-ranges:
     REQ: REQ-L0-000002-001..REQ-L0-000002-099
     ERR: ERR-L0-000002-1..ERR-L0-000002-9
   ```

### R4. Range Exhaustion, Overflow Handling, and Custom Delegation
1. **Primary Quantized Allocation:**
   By default, each specification document is assigned a quantized pool of up to 99 requirement identifiers (`001` through `099`).
2. **Intra-Document Overflow Blocks:**
   If a document exhausts its primary allocation during valid evolution, the author may declare a contiguous overflow block within the frontmatter (e.g., `100` through `199`), provided no collision occurs with existing registered allocations.
3. **Subsystem Decomposition Threshold:**
   If a single specification document exceeds 100 requirements, the author shall evaluate modular decomposition into discrete specification bundles as mandated by `ADR-L0-000001` (R4).
4. **Custom Delegation via Addendum ADR:**
   If a downstream project requires dedicated segmented ranges (e.g., reserving a dedicated block for enterprise compliance or external regulatory domains), such segmentation must be formalized through a ratified Addendum ADR allocated at `ADR-L0-000101+`.

### R5. Automated Pre-Commit Collision Gate (Stratum 0 Gating Invariant)
Repository-wide identifier uniqueness is enforced as an automated Stratum 0 pre-commit and continuous integration invariant:
1. Static analysis tools shall scan all specification files (`./specs/**/*.md`), parse declared frontmatter ranges, and extract all declared requirement identifiers (`REQ-*`) and error codes (`ERR-*`).
2. Any detected duplication across files or within a single file shall immediately abort the commit with exit code 1 under error `ERR-L0-000002-1`.
3. Any requirement identifier defined outside the document's declared frontmatter range shall fail validation under error `ERR-L0-000002-3`.
4. The verification system shall operate on a fail-closed basis: if identifier validity cannot be deterministically verified, the build process shall fail.

## Requirements (EARS)

- **REQ-L0-000002-001 (Ubiquitous):**
  The documentation system shall enforce the 6-digit flat numbering schema `L[Layer]-\d{6}` for all specification documents and architectural decision records across all system layers under error `ERR-L0-000002-2`.
  | Verification: test_flat_numbering_syntax()

- **REQ-L0-000002-002 (Ubiquitous):**
  The system shall structure all functional requirement identifiers strictly according to the pattern `REQ-L<Layer>-<DocIndex>-<ItemIndex>`, where `<DocIndex>` matches the 6-digit index of the owning document under error `ERR-L0-000002-2`.
  | Verification: test_requirement_identifier_structure()

- **REQ-L0-000002-003 (State-driven):**
  While resident in the specification corpus, every specification file shall declare its designated requirement and error identifier ranges in an `allocated-ranges` metadata block within its YAML frontmatter under error `ERR-L0-000002-4`.
  | Verification: test_frontmatter_range_declaration()

- **REQ-L0-000002-004 (Unwanted behaviour):**
  If duplicate requirement identifiers (`REQ-*`) are detected across any specification files in the repository, then the governance linter shall halt execution, exit with code 1, under error `ERR-L0-000002-1`.
  | Verification: test_global_requirement_uniqueness()

- **REQ-L0-000002-005 (Unwanted behaviour):**
  If an identifier fails to conform to the canonical syntax `REQ-L<Layer>-\d{6}-\d{3}`, then the static analyzer shall reject the artifact with exit code 1 under error `ERR-L0-000002-2`.
  | Verification: test_identifier_syntax_conformance()

- **REQ-L0-000002-006 (Complex):**
  While pre-commit validation executes, When requirement identifiers are parsed from document bodies, If any requirement identifier falls outside the declared `allocated-ranges` block in the document frontmatter, then the linter shall reject the document with exit code 1 under error `ERR-L0-000002-3`.
  | Verification: test_declared_range_boundary_enforcement()

- **REQ-L0-000002-007 (Unwanted behaviour):**
  If a specification document omits the mandatory `allocated-ranges` block in its YAML frontmatter, then the governance gatekeeper shall fail the validation run with exit code 1 under error `ERR-L0-000002-4`.
  | Verification: test_missing_range_metadata_rejection()

- **REQ-L0-000002-008 (Unwanted behaviour):**
  If an artifact outside the canonical foundational standards attempts to reserve or claim an identifier within Layer 0 positions `000001` through `000100`, then the governance linter shall abort validation with exit code 1 under error `ERR-L0-000002-5`.
  | Verification: test_canonical_l0_reservation_guard()

- **REQ-L0-000002-009 (Event-driven):**
  When a specification author requires identifier capacity beyond the initial allocation pool, the author shall either declare an intra-document overflow block in frontmatter or ratify an Addendum ADR at `ADR-L0-000101+` under error `ERR-L0-000002-7`.
  | Verification: test_overflow_and_addendum_protocol()

- **REQ-L0-000002-010 (Unwanted behaviour):**
  If non-deterministic, fluid, or UUID-based identification schemes are used for system requirements, then the governance linter shall reject the specification with exit code 1 under error `ERR-L0-000002-6`.
  | Verification: test_fluid_and_uuid_schemes_ban()

## Checks & Verification Matrix

| Check Name | Target Artifact | Verification Gate | Error Code | Failure Condition |
| :--- | :--- | :--- | :--- | :--- |
| Global Uniqueness Check | `./specs/**/*.md` | pre-commit / CI | `ERR-L0-000002-1` | Identical `REQ-*` declared in more than one specification. |
| Syntax Conformance Check | `./specs/**/*.md` | pre-commit / CI | `ERR-L0-000002-2` | Identifier does not match `REQ-L<Layer>-\d{6}-\d{3}` or `L<Layer>-\d{6}`. |
| Range Boundary Check | `./specs/**/*.md` | pre-commit / CI | `ERR-L0-000002-3` | Body requirement identifier falls outside frontmatter `allocated-ranges`. |
| Frontmatter Metadata Check | `./specs/**/*.md` | pre-commit / CI | `ERR-L0-000002-4` | Missing `allocated-ranges` metadata block in YAML frontmatter. |
| Canonical L0 Reservation Check | `./specs/**/*.md` | pre-commit / CI | `ERR-L0-000002-5` | Unauthorized document claims Layer 0 index between `000001` and `000100`. |
| Fluid/UUID Scheme Check | `./specs/**/*.md` | pre-commit / CI | `ERR-L0-000002-6` | Requirement uses random, hash-based, or non-deterministic identifier. |
| Overflow & Addendum Allocation Guard | `./specs/**/*.md` | pre-commit / CI | `ERR-L0-000002-7` | Exhausted identifier range without ratified Addendum ADR or overflow metadata. |

## Error Catalog & Machine Remediation

- **`ERR-L0-000002-1` (REQ-ID-COLLISION):**
  - *Trigger:* A requirement identifier (`REQ-*`) is declared in multiple specification documents or repeated within the same file.
  - *Action:* Inspect conflicting files, identify the colliding identifier, and renumber the offending requirement using a unique sequential index within the owning document's allocated range.
- **`ERR-L0-000002-2` (INVALID-ID-SYNTAX):**
  - *Trigger:* An identifier violates the required regex pattern (`^REQ-L[0-3]-\d{6}-\d{3}$` or `^L[0-3]-\d{6}$`).
  - *Action:* Reformat the identifier to strictly match the canonical pattern with appropriate layer prefix and padding.
- **`ERR-L0-000002-3` (UNDECLARED-RANGE-EXCURSION):**
  - *Trigger:* A requirement identifier in the document body falls outside the numerical bounds declared in `allocated-ranges`.
  - *Action:* Update the frontmatter `allocated-ranges` block to legitimately encompass the new index or renumber the requirement to fit within the existing pool.
- **`ERR-L0-000002-4` (MISSING-ALLOCATED-RANGE-METADATA):**
  - *Trigger:* A specification file lacks the `allocated-ranges` YAML metadata field.
  - *Action:* Add the `allocated-ranges` block to the document frontmatter specifying designated `REQ` and `ERR` identifier spans.
- **`ERR-L0-000002-5` (CANONICAL-RANGE-VIOLATION):**
  - *Trigger:* A project-specific or non-baseline document uses an ID in the range `000001` through `000100` of Layer 0.
  - *Action:* Reassign the document index to the next available index starting from `000101` upwards.
- **`ERR-L0-000002-6` (FLUID-OR-UUID-SCHEME-DETECTED):**
  - *Trigger:* Non-deterministic identifiers (e.g. UUID, GUID, MD5 hashes, or un-scoped arbitrary labels) detected in requirement statements.
  - *Action:* Replace arbitrary or random strings with canonical document-scoped sequential requirement identifiers.

- **`ERR-L0-000002-7` (OVERFLOW-ALLOCATION-UNRATIFIED):**
  - *Trigger:* Requirement identifiers generated beyond allocated range bounds without declaring an overflow block or ratifying an Addendum ADR (`ADR-L0-000101+`).
  - *Action:* Register an overflow block in frontmatter metadata or ratify an Addendum ADR starting at `ADR-L0-000101+`.

## Consequences

### Positive
- Eliminates requirement collisions across distributed and concurrent engineering workflows.
- Preserves 1-to-1 deterministic traceability from requirements to code, tests, and database schemas.
- Protects the foundational Layer 0 architectural profile from accidental pollution or namespace collisions.
- Provides immediate, single-screen diagnostic feedback to human engineers and LLM agents during pre-commit checks.
- Prevents cognitive hallucination and silent requirement deletion by AI coding assistants.

### Negative
- Authors must explicitly manage and declare identifier ranges in frontmatter before authoring requirements.
- Exhaustion of primary pools requires conscious management (declaring overflow blocks or decomposing large specifications).

## Alternatives Considered
- **Fluid / Ad-Hoc Layer Allocation:** Rejected. Sharing a numbering range fluidly across an entire stratum without document-level reservation leads inevitably to duplicate identifier collisions during concurrent development.
- **UUID / Hash-Based Identifiers:** Rejected. UUIDs destroy human legibility, bloat prompt token budgets, and prevent cognitive indexing by developers and LLM agents.
- **Hierarchical Multi-Dot Indexing (e.g., REQ-1.2.3.4):** Rejected. Multi-level hierarchical numbering introduces structural brittleness during document reorganization, whereas flat document-scoped indexing remains resilient.
