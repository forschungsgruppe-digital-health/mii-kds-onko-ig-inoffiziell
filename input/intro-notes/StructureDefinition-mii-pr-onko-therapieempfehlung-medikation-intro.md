<!-- markdownlint-disable MD041 -->
<!-- Migrated from Therapieempfehlung-Medikation-MedicationRequest.page.md
     (MII IG Modul Onkologie, Simplifier). Simplifier/FQL directives (page title,
     tree/XML/JSON/link tabs, FQL query blocks for profile metadata and the oBDS mapping)
     were removed - the IG Publisher renders all of that on this artifact page. The two
     pagelink directives were resolved to their targets.
     German mirror: input/translations/de/intro-notes/StructureDefinition-mii-pr-onko-therapieempfehlung-medikation-intro.md -->

This profile describes a **medication therapy recommendation** in the context of the tumor board. It
is based on the FHIR MedicationRequest and is typically used as part of a combination therapy
(RequestGroup) or as a standalone recommendation.

### Content

The MedicationRequest profile enables the structured recording of medication recommendations with:

- **Drug coding**: PZN (medicinal products) and/or ATC-DE (active substances)
- **Relation to the tumor disease**: mandatory reference to the primary tumor diagnosis
- **Additional justifications**: optional references to further Conditions or Observations

### Use cases

#### **Standalone medication recommendation**

For single-substance recommendations without a combination protocol:

```
MedicationRequest
├── intent: #proposal
├── medicationCodeableConcept: ATC L01XE27 (Ibrutinib)
├── authoredOn: 2024-01-15
└── reasonReference: Reference(Primärtumor)
```

#### **Part of a combination therapy**

As a component of a RequestGroup-based combination therapy:

```
RequestGroup (FOLFOX-Protokoll)
├── action[0].resource: MedicationRequest (5-FU)
├── action[1].resource: MedicationRequest (Oxaliplatin)
└── action[2].resource: MedicationRequest (Leucovorin)
```

### Technical implementation

#### **Intent semantics**

- **`#proposal`**: standalone therapy recommendation of the tumor board
- **`#option`**: part of a RequestGroup (combination therapy)

#### **Drug coding**

The `medicationCodeableConcept` element supports:

- **ATC-DE**: for active-substance-based recommendations
- **PZN**: for specific medicinal product recommendations
- **Free text**: for experimental or non-codable substances

#### **reasonReference extension**

Besides the mandatory reference to the primary tumor, the profile also allows:

- **Condition**: further relevant diseases as a justification
- **Observation**: supporting findings (e.g. biomarkers, staging)

```
reasonReference (Slicing: open, profile-based)
├── Primaertumor (1..1 MS): Reference(MII_PR_Onko_Diagnose_Primaertumor)
└── [weitere]: Reference(Condition or Observation)
```

### Use with the Extended CarePlan

This profile is primarily designed for use with the **Tumorkonferenz Detailed Recommendations
CarePlan** and the
[Therapieempfehlung Kombinationstherapie RequestGroup](StructureDefinition-mii-pr-onko-therapieempfehlung-kombinationstherapie.html):

- **Standard oBDS**: cancer registries record only the therapy type (e.g. "CH" for chemotherapy)
  without details on specific drugs
- **Extended CarePlan**: enables specific medication recommendations with ATC/PZN coding

<!-- DERIVED:bridge source=Therapieempfehlung-Medikation-MedicationRequest.page.md gate=B -->
> **Written during migration - review before release.** The source page cross-linked a profile
> "Tumorkonferenz Detailed Recommendations CarePlan". This module does not contain that profile, so
> the reference above is plain text rather than a link. Decide before release whether the profile is
> added or the sentence is rewritten against
> [Tumorkonferenz](StructureDefinition-mii-pr-onko-tumorkonferenz.html) and its extended slice.
{: .ig-highlight .ig-highlight-blue}

**Integration with the RequestGroup (combination therapy)**:

```
CarePlan (Detailed Recommendations)
└── activity.reference → RequestGroup
    ├── code: "CZ" (Chemo + zielgerichtete Substanzen)
    └── action.action.resource → MedicationRequest
        ├── medication: ATC L01XE (Trastuzumab)
        └── reasonReference: Reference(Primärtumor)
```

### oBDS context

This profile supports the recording of therapy recommendations per oBDS chapter 19:

- **19.1 Therapieempfehlung Typ**: via RequestGroup.code (for combination therapies)
- **Drug details**: structured recording via MedicationRequest

**Note**: the standard oBDS recording happens via `CarePlan.activity.detail.code` (therapy type
only). This MedicationRequest profile offers extended structuring for molecular tumor boards,
combination therapy protocols and specialized use cases.

### Terminology binding

**medicationCodeableConcept.coding**:

- At least one coding required (1..*)
- ATC-DE or PZN recommended
- Free text possible via `.text`

### Search parameters

1. The search parameter ```_id``` SHALL be supported:
    ```GET [base]/MedicationRequest?_id=1234```

2. The search parameter "_profile" SHALL be supported:
    ```GET [base]/MedicationRequest?_profile=https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-therapieempfehlung-medikation```

3. The search parameter "subject" SHALL be supported:
    ```GET [base]/MedicationRequest?subject=Patient/example```

4. The search parameter "intent" SHOULD be supported:
    ```GET [base]/MedicationRequest?intent=proposal```

5. The search parameter "medication" SHOULD be supported:
    ```GET [base]/MedicationRequest?medication=http://fhir.de/CodeSystem/bfarm/atc|L01XE27```
