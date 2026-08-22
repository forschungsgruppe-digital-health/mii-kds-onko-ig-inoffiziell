# Page-structure advice

**This report PROPOSES and never edits.** It reads the source and target repositories read-only and writes nothing into either of them. Every routing row below is the branch the MEASUREMENTS support - a human (or the skill at step 5) decides and applies it.

| Input | Value |
| --- | --- |
| source repo | `/private/tmp/claude-503/-Users-marcel-Development-cross-hub-patientportal/e2e22580-543a-4bf5-88cc-83677866f38a/scratchpad/candidates/onko-src` |
| target repo | `/private/tmp/claude-503/-Users-marcel-Development-cross-hub-patientportal/e2e22580-543a-4bf5-88cc-83677866f38a/scratchpad/onko-new` |
| generated | 2026-08-22T19:39:55Z |
| script | `page-structure-advice.py` v1.0.0 |

Contract limits in force: menu total <= 33, dropdown children <= 10, top level <= 8, menu depth <= 2; size gate at > 2500 words, > 4 merged sources, or ANY repeated heading title; hub at >= 3 children.

## 1. Source page tree

`sushi-config.yaml` has **no `pages:` block**, so the source page tree is **flat/unknown** - it is not reconstructed here. Counted instead: **1** files in `input/pagecontent/`.

Every routing row below therefore carries no depth evidence; treat the parent/child measurements as absent, not as zero.

## 2. Target page measurements

Words = whitespace tokens after removing HTML comments, table separator rows and the markup characters `>`, `|`, `*`, `_`, `` ` ``. Headings, list items, table cells and fenced code all count: the gate measures what the reader has to traverse. Repeated titles are compared case-sensitively; each repeat costs one publisher-appended anchor (`-2`, `-3`, ...). Merged sources are the distinct `<!-- source: X.md -->` section markers the migration itself left behind.

| Page | Words | h2 | h3 | h4 | other h | Repeated titles | Anchor collisions | Merged sources | Size gate |
| --- | ---: | ---: | ---: | ---: | ---: | ---: | ---: | ---: | --- |
| `ImplementationGuide-mii-ig-{{MODULE_SLUG}}.md` | 286 | 0 | 5 | 0 | 0 | 0 | 0 | 0 | ok |
| `capability-statements.md` | 31 | 0 | 1 | 0 | 0 | 0 | 0 | 0 | ok |
| `changes.md` | 560 | 0 | 1 | 1 | 1 | 0 | 0 | 0 | ok |
| `code-systems.md` | 148 | 0 | 1 | 0 | 0 | 0 | 0 | 0 | ok |
| `downloads.md` | 325 | 0 | 0 | 7 | 0 | 0 | 0 | 0 | ok |
| `examples.md` | 43 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | ok |
| `extensions.md` | 121 | 0 | 1 | 0 | 0 | 0 | 0 | 0 | ok |
| `guidance.md` | 130 | 0 | 2 | 0 | 0 | 0 | 0 | 0 | ok |
| `implementer-guidance.md` | 32 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | ok |
| `index.md` | 477 | 0 | 9 | 0 | 0 | 0 | 0 | 0 | ok |
| `logical-models.md` | 33 | 0 | 1 | 0 | 0 | 0 | 0 | 0 | ok |
| `metadata.md` | 2198 | 0 | 1 | 7 | 1 | 0 | 0 | 0 | ok |
| `operations.md` | 104 | 0 | 1 | 0 | 0 | 0 | 0 | 0 | ok |
| `profiles.md` | 77 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | ok |
| `rendering-artifacts.md` | 3933 | 0 | 8 | 3 | 0 | 0 | 0 | 0 | **TRIPS** - 3933 words > 2500 |
| `researcher-guidance.md` | 111 | 0 | 1 | 0 | 0 | 0 | 0 | 0 | ok |
| `search-parameters.md` | 112 | 0 | 1 | 0 | 0 | 0 | 0 | 0 | ok |
| `security-and-privacy.md` | 444 | 0 | 0 | 3 | 0 | 0 | 0 | 0 | ok |
| `translationinfo.md` | 80 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | ok |
| `uml-diagrams.md` | 42 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | ok |
| `value-sets.md` | 178 | 0 | 1 | 0 | 0 | 0 | 0 | 0 | ok |
| `version-history.md` | 548 | 0 | 0 | 6 | 0 | 0 | 0 | 0 | ok |

### 2.1 Pages that trip the size gate

- **`rendering-artifacts.md`** - 3933 words > 2500.
  - rule 5: re-run routing preferring branches 1 and 2, or split.

## 3. Menu budget

Clickable entries are the menu's real destinations: every `<li><a>` except the dropdown toggles, which only repeat their first child's href.

| Metric | Measured | Contract limit | Headroom |
| --- | ---: | ---: | ---: |
| total clickable entries | 26 | 33 | 7 |
| widest dropdown (Artifacts) | 11 | 10 | -1 |
| top-level entries | 7 | 8 | 1 |
| menu depth used | 2 | 2 | 0 |

| Dropdown | Children | Free (of 10) |
| --- | ---: | ---: |
| Guidance | 5 | 5 |
| Conformance | 5 | 5 |
| Artifacts | 11 | -1 |
| Metadata | 2 | 8 |

After the proposals in section 4: total 7 free, top level 1 free, freest dropdown Metadata (8 free).

## 4. Routing proposal (spec 9d/9e)

_No `pages:` block in the source - no per-source-page routing is proposed. Route the 1 files in `input/pagecontent/` by hand, or add the block._

## 5. Report queue 1 items

_None from the menu budget._

Size-gate trips (rule 5) needing a routing re-run or a split:

- `rendering-artifacts.md` - 3933 words > 2500.

