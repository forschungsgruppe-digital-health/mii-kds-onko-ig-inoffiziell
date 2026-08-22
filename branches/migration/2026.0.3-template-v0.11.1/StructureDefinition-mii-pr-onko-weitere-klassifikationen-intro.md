<!-- markdownlint-disable MD041 -->
<!-- source: TechnischeImplementierung/FHIR-Profile/Weitere-Klassifikationen/Weitere-Klassifikationen-Observation.page.md
     German mirror (source language): input/translations/de/intro-notes/StructureDefinition-mii-pr-onko-weitere-klassifikationen-intro.md -->

This profile describes further tumour classifications besides TNM.

### Delimitation: staging, grading and risk assessment

The "Weitere Klassifikationen" cover various kinds of assessment systems:

- **Staging systems**: determine the anatomical extent of the tumour (e.g. FIGO, Ann Arbor, AJCC)
- **Grading systems**: assess the histological differentiation and biological aggressiveness
- **Risk assessment systems**: prognostic scores based on multiple clinical parameters (e.g. IPI, FLIPI, IPSS)
- **Molecular classifications**: based on genetic/molecular markers (e.g. p16 status, ELN classification)

### Staging systems (anatomical extent)

- **FIGO classification** for gynaecological tumours
- **AJCC classifications** of various editions (6th, 7th, 8th edition)
- **Ann Arbor classification** for lymphomas (Hodgkin and non-Hodgkin)
- **Durie-Salmon staging** for multiple myeloma
- **Bismuth classification** for hilar cholangiocarcinoma

### Grading and assessment systems

- **Breslow/Clark system** for melanomas (tumour thickness and depth of invasion)
- **GIST mitotic rate** (gastrointestinal stromal tumours)
- **p16 status** (molecular marker, especially in HPV-associated carcinomas)

### Prognostic risk scores

- **Lymphomas**:
  - IPI (International Prognostic Index) for aggressive non-Hodgkin lymphomas
  - FLIPI for follicular lymphomas
  - MIPI for mantle cell lymphomas
  - GHSG risk classification for Hodgkin lymphomas
- **Leukaemias**:
  - European LeukemiaNet Classification (AML)
  - EUTOS Score (chronic myeloid leukaemia)
  - Sanz Score (acute promyelocytic leukaemia)
- **Myelodysplastic syndrome**: IPSS (International Prognostic Scoring System)
- **Multiple myeloma**: ISS/R-ISS (International Staging System)
- **Waldenström macroglobulinaemia**: ISSWM

The Plattform §65c provides a catalogue of how the most frequent classifications are to be coded **for the cancer registry report** for reasons of harmonisation:
https://plattform65c.atlassian.net/wiki/spaces/UMK/pages/15532511/Weitere+Klassifikationen

### Implementation notes

#### FHIR modelling following the mCODE STU4 pattern

This profile follows the **mCODE STU4 build pattern** for staging systems with a three-part structure:

- **`Observation.code`**: general staging concept (e.g. "FIGO Stage", "Ann Arbor Stage", "BINET Stage")
- **`Observation.method`**: specific classification system / assessment method (Must Support)
- **`Observation.value`**: concrete classification value from the corresponding ValueSet

**Example FIGO classification:**

```
code: 385361009 "FIGO Stage" (allgemeines Konzept)
method: "FIGO staging of cervical carcinoma" (spezifische Methode)
value: "Stage IIA" (konkreter Wert)
```

**Example haematological classification:**

```
code: "BINET staging system" (allgemeines Konzept)
method: "BINET staging for chronic lymphocytic leukemia" (spezifische Methode)
value: "BINET A" (konkreter Wert)
```

This structure makes it possible to distinguish various staging systems within the same tumour entity and to identify clearly which specific assessment procedure was used.

#### Terminology integration

Because of the multitude of possible scales and scores it is not possible to deposit a comprehensive and universally valid catalogue here, so that the concrete design is left to the manufacturers and systems. HL7 Deutschland provides notes on this at the following link: https://ig.fhir.de/basisprofile-de/stable/ig-markdown-Ressourcen-Observation-Skalen-und-Scores.html

**Important note**: for oBDS-specific classifications it should first be checked whether corresponding SNOMED CT or LOINC codes are available before proprietary oBDS codes are used.

**Prioritisation in the choice of terminology:**

1. **SNOMED CT** for established classification systems (preferred)
2. **LOINC** for laboratory-based and quantitative assessments
3. **NCI Thesaurus** for special oncological concepts
4. **oBDS-specific codes** only if no international standards are available

### Delimitation from the organ-specific modules

The following classifications will in future be covered by the organ-specific modules and shall no longer be coded via further classifications:

- **Gleason score** (Prostata module)
- **Further organ-specific scores** are being transferred into the corresponding modules successively

### Terminology binding

The profile uses a **preferred binding** for the ValueSet `MII_VS_Onko_Weitere_Klassifikationen`, whereby both international terminologies (SNOMED CT, NCI Thesaurus) and oBDS-specific codes are supported.

- ValueSet: MII VS Onko Weitere Klassifikationen (`https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/ValueSet/mii-vs-onko-weitere-klassifikationen`)

### Search parameters

The following search parameters are relevant for the Onkologie module, also in combination:

- The search parameter `_id` MUST be supported: `GET [base]/Observation?_id=1234`
- The search parameter `_profile` MUST be supported: `GET [base]/Observation?_profile=https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-weitere-klassifikationen`
- The search parameter `code` MUST be supported: `GET [base]/Observation?code=http://fhir.de/CodeSystem/sct|184305005`
- The search parameter `subject` MUST be supported: `GET [base]/Observation?subject=Patient/example`
- The search parameter `encounter` MUST be supported: `GET [base]/Observation?encounter=Encounter/example`
- The search parameter `date` MUST be supported: `GET [base]/Observation?date=2024-02-08`
- The search parameter `method` SHOULD be supported: `GET [base]/Observation?method=http://snomed.info/sct|254373007` — enables searching for specific classification methods (e.g. FIGO, Ann Arbor Hodgkin vs. non-Hodgkin)
