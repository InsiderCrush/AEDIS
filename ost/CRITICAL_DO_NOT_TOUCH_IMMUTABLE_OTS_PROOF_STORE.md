FILE_MUTATION: OPERATOR_ONLY
SPDX-FileCopyrightText: 2026 InsiderCrush
SPDX-License-Identifier: CC-BY-4.0

# CRITICAL: DO NOT TOUCH OR MODIFY THIS DIRECTORY UNDER ANY CIRCUMSTANCES
(meta: cryptographic proof vault protection | prevents hash invalidation and timestamp breakage | immutable storage)

## DOCUMENT CONTROL
- **Document ID:** AEDIS-GUARD-OST-001
- **Document Type (ISO 15289):** Critical Storage Protection Sentinel / Security Directive
- **Issuing Authority:** Operator (Sole Decision-Making Authority)
- **Applicability:** All Contours (Gemini, Kimi, External LLMs, Automated CI/CD, Human Agents)
- **Notation & Encoding:** CommonMark v0.31 (Strict AEDIS Profile, Zero-HTML) | UTF-8 (No BOM)
- **Lifecycle Status:** Baseline 0 (Permanent Invariant)

## CRITICAL LOCKS
- **OST_STORAGE_LOCK=1**: MUTATION=FORBIDDEN | OVERWRITE=FORBIDDEN | DELETE=FORBIDDEN | REENCODING=FORBIDDEN | LEVEL=CRITICAL

## 1. Absolute Immutability Directive

This directory (./ost/) is a dedicated cryptographic proof vault and historical evidentiary archive.

Under no circumstances shall any AI agent (Gemini, Kimi, Claude, GPT, or others), background process, automated formatter, linter, or human operator add, edit, format, delete, rename, or touch any files located inside this directory tree.

## 2. Technical Grounding & OpenTimestamps Invariant

Files stored within this directory hierarchy are cryptographically bound to detached timestamp proofs created via OpenTimestamps (see https://opentimestamps.org/).

1. Bitwise Hash Dependency: Each stamped file (such as ./ost/2026-10-11/README.md) has an associated proof file (.ots) containing cryptographic commitments directly rooted in the Bitcoin blockchain.
2. Irreversible Hash Corruption: Any modification whatsoever — including single-character replacements, whitespace trimming, newline conversions (LF to CRLF), or metadata touches — alters the SHA256 cryptographic digest of the source file.
3. Proof Invalidation: Altering the source file breaks mathematical verification against the .ots Merkle tree, irrevocably destroying legal and historical proof of existence for that artifact.

## 3. Operational Rule for Agent Contours

- Reading Directive: Agent contours may read timestamped archives strictly when explicitly directed by the Operator for audit or disaster recovery.
- Writing Directive: Zero write operations permitted. Any tool call or command attempting to mutate any path starting with ./ost/ is a critical protocol violation and shall terminate with Exit Code 1.
