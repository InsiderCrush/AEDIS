FILE_MUTATION: OPERATOR_ONLY
SPDX-FileCopyrightText: 2026 InsiderCrush
SPDX-License-Identifier: CC-BY-4.0

# AEDIS Licensing

(meta: repository licensing policy | human-readable layer over per-file SPDX headers | deployment scope, not part of the template universe)

This file is the single source of truth for repository component licensing. It implements the LICENSES section of ./README.md. Per-file SPDX headers carry identical normative force.

## LICENSES

| Component | License | Notes |
|---|---|---|
| Text: standard, corpus, methods, meta, reports, gates (all textual content) | CC-BY-4.0 | Free for any use, including commercial, with attribution to InsiderCrush. |
| Code: compiler, linters, drift verifiers, tests, tomls, configs (all machine artifacts) | PolyForm-Noncommercial-1.0.0 | Free for non-commercial use; commercial use requires a written agreement with the operator (purchase). |
| Project name and trademarks | Reserved | Reserved by InsiderCrush. Permitted for compatibility naming (e.g. "for AEDIS"), not for claiming endorsement. |
| Platform-contour files: src/, index.html, package.json, tsconfig.json, vite.config.ts, metadata.json, .env.example | Not licensed by the operator | Imposed by Google AI Studio project synchronization; the Operator cannot exclude these files. No rights are asserted and no responsibility is taken. Governed by the terms of the generating platform; ideally to be removed. |
| VCS service files: .gitignore, .gitattributes, .gitkeep | CC0-1.0 | Trivial functional service files; no rights reserved. |
| ost/ proof store: snapshots and *.ots | Snapshots: per embedded SPDX headers; .ots: not licensed | Historical frozen exhibits; content may contradict the current corpus. .ots are cryptographic evidence (OpenTimestamps), not creative works; no copyright asserted. |
