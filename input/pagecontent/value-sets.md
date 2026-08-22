<!-- markdownlint-disable MD041 -->
<!-- Split from the former terminology.md per the TF-KDS-agreed menu structure (one
     page per artifact type); SNOMED CT version policy from the meta wiki page
     "Terminology Version Policy". The IG Publisher lists the ValueSets on the
     artifact pages automatically; this page carries the MII notes on them.
     German mirror: input/translations/de/pagecontent/value-sets.md. -->
<!-- OPTIONAL-PAGE (0..1) — remove this marker when you KEEP the page; remove
     the page per docs/optional-pages.md when you don't. The convention check
     (M9) fails a release while this marker is present. -->

> **Optional page (0..1).** The KDS module menu lists this page as *optional*.
> Decide for your module: **keep** it — fill it in and delete this banner and
> the `OPTIONAL-PAGE` marker comment (in this file AND the German mirror) — or
> **remove** it, following the per-entry procedure in [`docs/optional-pages.md`](https://github.com/forschungsgruppe-digital-health/mii-kds-onko-ig-inoffiziell/blob/main/docs/optional-pages.md)
> of this repository. A release must not ship with this banner (convention
> check M9).
{: .ig-highlight .ig-highlight-grey}

### Value Sets

This page describes the ValueSets of the **Onkologie** module (naming
convention `MII_VS_<Module>_<Name>`). For general guidance on using codes, see
[FHIR Terminology](http://hl7.org/fhir/R4/terminologies.html); the code systems
the sets draw from are described on the [Code Systems](code-systems.html) page.

{:.bg-info}
**Expansions:** ValueSet expansions in this guide are produced by a FHIR
terminology server — SU-TermServ if the client certificate is configured,
otherwise the public HL7 server `tx.fhir.org` (in which case some KDS-specific
ValueSets may not expand completely).

> [TODO: If your module uses SNOMED CT, state the edition/version used. List
> the module's own ValueSets, or refer to the automatically generated artifact
> list — or remove this page if your module defines none.]
{: .ig-highlight .ig-highlight-grey}

<!-- source: Systemische-Therapie-Terminologien.page.md (Simplifier guide,
     TechnischeImplementierung/FHIR-Profile/Systemische-Therapie/) — a group page
     describing the systemic-therapy CodeSystem and ValueSet family, so it lands
     here as a section rather than as an artifact intro note. FQL blocks that
     queried name/status/version/code count were removed; the IG Publisher
     renders those on the artifact pages. -->
### Systemic therapy terminologies

#### Overview

The MII provides **curated, oncology-relevant terminologies** for systemic therapies:

- **Therapy protocols**: 96 oBDS-based standard protocols ([CodeSystem](https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/CodeSystem/mii-cs-onko-systemische-therapie-protokolle))
- **ATC substances**: main ValueSet + 8 year-specific ValueSets (2018-2025)
- **UNII substances**: for active substances without an ATC code ([ValueSet](https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/ValueSet/mii-vs-onko-systemische-therapie-substanzen-unii))

**Important**: the ValueSets contain only oncologically relevant substances, not the complete ATC classification.

#### Therapy protocols

The protocols are held in the CodeSystem `mii-cs-onko-systemische-therapie-protokolle`.

**Examples of frequent protocols**: FOLFOX, R-CHOP, AC, BEACOPP, ICE

Please submit new protocols via [GitHub Issues](https://github.com/medizininformatik-initiative/kerndatensatzmodul-onkologie/issues).

#### ATC substances

##### Main ValueSet (current codes)

The current codes are held in the ValueSet `mii-vs-onko-systemische-therapie-substanzen`.

##### Year-specific ValueSets

Year-specific ValueSets are available for validating historical data:

| Year | ValueSet | Canonical URL |
|------|----------|---------------|
| 2025 | mii-vs-onko-systemische-therapie-substanzen-2025 | [Link](https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/ValueSet/mii-vs-onko-systemische-therapie-substanzen-2025) |
| 2024 | mii-vs-onko-systemische-therapie-substanzen-2024 | [Link](https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/ValueSet/mii-vs-onko-systemische-therapie-substanzen-2024) |
| 2023 | mii-vs-onko-systemische-therapie-substanzen-2023 | [Link](https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/ValueSet/mii-vs-onko-systemische-therapie-substanzen-2023) |
| 2022 | mii-vs-onko-systemische-therapie-substanzen-2022 | [Link](https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/ValueSet/mii-vs-onko-systemische-therapie-substanzen-2022) |
| 2021 | mii-vs-onko-systemische-therapie-substanzen-2021 | [Link](https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/ValueSet/mii-vs-onko-systemische-therapie-substanzen-2021) |
| 2020 | mii-vs-onko-systemische-therapie-substanzen-2020 | [Link](https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/ValueSet/mii-vs-onko-systemische-therapie-substanzen-2020) |
| 2019 | mii-vs-onko-systemische-therapie-substanzen-2019 | [Link](https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/ValueSet/mii-vs-onko-systemische-therapie-substanzen-2019) |
| 2018 | mii-vs-onko-systemische-therapie-substanzen-2018 | [Link](https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/ValueSet/mii-vs-onko-systemische-therapie-substanzen-2018) |

##### ATC code transitions

The German ATC classification is updated annually. **Example quizartinib** (FLT3 inhibitor):

- **Until 31.12.2020**: `L01XE52`
- **From 01.01.2021**: `L01EX11`

**Coding recommendation**: use the ATC code that was valid at the time of therapy. In case of doubt the UNII code can be used instead.

Further examples: abemaciclib (L01XE50 → L01EF03), acalabrutinib (L01XE51 → L01EL02).

##### Post-hoc annotation of free text

DIZ **may** map historical free-text medication data to ATC codes after the fact, provided that:

1. **Provenance is documented** (mark the retrospective coding)
2. **Current ATC codes** are used (not historical ones)
3. **The original text is preserved** in `medicationCodeableConcept.text`

<details>
<summary>Example: post-annotation</summary>

```fsh
Instance: mii-exa-onko-medikation-quizartinib-postannotated
InstanceOf: MII_PR_Onko_Systemische_Therapie_Medikation

* status = #completed
* subject = Reference(Patient/example)
* medicationCodeableConcept.coding[atcClassDe] = $atc-de#L01EX11 "Quizartinib"
* medicationCodeableConcept.text = "Quizartinib (Original: Freitext aus oBDS)"
* effectivePeriod.start = "2020-09-15"  // Therapie vor Code-Änderung
* effectivePeriod.end = "2020-12-15"
```

</details>

#### UNII substances

The UNII codes are held in the ValueSet `mii-vs-onko-systemische-therapie-substanzen-unii`.

##### Substances without available codes

The following oBDS entries have neither ATC nor UNII codes:

- **EmboCept, Embozene, Hepasphere**: embolisation microspheres
- **GcMAF**: Gc protein-derived macrophage activating factor
- **G-CSF**: granulocyte colony-stimulating factor (generic designation)
- **Studienmedikament**: generic placeholder designation

→ Use `Coding.text` with free text.

**Newly available:** **Dinatriumfolinat** is now available as **LEUCOVORIN SODIUM** (UNII: 4MXU9LJS4Q) in the UNII ValueSet and as **Natriumfolinat** (ATC: V03AF06) in the ATC ValueSets.

<details>
<summary>Particular notes on UNII substances (click to expand)</summary>

- **OLAPTESED PEGOL** (UNII: MTM792B442): often documented only as "Olaptesed"
- **GEBASAXTUREV** (UNII: 4B57CWT710): also known as "Coxsackievirus A21"
- **Daromun**: corresponds to **DARLEUKIN** (UNII: 2OQ3OPV2F8) or **ONFEKAFUSP ALFA** (UNII: 6HXC0O6JMV)
- **Fibromun**: corresponds to **ONFEKAFUSP ALFA** (UNII: 6HXC0O6JMV)
- **LONCASTUXIMAB TESIRINE** (UNII: 7K5O7P6QIU): oBDS typo "Ioncastuzimab tesiren"
- **NIDANILIMAB** (UNII: ND296JF21I): listed in the oBDS as "Nadunolimab"
- **HUMAN PARVOVIRUS B19** (UNII: 94N635564T): possibly not identical to "Parvovirus H1"
- **PACLITAXEL** (UNII: P88XT4IS4D): the oBDS probably means "nab-Paclitaxel" (a separate UNII is possible)
- **CYTARABINE** (UNII: 04079A1RDZ): the oBDS probably means the liposomal formulation
- **DEPATUXIZUMAB** (UNII: W984C353CG): without the "mafodotin" part (toxin)

</details>

#### Terminology binding in the profiles

**Procedure (protocol)**:

```fsh
* usedCode from MII_VS_Onko_Systemische_Therapie_Protokolle (extensible)
```

**MedicationStatement (substance)**:

```fsh
* medicationCodeableConcept from MII_VS_Onko_Systemische_Therapie_Substanzen (extensible)
```

<!-- source: Weitere-Klassifikationen-Terminologien.page.md (Simplifier guide,
     TechnischeImplementierung/FHIR-Profile/Weitere-Klassifikationen/) — a group page
     describing the CodeSystem and ValueSet family behind the Weitere Klassifikationen
     profile, so it lands here as a section rather than as an artifact intro note (the
     source wording still says "this page"). FQL blocks that enumerated the concepts,
     the ValueSets and the profile elements were removed; the IG Publisher renders
     those on the artifact pages. -->
### Terminologies of the Weitere Klassifikationen

This page documents the terminologies for further classifications in oncology, including haematological and organ-specific staging systems.

<!-- DERIVED:bridge source=Weitere-Klassifikationen-Terminologien.page.md gate=B -->
> **Written during migration - review before release.** This section covers the
> terminology artefacts only. The profile that binds them is documented on its own
> page, [Weitere Klassifikationen](StructureDefinition-mii-pr-onko-weitere-klassifikationen.html),
> whose intro describes the classification systems clinically and sets out the
> code+method+value pattern in full.
{: .ig-highlight .ig-highlight-blue}

#### Background

<!-- Source defect, kept verbatim: this paragraph breaks off mid-sentence twice
     ("... oder Ann Arbor bei" and "Die Plattform 65c stellt"), spells "Nottingham"
     as "Nottigham", and its first sentence is grammatically broken in the source
     ("definiert ... aus"). Not corrected during migration - please review. -->
The oBDS mainly defines TNM as the staging system; many further disease- or organ-specific staging and grading systems are represented in the oBDS through the free-text field Weitere Klassifikationen. These include, for example, Nottigham Grading in breast cancer or Ann Arbor in
The Plattform 65c provides
Some of the staging systems are in international use and are already contained in CodeSystems such as SNOMED-CT and NCIt/UMLS, while others are used primarily in the German/German-speaking context.

Even though a SNOMED code exists for some staging systems, and this is better for interoperability than a proprietary CodeSystem, we decided on the representation according to the oBDS, because the data may be available at the sites directly in this format. A SNOMED annotation can be aimed for here in future versions via ConceptMaps.

#### Hierarchical CodeSystem for classification systems

The **Weitere Klassifikationen CodeSystem** uses a hierarchical structure to organise various staging and classification systems. It is published as `mii-cs-onko-weitere-klassifikationen-obds`.

<!-- Source defect: the source page carries the headings "Struktur des hierarchischen
     Ansatzes" and "Alle Klassifikationssysteme (Elternkonzepte)" with no content at
     all beneath them - the concept list was never written. The empty headings were
     dropped; the DERIVED summary below states what the published artefacts contain. -->

#### ValueSets with a descendant-of filter

The ValueSets use **descendant-of filters** for maintainable terminology management.

<!-- Source defect: the source page calls mii-vs-onko-weitere-klassifikationen the
     "Haupt-ValueSet für alle Klassifikationswerte" and names the filter operator
     "descendant-of". In the published artefacts the classification VALUES are in
     mii-vs-onko-weitere-klassifikationen-auspraegungen, the filter operator is
     "is-a", and mii-vs-onko-weitere-klassifikationen holds the classification
     SYSTEMS. Not corrected during migration - please review. -->

<!-- DERIVED:summary source=Weitere-Klassifikationen-Terminologien.page.md gate=B -->
> **Written during migration - review before release.** The source page listed the
> concepts and the ValueSets through generated queries, which do not carry over to
> this guide. The published family is: the CodeSystem
> [Weitere Klassifikationen oBDS](CodeSystem-mii-cs-onko-weitere-klassifikationen-obds.html),
> which holds 20 classification systems as top-level concepts and their 161
> classification values as child concepts; the ValueSet
> [Weitere Klassifikationen](ValueSet-mii-vs-onko-weitere-klassifikationen.html),
> which enumerates the classification systems themselves from SNOMED CT and the NCI
> Thesaurus; and the ValueSet
> [Weitere Klassifikationen - Auspraegungen](ValueSet-mii-vs-onko-weitere-klassifikationen-auspraegungen.html),
> which selects the values per classification system by a filter on the oBDS
> CodeSystem. The heading and the lead sentence above reproduce the source page,
> which assigns the values to the first of the two ValueSets and names the filter
> operator `descendant-of` - please reconcile before release.
{: .ig-highlight .ig-highlight-blue}

#### mCODE STU4 pattern integration

The implementation follows the **mCODE STU4 code+method+value pattern**.

**Example implementation:**

<!-- Source defect, kept verbatim: the block below names the instance
     mii-exa-onko-weitere-klassifikationen-binet and the alias
     $mii-cs-onko-weitere-klassifikationen; the published artefacts are
     mii-exa-onko-weitere-klassifikationen-4 and the CodeSystem
     mii-cs-onko-weitere-klassifikationen-obds. Not corrected during migration -
     please review. -->

```
Instance: mii-exa-onko-weitere-klassifikationen-binet
InstanceOf: MII_PR_Onko_Weitere_Klassifikationen

// Allgemeiner Code für Staging
* code = $sct#385388004 "Tumorstadium-Befund"

// Spezifische Methode
* method = $mii-cs-onko-weitere-klassifikationen#binet "BINET Staging System"

// Tatsächlicher Wert
* valueCodeableConcept = $mii-cs-onko-weitere-klassifikationen#binet-a "BINET A"
```

#### Mapping to the oBDS

The Weitere Klassifikationen correspond to the **oBDS field 9 "Weitere Klassifikationen"**.

#### SNOMED CT mappings

SNOMED CT equivalents exist for some classification systems:

- BINET → SNOMED CT: 1149214008 (Binet chronic lymphocytic leukemia staging)
- Ann Arbor → SNOMED CT: 254373007 (Ann Arbor lymphoma staging)
- WHO Grade → SNOMED CT: 277612008 (WHO tumor grade)

#### Examples

- FIGO stage IVB (ovarian tumours): [mii-exa-onko-weitere-klassifikationen-1](Observation-mii-exa-onko-weitere-klassifikationen-1.html)
- Ann Arbor stage IIIX: [mii-exa-onko-weitere-klassifikationen-2](Observation-mii-exa-onko-weitere-klassifikationen-2.html)
- FIGO grade 2: [mii-exa-onko-weitere-klassifikationen-3](Observation-mii-exa-onko-weitere-klassifikationen-3.html)

<!-- source: Terminologien.page.md (Simplifier guide,
     TechnischeImplementierung/Terminologien.page.md) — value-set-relevant part;
     the terminologies themselves are described on code-systems.md. -->
### Terminology bindings by data area

<!-- DERIVED:summary source=Terminologien.page.md gate=B -->
> **Written during migration - review before release.** Condensed from the
> source guide's *Terminologien* page, which describes each terminology in full
> on [Code Systems](code-systems.html). Which terminology the value sets bind
> to, by data area:
>
> - primary diagnosis, pre-existing conditions and cause of death — ICD-10-GM;
>   the module deliberately follows the oBDS here rather than the ICD-10-WHO
>   that the BfArM recommends for causes of death
> - site of the primary tumour — ICD-O-3 Topographie; its morphological
>   character — ICD-O-3 Morphologie
> - operative procedures — OPS
> - systemic-therapy medication — ATC, with UNII as the second system for
>   substances that have no established ATC code, which is why the
>   SystemischeTherapie MedicationStatement profile permits dual coding (the
>   value sets are listed in the section above)
> - adverse events — CTCAE in the Nebenwirkung profile; MedDRA covers the wider
>   pharmaceutical, biological, vaccine and drug/device scope
> - tumour stage — the TNM classification in its 8th edition, issued with the
>   Union for International Cancer Control (UICC)
> - observation codes and units of measure — LOINC, SNOMED CT and UCUM
{: .ig-highlight .ig-highlight-blue}
