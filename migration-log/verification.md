## Verification (generated — do not retype)

Produced by `verify-migration.py` from the target tree AND `migration-log/run.log`, the two oracles. **47 IDENTISCH · 13 DIVERGIERT · 20 NICHT PRÜFBAR.**

Verdicts: **IDENTISCH** = matches the source · **DIVERGIERT** = differs, named below · **NICHT PRÜFBAR** = could not be checked, which is **not** a pass and owes a named human an action.

| Layer | Check | What it asks | IDENTISCH | DIVERGIERT | NICHT PRÜFBAR |
|---|---|---|---|---|---|
| conservation | C1 | every source artefact still exists in the migrated module | 1 | 0 | 0 |
| conservation | C2 | every artefact is reachable from the rendered Artifacts page | 2 | 0 | 0 |
| conservation | C3 | every source guide page was migrated or explicitly retired | 0 | 0 | 1 |
| conservation | C4 | the source's narrative text is present somewhere in the target | 0 | 1 | 0 |
| conservation | C5 | menus lead somewhere, and every page is in a menu | 3 | 0 | 1 |
| conservation | C7 | content the migration wrote is marked as such in the guide | 1 | 0 | 2 |
| fidelity | F1 | module identity is unchanged (id, canonical, version, licence, ...) | 9 | 0 | 0 |
| fidelity | F2 | dependency versions are pinned exactly as the source pinned them | 0 | 3 | 7 |
| fidelity | F3 | the licence is asserted from evidence, never defaulted | 1 | 0 | 0 |
| fidelity | F4 | no mechanical FSH conversion residue is left | 1 | 0 | 0 |
| provenance | P1 | the rendered site reports the template package it was built with | 1 | 0 | 0 |
| provenance | P2 | the vendored template ref matches what the run log recorded | 1 | 0 | 0 |
| provenance | P3 | the IG Publisher version matches the workflow pin | 1 | 0 | 0 |
| provenance | P4 | the source guide was pinned to a published version, not 'current' | 0 | 0 | 1 |
| rendering | R1 | tables, tabs and images render with content, not empty | 2 | 0 | 1 |
| rendering | R2 | page header and footer metadata render correctly | 0 | 2 | 0 |
| rendering | R3 | a translated page really differs from the default language | 1 | 0 | 0 |
| rendering | R4 | no links point at template example artefacts that were deleted | 1 | 0 | 0 |
| rendering | R5 | every page has a title unit in the translation catalogue | 1 | 0 | 0 |
| log | L0 | a run log exists at all | 1 | 0 | 0 |
| log | L1 | every partial-success warning was acted on | 1 | 0 | 0 |
| log | L2 | every expected step actually wrote a log line | 17 | 0 | 5 |
| log | L3 | no identity contradiction is still open | 1 | 7 | 0 |
| log | L4 | the log's counts agree with what the tree holds | 1 | 0 | 2 |

### DIVERGIERT — each one a stop or a recorded decision

| id | Check | What it asks | Subject | Evidence | Next action | Auto-fixable |
|---|---|---|---|---|---|---|
| `C4-ef59ff` | C4 | the source's narrative text is present somewhere in the target | index.md | 1 of 1 PROSE runs of the source page are in no target page (first: # MII IG Modul Onkologie Feel free to modify this index page…) | map the missing text to a target page section, or record the loss in the report's content map | no |
| `F2-d14403` | F2 | dependency versions are pinned exactly as the source pinned them | de.basisprofil.r4 | target 1.5.4  vs  source pin 1.5.x (the source tree (--source)) | the source pin is the evidence; a registry dist-tag is not. Restore the pin or make the bump a Gate-A decision | no |
| `F2-0519f5` | F2 | dependency versions are pinned exactly as the source pinned them | de.medizininformatikinitiative.kerndatensatz.base | target 2026.0.1  vs  source pin 2026.0.x (the source tree (--source)) | the source pin is the evidence; a registry dist-tag is not. Restore the pin or make the bump a Gate-A decision | no |
| `F2-ce5cda` | F2 | dependency versions are pinned exactly as the source pinned them | de.medizininformatikinitiative.kerndatensatz.meta | target 2026.0.0  vs  source pin 2026.0.x (the source tree (--source)) | the source pin is the evidence; a registry dist-tag is not. Restore the pin or make the bump a Gate-A decision | no |
| `R2-d9eac4` | R2 | page header and footer metadata render correctly | /private/tmp/claude-503/-Users-marcel-Development-cross-hub-patientportal/e2e22580-543a-4bf5-88cc-83677866f38a/scratchpad/onko-pages/branches/migration/2026.0.3-template-v0.11.1/de id="ig-status" [{{] | on 1 page(s), e.g. searchform.html: Search {{title}} (Current Build) | rendered header/footer metadata defect -- qa.txt does not report it. Fix the metadata it renders (a jurisdiction code the template cannot resolve is the measured case) | no |
| `R2-53bae0` | R2 | page header and footer metadata render correctly | /private/tmp/claude-503/-Users-marcel-Development-cross-hub-patientportal/e2e22580-543a-4bf5-88cc-83677866f38a/scratchpad/onko-pages/branches/migration/2026.0.3-template-v0.11.1/en id="ig-status" [{{] | on 1 page(s), e.g. searchform.html: Search {{title}} (Current Build) | rendered header/footer metadata defect -- qa.txt does not report it. Fix the metadata it renders (a jurisdiction code the template cannot resolve is the measured case) | no |
| `L3-117415` | L3 | no identity contradiction is still open | identity field dependency:de.basisprofil.r4 | 1 unresolved contradiction WARN(s), first at 2026-08-22T19:43:18Z: identity-contradiction: field=dependency:de.basisprofil.r4 now=1.5.4 (tier R, sushi-config.yaml + registry res… | unresolved at verification time. It is a Gate-A decision, never a precedence puzzle to settle mechanically -- record it with a `decision:` line naming the field | no |
| `L3-e74aae` | L3 | no identity contradiction is still open | identity field dependency:de.medizininformatikinitiative.kerndatensatz.base | 1 unresolved contradiction WARN(s), first at 2026-08-22T19:43:18Z: identity-contradiction: field=dependency:de.medizininformatikinitiative.kerndatensatz.base now=2026.0.1 (tier … | unresolved at verification time. It is a Gate-A decision, never a precedence puzzle to settle mechanically -- record it with a `decision:` line naming the field | no |
| `L3-b02d70` | L3 | no identity contradiction is still open | identity field dependency:de.medizininformatikinitiative.kerndatensatz.biobank | 1 unresolved contradiction WARN(s), first at 2026-08-22T19:43:18Z: identity-contradiction: field=dependency:de.medizininformatikinitiative.kerndatensatz.biobank now=2026.0.1 (ti… | unresolved at verification time. It is a Gate-A decision, never a precedence puzzle to settle mechanically -- record it with a `decision:` line naming the field | no |
| `L3-525d25` | L3 | no identity contradiction is still open | identity field dependency:de.medizininformatikinitiative.kerndatensatz.medikation | 1 unresolved contradiction WARN(s), first at 2026-08-22T19:43:18Z: identity-contradiction: field=dependency:de.medizininformatikinitiative.kerndatensatz.medikation now=2026.0.1 … | unresolved at verification time. It is a Gate-A decision, never a precedence puzzle to settle mechanically -- record it with a `decision:` line naming the field | no |
| `L3-dce37c` | L3 | no identity contradiction is still open | identity field dependency:de.medizininformatikinitiative.kerndatensatz.meta | 1 unresolved contradiction WARN(s), first at 2026-08-22T19:43:18Z: identity-contradiction: field=dependency:de.medizininformatikinitiative.kerndatensatz.meta now=2026.0.0 (tier … | unresolved at verification time. It is a Gate-A decision, never a precedence puzzle to settle mechanically -- record it with a `decision:` line naming the field | no |
| `L3-b2c4cd` | L3 | no identity contradiction is still open | identity field dependency:de.medizininformatikinitiative.kerndatensatz.molgen | 1 unresolved contradiction WARN(s), first at 2026-08-22T19:43:18Z: identity-contradiction: field=dependency:de.medizininformatikinitiative.kerndatensatz.molgen now=2026.0.4 (tie… | unresolved at verification time. It is a Gate-A decision, never a precedence puzzle to settle mechanically -- record it with a `decision:` line naming the field | no |
| `L3-fac1a0` | L3 | no identity contradiction is still open | identity field title | 2 unresolved contradiction WARN(s), first at 2026-08-22T19:41:44Z: identity-contradiction: field=title now=MII Kerndatensatz Modul Onkologie (tier R, README.md first heading) vs… | unresolved at verification time. It is a Gate-A decision, never a precedence puzzle to settle mechanically -- record it with a `decision:` line naming the field | no |

### NICHT PRÜFBAR — not a pass; each needs a human

| id | Check | What it asks | Subject | Why not mechanisable | Who does what |
|---|---|---|---|---|---|
| `C3-5cae38` | C3 | every source guide page was migrated or explicitly retired | 1 source pages | no page map at ./migration-log/page-map.tsv | write step 5's ledger: source_page<TAB>target_page|RETIRED<TAB>reason |
| `C5-2d86b5` | C5 | menus lead somewhere, and every page is in a menu | target pages without a source counterpart | no page map at ./migration-log/page-map.tsv; 1 target page(s) are not the template's (ImplementationGuide-mii-ig-onko-de-v2026) | write step 5's ledger, then re-run: only it says which target page each source page became |
| `C7-b2b947` | C7 | content the migration wrote is marked as such in the guide | marker source= values | 106 marker(s) to resolve, but no page map at migration-log/page-map.tsv to resolve them against | write step 5's ledger (source_page<TAB>target_page|RETIRED<TAB>reason); until it exists, a marker's source= names a page nothing can confirm |
| `C7-c16051` | C7 | content the migration wrote is marked as such in the guide | unmarked derived content | 1 source page(s) lost prose (C4), but no page map at migration-log/page-map.tsv says which target page replaced them | write step 5's ledger, then re-run: without it the page that would have to carry the marker is unknown |
| `F2-6bfac0` | F2 | dependency versions are pinned exactly as the source pinned them | de.medizininformatikinitiative.kerndatensatz.biobank | target-only dependency 2026.0.0 (not in the source) | confirm at Gate A that this is template machinery (hl7.fhir.uv.crmi is) and not an accidental addition |
| `F2-fb1c14` | F2 | dependency versions are pinned exactly as the source pinned them | de.medizininformatikinitiative.kerndatensatz.medikation | target-only dependency 2026.0.1 (not in the source) | confirm at Gate A that this is template machinery (hl7.fhir.uv.crmi is) and not an accidental addition |
| `F2-60512e` | F2 | dependency versions are pinned exactly as the source pinned them | de.medizininformatikinitiative.kerndatensatz.molgen | target-only dependency 2026.0.4 (not in the source) | confirm at Gate A that this is template machinery (hl7.fhir.uv.crmi is) and not an accidental addition |
| `F2-ec259d` | F2 | dependency versions are pinned exactly as the source pinned them | de.medizininformatikinitiative.kerndatensatz.studie | target-only dependency 2026.0.2 (not in the source) | confirm at Gate A that this is template machinery (hl7.fhir.uv.crmi is) and not an accidental addition |
| `F2-fd0e73` | F2 | dependency versions are pinned exactly as the source pinned them | hl7.fhir.uv.crmi | target-only dependency 2.0.0 (not in the source) | confirm at Gate A that this is template machinery (hl7.fhir.uv.crmi is) and not an accidental addition |
| `F2-047205` | F2 | dependency versions are pinned exactly as the source pinned them | hl7.fhir.uv.extensions.r4 | target-only dependency 5.3.0 (not in the source) | confirm at Gate A that this is template machinery (hl7.fhir.uv.crmi is) and not an accidental addition |
| `F2-8f9355` | F2 | dependency versions are pinned exactly as the source pinned them | hl7.terminology.r4 | target-only dependency 7.3.0 (not in the source) | confirm at Gate A that this is template machinery (hl7.fhir.uv.crmi is) and not an accidental addition |
| `P4-379bde` | P4 | the source guide was pinned to a published version, not 'current' | source guide version | no `?version=` recorded in the run log or the harvest manifest | record the pinned, PUBLISHED guide version like the source commit SHA (spec 5.1c.3) |
| `R1-76f413` | R1 | tables, tabs and images render with content, not empty | source-versus-target rendering | no harvested source HTML (./migration-log/guide-harvest/html) and/or no page map | harvest with --keep-html and write the page map; without a source rendering, 'non-empty where non-empty in the source' has no reference |
| `L2-07bdbb` | L2 | every expected step actually wrote a log line | 5.1c simplifier-discover | no line in the log; the step is conditional (no rendered-IG URL was supplied) | confirm the condition did not hold -- Without the discovery chain the guide is not found, and a migration then ships the template's starter pages. |
| `L2-930ba2` | L2 | every expected step actually wrote a log line | 5.1d guide-harvest | no line in the log; the step is conditional (the narrative is not in the repository) | confirm the condition did not hold -- This is the step whose absence shipped the template's starter pages under a module's name. |
| `L2-ec69ec` | L2 | every expected step actually wrote a log line | 5.4a optional-page-decisions | no line in the log; the step is conditional (target template >= v0.8) | confirm the condition did not hold -- The seven OPTIONAL (0..1) pages must each be decided — keep (banner + marker deleted, both languages) or remove per the template's procedure (spec §9a); the template's M9 fails a module release while undecided, and a migration with no line here silently shipped seven "decide me" banners. |
| `L2-b6ec8c` | L2 | every expected step actually wrote a log line | 5.4b security-privacy-decision | no line in the log; the step is conditional (target template >= v0.8) | confirm the condition did not hold -- Stage 3 of security-and-privacy: module aspects written or the default text adopted, and the scaffold's Person example + ILLUSTRATIVE-EXAMPLE marker deleted in both languages (spec §9a); the template's M11 fails a release branch while it is present. |
| `L2-a85d96` | L2 | every expected step actually wrote a log line | 5.5 gen-page-title-po | no line in the log; the step is conditional (bilingual target) | confirm the condition did not hold -- Page titles fall back to the default language with no error anywhere. |
| `L4-106e61` | L4 | the log's counts agree with what the tree holds | conversion count | no `gofsh-convert … actual=` line in the log | shape B only; for shape A there is nothing to convert |
| `L4-f17740` | L4 | the log's counts agree with what the tree holds | page count | no harvested count in the log and/or no harvest manifest | harvest the guide (step 2c) where the narrative is not in the repo |

**Inputs:** target `.` · source `/private/tmp/claude-503/-Users-marcel-Development-cross-hub-patientportal/e2e22580-543a-4bf5-88cc-83677866f38a/scratchpad/candidates/onko-src` · rendered `/private/tmp/claude-503/-Users-marcel-Development-cross-hub-patientportal/e2e22580-543a-4bf5-88cc-83677866f38a/scratchpad/onko-pages/branches/migration/2026.0.3-template-v0.11.1` · log `./migration-log/run.log`
