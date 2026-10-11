FILE_MUTATION: OPERATOR_ONLY
SPDX-FileCopyrightText: 2026 InsiderCrush
SPDX-License-Identifier: CC-BY-4.0

# Specification and Protocol for LLM Harness Document Formatting
(meta: technical documentation structure standard for LLM contour | single-point cascading migration | zero entropy harness schema)

## DOCUMENT CONTROL
- **Document ID:** AEDIS-PROT-HARNESS-001
- **Document Type (ISO 15289):** Technical Standard / Formatting Protocol
- **Issuing Authority:** Operator (Sole Decision-Making Authority)
- **Applicability:** Component 3 Technical Documentation & Component 4 Project Artifacts (State Files, Relays, Gateways, Protocols)
- **Notation & Encoding:** CommonMark v0.31 (Strict AEDIS Profile, Zero-HTML) | UTF-8 (No BOM)
- **Lifecycle Status:** Baseline 0 (Active Standard)

## HARNESS_FORMAT LOCKS
- **HARNESS_FORMAT_MUTATION_LOCK=1**: WRITE_PROTOCOL=OPERATOR_DIRECT_CMD_ONLY | AUTONOMOUS_MUTATION=FORBIDDEN | LEVEL=CRITICAL

---

## 1. Primary Objective & Strategic Goal

1.1. **Self-Describing Master Template (Metacircular Prototype):** This document is a 100% self-describing normative template for Component 3 of the AEDIS standard (Technical documentation describing the working contour of LLMs and AI agents with this template). It does not merely describe abstract rules for other files, but itself embodies and satisfies the exact structural schema it mandates, serving as both the authoritative standard and the live casting mold for all subordinate artifacts.

1.2. **Canonical AEDIS Composition & Boundaries of Applicability:**
The AEDIS standard includes four fundamental components:
- A formal Life Cycle Configuration Baseline (Baseline 0, BL-0), implemented on the basis of the international standards ISO/IEC/IEEE 12207, ISO/IEC/IEEE 15288, ISO/IEC/IEEE 29148, ISO/IEC/IEEE 29119, and ISO/IEC 25010 through documented tailoring.
- Methods and mechanisms for working with it to implement new technical projects on its basis, including software tools.
- Technical documentation describing the working contour of LLMs and AI agents with this template; these documents themselves are an integral part of the Life Cycle Configuration Baseline (Baseline 0, BL-0).
- The working contour of LLMs and AI agents — entry and work according to these documents; the contour is described for specific systems: Google AI Studio and GitHub.

This protocol is established as the authoritative normative source and canon of Component 3 ("Technical documentation describing the working contour of LLMs and AI agents with this template"). The jurisdiction of this standard is strictly bounded to governing the technical documentation of Component 3 in its entirety, as well as the operational artifacts of Component 4 specifically within this project (agent state files, operational relays, entry gateways, manifests, and interaction protocols). Components 1 and 2 possess distinct, rigorous system-level governance and are excluded from the jurisdiction of this protocol; the standard does not govern product application code or broader system engineering lifecycles outside this contour.

1.3. **Elimination of Structural Entropy:** Enforce absolute topological uniformity across all human-AI and agent-to-agent interfaces, ensuring Transformer attention mechanisms operate under zero structural ambiguity (D(S, T) = 0).

1.4. **Single-Point Cascading Migration (Self-Application):** Act as the single source of truth for the entire operational harness. Whenever this protocol is amended or upgraded by the Operator, all downstream Component 4 files shall be deterministically refactored and updated through automated conveyor execution (T1), cascading structural changes across all operational rails in a batch, predictable regime without ad-hoc manual deviation.

1.5. **Canonical Carrier Language & Normative Representation Profile (Strict AEDIS CommonMark Profile):**
The master representation language for all Component 3 normative documentation and Component 4 contour artifacts shall strictly be the CommonMark Specification (v0.31) under the deterministic Strict AEDIS CommonMark Profile. This profile is an imperative representation standard with zero tolerance for deviations:
- **Base Specification:** CommonMark v0.31 with GFM Tables extension.
- **Character Encoding & Newlines:** UTF-8 strictly without Byte Order Mark (BOM). Newlines shall be normalized Unix LF ("\n").
- **Paragraph Topology & Vertical Spacing (Vertical Spacing Invariant):**
  - Numbered clauses, paragraphs, tables, and specification blocks shall be separated by exactly one blank line (Unix LF LF). Concatenation of clauses into a single paragraph block (single LF without blank line) is strictly prohibited.
  - Redundant blank lines (two or more consecutive LF) are strictly prohibited (vertical whitespace collapse).
  - Lists shall remain monolithic (Tight Lists): blank lines between adjacent bullet items of the same level are prohibited to prevent parser layout inflation.
- **Permitted Syntax Nodes (Whitelisted AST / Allowed AST):**
  - ATX Headings: # and ## strictly (heading levels 3+ restricted exclusively to specification subclause numbering).
  - Unordered flat bullet lists: using hyphen marker - exclusively.
  - ISO/IEC 11179 Key-Value attributes: formatted strictly as "- **[Key]:** [Value]".
  - Tables: standard GFM pipe syntax ("|---|").
  - Textual blocks: using flat boundary delimiters (TEMPLATE_*_START / TEMPLATE_*_END) or standard 4-space indentation.
- **Prohibited Syntax Nodes (Forbidden AST):**
  - Raw HTML elements of any type ("&lt;div&gt;", "&lt;span&gt;", "&lt;br&gt;") and unescaped angle brackets in running text.
  - Hidden HTML comments ("&lt;!-- --&gt;") with zero exceptions. References to comments shall be formulated terminology-wise (HTML comment syntax) or entity-escaped (&lt;!-- --&gt;).
  - Backticks of any kind with zero exceptions: both triple fenced codeblocks and single inline backticks (CodeSpan). Literal commands, identifiers, and machine tokens shall be represented using uppercase letters, straight quotes, or 4-space indentation.
  - Mathematical dollar delimiters and pseudo-LaTeX formatting: usage of dollar symbols ($ and $$) is strictly forbidden. All formulas, equations, and invariants shall be expressed exclusively via plain text / ASCII (e.g., D(S, T) = 0).
  - Decorative inline formatting (italics, strikethrough, emojis, colored text).
- **Interoperability Principle:** For external runtime environments requiring alternative representations (unrendered terminal streams, legacy operating systems, binary compilers, requirements databases), deterministic translation adapters (CommonMark AST -> Plaintext / JSON / PDF) shall be utilized. Information invariance (D(S, T) = 0) shall be mathematically preserved across all representation transformations.

---

## 2. Problem Statement

2.1. **Context Drift and Intention Misinterpretation:** When normative documents utilize unrefined or ambiguous introductory headings (such as "Preamble"), Large Language Models (LLMs) interpret the normative text as passive background or historical context, decreasing its execution attention weight (Attention Weight Drift).

2.2. **Asymmetric Context Degradation:** The use of hidden markup tags ("&lt;!-- --&gt;") to transmit normative rules or covert prompt steering introduces context asymmetry: the LLM parses hidden comments while the Operator viewing the repository interface does not. This violates the core transparency principle of AEDIS.

2.3. **Absence of Canonical Layout Rules:** Lack of a standardized document structure leads to ad-hoc formatting across new harness artifacts (Charter, Agent Manifests, Contour State, Protocols), increasing entropy and causing role ambiguity during LLM execution.

2.4. **High Friction in Scaffolding Refactoring:** Without a centralized structural schema, updating operational conventions across multiple agent contour files requires fragmented, error-prone manual edits instead of deterministic, rule-driven cascading migration.

---

## 3. Technical Specification

All Component 3 documents and Component 4 operational harness artifacts shall conform to the following component inventory (initial aggregation list prior to structural categorization).

### 3.0. Canonical Micro-Template for Specification Elements (Clause Drafting Standard)
Every component within Section 3 shall be authored strictly according to the following three-tier micro-schema to guarantee mathematical uniformity, cognitive authority, and verifiable ground truth:

#### 3.0.1. Tier 1: Formal Definition & Syntax Structure
- **Classification (ISO/IEC/IEEE 15289 & ISO Directives Part 2):** Formal topological category and standardized element classification.
- **Exact Literal Syntax:** Verbatim representation of the element (flat string, key-value block, or template envelope).
- **Normative Placement Rule:** Strict physical line index, token budget, and structural isolation rules formulated with the modal verb "shall".

#### 3.0.2. Tier 2: Engineering Justifications & Cognitive Architecture
- Formulated as discrete atomic theses (J1..JN), where every thesis shall mandate two structural fields:
  - **Thesis:** High-density causal statement articulating the physical failure mode prevented, the cybernetic mechanism enforced, and its direct mathematical impact on entropy (D(S, T) = 0).
  - **Authority & Precedents:** Authoritative standard citations (ISO/IEC/IEEE, RFC), peer-reviewed scientific literature (author, publication), and verified historical systems engineering precedents (POSIX, compiler internals, runtime invariants).

#### 3.0.3. Tier 3: Quad-Verification Pipeline & ISO Synthesis Gate
Prior to the normative drafting or ratification of any candidate element, it shall unconditionally pass the four-stage epistemological verification conveyor:
1. **De Jure Benchmarking (ISO Audit):** Mandatory verification against relevant international standards (ISO/IEC/IEEE 15288, 12207, 15289, 29148, 25010, ISO Directives Part 2). Identify existing formal definitions, taxonomies, and structural rules.
2. **Temporal Grounding (Current-Date Verification):** Active real-time investigation of the state of the art as of the live operational timestamp. Reject obsolete training biases; ground rules in current empirical reality.
3. **De Facto Empirical Audit (Production Runtime Verification):** Cross-examination against verified implementations across operating system kernels, compiler infrastructure, production CI/CD architectures, and autonomous agent runtime environments.
4. **Formal ISO-Anchored Synthesis:** Harmonize empirical findings with formal de jure standards. The resulting specification shall be synthesized and packed strictly through ISO-compliant terminology, modal requirements syntax ("shall"), and closed-loop verification criteria (D(S, T) = 0).

---

### 3.1. Element 1: Operational Sentinel (MUTATION LOCK)

#### 3.1.1. Formal Definition & Syntax
- **Classification (ISO/IEC/IEEE 15289 & ISO Directives Part 2):** Preliminary Element / Operational Sentinel (Access Control Prefix).
- **Exact Literal Syntax:** Flat, unadorned string placed strictly on Line 1 (Token Index 0):
    FILE_MUTATION: OPERATOR_ONLY
- **Normative Rule:** The sentinel shall occupy Line 1 in complete isolation, with zero preceding blank lines, leading whitespace, markdown tags, or decorative characters.

#### 3.1.2. Engineering Justifications & Cognitive Architecture
- **J1. Lexical & AST Independence (The "Magic Line" Invariant):**
  - **Thesis:** Raw flat-text placement at Byte 0 / Line 1 decouples mutation enforcement from markdown Abstract Syntax Tree (AST) parsing. Enables deterministic O(1) sub-millisecond ingress filtering via lightweight shell utilities ("head -n 1", "grep") and CI/CD pre-commit hooks prior to runtime compiler bootstrap.
  - **Authority & Precedents:** ISO/IEC/IEEE 15288:2023 §6.3.5 (Configuration Baseline Integrity); ISO/IEC/IEEE 15289:2019 §6.1 (Preliminary Control Elements); POSIX execve shebang ("#!"); Ruby "# frozen_string_literal: true"; Vim modeline ("set ro").
- **J2. Attention Sink & Autoregressive Primacy (Zero-Hop Circuit Breaker):**
  - **Thesis:** Transformer self-attention softmax normalization mathematically dumps residual attention mass onto initial sequence tokens (Attention Sink phenomenon / StreamingLLM). Positioned at Token 0 under causal attention masking (M_ij = 0 for j > i), the immutability constraint is injected into the receptive field of 100% downstream tokens, forcing logit suppression against mutating tool calls ("edit_file", "write") prior to semantic plan synthesis.
  - **Authority & Precedents:** Xiao et al. (StreamingLLM, NeurIPS); Lost-in-the-Middle mitigation; Autoregressive Logit Masking; Ingress Tool Guardrails.
- **J3. Structural Primacy of Access Control over Semantics:**
  - **Thesis:** In formal cybernetics and secure systems engineering, ingress authorization checks must strictly precede state and semantic evaluation. Evaluating whether an agent possesses write authority governs and preempts any cognitive interpretation of document payload, preventing speculative refactoring hallucinations.
  - **Authority & Precedents:** ISO/IEC 27002:2022 §8.4 (Source Code Access) & §8.12 (Data Modification Prevention); ISO/IEC/IEEE 15288:2023 §6.4.14 (System Security Engineering / Security Perimeter Validation).
- **J4. Zero-Distortion Context Parity (D(S, T) = 0):**
  - **Thesis:** Unformatted raw-text ingress guarantees 100% bitwise parity across terminal displays ("cat", "less"), Git forge previews, raw API context feeds, and operator web consoles. Eliminates hidden markdown rendering artefacts, token truncation, and human-agent context asymmetry.
  - **Authority & Precedents:** ISO/IEC/IEEE 29148:2018 (Singular and Unambiguous Interpretation); AEDIS Invariant |S| = argmin {|S| : D(S, T) = 0}.

### 3.2. Element 2: Flat Legal Provenance Sentinels (FLAT PROVENANCE SENTINELS)

#### 3.2.1. Formal Definition & Syntax Structure
- **Classification (ISO/IEC/IEEE 15289:2019 Clause 6.1 & ISO Directives Part 2 Clause 6.1):** Preliminary Informative Element / Flat Legal Provenance Sentinels.
- **Exact Literal Syntax:** Two flat, unadorned strings positioned strictly on Line 2 and Line 3 (by direct analogy with the Operational Sentinel on Line 1), with zero HTML comments, markdown formatting characters, list markers, or whitespace padding:
    Line 2: SPDX-FileCopyrightText: [Year] [Holder]
    Line 3: SPDX-License-Identifier: [SPDX-ID]
- **Normative Placement Rule:** Line 2 and Line 3 shall immediately follow the Operational Sentinel (Line 1) with zero intervening blank lines. Line 3 shall be separated from the subsequent document title by exactly one blank line (LF delimiter). Any usage of HTML comment wrappers ("&lt;!-- --&gt;") is strictly prohibited.

#### 3.2.2. Engineering Justifications & Cognitive Architecture
- **J1. Absolute Human-AI Context Parity & Elimination of Hidden Layers (D(S, T) = 0):**
  - **Thesis:** Complete elimination of HTML comment syntax ("&lt;!-- --&gt;") guarantees that Human Operators viewing Markdown renderers (GitHub, GitLab, documentation engines) and LLMs processing raw token sequences observe bitwise-identical content. Eliminates covert information sublayers, eradicates cognitive asymmetry, and enforces the core AEDIS transparency invariant under the Strict Zero-HTML Profile.
  - **Authority & Precedents:** ISO/IEC/IEEE 29148:2018 (Specification Singularity and Transparency); CommonMark v0.31 Strict AEDIS Profile (Zero-HTML AST Invariant); AEDIS System Constitution (Open Context Principle).
- **J2. AST Independence & O(1) CLI Ingress Filtering ("Magic Lines" Derivative):**
  - **Thesis:** Identical to the Operational Sentinel (Line 1), flat SPDX sentinels require no Abstract Syntax Tree (AST) parsing. The Preliminary Control Triad (Lines 1–3) is extracted via lightweight Unix streaming utilities ("head -n 3") and pre-commit CI/CD hooks in O(1) sub-millisecond execution time prior to invoking heavyweight compilers or validators.
  - **Authority & Precedents:** ISO/IEC/IEEE 15288:2023 §6.3.5 (Configuration Baseline Integrity); POSIX stream processing primitives; Linux Foundation REUSE Software Specification v3.0 (Tagging Plaintext and Commentless Files).
- **J3. Full Compliance with International Standard SPDX (ISO/IEC 5962:2021):**
  - **Thesis:** ISO/IEC 5962 and REUSE directly mandate flat, commentless tags for textual file formats lacking native comment constructs. Automated license compliance analyzers (FOSSology, reuse-tool, scancode) detect "SPDX-FileCopyrightText:" and "SPDX-License-Identifier:" via header regex matching independently of comment delimiters.
  - **Authority & Precedents:** ISO/IEC 5962:2021 §4.2; Linux Foundation REUSE 3.0 Clause 2.1; Software Package Data Exchange (SPDX) Specification v2.3/v3.0.
- **J4. Cognitive Primacy of Intellectual Property (IP Attention Primacy):**
  - **Thesis:** Placing legal copyright and licensing terms on immediate initial attention indices (tokens 5–25) directly behind the Operational Sentinel grounds the legal regime within the Transformer's initial attention sink. This prevents intellectual property distortion during downstream specification synthesis and suppresses autoregressive hallucinations regarding copyright reassignment.
  - **Authority & Precedents:** Vaswani et al. (Attention Is All You Need — Positional Encodings); Prompt Injection & Guardrail Anchoring; ISO/IEC/IEEE 15288:2023 §6.4.14 (System Security Engineering and Asset Integrity).

#### 3.2.3. Quad-Verification Pipeline & ISO Synthesis Gate
1. **De Jure Benchmarking (ISO Audit):** Conforms to ISO Directives Part 2 (Clause 6.1) and ISO/IEC 5962:2021.
2. **Temporal Grounding (2026):** Fully aligns with Linux Foundation REUSE v3.0 specification for commentless file tagging.
3. **De Facto Empirical Audit:** Matches verified plain-text licensing conventions across modern open-source toolchains and AI system harnesses.
4. **Formal ISO-Anchored Synthesis:** Requirements structured through formal ISO modal syntax ("shall") enforcing closed-loop verification (D(S, T) = 0).

### 3.3. Component 3: Title and Meta-Annotation
Every document shall commence with a level-1 heading "# Title" followed immediately by a single-line parenthetical meta-annotation "(meta: ...)" within the first 50 tokens of the file:
    # [Document Title]
    (meta: <purpose> | <primary effect> | <target contour>)

### 3.4. Component 4: Document Control Block (DOCUMENT CONTROL)
A mandatory Key-Value metadata block complying with ISO/IEC 11179 and ISO/IEC/IEEE 15289:
    ## DOCUMENT CONTROL
    - **Document ID:** AEDIS-[TYPE]-[NUMBER]
    - **Document Type (ISO 15289):** [Charter | Manifest | State | Protocol]
    - **Issuing Authority:** Operator (Sole Decision-Making Authority)
    - **Applicability:** [Target Agents / Operator]
    - **Lifecycle Status:** [Baseline Status]

### 3.5. Component 5: Security & Immutability Locks (LOCKS)
Every operational file shall declare explicit operational and mutation constraints directly under "## [NAME] LOCKS":
    - **[LOCK_NAME]=1**: [MUTATION_RULE] | [UNLOCK_CONDITION] | LEVEL=[CRITICAL | HIGH | OPERATIONAL]

### 3.6. Component 6: Role Directive Block (HARNESS DIRECTIVE)
When a document establishes normative rules, behavioral boundaries, or role mandates for LLMs, these instructions shall be structured under an explicit "## HARNESS DIRECTIVE" heading, replacing passive "Preamble" sections.

### 3.7. Component 7: Full Transparency and Tag Prohibition
Hidden HTML comments ("&lt;!-- --&gt;") and invisible markup of any kind are strictly prohibited. All normative rules, behavioral directives, and legal provenance descriptors shall remain 100% visible to both Human Operators and AI Agents under the Strict CommonMark Profile (Zero-HTML).

---

## 4. Cascading Self-Migration Protocol

4.1. **Cascade Authority:** AEDIS-PROT-HARNESS-001 is the root schema. Any amendment ratified by the Operator triggers a mandatory downstream schema synchronization.

4.2. **Conveyor Execution:** Migration of downstream Component 4 files shall proceed strictly through Conveyor T1 (Verbatim Execution) without speculative reinterpretation:
   - Identify structural delta between current file layout and updated AEDIS-PROT-HARNESS-001 schema.
   - Formulate discrete replacement tasks (STEP 1..N) targeting each affected artifact in "./aedis/agents/".
   - Execute verification checks across all canonical components defined in Section 3.

4.3. **Atomic Rollout:** Cascading migrations shall be executed atomically to ensure no mixed-version states exist across agent contours.

---

## 5. Rationale and Technical Justification

5.1. **Rationale for Replacing "Preamble" with HARNESS DIRECTIVE:**
- **Cause:** In LLM pre-training datasets, the token "Preamble" correlates with non-binding introductions or historical background text.
- **Effect:** Transitioning to HARNESS DIRECTIVE switches the Transformer's attention mechanism into an active instruction-following mode.

5.2. **Rationale for Parenthetical (meta: ...) Annotation in First 50 Tokens:**
- **Cause:** Transformer architectures assign high attention weights to initial sequence tokens.
- **Effect:** The (meta: ...) annotation establishes single-hop semantic indexing and role context prior to parsing detailed specifications.

5.3. **Rationale for ISO/IEC 11179 Key-Value Structure (DOCUMENT CONTROL):**
- **Cause:** Named Entity Recognition (NER) and instruction extraction in LLMs operate with maximum precision on structured Key-Value pairs.
- **Effect:** Eliminates entity hallucination by explicitly declaring "Issuing Authority" and "Applicability".

5.4. **Rationale for Single-Point Cascading Migration:**
- **Cause:** Manual per-file edits in multi-agent environments cause semantic drift and version divergence.
- **Effect:** Guarantees mathematical consistency (D(S, T) = 0) across all agent gates through algorithmic schema propagation.

5.5. **Rationale for Prohibiting Hidden Comments ("&lt;!-- --&gt;"):**
- **Cause:** Hidden comments break context parity between Operator and AI Agent.
- **Effect:** Guarantees 100% deterministic, shared context visibility across human and machine interfaces.
