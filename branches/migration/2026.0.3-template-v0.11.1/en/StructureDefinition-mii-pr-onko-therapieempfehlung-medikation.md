# MII PR Onkologie Therapieempfehlung Medikation - MII IG Kerndatensatz-Modul Onkologie v2026.0.3

* [**Table of Contents**](toc.md)
* [**Artifacts Summary**](artifacts.md)
* **MII PR Onkologie Therapieempfehlung Medikation**

## Resource Profile: MII PR Onkologie Therapieempfehlung Medikation 

| | |
| :--- | :--- |
| *Official URL*:https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-therapieempfehlung-medikation | *Version*:2026.0.3 |
| Active as of 2026-08-22 | *Computable Name*:MII_PR_Onko_Therapieempfehlung_Medikation |

 
Dieses Profil beschreibt eine Medikations-Tumorempfehlung 

This profile describes a **medication therapy recommendation** in the context of the tumor board. It is based on the FHIR MedicationRequest and is typically used as part of a combination therapy (RequestGroup) or as a standalone recommendation.

### Content

The MedicationRequest profile enables the structured recording of medication recommendations with:

* **Drug coding**: PZN (medicinal products) and/or ATC-DE (active substances)
* **Relation to the tumor disease**: mandatory reference to the primary tumor diagnosis
* **Additional justifications**: optional references to further Conditions or Observations

### Use cases

#### Standalone medication recommendation

For single-substance recommendations without a combination protocol:

```
MedicationRequest
├── intent: #proposal
├── medicationCodeableConcept: ATC L01XE27 (Ibrutinib)
├── authoredOn: 2024-01-15
└── reasonReference: Reference(Primärtumor)

```

#### Part of a combination therapy

As a component of a RequestGroup-based combination therapy:

```
RequestGroup (FOLFOX-Protokoll)
├── action[0].resource: MedicationRequest (5-FU)
├── action[1].resource: MedicationRequest (Oxaliplatin)
└── action[2].resource: MedicationRequest (Leucovorin)

```

### Technical implementation

#### Intent semantics

* **`#proposal`**: standalone therapy recommendation of the tumor board
* **`#option`**: part of a RequestGroup (combination therapy)

#### Drug coding

The `medicationCodeableConcept` element supports:

* **ATC-DE**: for active-substance-based recommendations
* **PZN**: for specific medicinal product recommendations
* **Free text**: for experimental or non-codable substances

#### reasonReference extension

Besides the mandatory reference to the primary tumor, the profile also allows:

* **Condition**: further relevant diseases as a justification
* **Observation**: supporting findings (e.g. biomarkers, staging)

```
reasonReference (Slicing: open, profile-based)
├── Primaertumor (1..1 MS): Reference(MII_PR_Onko_Diagnose_Primaertumor)
└── [weitere]: Reference(Condition or Observation)

```

### Use with the Extended CarePlan

This profile is primarily designed for use with the **Tumorkonferenz Detailed Recommendations CarePlan** and the [Therapieempfehlung Kombinationstherapie RequestGroup](StructureDefinition-mii-pr-onko-therapieempfehlung-kombinationstherapie.md):

* **Standard oBDS**: cancer registries record only the therapy type (e.g. "CH" for chemotherapy) without details on specific drugs
* **Extended CarePlan**: enables specific medication recommendations with ATC/PZN coding

> **Written during migration - review before release.** The source page cross-linked a profile "Tumorkonferenz Detailed Recommendations CarePlan". This module does not contain that profile, so the reference above is plain text rather than a link. Decide before release whether the profile is added or the sentence is rewritten against [Tumorkonferenz](StructureDefinition-mii-pr-onko-tumorkonferenz.md) and its extended slice.

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

* **19.1 Therapieempfehlung Typ**: via RequestGroup.code (for combination therapies)
* **Drug details**: structured recording via MedicationRequest

**Note**: the standard oBDS recording happens via `CarePlan.activity.detail.code` (therapy type only). This MedicationRequest profile offers extended structuring for molecular tumor boards, combination therapy protocols and specialized use cases.

### Terminology binding

**medicationCodeableConcept.coding**:

* At least one coding required (1..*)
* ATC-DE or PZN recommended
* Free text possible via `.text`

### Search parameters

1. The search parameter `_id` SHALL be supported: `GET [base]/MedicationRequest?_id=1234`
1. The search parameter "_profile" SHALL be supported: `GET [base]/MedicationRequest?_profile=https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-therapieempfehlung-medikation`
1. The search parameter "subject" SHALL be supported: `GET [base]/MedicationRequest?subject=Patient/example`
1. The search parameter "intent" SHOULD be supported: `GET [base]/MedicationRequest?intent=proposal`
1. The search parameter "medication" SHOULD be supported: `GET [base]/MedicationRequest?medication=http://fhir.de/CodeSystem/bfarm/atc|L01XE27`

**Usages:**

* Refer to this Profile: [MII PR Onkologie Therapieempfehlung Kombinationstherapie](StructureDefinition-mii-pr-onko-therapieempfehlung-kombinationstherapie.md)
* Examples for this Profile: [MedicationRequest/mii-exa-onko-cdk46-class-medication](MedicationRequest-mii-exa-onko-cdk46-class-medication.md), [MedicationRequest/mii-exa-onko-folfox-5fu-request](MedicationRequest-mii-exa-onko-folfox-5fu-request.md), [MedicationRequest/mii-exa-onko-folfox-leucovorin-request](MedicationRequest-mii-exa-onko-folfox-leucovorin-request.md), [MedicationRequest/mii-exa-onko-folfox-oxaliplatin-request](MedicationRequest-mii-exa-onko-folfox-oxaliplatin-request.md)... Show 5 more, [MedicationRequest/mii-exa-onko-modification-5fu-request](MedicationRequest-mii-exa-onko-modification-5fu-request.md), [MedicationRequest/mii-exa-onko-modification-leucovorin-request](MedicationRequest-mii-exa-onko-modification-leucovorin-request.md), [MedicationRequest/mii-exa-onko-modification-oxaliplatin-request](MedicationRequest-mii-exa-onko-modification-oxaliplatin-request.md), [MedicationRequest/mii-exa-onko-tdm1-option](MedicationRequest-mii-exa-onko-tdm1-option.md) and [MedicationRequest/mii-exa-onko-tucatinib-option](MedicationRequest-mii-exa-onko-tucatinib-option.md)
* CapabilityStatements using this Profile: [MII CPS Onkology CapabilityStatement](CapabilityStatement-mii-cps-onko-capabilitystatement.md)

You can also check for [usages in the FHIR IG Statistics](https://packages2.fhir.org/xig/resource/de.medizininformatikinitiative.kerndatensatz.onkologie|current/StructureDefinition/StructureDefinition-mii-pr-onko-therapieempfehlung-medikation.json)

### Formal Views of Profile Content

 [Description of Profiles, Differentials, Snapshots, and their representations](http://build.fhir.org/ig/FHIR/ig-guidance/readingIgs.html#structure-definitions). 

 

Other representations of profile: [CSV](../StructureDefinition-mii-pr-onko-therapieempfehlung-medikation.csv), [Excel](../StructureDefinition-mii-pr-onko-therapieempfehlung-medikation.xlsx), [Schematron](../StructureDefinition-mii-pr-onko-therapieempfehlung-medikation.sch) 



## Resource Content

```json
{
  "resourceType" : "StructureDefinition",
  "id" : "mii-pr-onko-therapieempfehlung-medikation",
  "extension" : [{
    "url" : "https://www.medizininformatik-initiative.de/fhir/modul-meta/StructureDefinition/mii-ex-meta-license-codeable",
    "valueCodeableConcept" : {
      "coding" : [{
        "system" : "http://hl7.org/fhir/spdx-license",
        "code" : "CC-BY-4.0",
        "display" : "Creative Commons Attribution 4.0 International"
      }]
    }
  }],
  "url" : "https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-therapieempfehlung-medikation",
  "version" : "2026.0.3",
  "name" : "MII_PR_Onko_Therapieempfehlung_Medikation",
  "title" : "MII PR Onkologie Therapieempfehlung Medikation",
  "status" : "active",
  "date" : "2026-08-22T22:11:44+00:00",
  "publisher" : "NUM-DIZ",
  "_publisher" : {
    "extension" : [{
      "extension" : [{
        "url" : "lang",
        "valueCode" : "de"
      },
      {
        "url" : "content",
        "valueString" : "NUM-DIZ"
      }],
      "url" : "http://hl7.org/fhir/StructureDefinition/translation"
    }]
  },
  "contact" : [{
    "name" : "NUM-DIZ",
    "telecom" : [{
      "system" : "url",
      "value" : "https://www.netzwerk-universitaetsmedizin.de"
    }]
  }],
  "description" : "Dieses Profil beschreibt eine Medikations-Tumorempfehlung",
  "jurisdiction" : [{
    "coding" : [{
      "system" : "urn:iso:std:iso:3166",
      "code" : "DE",
      "display" : "Germany"
    }]
  }],
  "fhirVersion" : "4.0.1",
  "mapping" : [{
    "identity" : "oBDS",
    "name" : "Mapping FHIR zu oBDS"
  }],
  "kind" : "resource",
  "abstract" : false,
  "type" : "MedicationRequest",
  "baseDefinition" : "https://www.medizininformatik-initiative.de/fhir/core/modul-medikation/StructureDefinition/MedicationRequest",
  "derivation" : "constraint",
  "differential" : {
    "element" : [{
      "id" : "MedicationRequest",
      "path" : "MedicationRequest"
    },
    {
      "id" : "MedicationRequest.intent",
      "path" : "MedicationRequest.intent",
      "short" : "proposal | option",
      "definition" : "Verwenden Sie 'proposal' für eigenständige Therapieempfehlungen. Verwenden Sie 'option' wenn die MedicationRequest Teil einer RequestGroup ist (z.B. Kombinationstherapie)."
    },
    {
      "id" : "MedicationRequest.medication[x]:medicationCodeableConcept",
      "path" : "MedicationRequest.medication[x]",
      "sliceName" : "medicationCodeableConcept",
      "min" : 1,
      "type" : [{
        "code" : "CodeableConcept"
      }]
    },
    {
      "id" : "MedicationRequest.medication[x]:medicationCodeableConcept.coding",
      "path" : "MedicationRequest.medication[x].coding",
      "min" : 1
    },
    {
      "id" : "MedicationRequest.subject",
      "path" : "MedicationRequest.subject",
      "type" : [{
        "code" : "Reference",
        "targetProfile" : ["http://hl7.org/fhir/StructureDefinition/Patient"]
      }]
    },
    {
      "id" : "MedicationRequest.supportingInformation",
      "path" : "MedicationRequest.supportingInformation",
      "mustSupport" : true
    },
    {
      "id" : "MedicationRequest.authoredOn",
      "path" : "MedicationRequest.authoredOn",
      "min" : 1
    },
    {
      "id" : "MedicationRequest.reasonReference",
      "path" : "MedicationRequest.reasonReference",
      "slicing" : {
        "discriminator" : [{
          "type" : "profile",
          "path" : "$this.resolve()"
        }],
        "ordered" : false,
        "rules" : "open"
      },
      "min" : 1,
      "type" : [{
        "code" : "Reference",
        "targetProfile" : ["https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-diagnose-primaertumor",
        "http://hl7.org/fhir/StructureDefinition/Condition",
        "http://hl7.org/fhir/StructureDefinition/Observation"]
      }]
    },
    {
      "id" : "MedicationRequest.reasonReference:Primaertumor",
      "path" : "MedicationRequest.reasonReference",
      "sliceName" : "Primaertumor",
      "short" : "Tumorerkrankung (Pflicht)",
      "definition" : "Referenz auf die Primärtumor-Diagnose, auf die sich diese Therapieempfehlung bezieht.",
      "min" : 1,
      "max" : "1",
      "type" : [{
        "code" : "Reference",
        "targetProfile" : ["https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-diagnose-primaertumor"]
      }],
      "mustSupport" : true
    }]
  }
}

```
