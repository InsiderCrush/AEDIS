---
title: Canonical Glossary
status: accepted
date: 2026-10-04
version: 1.0.0
related: [ADR-L0-000003]
---
<!-- SPDX-FileCopyrightText: 2026 InsiderCrush -->
<!-- SPDX-License-Identifier: CC-BY-NC-4.0 -->

# Canonical Glossary

## Status
Accepted

## Context
The canonical dual-key glossary of the bundle: the closed vocabulary and the only legitimate source of terms (ADR-L0-000003/R1). Mined from the corpus, the method texts, the session vocabulary of 2026-10-04, and external factura (marked reserved, non-normative). Active terms carry self-sufficient definitions with ratified sources; forbidden synonyms guard against synonymy drift; the reserved fund registers external concepts awaiting adoption.

Conformance rule: corpus documents issued before this glossary are conformant by grandfathering until their rebirth through the conveyor (pipeline P5); machine lexicon enforcement begins with the canonical linter (pipeline P6). Until then this document is the registration layer, not a gate.

## Dual-Key Matrix
| Term (EN)                | Term (RU)                      | Variants                             | Status   |
| :----------------------- | :----------------------------- | :----------------------------------- | :------- |
| a-item                   | A-пункт                        | A-row, debt item                     | active   |
| adr                      | АДР                            | архитектурная записка о решении      | active   |
| allocated-ranges         | выделенные диапазоны           |                                      | active   |
| anti-pattern             | анти-паттерн                   | requirement anti-pattern             | active   |
| authoring-instrument     | инструмент порождения          | authoring tool                       | active   |
| blast-radius             | радиус поражения               | blast radius                         | active   |
| bundle                   | бандл                          | specification bundle                 | active   |
| bundle-root              | корень бандла                  | bundle root                          | active   |
| circuit-alpha            | Circuit Alpha                  | alpha circuit                        | active   |
| circuit-beta             | Circuit Beta                   | beta circuit                         | active   |
| clause-order             | порядок клауз                  | canonical clause order               | active   |
| clean-session            | чистая сессия                  | clean run                            | active   |
| closed-loop-verification | верификация замкнутого контура | closed-loop                          | active   |
| compiler                 | компилятор                     | ADR compiler                         | active   |
| compound-statement       | составное требование           | compound requirement                 | active   |
| context-ceiling          | контекстный потолок            | context ceiling                      | active   |
| conveyor                 | конвейер                       | pipeline                             | active   |
| corpus                   | корпус                         | normative corpus                     | active   |
| corpus-rebirth           | перерождение корпуса           | corpus rebirth                       | active   |
| critical-scope           | критичный скоуп                | critical fabrication scope           | active   |
| debt-ledger              | долговая книга                 | DEBT                                 | active   |
| dependency-graph         | граф зависимостей              | dependency graph                     | active   |
| derivation               | деривация нормы                | norm derivation                      | active   |
| derived-lockfile         | производный локфайл            | derived lockfile                     | active   |
| deterministic-lowering   | детерминированный лоуэринг     | deterministic lowering               | active   |
| disclosure-matrix        | матрица раскрытия              | disclosure matrix                    | active   |
| dod                      | DoD                            | definition of done                   | active   |
| draft                    | драфт                          | compiled draft                       | active   |
| dual-key                 | Dual-Key                       | двухключевая матрица                 | active   |
| ears                     | EARS                           | Easy Approach to Requirements Syntax | active   |
| ears-pattern             | паттерн EARS                   | EARS pattern                         | active   |
| err-identifier           | ERR-идентификатор              | ERR code                             | active   |
| errata                   | эратта                         | erratum protocol                     | active   |
| error-catalog            | каталог ошибок                 | error registry (obsolete)            | active   |
| factura                  | фактура                        | raw factura                          | active   |
| fitting                  | подгонка                       | spec-to-code fitting                 | active   |
| fixture                  | фикстура                       | test fixture                         | active   |
| forbidden-synonym        | запрещённый синоним            | forbidden alias                      | active   |
| form-only-evaluation     | оценка только формы            | form-only                            | active   |
| formula-b                | формула Б                      | Formula B                            | active   |
| frontmatter              | фронтматер                     | YAML front matter                    | active   |
| fsm                      | КА                             | FSM, finite state machine            | active   |
| gherkin                  | Gherkin                        |                                      | reserved |
| glossary                 | глоссарий                      | canonical glossary                   | active   |
| halt                     | остановка                      | halt-and-report                      | active   |
| hyper-glossary           | гиперглоссарий                 | hyper-redundant glossary             | active   |
| intake                   | интейк                         |                                      | active   |
| interaction-map          | карта взаимодействия           | interaction map                      | active   |
| lifecycle-fsm            | жизненный цикл документа       | document lifecycle                   | active   |
| linter                   | линтер                         | governance linter                    | active   |
| living-record            | живая запись                   | living document                      | active   |
| log4brains               | Log4brains                     |                                      | reserved |
| madr                     | MADR                           |                                      | reserved |
| meta-block               | META_BLOCK                     |                                      | active   |
| meta-comment             | мета-комментарий               | markdown comment, HTML comment       | active   |
| meta-preamble            | META_PREAMBLE                  |                                      | active   |
| micro-step               | микрошаг                       | micro-stepped step                   | active   |
| minimal-completeness     | минимальная полнота            | minimal completeness                 | active   |
| mutation-score           | mutation testing score         |                                      | reserved |
| mutation-self-test       | мутационный самотест           | mutation self-test                   | active   |
| norm-manifest            | норм-манифест                  | norm manifest                        | active   |
| norm-ref                 | norm_ref                       | norm reference                       | active   |
| orphan-policy            | политика сирот                 | orphan policy                        | active   |
| pass                     | пасс                           | sync pass                            | active   |
| preflight                | префлайт                       | compile preflight                    | active   |
| projection               | проекция                       | GitHub projection                    | active   |
| ratification             | ратификация                    | acceptance (FSM)                     | active   |
| referential-integrity    | ссылочная целостность          | referential integrity                | active   |
| regen-tool               | реген-инструмент               | regen                                | active   |
| registration-gate        | регистрационный гейт           | registration gate                    | active   |
| related                  | related                        | карта цитирования, библиография      | active   |
| req-identifier           | REQ-идентификатор              | REQ id                               | active   |
| reqif                    | ReqIF                          |                                      | reserved |
| reserved-term            | зарезервированный термин       | reserved entry                       | active   |
| rtm                      | RTM                            | requirements traceability matrix     | active   |
| sbom                     | SBOM                           |                                      | reserved |
| scope-lock               | скоуп-лок                      | scope lock                           | active   |
| sdd                      | СДД                            | SDD                                  | active   |
| seal                     | печать                         |                                      | active   |
| self-hosting             | самоподдержка                  | self-description                     | active   |
| single-screen-payload    | одноэкранная полезная нагрузка | single-screen payload                | active   |
| skeleton-check           | скелетная проверка             | skeleton check                       | active   |
| slot-file                | слот-файл                      | slots, слоты                         | active   |
| spec-kit                 | Spec Kit                       |                                      | reserved |
| spec-md                  | spec.md                        |                                      | active   |
| staging                  | стейджинг                      |                                      | active   |
| state-registry           | реестр состояний               |                                      | active   |
| strictdoc                | StrictDoc                      |                                      | reserved |
| structurizr              | Structurizr                    |                                      | reserved |
| sync                     | синк                           | synchronization                      | active   |
| synonymy-drift           | дрейф синонимии                | synonym drift                        | active   |
| test-binding             | тестовая привязка              | test binding                         | active   |
| test-contour             | тестовый контур                | test contour                         | active   |
| tighten-only             | принцип ужесточения            | tighten-only metrics                 | active   |
| tla-plus                 | TLA+                           |                                      | reserved |
| transactionality         | транзакционность               | zero bytes on error                  | active   |
| transition-matrix        | матрица переходов              |                                      | active   |
| tripartite-closure       | трипартитное замыкание         | tripartite closure                   | active   |
| tty-verdict              | вердикт TTY                    | operator verdict                     | active   |
| verbatim-anchor          | дословный анкор                | verbatim OLD/NEW                     | active   |
| verification-instrument  | инструмент верификации         | verification tool                    | active   |
| verification-trailer     | трейлер проверки               | Verification trailer                 | active   |
| weak-modality            | слабая модальность             |                                      | active   |
| zero-embedded-data       | ноль данных в коде             | zero embedded data                   | active   |

## Definitions
**a-item** (A-пункт) — One numbered row of the debt ledger (A1, A9, A26); a gap, defect or open question under tracking.
| Source: DEBT-L0-000001; Related: debt-ledger

**adr** (АДР) — Architecture Decision Record: an immutable normative document recording exactly one decision; the atomic unit of the corpus.
| Source: ADR-L0-000001/R1,R2; Related: corpus, lifecycle-fsm, seal

**allocated-ranges** (выделенные диапазоны) — The per-document REQ/ERR identifier ranges declared in frontmatter; identifiers must stay inside.
| Source: ADR-L0-000002/R3; Related: frontmatter, req-identifier

**anti-pattern** (анти-паттерн) — One of the eight prohibited requirement formulations (weak modality, escape clause, compound, and others).
| Source: ADR-L0-000004/R3; Related: ears, weak-modality

**authoring-instrument** (инструмент порождения) — Instrument class that transforms state and produces artifacts; the compiler is the instance.
| Source: ADR-L0-000013/Context (operator verdict 2026-10-04); Related: compiler, verification-instrument

**blast-radius** (радиус поражения) — The inherited risk scope of a module; routes fabrication intensity (critical vs standard).
| Source: 4lk.md (risk routing); Related: circuit-beta, critical-scope

**bundle** (бандл) — Specification Bundle: spec.md + plan.md + tasks.md per topic; the fabrication and review unit of code documents.
| Source: ADR-L0-000001/R4; Related: sdd, spec-md

**bundle-root** (корень бандла) — The governance/ directory; the anchor of every bundle-relative path.
| Source: ADR-L0-000013/REQ (anchor pin) + session fix pass 125; Related: frontmatter, test-contour

**circuit-alpha** (Circuit Alpha) — The amnesia-boundary audit of a fabricated block against its specification.
| Source: 4lk.md (PASS 2); Related: circuit-beta, clean-session

**circuit-beta** (Circuit Beta) — The freeze-replay plus mutation-testing gate executed at integration.
| Source: 4lk.md (PASS 3-4); Related: circuit-alpha, mutation-self-test

**clause-order** (порядок клауз) — The mandatory EARS clause order While -> When -> Where -> If.
| Source: ADR-L0-000004/R2; Related: ears

**clean-session** (чистая сессия) — A session loading only the task-declared context; the amnesia boundary of the method.
| Source: scqg.md + 4lk.md; Related: micro-step, disclosure-matrix

**closed-loop-verification** (верификация замкнутого контура) — Requirement text binds a test; the instrument executes it; verdicts feed the lockfile; drift fails the gate.
| Source: ADR-L0-000009/R1; Related: rtm, linter

**compiler** (компилятор) — The authoring instrument rendering normative documents from slot files; holds no normative data.
| Source: ADR-L0-000013; Related: authoring-instrument, conveyor

**compound-statement** (составное требование) — A requirement expressing two or more independent thoughts; prohibited, must be split.
| Source: ADR-L0-000004/R3 (A1); Related: anti-pattern, ears

**context-ceiling** (контекстный потолок) — The dynamic byte ceiling of the compile preflight: max(98304, 2 x total bytes of ./specs/ADR-L0-*.md), recomputed every compile.
| Source: ADR-L0-000012/R20; Related: preflight, related

**conveyor** (конвейер) — The slot -> compile -> seal -> verify pipeline; the only legitimate birth mechanism for corpus documents.
| Source: scqg.md + meta/pipeline.md; Related: micro-step, slot-file

**corpus** (корпус) — The immutable normative document set under ./specs/, guarded by the linter; grows only by seal.
| Source: ADR-L0-000001/R8; Related: adr, linter

**corpus-rebirth** (перерождение корпуса) — Re-issuing ratified corpus documents through the conveyor from their slot sources, one document per cycle; the self-hosting principle applied to the whole corpus.
| Source: meta/pipeline.md (P4) + ADR-L0-000013/R7; Related: self-hosting, conveyor

**critical-scope** (критичный скоуп) — Full 4-Pass fabrication with both circuits; applied to modules whose blast radius is total.
| Source: 4lk.md (scope routing); Related: blast-radius, circuit-beta

**debt-ledger** (долговая книга) — DEBT-L0: the living ledger of gaps, defects and open questions; closed items are deleted, never archived.
| Source: ADR-L0-000001/R8 + DEBT-L0-000001 header; Related: living-record, a-item

**dependency-graph** (граф зависимостей) — The derived lockfile of the module topology; regenerated by instruments.
| Source: ADR-L0-000008/R1.2; Related: interaction-map, derived-lockfile

**derivation** (деривация нормы) — Every enforced check derives from a ratified L0 R-point recorded in its norm_ref; un-derived checks are refused.
| Source: ADR-L0-000013/R5; Related: norm-ref, formula-b

**derived-lockfile** (производный локфайл) — An instrument-regenerated hash or trace file (rtm.lock.json, req-hashes.lock.json); hand-editing is prohibited.
| Source: ADR-L0-000011/R2 + ADR-L0-000009/R3; Related: regen-tool, rtm

**deterministic-lowering** (детерминированный лоуэринг) — The stage from slot AST to rendered document is pure deterministic standard code; neural calls, generative heuristics and external APIs are prohibited in the pipeline.
| Source: ADR-L0-000013/R8; Related: zero-embedded-data, compiler

**disclosure-matrix** (матрица раскрытия) — The per-file table of governing ADRs; loading more than 3 ADRs per task is an architectural signal.
| Source: ADR-L0-000012/R2,R3; Related: clean-session, norm-manifest

**dod** (DoD) — Definition of Done: the immutable acceptance checklist of a document class.
| Source: ADR-L0-000001/R10; Related: bundle, skeleton-check

**draft** (драфт) — A compiled, not yet sealed document; exists only in staging and dies by seal or cleanup.
| Source: scqg.md; Related: staging, seal

**dual-key** (Dual-Key) — The two-key term matrix (EN key + RU key) with 1-to-1 mapping; unmapped terms fail ERR-L0-000003-1.
| Source: ADR-L0-000003/R1; Related: glossary, synonymy-drift

**ears** (EARS) — The six-pattern requirement syntax; the only legitimate form of a normative requirement.
| Source: ADR-L0-000004/R1; Related: ears-pattern, clause-order

**ears-pattern** (паттерн EARS) — One of six canonical patterns: Ubiquitous, Event-driven, State-driven, Optional feature, Unwanted behaviour, Complex.
| Source: ADR-L0-000004/R1; Related: ears, clause-order

**err-identifier** (ERR-идентификатор) — Document-scoped error code binding a failure mode to a requirement by req_num.
| Source: ADR-L0-000002/R3 + ADR-L0-000013/R5; Related: req-identifier, error-catalog

**errata** (эратта) — The correction protocol for accepted documents; suspended during zero-template authoring, where corrections land in place.
| Source: ADR-L0-000007/R1-R3 + operator doctrine 2026-10-04; Related: ratification, living-record

**error-catalog** (каталог ошибок) — The declarative registry of error codes with trigger and remediation; a diagnostic reference, not a projection.
| Source: ADR-L0-000013/Context (rustc precedent, debate 2026-10-04); Related: err-identifier, tripartite-closure

**factura** (фактура) — Raw extracted material (quotes plus sources) accumulated before synthesis; temporary by design.
| Source: session 2026-10-04 (111.md protocol); Related: hyper-glossary

**fitting** (подгонка) — Shaping a specification to please a checker or existing code; prohibited; defects become explicit norms instead.
| Source: ADR-L0-000011/R1 + session verdict 2026-10-04; Related: form-only-evaluation, derivation

**fixture** (фикстура) — A frozen test-case input defined before the code under test; the contract of a block.
| Source: 4lk.md (PASS 1); Related: test-contour, circuit-alpha

**forbidden-synonym** (запрещённый синоним) — A registered alias that must not be used for a concept; redirects to the canonical term.
| Source: ADR-L0-000003/R1 + this document; Related: glossary, synonymy-drift

**form-only-evaluation** (оценка только формы) — The compiler evaluates document form and never content merit; it never ranks, rewrites, or rejects statements by meaning.
| Source: ADR-L0-000013/R6; Related: compiler, fitting

**formula-b** (формула Б) — The closure semantics: referential integrity (REQ-codes and matrix-codes exist in the catalog) plus orphan policy (every cataloged code is bound to a requirement or a check). Strict equality is a special case.
| Source: ADR-L0-000013 + Dzhemi debate 2026-10-04; Related: referential-integrity, orphan-policy

**frontmatter** (фронтматер) — The YAML header of a corpus document: id, title, status, version, date, related, allocated-ranges.
| Source: ADR-L0-000012/R4; Related: related, allocated-ranges

**fsm** (КА) — Finite State Machine: the executable semantics layer of the corpus; states plus a closed transition matrix.
| Source: ADR-L0-000005/R1; Related: state-registry, transition-matrix

**gherkin** (Gherkin) — BDD scenario syntax (Given/When/Then). External; not a requirement form here.
| Source: external (111.md Pass E); Related: ears

**glossary** (глоссарий) — This document: the closed Dual-Key vocabulary; the only legitimate source of terms.
| Source: ADR-L0-000003/R1; Related: dual-key, forbidden-synonym

**halt** (остановка) — Mandatory stop after each micro-step with a one-line report; the next step starts in a new session.
| Source: scqg.md; Related: micro-step

**hyper-glossary** (гиперглоссарий) — This glossary's form: self-sufficient definitions, mined sources, forbidden synonyms, reserved fund.
| Source: meta/pipeline.md (P2) + brainstorm 2026-10-04; Related: glossary, factura

**intake** (интейк) — ./new-adr/intake/: zone holding slot files awaiting compilation.
| Source: ADR-L0-000013/R3; Related: slot-file, staging

**interaction-map** (карта взаимодействия) — The per-layer edge list of module dependencies instantiated at ./interaction_map.yaml.
| Source: ADR-L0-000008/R2; Related: dependency-graph, bundle

**lifecycle-fsm** (жизненный цикл документа) — Document states per ADR-L0-000001/R2: proposed -> accepted -> rejected -> deprecated/superseded.
| Source: ADR-L0-000001/R2; Related: adr, seal

**linter** (линтер) — The verification instrument guarding the corpus; interim instance linter_v2.py until rebirth.
| Source: ADR-L0-000001/R8.1 + DEBT A23; Related: verification-instrument, corpus

**living-record** (живая запись) — Mutable document class (SDD, DEBT) updated synchronously with its subject in the same commit.
| Source: ADR-L0-000001/R1; Related: sdd, debt-ledger

**log4brains** (Log4brains) — ADR manager tool. External; not our conveyor.
| Source: external (111.md Pass E); Related: adr

**madr** (MADR) — Markdown Architectural Decision Records template (adr/madr). External; our ADR anatomy differs; do not use for our documents.
| Source: external (111.md Pass E2); Related: adr

**meta-block** (META_BLOCK) — A numbered, pre-annotated fabrication block inside an SDD (01_SUBSYSTEM_IDENTIFIER and others).
| Source: 4lk.md (template anatomy); Related: sdd, micro-step

**meta-comment** (мета-комментарий) — Invisible-in-render comment carrier (`<!-- -->`); the canonical form of license notices after frontmatter.
| Source: ADR-L0-000001/REQ-L0-000001-014; Related: frontmatter

**meta-preamble** (META_PREAMBLE) — The header block of an SDD naming the file, its mission, responsibility, and contract.
| Source: 4lk.md (template anatomy); Related: sdd, meta-block

**micro-step** (микрошаг) — One indivisible conveyor step executed in a clean session with halt-and-report; no chaining.
| Source: scqg.md + 4lk.md; Related: clean-session, halt

**minimal-completeness** (минимальная полнота) — Every element is necessary: removing any one distorts the result; the ablation criterion of the template.
| Source: meta/CONCEPT.md + DEBT A22; Related: dod, derivation

**mutation-score** (mutation testing score) — Ratio of killed mutants; external quality metric. External here; Circuit Beta uses mutation testing as a gate, not a score.
| Source: external (111.md Pass E); Related: circuit-beta

**mutation-self-test** (мутационный самотест) — The compiler runs its mutation self-test before processing any input.
| Source: ADR-L0-000013/R2 (self-test-first REQ); Related: compiler, circuit-beta

**norm-manifest** (норм-манифест) — ./specs/templates/norm-manifest.yaml: the registration table mapping files to their governing ADRs.
| Source: ADR-L0-000010/R2; Related: registration-gate, disclosure-matrix

**norm-ref** (norm_ref) — The machine-readable field of a checks-matrix row pointing to the ratified L0 R-point the check derives from.
| Source: ADR-L0-000013/checks_matrix + Dzhemi debate Q2; Related: tripartite-closure, derivation

**orphan-policy** (политика сирот) — Every cataloged error code is referenced by at least one requirement or one check; undeclared-and-unbound codes are violations.
| Source: ADR-L0-000013 (formula Б); Related: formula-b

**pass** (пасс) — One synchronized mutation cycle: workspace edit, sync to projection, post-sync verification.
| Source: session convention 2026-10-04 + README/SYNCHRONIZATION; Related: sync

**preflight** (префлайт) — The compile-time gate checking the dynamic context ceiling and slot form before rendering.
| Source: ADR-L0-000012/R20 + ADR-L0-000013; Related: context-ceiling, slot-file

**projection** (проекция) — The GitHub mirror of the workspace at the moment of sync; trusted only through post-sync diff verification.
| Source: README/SYNCHRONIZATION; Related: sync

**ratification** (ратификация) — The FSM transition proposed -> accepted performed by seal; the document becomes immutable.
| Source: ADR-L0-000001/R2 + ADR-L0-000013/R1; Related: seal, lifecycle-fsm

**referential-integrity** (ссылочная целостность) — Every error code referenced from requirements or the checks matrix exists in the error catalog.
| Source: ADR-L0-000013 (formula Б); Related: formula-b

**regen-tool** (реген-инструмент) — The instrument that regenerates derived lockfiles; the only legitimate writer of rtm.lock.json and req-hashes.lock.json.
| Source: ADR-L0-000011/R2 + session usage; Related: derived-lockfile

**registration-gate** (регистрационный гейт) — A file absent from the manifest is ungoverned; registration precedes protection.
| Source: ADR-L0-000010/R2,R4; Related: norm-manifest, linter

**related** (related) — Frontmatter bibliography of cited corpus ADRs; bounded by the dynamic byte ceiling, not by document count.
| Source: ADR-L0-000012/R20; Related: frontmatter, context-ceiling

**req-identifier** (REQ-идентификатор) — Document-scoped requirement identifier `REQ-L<Layer>-<DocIndex>-<ItemIndex>` inside declared ranges.
| Source: ADR-L0-000002/R3; Related: allocated-ranges, err-identifier

**reqif** (ReqIF) — OMG Requirements Interchange Format; an external exchange standard. Candidate for future interop; not used in this corpus.
| Source: external (111.md Pass E2); Related: rtm

**reserved-term** (зарезервированный термин) — A registered term or external concept not yet in use; usage is forbidden until activation.
| Source: ADR-L0-000012/R14 (reserved logic, analogy) + this document; Related: glossary, factura

**rtm** (RTM) — The Requirements Traceability Matrix binding every requirement identifier to executable test targets with verdicts.
| Source: ADR-L0-000009/R2; Related: test-binding, derived-lockfile

**sbom** (SBOM) — Software Bill of Materials, supply-chain record. External; license/inventory practice only.
| Source: external (111.md Pass E); Related: derived-lockfile

**scope-lock** (скоуп-лок) — The explicit list of files a task may touch; every file outside is forbidden.
| Source: README/TASK FLOW (template T1); Related: micro-step

**sdd** (СДД) — Software Design Description: the living per-file record carrying META_PREAMBLE and META_BLOCKs; the mutable counterpart of an ADR.
| Source: ADR-L0-000001/R8,R10; Related: adr, living-record

**seal** (печать) — The ratification act moving a draft into the corpus; performed only after the operator TTY verdict.
| Source: ADR-L0-000013/R1; Related: tty-verdict, corpus

**self-hosting** (самоподдержка) — The compiler re-emits every ratified corpus document that possesses a registered slot source; the corpus describes the instrument that produces it.
| Source: ADR-L0-000013/R7 (re-emission REQ); Related: compiler, corpus-rebirth

**single-screen-payload** (одноэкранная полезная нагрузка) — Diagnostics limited to 10 lines with keys anchor, problem, action, location, norm.
| Source: ADR-L0-000012/R8; Related: preflight

**skeleton-check** (скелетная проверка) — Verification that every entry of the R8 bundle skeleton exists; derived from REQ-L0-000001-013.
| Source: ADR-L0-000001/REQ-L0-000001-013 + DEBT A22; Related: dod, linter

**slot-file** (слот-файл) — TOML source of one document; the only legitimate input of the conveyor.
| Source: ADR-L0-000013/Context + scqg.md; Related: conveyor, intake

**spec-kit** (Spec Kit) — GitHub's spec-driven development toolkit. External; our conveyor and norms are not Spec Kit.
| Source: external (111.md Pass E); Related: conveyor

**spec-md** (spec.md) — The normative core of a bundle: requirements, FSM, error catalog, matrices; budget 150 lines.
| Source: ADR-L0-000001/R4; Related: bundle, dod

**staging** (стейджинг) — ./new-adr/staging/: zone holding compiled drafts awaiting the seal verdict; ends clean after each pass.
| Source: ADR-L0-000013/R3; Related: draft, seal

**state-registry** (реестр состояний) — The closed table of states with id, owning module, and description.
| Source: ADR-L0-000005/R2; Related: fsm

**strictdoc** (StrictDoc) — Doc-as-code requirements tool with SDoc grammar. External; our slot TOML differs.
| Source: external (111.md Pass E2); Related: slot-file

**structurizr** (Structurizr) — C4 model tooling. External; not our interaction map.
| Source: external (111.md Pass E); Related: interaction-map

**sync** (синк) — Propagation of the AI Studio workspace state to the GitHub projection; the projection is a read-only snapshot for the external contour.
| Source: README/SYNCHRONIZATION (INVARIANT); Related: projection, pass

**synonymy-drift** (дрейф синонимии) — Uncontrolled naming variants of one concept; guarded by the glossary and forbidden-synonym fields.
| Source: ADR-L0-000004/R3 (A6) + ADR-L0-000003/R1; Related: dual-key, forbidden-synonym

**test-binding** (тестовая привязка) — The named executable test target attached to a requirement via the verification trailer.
| Source: ADR-L0-000009/R2; Related: verification-trailer, rtm

**test-contour** (тестовый контур) — The bundle-external test universe of an instrument, anchored bundle-relative.
| Source: ADR-L0-000006/R7; Related: circuit-alpha, fixture

**tighten-only** (принцип ужесточения) — Metric thresholds may only tighten; any relaxation requires justification.
| Source: ADR-L0-000011/R4; Related: linter, context-ceiling

**tla-plus** (TLA+) — Formal specification language with model checking. External; candidate for FSM-era analysis.
| Source: external (111.md Pass E); Related: fsm, transition-matrix

**transactionality** (транзакционность) — A failed compile removes every artifact of the failed run and exits non-zero; partial output is prohibited.
| Source: ADR-L0-000013/R2; Related: seal, draft

**transition-matrix** (матрица переходов) — The closed table of transitions with source state, event, guard, action, and target state.
| Source: ADR-L0-000005/R3; Related: fsm

**tripartite-closure** (трипартитное замыкание) — The consistency mechanism across requirement bindings, checks matrix, and error catalog.
| Source: ADR-L0-000013/REQ (closure REQ); Related: formula-b, error-catalog

**tty-verdict** (вердикт TTY) — The explicit interactive verdict of the operator required for any seal.
| Source: ADR-L0-000013/R1; Related: seal

**verbatim-anchor** (дословный анкор) — A task fragment copied byte-exact from the live raw file; composing anchors from memory is a defect.
| Source: README/T1 + session correction 2026-10-04; Related: scope-lock, draft

**verification-instrument** (инструмент верификации) — Instrument class that only measures and pronounces verdicts; the linter is the instance.
| Source: ADR-L0-000013/Context + DEBT A26; Related: linter, authoring-instrument

**verification-trailer** (трейлер проверки) — The mandatory suffix | Verification: test_target_name() of every requirement.
| Source: ADR-L0-000004/R1 + ADR-L0-000003/R6; Related: test-binding, ears

**weak-modality** (слабая модальность) — Prohibited modal verbs (should, may, might, could); the modal verb shall is used exclusively.
| Source: ADR-L0-000003/R2; Related: anti-pattern

**zero-embedded-data** (ноль данных в коде) — The compiler holds no normative data; every template, schema, threshold, and vocabulary is read from ratified documents or registered data files at execution time.
| Source: ADR-L0-000013/R7; Related: compiler, deterministic-lowering

## Forbidden Synonyms
| Forbidden alias                    | Canonical term                                        |
| :--------------------------------- | :---------------------------------------------------- |
| ticket                             | [a-item](#a-item)                                     |
| issue                              | [a-item](#a-item)                                     |
| decision record                    | [adr](#adr)                                           |
| MADR-style ADR                     | [adr](#adr)                                           |
| generator (ambiguous)              | [authoring-instrument](#authoring-instrument)         |
| impact (informal)                  | [blast-radius](#blast-radius)                         |
| monorepo                           | [bundle](#bundle)                                     |
| package                            | [bundle](#bundle)                                     |
| repository root                    | [bundle-root](#bundle-root)                           |
| current working directory          | [bundle-root](#bundle-root)                           |
| self review                        | [circuit-alpha](#circuit-alpha)                       |
| golden test                        | [circuit-beta](#circuit-beta)                         |
| random clause order                | [clause-order](#clause-order)                         |
| ongoing chat                       | [clean-session](#clean-session)                       |
| one-off test run                   | [closed-loop-verification](#closed-loop-verification) |
| code generator                     | [compiler](#compiler)                                 |
| templater                          | [compiler](#compiler)                                 |
| and-statement requirement          | [compound-statement](#compound-statement)             |
| fixed token limit                  | [context-ceiling](#context-ceiling)                   |
| workflow                           | [conveyor](#conveyor)                                 |
| process                            | [conveyor](#conveyor)                                 |
| docs folder                        | [corpus](#corpus)                                     |
| wiki                               | [corpus](#corpus)                                     |
| bulk rewrite                       | [corpus-rebirth](#corpus-rebirth)                     |
| quick path                         | [critical-scope](#critical-scope)                     |
| changelog                          | [debt-ledger](#debt-ledger)                           |
| todo list                          | [debt-ledger](#debt-ledger)                           |
| ad-hoc check                       | [derivation](#derivation)                             |
| hand-maintained registry           | [derived-lockfile](#derived-lockfile)                 |
| LLM-polished output                | [deterministic-lowering](#deterministic-lowering)     |
| reading list                       | [disclosure-matrix](#disclosure-matrix)               |
| acceptance criteria (free-form)    | [dod](#dod)                                           |
| work in progress page              | [draft](#draft)                                       |
| translation table                  | [dual-key](#dual-key)                                 |
| user story                         | [ears](#ears)                                         |
| shall-statement (free-form)        | [ears](#ears)                                         |
| exception text                     | [err-identifier](#err-identifier)                     |
| hotfix                             | [errata](#errata)                                     |
| error registry                     | [error-catalog](#error-catalog)                       |
| notes                              | [factura](#factura)                                   |
| tweak the spec                     | [fitting](#fitting)                                   |
| make the linter happy              | [fitting](#fitting)                                   |
| example data                       | [fixture](#fixture)                                   |
| alias (free-form)                  | [forbidden-synonym](#forbidden-synonym)               |
| semantic review                    | [form-only-evaluation](#form-only-evaluation)         |
| 1:1:1 bijection (obsolete)         | [formula-b](#formula-b)                               |
| header                             | [frontmatter](#frontmatter)                           |
| preamble                           | [frontmatter](#frontmatter)                           |
| state diagram (informal)           | [fsm](#fsm)                                           |
| dictionary                         | [glossary](#glossary)                                 |
| terminology page                   | [glossary](#glossary)                                 |
| continue                           | [halt](#halt)                                         |
| proceed to next                    | [halt](#halt)                                         |
| inbox                              | [intake](#intake)                                     |
| architecture diagram (informal)    | [interaction-map](#interaction-map)                   |
| draft review cycle                 | [lifecycle-fsm](#lifecycle-fsm)                       |
| formatter                          | [linter](#linter)                                     |
| style checker                      | [linter](#linter)                                     |
| section                            | [meta-block](#meta-block)                             |
| visible header line                | [meta-comment](#meta-comment)                         |
| hashtag comment at file top        | [meta-comment](#meta-comment)                         |
| docstring header                   | [meta-preamble](#meta-preamble)                       |
| batch                              | [micro-step](#micro-step)                             |
| all-in-one run                     | [micro-step](#micro-step)                             |
| nice to have                       | [minimal-completeness](#minimal-completeness)         |
| smoke test                         | [mutation-self-test](#mutation-self-test)             |
| config file                        | [norm-manifest](#norm-manifest)                       |
| comment reference                  | [norm-ref](#norm-ref)                                 |
| reserved error code (unregistered) | [orphan-policy](#orphan-policy)                       |
| sprint                             | [pass](#pass)                                         |
| iteration                          | [pass](#pass)                                         |
| backup                             | [projection](#projection)                             |
| remote                             | [projection](#projection)                             |
| sign-off                           | [ratification](#ratification)                         |
| dangling code                      | [referential-integrity](#referential-integrity)       |
| manual edit of lockfiles           | [regen-tool](#regen-tool)                             |
| implicit coverage                  | [registration-gate](#registration-gate)               |
| links section                      | [related](#related)                                   |
| ticket id                          | [req-identifier](#req-identifier)                     |
| future work mention                | [reserved-term](#reserved-term)                       |
| coverage report                    | [rtm](#rtm)                                           |
| best effort                        | [scope-lock](#scope-lock)                             |
| touch what you need                | [scope-lock](#scope-lock)                             |
| design doc                         | [sdd](#sdd)                                           |
| readme                             | [sdd](#sdd)                                           |
| commit                             | [seal](#seal)                                         |
| merge                              | [seal](#seal)                                         |
| release                            | [seal](#seal)                                         |
| bootstrap (generic)                | [self-hosting](#self-hosting)                         |
| stack trace dump                   | [single-screen-payload](#single-screen-payload)       |
| template file                      | [slot-file](#slot-file)                               |
| blueprint                          | [slot-file](#slot-file)                               |
| specification document             | [spec-md](#spec-md)                                   |
| cache                              | [staging](#staging)                                   |
| temp                               | [staging](#staging)                                   |
| deploy                             | [sync](#sync)                                         |
| publish                            | [sync](#sync)                                         |
| rich vocabulary                    | [synonymy-drift](#synonymy-drift)                     |
| test mention                       | [test-binding](#test-binding)                         |
| test folder (inside bundle)        | [test-contour](#test-contour)                         |
| adjust threshold                   | [tighten-only](#tighten-only)                         |
| best-effort output                 | [transactionality](#transactionality)                 |
| flowchart                          | [transition-matrix](#transition-matrix)               |
| three-way equality (obsolete)      | [tripartite-closure](#tripartite-closure)             |
| approval checkbox                  | [tty-verdict](#tty-verdict)                           |
| LGTM                               | [tty-verdict](#tty-verdict)                           |
| approximate quote                  | [verbatim-anchor](#verbatim-anchor)                   |
| tester (ambiguous)                 | [verification-instrument](#verification-instrument)   |
| should                             | [weak-modality](#weak-modality)                       |
| may                                | [weak-modality](#weak-modality)                       |
| might                              | [weak-modality](#weak-modality)                       |
| hardcoded constants                | [zero-embedded-data](#zero-embedded-data)             |

## Reserved Fund
| Term           | Note                                                | Source                    |
| :------------- | :-------------------------------------------------- | :------------------------ |
| gherkin        | external, non-normative                             | external (111.md Pass E)  |
| log4brains     | external, non-normative                             | external (111.md Pass E)  |
| madr           | external, non-normative; forbidden as alias for ADR | external (111.md Pass E2) |
| mutation-score | external, non-normative                             | external (111.md Pass E)  |
| reqif          | external, non-normative                             | external (111.md Pass E2) |
| sbom           | external, non-normative                             | external (111.md Pass E)  |
| spec-kit       | external, non-normative                             | external (111.md Pass E)  |
| strictdoc      | external, non-normative                             | external (111.md Pass E2) |
| structurizr    | external, non-normative                             | external (111.md Pass E)  |
| tla-plus       | external, non-normative                             | external (111.md Pass E)  |
