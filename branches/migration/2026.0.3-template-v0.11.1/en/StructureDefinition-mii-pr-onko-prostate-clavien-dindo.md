# MII PR Onkologie Clavien Dindo - MII IG Kerndatensatz-Modul Onkologie v2026.0.3

* [**Table of Contents**](toc.md)
* [**Artifacts Summary**](artifacts.md)
* **MII PR Onkologie Clavien Dindo**

## Resource Profile: MII PR Onkologie Clavien Dindo 

| | |
| :--- | :--- |
| *Official URL*:https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-prostate-clavien-dindo | *Version*:2026.0.3 |
| Active as of 2026-08-22 | *Computable Name*:MII_PR_Onko_Prostata_Clavien_Dindo |

 
Dieses Profil beschreibt den Clavien-Dindo-Score für die Prostatektomie in der Onkologie 

This profile describes the Clavien-Dindo score for prostatectomy in oncology. The Clavien-Dindo classification is a standardised system for assessing post-operative complications on the basis of their severity and of the treatment they require.

The profile is based on a FHIR Observation resource and uses SNOMED CT to code the assessment procedure. It supports both the SNOMED CT Clavien-Dindo grades and the oBDS-specific codings for post-operative complications.

### Links to other resources

The Clavien-Dindo score is an important post-operative observation:

* references the primary diagnosis (MII_PR_Onko_Diagnose_Primaertumor) via `Observation.focus[Diagnose]`
* references the operation performed (MII_PR_Onko_Operation) via `Observation.focus[Operation]`
* references the patient (Patient resource) via `Observation.subject`
* can be linked to a specific encounter via `Observation.encounter`
* can be linked to the corresponding tissue specimens via `Observation.specimen`

### oBDS context

According to oBDS, post-operative complications after prostatectomy are recorded systematically. The Clavien-Dindo classification complements the oBDS coding with an internationally standardised assessment of the complication severity.

### Terminology binding

The profile uses **required** bindings for both coding systems:

#### Assessment method

* **SNOMED CT**: 789278003 "Clavien-Dindo classification (assessment scale)"

#### Observation code

* **SNOMED CT**: 789279006 "Clavien-Dindo classification grade (observable entity)"

#### Clavien-Dindo ValueSet

The ValueSet covers the SNOMED CT codes for all Clavien-Dindo grades: MII VS Onko Prostata Clavien-Dindo.

#### oBDS post-operative complications ValueSet

In addition, oBDS-specific codes for post-operative complications are supported: MII VS Onko Prostata Postsurgical Complications.

### Search parameters

The following search parameters are relevant for the Prostata-Clavien-Dindo profile, including in combination:

* The search parameter `_id` MUST be supported: `GET [base]/Observation?_id=12345`
* The search parameter `_profile` MUST be supported: `GET [base]/Observation?_profile=https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-prostate-clavien-dindo`
* The search parameter `code` MUST be supported: `GET [base]/Observation?code=http://snomed.info/sct|789279006`
* The search parameter `subject` MUST be supported: `GET [base]/Observation?subject=Patient/test`
* The search parameter `focus` MUST be supported: `GET [base]/Observation?focus=Condition/primaertumor`, `GET [base]/Observation?focus=Procedure/prostatektomie`
* The search parameter `method` MUST be supported: `GET [base]/Observation?method=http://snomed.info/sct|789278003`
* The search parameter `value-concept` MUST be supported: `GET [base]/Observation?value-concept=http://snomed.info/sct|1367521005`

**Usages:**

* Examples for this Profile: [Observation/mii-exa-onko-prostata-surgical-complication-1](Observation-mii-exa-onko-prostata-surgical-complication-1.md)
* CapabilityStatements using this Profile: [MII CPS Onkology CapabilityStatement](CapabilityStatement-mii-cps-onko-capabilitystatement.md)

You can also check for [usages in the FHIR IG Statistics](https://packages2.fhir.org/xig/resource/de.medizininformatikinitiative.kerndatensatz.onkologie|current/StructureDefinition/StructureDefinition-mii-pr-onko-prostate-clavien-dindo.json)

### Formal Views of Profile Content

 [Description of Profiles, Differentials, Snapshots, and their representations](http://build.fhir.org/ig/FHIR/ig-guidance/readingIgs.html#structure-definitions). 

 

Other representations of profile: [CSV](../StructureDefinition-mii-pr-onko-prostate-clavien-dindo.csv), [Excel](../StructureDefinition-mii-pr-onko-prostate-clavien-dindo.xlsx), [Schematron](../StructureDefinition-mii-pr-onko-prostate-clavien-dindo.sch) 



## Resource Content

```json
{
  "resourceType" : "StructureDefinition",
  "id" : "mii-pr-onko-prostate-clavien-dindo",
  "url" : "https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-prostate-clavien-dindo",
  "version" : "2026.0.3",
  "name" : "MII_PR_Onko_Prostata_Clavien_Dindo",
  "title" : "MII PR Onkologie Clavien Dindo",
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
  "description" : "Dieses Profil beschreibt den Clavien-Dindo-Score für die Prostatektomie in der Onkologie",
  "jurisdiction" : [{
    "coding" : [{
      "system" : "urn:iso:std:iso:3166",
      "code" : "DE",
      "display" : "Germany"
    }]
  }],
  "fhirVersion" : "4.0.1",
  "mapping" : [{
    "identity" : "workflow",
    "uri" : "http://hl7.org/fhir/workflow",
    "name" : "Workflow Pattern"
  },
  {
    "identity" : "sct-concept",
    "uri" : "http://snomed.info/conceptdomain",
    "name" : "SNOMED CT Concept Domain Binding"
  },
  {
    "identity" : "v2",
    "uri" : "http://hl7.org/v2",
    "name" : "HL7 v2 Mapping"
  },
  {
    "identity" : "w5",
    "uri" : "http://hl7.org/fhir/fivews",
    "name" : "FiveWs Pattern Mapping"
  },
  {
    "identity" : "sct-attr",
    "uri" : "http://snomed.org/attributebinding",
    "name" : "SNOMED CT Attribute Binding"
  }],
  "kind" : "resource",
  "abstract" : false,
  "type" : "Observation",
  "baseDefinition" : "http://hl7.org/fhir/StructureDefinition/Observation",
  "derivation" : "constraint",
  "differential" : {
    "element" : [{
      "id" : "Observation",
      "path" : "Observation"
    },
    {
      "id" : "Observation.meta.profile",
      "path" : "Observation.meta.profile",
      "mustSupport" : true
    },
    {
      "id" : "Observation.code",
      "path" : "Observation.code",
      "short" : "Postoperative Komplikation nach Clavien-Dindo",
      "definition" : "Posteroperative Komplikationssschwere nach Clavien-Dindo für die Prostatektomie in der Onkologie",
      "mustSupport" : true
    },
    {
      "id" : "Observation.code.coding",
      "path" : "Observation.code.coding",
      "patternCoding" : {
        "system" : "http://snomed.info/sct",
        "code" : "789279006",
        "display" : "Clavien-Dindo classification grade (observable entity)"
      }
    },
    {
      "id" : "Observation.subject",
      "path" : "Observation.subject",
      "min" : 1,
      "type" : [{
        "code" : "Reference",
        "targetProfile" : ["http://hl7.org/fhir/StructureDefinition/Patient"]
      }],
      "mustSupport" : true
    },
    {
      "id" : "Observation.focus",
      "path" : "Observation.focus",
      "slicing" : {
        "discriminator" : [{
          "type" : "profile",
          "path" : "resolve()"
        }],
        "description" : "Slice to differentiate between focus condition and focus procedure",
        "ordered" : false,
        "rules" : "open"
      },
      "min" : 2,
      "mustSupport" : true
    },
    {
      "id" : "Observation.focus:Diagnose",
      "path" : "Observation.focus",
      "sliceName" : "Diagnose",
      "min" : 1,
      "max" : "1",
      "type" : [{
        "code" : "Reference",
        "targetProfile" : ["https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-diagnose-primaertumor"]
      }],
      "mustSupport" : true
    },
    {
      "id" : "Observation.focus:Operation",
      "path" : "Observation.focus",
      "sliceName" : "Operation",
      "min" : 1,
      "max" : "1",
      "type" : [{
        "code" : "Reference",
        "targetProfile" : ["https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-operation"]
      }],
      "mustSupport" : true
    },
    {
      "id" : "Observation.encounter",
      "path" : "Observation.encounter",
      "mustSupport" : true
    },
    {
      "id" : "Observation.value[x]",
      "path" : "Observation.value[x]",
      "min" : 1,
      "type" : [{
        "code" : "CodeableConcept"
      }],
      "mustSupport" : true
    },
    {
      "id" : "Observation.value[x].coding",
      "path" : "Observation.value[x].coding",
      "slicing" : {
        "discriminator" : [{
          "type" : "value",
          "path" : "system"
        }],
        "description" : "Slicing für Clavien-Dindo und oBDS Postoperative Komplikationen",
        "ordered" : false,
        "rules" : "open"
      },
      "_short" : {
        "extension" : [{
          "extension" : [{
            "url" : "lang",
            "valueCode" : "de-DE"
          },
          {
            "url" : "content",
            "valueString" : "PSA-Wert"
          }],
          "url" : "http://hl7.org/fhir/StructureDefinition/translation"
        }]
      },
      "_definition" : {
        "extension" : [{
          "extension" : [{
            "url" : "lang",
            "valueCode" : "de-DE"
          },
          {
            "url" : "content",
            "valueString" : "PSA-Wert aus Blut/Plasma in ng/ml"
          }],
          "url" : "http://hl7.org/fhir/StructureDefinition/translation"
        }]
      },
      "min" : 1
    },
    {
      "id" : "Observation.value[x].coding:ClavienDindo",
      "path" : "Observation.value[x].coding",
      "sliceName" : "ClavienDindo",
      "short" : "PSA-Wert",
      "definition" : "PSA-Wert aus Blut/Plasma in ng/ml",
      "min" : 0,
      "max" : "1",
      "mustSupport" : true,
      "binding" : {
        "strength" : "required",
        "valueSet" : "https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/ValueSet/mii-vs-onko-prostata-clavien-dindo"
      }
    },
    {
      "id" : "Observation.value[x].coding:ClavienDindo.system",
      "path" : "Observation.value[x].coding.system",
      "min" : 1,
      "patternUri" : "http://snomed.info/sct"
    },
    {
      "id" : "Observation.value[x].coding:OBDSPostOPKompl",
      "path" : "Observation.value[x].coding",
      "sliceName" : "OBDSPostOPKompl",
      "min" : 0,
      "max" : "1",
      "mustSupport" : true,
      "binding" : {
        "strength" : "required",
        "valueSet" : "https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/ValueSet/mii-vs-onko-prostata-postsurgical-complications"
      }
    },
    {
      "id" : "Observation.value[x].coding:OBDSPostOPKompl.system",
      "path" : "Observation.value[x].coding.system",
      "min" : 1,
      "patternUri" : "https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/CodeSystem/mii-cs-onko-prostata-postsurgical-complications"
    },
    {
      "id" : "Observation.method",
      "path" : "Observation.method",
      "patternCodeableConcept" : {
        "coding" : [{
          "system" : "http://snomed.info/sct",
          "code" : "789278003",
          "display" : "Clavien-Dindo classification (assessment scale)"
        }]
      }
    },
    {
      "id" : "Observation.specimen",
      "path" : "Observation.specimen",
      "mustSupport" : true
    }]
  }
}

```
