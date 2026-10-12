# Repository Directory Taxonomy & Documentation Tree Architecture

## DOCUMENT CONTROL
- Status: Raw Factura Fund & Comparative Taxonomy
- Scope: Standardized Directory Hierarchies, ISO Process Mapping, Aerospace & Mission-Critical Repositories
- Encoding: UTF-8 (Strict CommonMark Profile)

---

## 1. ISO/IEC/IEEE Standards Taxonomy

### 1.1 ISO/IEC/IEEE 15289:2019 (Content of Life-Cycle Information Items)
ISO 15289 defines the normative types and content of information items across systems and software life cycles. It classifies all information artifacts into 7 generic document types:

1. **Policy (POL):** Directive defining organizational requirements, rules, and commitments.
2. **Plan (PLN):** Document defining objectives, activities, resources, and schedules for a life-cycle process.
3. **Procedure (PRC):** Mandatory step-by-step instructions for executing an operational activity.
4. **Specification (SPC):** Explicit statement of verifiable requirements, architecture, design, interfaces, or verification criteria.
5. **Description (DSC):** Explanatory model, architectural overview, system breakdown, or conceptual manual.
6. **Report (RPT):** Document recording results, measurements, audits, test evaluations, or findings at a specific point in time.
7. **Request (REQ):** Formal solicitation for action, baseline modification, erratum, or deviation.

#### ISO 15289 Mandatory Information Item Categories by Life Cycle Phase:
- **Governance & Management Items:** Project Charter, Information Management Plan, Configuration Management Plan, Quality Assurance Plan, Risk Management Plan, Decision Management Log.
- **Requirements & Interface Items:** Stakeholder Needs, System Requirements Specification (SyRS), Software Requirements Specification (SRS), Interface Requirements Specification (IRS), Interface Design Description (IDD).
- **Design & Architecture Items:** System Architecture Description (SAD), Software Design Description (SDD), Database Design Description (DBDD).
- **Verification & Validation Items:** Verification Plan, Validation Plan, Test Plan (STP), Test Design, Test Case Specification, Test Procedure (STPr), Test Evaluation Report (STR), Requirements Traceability Matrix (RTM).
- **Configuration & Release Items:** Configuration Baseline Record, Configuration Status Accounting Report, Version Description Document (VDD), Change Request (CR), Errata / Non-Conformance Record.
- **Maintenance & Disposal Items:** Maintenance Plan, Problem Resolution Log, Disposal Plan.

---

### 1.2 ISO/IEC/IEEE 12207:2017 & 15288:2015 (Process Architecture Mapping)
The international standard organizes systems and software engineering into 30 core processes across 4 groups. A comprehensive repository structure maps these processes to dedicated functional tiers:

```
[4 Group Process Architecture]
├── 1. Agreement Processes
│   ├── Acquisition Process
│   └── Supply Process
├── 2. Organizational Project-Enabling Processes
│   ├── Life Cycle Model Management
│   ├── Infrastructure Management
│   ├── Portfolio Management
│   ├── Human Resource Management
│   ├── Quality Management
│   └── Knowledge Management
├── 3. Technical Management Processes
│   ├── Project Planning
│   ├── Project Assessment and Control
│   ├── Decision Management
│   ├── Risk Management
│   ├── Configuration Management
│   ├── Information Management
│   ├── Measurement
│   └── Quality Assurance
└── 4. Technical Processes
    ├── Business or Mission Analysis
    ├── Stakeholder Needs and Requirements Definition
    ├── System/Software Requirements Definition
    ├── Architecture Definition
    ├── Design Definition
    ├── System Analysis
    ├── Implementation
    ├── Integration
    ├── Verification
    ├── Transition
    ├── Validation
    ├── Operation
    ├── Maintenance
    └── Disposal
```

---

## 2. Aerospace & Defense Systems Engineering Structures

### 2.1 NASA Systems Engineering Hierarchy (NPR 7123.1 & NASA-STD-2100-91)
NASA documentation is strictly partitioned into a 4-volume structure aligned with the Product Breakdown Structure (PBS):

- **Volume 1: Management Plans (PLN):**
  - Systems Engineering Management Plan (SEMP)
  - Configuration Management Plan (CMP)
  - Risk Management Plan (RMP)
  - Verification & Validation Plan (VVP)
- **Volume 2: Product Specifications (SPC):**
  - Concept of Operations (ConOps)
  - Functional & Performance Requirements (SRS / SyRS)
  - Interface Control Documents (ICD)
  - System Architecture & Design Descriptions
- **Volume 3: Assurance, Verification & Test Procedures (PRC):**
  - Test Procedures & Scripts
  - Inspection Checklists
  - Safety & Quality Assurance Procedures
- **Volume 4: Reports & Logs (RPT):**
  - Verification Compliance Matrices (VCM)
  - Test Execution Reports
  - Anomaly & Non-Conformance Reports (NCR)
  - Decision / Trade Study Reports

---

### 2.2 MIL-STD-498 (22 Standardized Data Item Descriptions / DIDs)
MIL-STD-498 provides an exhaustive taxonomy of 22 formal software life cycle artifacts:

| DID Acronym | Title | Lifecycle Scope |
|---|---|---|
| SDP | Software Development Plan | Planning & Management |
| SCMP | Software Configuration Management Plan | Governance & Baselines |
| SQAP | Software Quality Assurance Plan | Compliance & Audits |
| OCD | Operational Concept Description | Mission Concept & ConOps |
| SSRS | System/Subsystem Requirements Specification | System Requirements |
| SRS | Software Requirements Specification | Software Requirements |
| IRS | Interface Requirements Specification | Interface Boundaries |
| SDD | Software Design Description | Architectural & Detailed Design |
| IDD | Interface Design Description | Interface Protocols & Schemas |
| DBDD | Database Design Description | Relational/Physical DB Schemas |
| STP | Software Test Plan | Verification Planning |
| STD | Software Test Description | Test Cases & Procedures |
| STR | Software Test Report | Test Execution & Verification Evidence |
| SPS | Software Product Specification | As-Built Master Configuration |
| VDD | Version Description Document | Release Notes & Artifact Hashes |
| SCOM | Software Computer Operation Manual | Operation & Deployment |
| CPM | Computer Programming Manual | Developer Reference & Tooling |

---

### 2.3 ECSS (European Cooperation for Space Standardization - ECSS-E-ST-10C)
ECSS documentation tree utilizes a formal document breakdown:

```
[ECSS Document Tree Levels]
Level 0: Policy, Standards, and Mandates
Level 1: System Level (Requirements, ConOps, Mission Objectives)
Level 2: Subsystem Level (Subsystem Specs, Architectural Designs, ICDs)
Level 3: Equipment / Assembly Level (Hardware/Software Units, Algorithms)
Level 4: Manufacturing, Test Procedures, and Verifications
Level 5: Acceptance Data Packages (ADP), Test Logs, As-Built Records
```

---

## 3. High-Integrity & Mission-Critical Software Repository Taxonomies

### 3.1 Tiered Layering Model (Multi-Tier Monorepo Pattern)
In systems managing thousands of specifications, codes, tests, and reports, flat repositories experience namespace collisions and link rot. The proven architectural pattern isolates concerns into orthogonal tiers:

```
/
├── .governance/              # Governance & Charter (ISO 12207 §6.2)
│   ├── charter/              # System Constitution & Core Invariants
│   └── policies/             # Project-wide Tailoring Policies
│
├── specs/                    # Baseline 0 (BL-0) Normative Specifications (The Source of Truth)
│   ├── bl-0/                 # BL-0 Core Specifications & System Requirements (ISO 15289 SPC)
│   └── schemas/              # Information Models, Ontologies & DB DDLs (ISO 11179)
│
├── pipeline/                 # Conveyor & Ingestion Workflows
│   ├── intake/               # Raw slots, drafts, candidate proposals
│   ├── staging/              # Pre-seal validation, lint staging
│   └── rejected/             # Quarantined proposals
│
├── instruments/              # Methods & Software Tools (Lead Item 2)
│   ├── compilers/            # Document compilers, AST lowerers (ISO 24765 §3.731)
│   ├── linters/              # Static analysis checkers, rule engines (ISO 24765 §3.4116)
│   └── verifiers/            # Drift detectors, hash lockers (ISO 29119)
│
├── src/                      # Software Implementation (Executable Code)
│   ├── kernel/               # Foundational runtime engines (ISO 12207 §6.4.7)
│   └── adapters/             # Storage, database, and I/O drivers (ISO 15288 §6.4.7)
│
├── tests/                    # Verification & Quality Assurance (ISO 29119)
│   ├── unit/                 # Unit test harnesses
│   ├── contract/             # Closed-loop spec-to-code conformance tests
│   ├── fixtures/             # Valid and mutant test vectors
│   └── locks/                # Machine lockfiles (hashes, RTM locks)
│
├── reports/                  # Generated Verification Evidence & Records (ISO 15289 RPT)
│   ├── rtm/                  # Requirements Traceability Matrices
│   └── linters/              # Static analysis run summaries
│
└── ledger/                   # Configuration Change Control & Debt (ISO 12207 §6.4.5)
    ├── decisions/            # Architectural Decision Records (DECISIONS.md)
    ├── errata/               # Official bug corrections to sealed baselines
    └── debt/                 # Registered technical debt items (DEBT-NNNN)
```

---

## 4. Repository Pathing & Hyperlink Invariants

### 4.1 The Re-nesting Hazard (Link Rot Catastrophe)
When directories are re-nested by domain or depth during project scaling (e.g. moving `specs/foo.md` to `specs/subsystem/module/foo.md`), internal relative links (`../../bar.md`) break catastrophically across hundreds of documents.

### 4.2 Architectural Counter-Measures (Best Practices)
1. **Root-Anchored Absolute Virtual Paths:**
   - Define a universal virtual root identifier (e.g., `./` anchoring at the canonical repository boundary, or `/aedis/` as the virtual root).
   - Invariants enforce that all cross-document references resolve relative to the top-level repository root rather than relative directory depths (`./specs/kernel/glossary.md` rather than `../../../glossary.md`).

2. **Deterministic Identifier-Based Addressing:**
   - Every specification, requirement, test, and debt item carries an immutable globally unique identifier (e.g., `SPEC-L0-000001`, `REQ-00042`, `DEBT-000013`).
   - Compilers and linters resolve references via an internal Index/Catalog rather than physical path crawling. Moving a file within the taxonomy does not invalidate requirement links.

3. **Orthogonal Separation of Concerns:**
   - **Form (Format):** Markdown vs Python vs JSON vs SQL.
   - **Role (Function):** Norm vs Implementation vs Verification.
   - **Lifecycle State:** Draft (Intake) vs Sealed (Corpus) vs Retired (Archive).
   - Never mix lifecycle states inside the same directory (e.g., do not place active specs and discarded drafts in the same folder).

4. **Directory Depth Limit (Maximum 3–4 Levels):**
   - High-integrity engineering taxonomies enforce a maximum nesting depth of 3 to 4 levels below root to maintain structural readability and prevent path length overflow on diverse operating systems.

---

## 5. Real-World Catastrophes of Flawed Directory Structures

### 5.1 Case Study 1: The "Big Ball of Mud" & Circular Layer Inversion
- **Failure Mode:** Directory structure was organized purely by superficial feature names (`feature-a/`, `feature-b/`) rather than by strict acyclic abstraction tiers.
- **Catastrophe:** Module A imported from Module B, which silently imported from Module A's subfolder. When the codebase reached 50,000 lines, circular dependency graph cycles paralyzed the build system, made unit testing impossible in isolation, and caused tree-shaking and compilation deadlock.
- **Root Cause:** Absence of a mandatory unidirectional dependency law between directory tiers (Tier N must never import or reference Tier >= N).

### 5.2 Case Study 2: Cross-Platform Case-Sensitivity Collision (The Git Checkout Meltdown)
- **Failure Mode:** Developers on Linux (case-sensitive ext4 filesystem) created files with mixed casing: `Spec.md` and `spec.md`, or folders `Tools/` and `tools/`.
- **Catastrophe:** When Windows (NTFS) or macOS (APFS case-insensitive) developers ran `git checkout` or `git pull`, git silently overwrote or corrupted one file with the other, resulting in unstaged phantom diffs, broken build pipelines, and unresolvable merge conflicts.
- **Root Cause:** Lack of an automated gate enforcing strictly uniform lowercase `kebab-case` for all paths across the entire repository.

### 5.3 Case Study 3: The MAX_PATH (260-Character) Tree Collapse
- **Failure Mode:** Unconstrained directory nesting (exemplified historically by early npm nested `node_modules` trees, e.g., `pkg/node_modules/dep/node_modules/subdep/...`).
- **Catastrophe:** Deep subtrees exceeded the Windows Win32 API 260-character path limit (`MAX_PATH`). Continuous Integration (CI) agents crashed, file deletion tools threw unrecoverable I/O errors, backup software failed to archive files, and developer IDEs froze.
- **Root Cause:** Failure to enforce a hard maximum nesting depth (3–4 levels) and maximum path length ceiling (< 120 characters).

### 5.4 Case Study 4: The Massive Hyperlink Rot & Git Blame Amputation Disaster
- **Failure Mode:** A large-scale documentation repository (thousands of markdown files) was reorganized from a flat list into nested topical folders.
- **Catastrophe:** Tens of thousands of relative cross-references (`../../spec-a.md`) shattered overnight ("404 Link Rot"). Furthermore, mass file moves broken git history (`git blame`) across the repository, amputating legal provenance, author accountability, and historical rationale behind critical engineering decisions.
- **Root Cause:** Tight coupling of documentation hyperlinks to physical disk paths instead of immutable logical identifiers (e.g., `REQ-ID`, `SPEC-ID`), combined with lack of virtual root path anchoring.

### 5.5 Case Study 5: The "Kitchen Sink" / "Common" Singularity
- **Failure Mode:** Creation of a generic `utils/`, `common/`, or `misc/` folder at the root to "temporarily" store helper functions, shared schemas, or unclassified documents.
- **Catastrophe:** Over 3 years, every subsystem began dumping code and specifications into `common/`. `common/` became an omni-dependent architectural black hole: changing one line in `common/` triggered recompilation and re-testing of 100% of the repository. Refactoring it became impossible due to social and technical inertia.
- **Root Cause:** Violation of the Zero-Common Policy. Every entity must belong to an explicit, typed domain or formal life cycle process.

### 5.6 Case Study 6: The "Drafts in Production" Hazard (Lifecycle Pollution)
- **Failure Mode:** Storing draft proposals, experimental notes, and rejected designs in subfolders adjacent to active normative standards (e.g., `specs/drafts/` alongside `specs/approved/`).
- **Catastrophe:** Automated tools, LLMs, and external engineers inadvertently consumed draft or deprecated specifications as active normative truth. In safety-critical aerospace and medical software, this caused defects where obsolete test criteria were certified against production code.
- **Root Cause:** Mixing distinct lifecycle states (Draft vs Sealed vs Retired) inside the same top-level directory namespace.

---

## 6. The AEDIS Architectural Safeguards (Engineering Invariants)

To guarantee that the AEDIS repository architecture scales from 50 files to 50,000 files without structural collapse, the following 6 invariants are mandated:

1. **Unidirectional Layer DAG Law:**
   Dependencies and references flow strictly downwards (`Tier 7 -> Tier 6 -> ... -> Tier 1 -> Tier 0`). Circular references across directory tiers are treated as fatal compilation defects ($D > 0$).
2. **Strict Kebab-Case & ASCII-Only Gate:**
   All directories and filenames must strictly match `^[a-z0-9]+(-[a-z0-9]+)*(\.[a-z0-9]+)?$`. Mixed case, spaces, and non-ASCII characters are rejected at the intake gate to eliminate cross-platform filesystem collisions.
3. **Bounded Nesting Depth Ceiling (Depth <= 4, Path <= 120 chars):**
   No file path may exceed 4 levels of directory depth from the repository root, guaranteeing deterministic performance across all operating systems.
4. **Logical Identifier Decoupling (ID-Based Addressing):**
   Internal cross-references must link via permanent entity IDs (`SPEC-L0-000001`, `REQ-00042`, `GLOSS-001`) resolved by compiler index tables, insulating the corpus against physical file movement.
5. **Zero-Common Policy (Strict Domain Typing):**
   Generic folders such as `utils/`, `common/`, or `misc/` are strictly forbidden. Every file belongs to an explicit ISO process or typed architectural tier.
6. **Physical Lifecycle Quarantine:**
   Unsealed, draft, and candidate files exist exclusively within `pipeline/intake/` and `pipeline/staging/`. The `specs/` directory contains exclusively sealed, immutable baselines ($D = 0$).

---

## 7. Canonical AEDIS Directory Architecture Matrix (Version 1.0.0)

| System Domain | Canonical Path | ISO Standard & Process Mapping | File Naming Convention | Lifecycle State | Permitted DAG References |
|---|---|---|---|---|---|
| **Root Entry** | `./` | Root Entry & Universal Gates (ISO 15289 Entry Points) | `README.md`, `LICENSE`, `metadata.json`, `.gitattributes` | Sealed / Root Baseline | Terminal Sink (Self-contained) |
| **Governance** | `./aedis/governance/` | Organizational Enabling & Governance (ISO 12207 §6.2) | `charter-*.md`, `manifest-*.md` | Immutable Constitution (Seal) | Root only |
| **Agent Contour** | `./aedis/agents/` | AI Agent Operational Contour (Lead Item 4 / ISO 22989) | `protocol-*.md`, `state-*.md`, `manifest-*.md` | Operational State & Working Memory | Root, Governance |
| **BL-0 Specifications** | `./aedis/specs/bl-0/` | Baseline 0 Normative Standards (Lead Item 1 & 3 / ISO 15289 SPC) | `glossary.md`, `SPEC-BL0-*.md` | Sealed Baseline ($D=0$) | Governance, Root |
| **Schemas & Models** | `./aedis/specs/schemas/` | Information Models, Ontologies & DB DDLs (ISO 11179 / ISO 15289 DBDD) | `*.schema.json`, `*.ddl.sql`, `*.slots.toml` | Sealed Schema | BL-0, Governance |
| **Pipeline (Intake)** | `./aedis/pipeline/intake/` | Candidate Ingestion & Authoring Gateway (ISO 15289 REQ) | `*.candidate.toml`, `*.slot.md`, `*.draft.md` | Ephemeral / Mutable (Unsealed) | Quarantined (Read-only to BL-0) |
| **Pipeline (Staging)** | `./aedis/pipeline/staging/` | Pre-Seal Verification & Linter Staging (ISO 12207 §6.4.9) | `*.staging.md`, `*.staged.json` | Transient / Candidate Baseline | Read-only to BL-0, Governance |
| **Instruments (Linters)** | `./aedis/instruments/linters/` | Static Analysis Tools & Syntax Enforcers (ISO 24765 §3.4116) | `linter_*.py`, `rule_*.py` | Verified Tooling (Executable) | Schemas, Governance |
| **Instruments (Compilers)** | `./aedis/instruments/compilers/` | Specification Compilers & Lowerers (ISO 24765 §3.731) | `compiler_*.py`, `ast_builder.py` | Verified Tooling (Executable) | Schemas, Governance |
| **Instruments (Verifiers)** | `./aedis/instruments/verifiers/` | Drift Detectors & Fingerprint Generators (ISO 29119) | `hash_locker.py`, `rtm_builder.py` | Verified Tooling (Executable) | BL-0, Governance |
| **Runtime (Kernel)** | `./aedis/src/kernel/` | Foundational Runtime & Core Engines (ISO 12207 §6.4.7) | `*.py`, `*.ts`, `*.sql` | Production Code (Implementation) | Implements BL-0 Specs |
| **Runtime (Adapters)** | `./aedis/src/adapters/` | Storage, Database, and I/O Drivers (ISO 15288 §6.4.7) | `storage_*.py`, `db_*.py` | Production Code (Adapters) | Runtime Kernel, BL-0 |
| **Tests (Unit)** | `./aedis/tests/unit/` | Isolated Component Test Suites (ISO 29119-2) | `test_*.py` | Test Code (Executable) | Tests Instruments, Runtime |
| **Tests (Contract)** | `./aedis/tests/contract/` | Closed-Loop Spec-to-Code Conformance Tests (ISO 29119-4) | `test_contract_*.py` | Test Code (Executable) | Tests Runtime against BL-0 |
| **Tests (Fixtures)** | `./aedis/tests/fixtures/` | Canonical Test Vectors & Mutation Test Inputs (ISO 29119) | `valid_*.json`, `invalid_*.md`, `mutant_*.toml` | Static Test Fixtures | Self-contained |
| **Tests (Locks)** | `./aedis/tests/locks/` | Deterministic Fingerprints & Integrity Seals (ISO 12207 CM) | `hashes.lock.json`, `rtm.lock.json` | Machine Lockfiles (Read-Only) | References BL-0, Instruments |
| **Reports (RTM)** | `./aedis/reports/rtm/` | Requirements Traceability Matrices (ISO 29148 / 29119 RTM) | `RTM-*.md`, `traceability.report.json` | Generated Evidence (Audit Record) | Derived from BL-0, Runtime, Tests |
| **Reports (Linters)** | `./aedis/reports/linters/` | Static Analysis Diagnostic Summaries (ISO 15289 RPT) | `linter_report_*.md`, `summary.json` | Generated Evidence (Audit Record) | Derived from Instrument runs |
| **Ledger (Decisions)** | `./aedis/ledger/decisions/` | Architectural Decision Records (ISO 12207 Decision Management) | `DECISIONS.md`, `ADR-*.md` | Cumulative Append-Only Ledger | Historical Audit Log |
| **Ledger (Errata)** | `./aedis/ledger/errata/` | Official Baseline Corrections (ISO 12207 §6.4.5 Errata Protocol) | `ERR-*.md` | Cumulative Append-Only Ledger | Amends BL-0 baselines |
| **Ledger (Debt)** | `./aedis/ledger/debt/` | Technical Debt & Exception Register (ISO 15288 Problem Resolution) | `DEBT-*.md` | Tracked Queue (Open / Closed) | References BL-0, Runtime |

---

## 8. The AI Agent Operational Contour: Standardizing the ISO Blind Spot

### 8.1 The ISO Blind Spot Explained
Classical systems engineering standards (ISO/IEC/IEEE 12207, 15288, 15289) were formulated under the assumption that all human actors possess persistent personal memory, shared common-sense background context, and operate standard deterministic software tools.
In modern collaborative Human-AI engineering, Large Language Models (LLMs) and autonomous AI agents introduce unique structural realities that traditional ISO documentation frameworks fail to address:
1. **Context Window Ceiling & Memory Loss:** Clean sessions start with zero state; unconstrained preloading of hundreds of rules causes prompt bloating, hallucination, and semantic drift.
2. **Semi-Autonomous Contour Boundaries:** Multiple models (e.g., Gemini in Google AI Studio as the Live Mutator, Kimi on GitHub as the Auditor/Reviewer) require explicit operational boundaries and cross-reading bans.
3. **Transport Hygiene Vulnerabilities:** Web interfaces and clipboard buffers mangle backtick-fenced code blocks, raw HTML comment tags, and math notation.
4. **1-Hop Lazy Dispatch:** Models require structured operational relays to load normative rules strictly on demand rather than preloading entire specification corpora.

### 8.2 Internal Architecture of `./aedis/agents/`
AEDIS elevates the agent operational contour into a first-class foundational tier (Tier 0). Its internal anatomy is partitioned into 4 distinct functional subdomains:

```
./aedis/agents/
├── protocols/                # Shared Operational Rules & Conveyor Formats
│   ├── protocol-state.md     # Authoritative rules (§P0–§P8: tasks, debates, conduct)
│   ├── format-harness.md     # Machine format rules for prompt-response envelopes
│   └── transport-hygiene.md  # AST invariants (zero-HTML, escaping, backtick rules)
│
├── state/                    # Dynamic Contour Memory Boards & State Relays
│   ├── state-gemini.md       # Live Google AI Studio mutator memory board
│   ├── state-kimi.md         # GitHub auditor and reviewer memory board
│   └── relay-dispatch.md     # 1-hop cybernetic dispatch table
│
├── harness/                  # Context Optimization & Token Economy Scaffolding
│   ├── context-budgets.toml  # Maximum token thresholds per session type
│   └── gate-selectors.json   # Automatic paragraph selector mapping
│
└── manifests/                # Boundary Declarations & Scope Locks
    ├── manifest-agents.md    # Contour capability declarations & legal roles
    └── manifest-state.md     # Memory zone access control (Sovereign zones)
```

### 8.3 Normative Rules for the Agent Contour
1. **Contour Isolation Law:** An agent operating within Contour Alpha shall never read or mutate the private memory state of Contour Beta.
2. **Sovereign Zone Protection:** Working memory designated as LLM Sovereign Zone is read-only for operator audit and mutable solely by the assigned model.
3. **Verbatim Conveyor Execution:** Work directives passed between contours must strictly follow predefined machine-verifiable task templates (Template T1) with explicit file scope-locks.

---

## 9. Canonical File Envelope & AST Representation Invariants (AEDIS-PROT-HARNESS-001)

Every file within the AEDIS directory tree governed by Baseline 0 must satisfy the uniform, deterministic structural envelope defined by `AEDIS-PROT-HARNESS-001`. This guarantees $D(S, T) = 0$ at the physical file layout boundary.

### 9.1 Mandatory Physical Header Layout (Lines 1–6)
- **Line 1 (Byte 0 Sentinel):** `FILE_MUTATION: OPERATOR_ONLY`
  - Unadorned flat string. Enables $O(1)$ CLI pre-commit ingress filtering (`head -n 1`) prior to AST bootstrap, and anchors the Attention Sink token against mutating logit synthesis.
- **Line 2 (SPDX Copyright Sentinel):** `SPDX-FileCopyrightText: [Year] [Holder]`
  - Flat plaintext tag compliant with ISO/IEC 5962:2021 and REUSE v3.0. Zero HTML comment wrappers.
- **Line 3 (SPDX License Sentinel):** `SPDX-License-Identifier: [SPDX-ID]`
  - Standardized SPDX license identifier.
- **Line 4:** Exactly one blank line (LF delimiter).
- **Line 5:** Document title ATX heading `# [Title]`.
- **Line 6:** Parenthetical meta-annotation `(meta: <purpose> | <primary effect> | <target contour>)` placed strictly within the initial 50 tokens for single-hop semantic indexing.

### 9.2 Mandatory Document Body Sections
- **Document Control Block (`## DOCUMENT CONTROL`):**
  - Key-Value metadata block complying with ISO/IEC 11179 and ISO/IEC/IEEE 15289 (`Document ID`, `Document Type`, `Issuing Authority`, `Applicability`, `Lifecycle Status`).
- **Immutability Locks Block (`## [NAME] LOCKS`):**
  - Explicit operational constraint syntax: `- **[LOCK_NAME]=1**: [RULE] | [UNLOCK] | LEVEL=[CRITICAL]`.
- **Active Instruction Anchor (`## HARNESS DIRECTIVE`):**
  - Replaces passive introductory text ("Preamble") to prevent Attention Weight Drift and force LLM causal attention into active instruction-following mode.

### 9.3 Representation Profile (Strict AEDIS CommonMark v0.31 Profile)
- **Encoding & Line Endings:** UTF-8 strictly without BOM, normalized Unix LF (`\n`).
- **Zero-HTML Mandate:** Complete prohibition of raw HTML tags and hidden HTML comments (`<!-- -->`). Human Operators viewing rendered markdown and LLMs parsing raw tokens observe 100% bitwise context parity.
- **Zero-Backtick Mandate:** Complete prohibition of fenced triple backticks and inline backticks. Machine tokens and literals are expressed via uppercase, straight quotes, or 4-space indentation to prevent clipboard and web transport mangling.
- **Zero-Math Dollar Sign Mandate:** Prohibition of `$`, `$$`, and pseudo-LaTeX delimiters. Formulas expressed strictly via plain ASCII (`D(S, T) = 0`).
- **Vertical Spacing Invariant:** Exactly one blank line (LF LF) between numbered clauses, headings, and blocks. Redundant blank lines collapsed; lists formatted as monolithic tight lists.

---

## 10. The Four-Component Composition & Final Convergence Architecture

AEDIS partitions the entire universe of the project into four interrelated components:

```
[AEDIS Canonical System Composition]
├── Component 1: Formal Life Cycle Configuration Baseline 0 (BL-0)
│   └── Tailored international standards (ISO 12207, 15288, 29148, 29119, 25010)
│       └── Physical Location: ./aedis/specs/bl-0/
│
├── Component 2: Methods and Mechanisms (Software Tools & Instruments)
│   └── Compilers, linters, drift verifiers, and execution pipelines
│       └── Physical Location: ./aedis/instruments/ & ./aedis/pipeline/
│
├── Component 3: Normative Technical Documentation of the Agent Working Contour
│   └── Specifications governing how the agent contour is structured and operated
│       └── Status: Integral normative specification of Baseline 0 (BL-0)
│       └── Target Baseline Directory: ./aedis/specs/bl-0/ (exact filenames allocated upon formal seal)
│
└── Component 4: The Live Working Contour of LLMs and AI Agents
    └── Runtime operational instances, memory boards, and active relays
    └── Tailored for Google AI Studio (Gemini) and GitHub (Kimi)
    └── Physical Location: ./aedis/agents/
```

### 10.1 The Final Convergence Invariant
- **Development Phase (Bootstrap):** Component 3 acts as the operational casting mold, temporarily co-located within `./aedis/agents/` to guide live synchronization between Operator and Agents.
- **Baseline Freeze (Release):** Component 3 specifications are formally compiled, sealed, and integrated into `./aedis/specs/bl-0/` alongside Component 1 standards.
- **Permanent Role of `./aedis/agents/`:** Retains strictly Component 4 runtime operational artifacts (dynamic memory states, active execution relays, session handovers) operating in strict compliance with the ratified Component 3 standards.

### 10.2 On-Demand Directory Creation Policy (Lazy Materialization)
- **Zero Preemptive Scaffolding:** Physical directories shall not be generated in bulk as empty placeholders.
- **JIT Allocation:** A directory path is created strictly when a verified task requires writing a physical file into that location.
- **Decoupled Architecture Mapping:** The architecture matrix establishes structural intent and destination topology; physical file system presence follows operational need.

---

## 11. Exhaustive ISO Justification & Physical Entity Mapping

This section establishes the definitive evidentiary rationale and physical occupant inventory for every directory within the AEDIS architecture. It bridges our historical Stage 0 Shadow Bootstrap assets (`./shadow-bootstrap/`) into their canonical permanent homes in Baseline 0 (`./aedis/`).

### 11.1 Governance: `./aedis/governance/`
- **ISO Process Mapping:** ISO/IEC/IEEE 12207:2017 §6.2.1 (Life Cycle Model Management) and §6.2.6 (Knowledge Management Process); ISO/IEC/IEEE 15289:2019 POL (Policy) and DSC (Description).
- **Architectural Rationale:** Establishes the constitutional legal foundation of the system. Documents here possess maximum normative authority, subject to strict `CHARTER_MUTATION_LOCK` and mutable solely by direct Operator command.
- **Actual Physical Occupants (Mapped from Live Artifacts):**
  - `charter-project.md`: The System Constitution (AEDIS-CHARTER-001). Formalizes the Project Goal, the Minimal Functionally Complete Basis, strict unidirectional dependencies, the two legal adoption channels for external knowledge, the discipline of immediate problem resolution, the self-correction principle, and the Operator exception authority.
  - `charter-project-ru.md`: Russian-language mirror of the System Constitution for transparent Operator audit.
  - `manifest-aedis.md`: Root project capability declaration and boundary perimeter.

### 11.2 Agent Operational Contour: `./aedis/agents/` (Lead Item 4)
- **ISO Process Mapping:** ISO/IEC 22989:2022 (Artificial Intelligence Concepts and Terminology) and ISO/IEC 42001:2023 (Artificial Intelligence Management System); tailored under AEDIS Sovereign Agent Contour Standard.
- **Architectural Rationale:** Isolates the active, semi-autonomous runtime environment of LLMs from the normative baseline corpus. Manages the reality of model context limits, token budget depletion, and multi-model collaboration without contaminating static standards.
- **Internal Sub-Structure & Actual Physical Occupants:**
  - `state/state-gemini.md`: Live memory board and operational relay for the Google AI Studio contour (Gemini as Live Workspace Mutator). Contains Block 1 (Relay Dispatch), Block 2 (Operative State), and Block 3 (LLM Sovereign Zone with physical AST invariants).
  - `state/state-kimi.md`: Live memory board for the external GitHub contour (Kimi as Read-Only Auditor and Reviewer).
  - `protocols/protocol-state.md`: Authoritative interaction protocol book containing lazy-loaded paragraphs:
    - `§P0-TOPOLOGY`: Workspace Topology & File Index.
    - `§P1-TASK-T1`: Conveyor T1 execution format (Verbatim execution with scope-locks).
    - `§P2-DEBATE-T2`: Peer Debate protocol between equal agent contours.
    - `§P3-HANDOVER`: Session teardown and milestone handover rules.
    - `§P4-CONDUCT`: Requirements syntax (ISO 29148) and markdown hygiene.
    - `§P5-META`: Teleological intent grounding.
    - `§P6-FAILSAFE`: Task ambiguity and anchor mismatch handling.
    - `§P7-DEBUG`: Harness diagnostics.
    - `§P8-CO-ARCHITECT`: Concept design and brainstorming framework.
  - `manifests/manifest-agents.md` & `manifests/manifest-state.md`: Access control boundaries enforcing contour isolation and sovereign zone auditability.

### 11.3 Baseline 0 Specifications: `./aedis/specs/bl-0/` (Lead Items 1 & 3)
- **ISO Process Mapping:** ISO/IEC/IEEE 15289:2019 SPC (Specification) and ISO/IEC/IEEE 12207:2017 §6.4.3 (System/Software Requirements Definition Process); ISO/IEC/IEEE 29148:2018 (Requirements Engineering).
- **Architectural Rationale:** The normative heart of the project. Contains exclusively ratified, sealed, immutable specifications ($D=0$) that define Baseline 0 (BL-0). No drafts or unverified proposals are permitted in this directory.
- **Actual Physical Occupants (Mapped from Live Artifacts):**
  - `glossary.md`: The Canonical Dual-Key / Genesis Glossary. Contains the axiomatic self-describing core (59 foundational terms categorized across actors, ontology, file systems, lifecycle transitions, and formats).
  - The 13 Ratified Foundation Standards (Migrating from `./shadow-bootstrap/governance/specs/`):
    - `SPEC-BL0-000001`: Specification Lifecycle, Bootstrap & Bundle Architecture.
    - `SPEC-BL0-000002`: Deterministic Numbering & Unique Range Allocation.
    - `SPEC-BL0-000003`: Unified Taxonomy, Naming Rules & Directory Topology.
    - `SPEC-BL0-000004`: Verifiable Requirements Engineering (Transitioning EARS to sovereign STA-Contract notation).
    - `SPEC-BL0-000005`: FSM Grammar, Syntax & State Transition Registry.
    - `SPEC-BL0-000006`: External Test Infrastructure & Sandbox Isolation.
    - `SPEC-BL0-000007`: Official Errata & Refactoring Protocols.
    - `SPEC-BL0-000008`: Module Dependency Topology & Interaction Map (Acyclic DAG Law).
    - `SPEC-BL0-000009`: Requirements Traceability Matrix (RTM) & Closed-Loop Verification.
    - `SPEC-BL0-000010`: Norm Applicability Manifest & File Registration Gate.
    - `SPEC-BL0-000011`: Anti-Rationalization & Specification Mutation Prevention.
    - `SPEC-BL0-000012`: Context Economy & Machine-Readable Standards for LLM.
    - `SPEC-BL0-000013`: The Specification Compiler Architecture.
  - `SPEC-BL0-HARNESS-FORMAT.md`: The ratified Component 3 standard governing the formatting and structural envelope of all agent artifacts (derived from `AEDIS-PROT-HARNESS-001`).

### 11.4 Authoring & Fabrication Procedures: `./aedis/specs/procedures/`
- **ISO Process Mapping:** ISO/IEC/IEEE 15289:2019 PRC (Procedure) and ISO/IEC/IEEE 12207:2017 §6.4.7 (Implementation Process); ISO 9001 Standard Operating Procedures.
- **Architectural Rationale:** Permanent, binding procedural specifications governing *how* specifications and code are synthesized. Elevates our core methodologies out of temporary workshop subdirectories into first-class standards.
- **Actual Physical Occupants (Mapped from Live Artifacts):**
  - `4lk.md` (Migrating from `./shadow-bootstrap/governance/new-code/the-method/`): The 4-Layer (4-Pass) Code Fabrication & Adversarial Verification Standard. Eliminates "vibe-coding" via risk-graduated 4-pass synthesis: Pass 1 (Topological Meta-Skeleton), Pass 2 (In-Situ Contract-as-Assert), Pass 3 (Deterministic Block Implementation), Pass 4 (Static AST Integrity Scan).
  - `adr_compiler_method.md` (Migrating from `./shadow-bootstrap/governance/new-adr/the-method/adr_compiler.md`): The "Linter-in-Reverse" (Correct by Construction) method. Enforces that humans and LLMs author only structured data slots, offloading syntax layout and verification guarantees to a deterministic compiler.
  - `scqg.md`: Semantic Context Question Generator protocol for iterative multi-pass specification convergence.
  - `tech-debate.md`: The formal procedural specification for conducting positional engineering debates between equal agent contours.

### 11.5 Schemas & Structured Models: `./aedis/specs/schemas/`
- **ISO Process Mapping:** ISO/IEC 11179-3:2023 (Metadata Registries - Metamodel) and ISO/IEC/IEEE 15289:2019 DBDD (Database Design Description).
- **Architectural Rationale:** Machine-verifiable data structures, relational DDLs, and authoring slot schemas that govern automated tools and database migrations.
- **Actual Physical Occupants (Mapped from Live Artifacts):**
  - `adr-000013.slots.toml`: Typed slot schema for specification authoring.
  - `glossary.slots.toml`: Typed slot schema for glossary concept ingestion.
  - `norm-manifest.schema.yaml`: Schema for file registration and applicability manifests.
  - Future SQL DDLs for relational migration of terms and specifications (`glossary.ddl.sql`).

### 11.6 Conveyor & Ingestion Pipelines: `./aedis/pipeline/`
- **ISO Process Mapping:** ISO/IEC/IEEE 12207:2017 §6.4.5 (Configuration Management - Change Control & Baseline Ingestion Gateway); ISO 15289 REQ (Request).
- **Architectural Rationale:** The active assembly line. Physically quarantines unverified, transient drafts and raw proposals away from the sealed corpus.
- **Internal Sub-Structure & Actual Physical Occupants:**
  - `intake/`: Ingestion hopper for raw candidate slots (`*.candidate.toml`, `*.slot.md`).
  - `staging/`: Pre-seal verification sandbox. Newly compiled specifications or synthesized code modules reside here while undergoing automated static analysis, linter execution, and mutant testing before formal seal.
  - `rejected/`: Quarantined proposals that failed verification with persistent diagnostic records.

### 11.7 Software Instruments & Automation Tooling: `./aedis/instruments/` (Lead Item 2)
- **ISO Process Mapping:** ISO/IEC/IEEE 12207:2017 §6.2.2 (Infrastructure Management Process - Tooling & Environment); ISO/IEC/IEEE 24765:2017 §3.731 (Compiler) and §3.4116 (Static Analyzer).
- **Architectural Rationale:** Deterministic machine tools built strictly on standard library (stdlib) primitives with zero heavy external dependencies. Act as the automated guardians of the system invariants.
- **Internal Sub-Structure & Actual Physical Occupants:**
  - `linters/`:
    - `linter_v2.py` (Migrating from `./shadow-bootstrap/governance/instruments/linters/`): First-generation AST and syntax checker.
    - `linter.py`: The second-generation sovereign micro-linter verifying glossary integrity, kebab-case adherence, and table syntax.
  - `compilers/`:
    - `adr_compiler.py` (Migrating from `./shadow-bootstrap/governance/instruments/`): The First-generation deterministic document compiler converting input slots into canonical Markdown.
  - `verifiers/`:
    - Hash lock generators, drift detectors, and RTM matrix assemblers.

### 11.8 Software Implementation Runtime: `./aedis/src/`
- **ISO Process Mapping:** ISO/IEC/IEEE 12207:2017 §6.4.7 (Software Implementation Process); ISO/IEC/IEEE 15288:2015 §6.4.7.
- **Architectural Rationale:** The physical home of production code implementing the AEDIS engine.
- **Internal Sub-Structure & Actual Physical Occupants:**
  - `kernel/`: Minimal execution runtime, FSM transition engine, and AST traversal logic.
  - `adapters/`: File system I/O, SQLite/PostgreSQL database connectors, and CLI stream adapters.

### 11.9 Verification & Quality Assurance: `./aedis/tests/`
- **ISO Process Mapping:** ISO/IEC/IEEE 29119:2022 (Software Testing: Concepts, Test Processes, Test Techniques).
- **Architectural Rationale:** Provides independent, repeatable verification evidence enforcing closed-loop integrity ($D=0$).
- **Internal Sub-Structure & Actual Physical Occupants:**
  - `unit/`: Unit tests for tooling (`test_adr_compiler.py`, `test_linter.py`).
  - `contract/`: CPAC (Contract Preservation Across Compilation) conformance tests.
  - `fixtures/`: Test vectors including intentionally malformed slots and mutated specifications.
  - `locks/`: Machine integrity seals:
    - `req-hashes.lock.json`: Cryptographic SHA-256 hashes of every normative requirement.
    - `rtm.lock.json`: Machine lockfile binding requirements to code functions and test procedures.

### 11.10 Generated Evidence & Records: `./aedis/reports/`
- **ISO Process Mapping:** ISO/IEC/IEEE 15289:2019 RPT (Report) and ISO/IEC/IEEE 12207:2017 §6.4.9 (Verification Records).
- **Architectural Rationale:** Immutable audit records recording verification runs and traceability health.
- **Actual Physical Occupants:**
  - `rtm/`: Full human-readable Requirements Traceability Matrices.
  - `linters/`: Machine-generated diagnostic reports (`linter_v2_report.md`).

### 11.11 Configuration Change Control & Ledger: `./aedis/ledger/`
- **ISO Process Mapping:** ISO/IEC/IEEE 12207:2017 §6.3.3 (Decision Management Process) and §6.4.5 (Configuration Management - Change Records); ISO/IEC/IEEE 15288:2015 §6.4.10 (Problem Resolution Process).
- **Architectural Rationale:** Append-only historical tracking of human architectural decisions, official errata corrections, and tracked technical debt.
- **Internal Sub-Structure & Actual Physical Occupants:**
  - `decisions/DECISIONS.md`: The single-line construction debate log (D-001..D-NNN) recording every architectural decision, rationale, and prevented failure mode.
  - `errata/`: Formal records of sanctioned changes to sealed baselines (ERR-NNNN).
  - `debt/DEBT-L0-000001.md`: The Live Technical Debt Ledger tracking existing open debt items (including CRLF normalization, sandbox isolation, compiler bootstrapping, and glossary resolution loops).

---

## 12. Long-Term Stress-Test Threats & Real-World Failure Post-Mortems

This section documents explicit 1-3 year architectural stress-test threats and their historical industry post-mortems to ensure resilient repository governance.

### 12.1 Threat 1: The Specification Decomposition Crisis (Specification Rot & Drift)
- **Real-World Case Analogy:** Large-scale enterprise and open-source monorepos (e.g., Linux Kernel subsystem documentation vs source divergence, massive enterprise microservice refactoring post-mortems).
- **Failure Mechanism:** When normative specifications (`./aedis/specs/bl-0/`) and implementation code (`./aedis/src/`) reside in separate directory trees, rapid implementation cycles under deadline pressure cause developers and AI agents to update source code while omitting corresponding specification updates. Over 1-3 years, specification rot divorces documentation from physical truth, rendering baselines obsolete.
- **Architectural Safeguard:** Mandatory automated bidirectional hash-locking between requirements (`REQ-ID`) and code test targets enforced at the CI gate.

### 12.2 Threat 2: The Taxonomy Straightjacket (Rigid Suffix Saturation)
- **Real-World Case Analogy:** Early J2EE and CORBA enterprise framework design collapses where rigid architectural role classifications failed to accommodate emergent domain concerns.
- **Failure Mechanism:** Strict adherence to a closed set of component role suffixes (`*Engine`, `*Supervisor`, `*Watchdog`, `*Ledger`, `*Adapter`, `*Gateway`, `*Envelope`, `*Sentinel`) inevitably faces novel domain primitives that fit none of the categories after 18-24 months of evolution. Engineers resort to mislabeling components (e.g., calling simple caches `*Gateway`), corrupting semantic clarity and rendering static analysis linters obsolete.
- **Architectural Safeguard:** Formal ADR-governed taxonomy expansion protocols requiring explicit versioned updates to the taxonomy specification before introducing new suffixes.

### 12.3 Threat 3: Pipeline Trash Heap & Staging Paralysis
- **Real-World Case Analogy:** Unmanaged AI agent staging buffers and continuous ingestion queues in multi-agent autonomous engineering pipelines.
- **Failure Mechanism:** Unmonitored staging and intake directories (`./aedis/pipeline/intake/`, `./aedis/pipeline/staging/`) accumulate hundreds of unsealed candidate proposals, abandoned drafts, and mutant test files generated by autonomous agent contours (Gemini and Kimi). Without cleanup protocols, agents ingest stale drafts as normative truth, choking the ingestion pipeline.
- **Architectural Safeguard:** Enforced Time-to-Live (TTL) expiration policies and automated garbage collection routines quarantining unsealed proposals after 14 days.

### 12.4 Threat 4: The Hyperlink Rot & Git Blame Amputation
- **Real-World Case Analogy:** Massive W3C specification restructuring and cloud-native documentation repository splits.
- **Failure Mechanism:** Extensive cross-document hyperlinking coupled with folder restructuring shatters relative links (`../../specs/...`) across thousands of files. Furthermore, mass file moves (`git mv`) can fracture historical authorship provenance (`git blame`), erasing the causal rationale behind critical engineering decisions.
- **Architectural Safeguard:** Universal logical identifier addressing (`SPEC-ID`) resolved via compiler index lookup tables combined with invariant relative path rooting.





