# Migration report — MII KDS Modul Onkologie → MII KDS module template

**Module:** Onkologie · **Report author:** agent run of the `mii-ig-migration` skill v0.20.2 · **Report date:** 2026-08-23
**Written for:** the MII Onkologie module team and TF-KDS (the MII Taskforce Kerndatensatz, which owns cross-module conventions), plus the maintainers of the module template and of this skill
**Decision requested:** approve the findings as decision input, and keep the branch unmerged — this is an unofficial try-run sandbox and must not be merged into any official MII repository
**State:** complete through build and verification
**Published?** No package was released to any registry. The rendered preview is public at
<https://forschungsgruppe-digital-health.github.io/mii-kds-onko-ig-inoffiziell/branches/migration/2026.0.3-template-v0.11.1/> (English `…/en/`, German `…/de/`).
**Recommendation:** treat this as evidence that the largest MII KDS module migrates intact — identity, all 489 artefacts and the whole page tree survive — while five items below need a human: the licence file, the resolved dependency pins, the identity contradictions, an unproven QA baseline, and a preview-size limit that belongs to the template.

## How to use this report

1. Read **Summary** and **Applied fixes** first: that is everything that already changed.
2. Then work ① Decisions, ② Reviews, ③ QA triage in order. Every item names its owner.
3. Gate 0, Identity and Verification are evidence — open them to check an item.
4. Item ids are greppable (`DEC-2`, `REV-1`, `QA-1`, `FIX-3`); quote the id when you answer.
5. Nothing is published and every applied change is revertible, but doing nothing is not neutral: read each **If nobody acts**.

## Summary — read this first

The MII publishes Onkologie as FHIR profiles plus a German Simplifier guide. Both were moved onto the MII KDS module template, which builds the guide with the standard HL7 toolchain on GitHub.

- **Source:** `medizininformatik-initiative/kerndatensatzmodul-onkologie` @ `0be6ba2` (tag `v2026.0.3`), shape A. Narrative from the **guide tree** `ImplementationGuide-2026.x-DE` (149 pages), chosen over `input/pagecontent` by measurement — see Gate 0.
- **Scale:** this is the largest MII KDS module — 489 generated artefacts, 362 FSH files, three guide trees, 38 ConceptMaps, 43 CodeSystems, 98 ValueSets.
- **Build:** SUSHI reports **0 errors** and writes 488 resources; the IG Publisher's separate QA report lists **494 errors / 2348 warnings**. Two tools, two counts — QA errors do not fail the build.
- **Artefact conservation is exact:** the generated resource set is **filename-identical to the source in both directions, 489 to 489**.
- **Verification:** **47 IDENTISCH · 13 DIVERGIERT · 20 NICHT PRÜFBAR** — the check ran and matched · the check ran and found a named difference · the check could not run, which is **not** a pass. All 13 divergences are the recorded decisions below.
- **Open for humans:** 5 decisions, 3 reviews, 2 QA items.
- **Not checked here:** clinical correctness of any prose, oBDS conformance, and the terminology licences (SNOMED CT, ICD-O-3, OPS) — unchanged from the source and out of scope.

## Where the evidence lives

| File | What it is |
|---|---|
| `migration-log/run.log` | 451 lines, 74 warnings: every step, its command, and what that command measurably produced |
| `migration-log/preflight-analysis.json` | the measured scope of the **unmigrated source** (Gate 0) |
| `migration-log/postflight-analysis.json` | the same measurement on the **migrated target**, for comparison |
| `migration-log/verification.md` / `…-findings.tsv` | the verifier's per-check table with a next action per row |
| `migration-log/derived-content.tsv` | 106 markers: every passage the migration **wrote** rather than carried |
| `migration-log/identity-claims.tsv` | 31 identity claims with their tier and contradictions |

## Gate 0 — pre-flight scope, and what it changed

| Aspect | Measured on the source | Consequence |
|---|---|---|
| Artefacts | 461 published + **38 ConceptMaps and 2 ObservationDefinitions** in the open bucket | the ConceptMaps have no page in the agreed set; they were routed to intro notes on their own artefact pages |
| Narrative sources | **dual**: guide tree last changed 2026-03-27, `input/pagecontent` 2025-05-11 | the guide tree is ten months newer, so it is authoritative — decided by freshness, not by rank |
| Dependency health | 6 of 7 pins **floating** (`1.5.x`, `2026.0.x`); no direct THO/extensions pin | pins resolved (DEC-2); direct pins added, so the injection risk is now false |
| Licence | CC0-1.0, **not** contradictory | became contradictory in the target — see DEC-1 |
| Canonical space | 12 predicted special URLs | unchanged in the target |
| QA baseline | **none in the tree** | still not obtained — QA-1 |

## ① Decision queue (Gate A)

**DEC-1 — the licence file contradicts the declared licence** · severity **high**
- **What it is:** `sushi-config.yaml` declares `CC0-1.0`, carried from the source, while the repository ships the template's `LICENSE` whose text is CC-BY-4.0 ("Attribution 4.0 International"). The source ships no LICENSE file at all.
- **Where:** `LICENSE` line 1 · `sushi-config.yaml` `license:`
- **If nobody acts:** the module makes two contradictory licence statements, one of them the legally operative file. The pre/post comparison shows this is the one property the migration made *worse*.
- **Next action:** replace `LICENSE` with the CC0-1.0 text, or change the declaration — a licence decision, not a formatting one.
- **Who decides:** the module maintainers with TF-KDS. **Effort · impact:** minutes · legal. **Reversible:** yes, single file.
- **Evidence:** run.log `7 licence-regression`; the same defect exists in the PROs and Dokument sandboxes.

**DEC-2 — six dependency pins were floating and are now resolved** · severity **high**
- **What it is:** the source, *and its published package manifest*, float six of seven dependencies (`de.basisprofil.r4 1.5.x`, and `2026.0.x` for meta, base, biobank, medikation, molgen), so the released artefact is not reproducible from its own manifest. The template's release check M7 (no floating pins) rejects them.
- **Where:** `sushi-config.yaml` `dependencies:` · both readings in `migration-log/identity-claims.tsv`
- **If nobody acts:** the target keeps the resolved pins and the verifier keeps reporting three of them as differing from the source — correctly, because they do.
- **Options:** keep the resolution (reproducible) · restore the floating pins (M7 fails) · pick different versions.
- **Next action:** confirm each: `de.basisprofil.r4` 1.5.4 (highest 1.5.z, **not** the newer 1.6.0), meta 2026.0.0, base 2026.0.1, biobank 2026.0.0, medikation 2026.0.1, molgen 2026.0.4, studie 2026.0.2.
- **Who decides:** module maintainers. **Effort · impact:** minutes · consumer-visible. **Reversible:** yes.

**DEC-3 — seven identity contradictions are open** · severity **medium**
- **What it is:** the same field reads differently across sources, e.g. `title` is "MII IG Kerndatensatz-Modul Onkologie" in sushi-config, "MII IG Onkologie" in the published package and "MII Kerndatensatz Modul Onkologie" in the README.
- **Where:** `migration-log/identity-claims.tsv`; the verifier reports them as seven L3 rows.
- **If nobody acts:** they stay open; nothing is rewritten, which is deliberate.
- **Next action:** pick one value per field upstream. **Who decides:** module maintainers. **Reversible:** n/a.

**DEC-4 — invented values** · severity **medium** · NCI topic code `C3262` and copyright start year `2021` are stand-ins in `sushi-config.yaml`; confirm or replace.

**DEC-5 — one source page describes a profile the module does not ship** · severity **medium**
- `Tumorkonferenz-Detailed-Recommendations-CarePlan.page.md` documents `mii-pr-onko-tumorkonferenz-detailed-recommendations`, which exists in no FSH and no generated resource, yet `input/fsh/capability-statement.fsh:305` promises it as a SHALL profile. No intro note was invented. Upstream decision.

## ② Review queue (Gates B/C)

Rows below are generated from `migration-log/derived-content.tsv` (`python3 scripts/derived-scan.py --target . --markdown`).

**REV-1 — 106 passages the migration wrote** (56 summaries, 50 bridges), each rendering as a highlighted box on its page in both languages. They are review items, not defects; whether any may remain at publication is a Gate-D decision. Scan is clean: no malformed marker, no marker without a box, no missing language twin.

**REV-2 — two intro notes were re-pointed** because the source's `subject:` names a canonical that matches no artefact (`Mamma-Operation-Procedure`, `KRK-MRT-Mesorektale-Faszie-Observation`). Each carries a bridge marker naming the stale canonical and the artefact chosen. Confirm the targets; the KRK example instance still uses the old spelling upstream.

**REV-3 — eleven source pages were not routed**, ten of them folder landing pages whose entire body is "Diese Seite wurde absichtlich leer gelassen"; the eleventh is DEC-5. Nothing was invented for them.

## ③ QA triage

| # | Finding | Count | Whose problem | Next action |
|---|---|---|---|---|
| QA-1 | 494 QA errors in the rendered guide | 494 | **unclassified — provenance not proven.** Gate 0 found no QA baseline and the unmigrated source was not built, so no claim of "pre-existing" is made here | build the source with the same pinned toolchain and compare by element path, as was done for the PRO module |
| QA-2 | two header/footer rendering findings | 2 | publisher chrome, source-authored metadata | inspect on the preview; no action expected |

## Applied fixes (revertible)

| # | Fix | Commit | If reverted |
|---|---|---|---|
| FIX-1 | migration of artefacts and identity | `ecb8b69` | the module is gone |
| FIX-2 | narrative migration completed | `552f09f` | 111 intro notes and all sections are lost |
| FIX-3 | template demo page and its dead example links removed | `9299505` | check M8 fails and two dead links return |
| FIX-4 | IG resource file names derived from the module **id**, not the slug | `b7de5fc` | the publisher dies with a missing-file error |
| FIX-5 | preview pruned of files above 95 MB | `8e3a5ba` | the preview push is rejected again (`full-ig.zip` is 142 MB) |

## Content map

149 guide-tree pages: **111 became intro notes** on the artefact pages they describe (both languages), the rest became sections on pages the agreed menu already carries (`profiles`, `implementer-guidance`, `code-systems`, `value-sets`, `capability-statements`, `guidance`, `index`, `changes`, `logical-models`). **No page was invented and the menu did not grow** — it stays at 23 of a 33-entry budget, two levels deep. The other two guide trees are retained unchanged: `2025.x-DE` historical, `2025.x-EN` a stale parallel-language seed.

## Identity (verified unchanged)

| Field | Value |
|---|---|
| canonical | `https://www.medizininformatik-initiative.de/fhir/ext/modul-onko` |
| id / name | `mii-ig-onko-de-v2026` / `MII_IG_Onko_DE` |
| packageId / version | `de.medizininformatikinitiative.kerndatensatz.onkologie` / `2026.0.3` |
| licence | `CC0-1.0` (see DEC-1) |
| publisher (IG chrome) | NUM-DIZ, per the template rule; the module's own artefact publisher is untouched |

## Verification

`verify-migration.py` v0.20.2 against target, source and the rendered preview: **47 IDENTISCH / 13 DIVERGIERT / 20 NICHT PRÜFBAR**, exit 1 — not a pass, as designed. The 13: seven L3 (open identity contradictions, DEC-3), three F2 (the pin resolution, DEC-2), two R2 (QA-2) and one C4 (the source's single `input/pagecontent/index.md`, superseded by the newer guide tree). The 20 NICHT PRÜFBAR are checks whose inputs this route does not produce, each named in `verification.md`.

## Protocol

Generated from `migration-log/run.log` (451 lines, 74 warnings, committed with the branch): Gate 0 → source pin and guide-tree selection → identity ledger (31 claims, 7 contradictions, 6 floating pins resolved) → skeleton on template v0.11.1 with a per-definition alias collision fix → FSH transfer (362 files, structure preserved after one repaired flattening) → routing of 149 pages per spec §9e → 106 derived markers → SUSHI 0 errors → CI build and preview → verification (three runs) → five revertible fixes. Toolchain: SUSHI 3.20.1, IG Publisher 2.3.2, Jekyll 4.4.1, skill v0.20.2.

## Mini-glossary

Every code used here — the release checks M1–M11, the verification checks C/F/P/R/L, the gates and the marker kinds — is listed in plain language in the skill's `references/codes.md`; the generated tables also carry that meaning inline.
