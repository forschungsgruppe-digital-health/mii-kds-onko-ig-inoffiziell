# MII PR Onkologie Tod - MII IG Kerndatensatz-Modul Onkologie v2026.0.3

* [**Table of Contents**](toc.md)
* [**Artifacts Summary**](artifacts.md)
* **MII PR Onkologie Tod**

## Resource Profile: MII PR Onkologie Tod 

| | |
| :--- | :--- |
| *Official URL*:https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-tod | *Version*:2026.0.3 |
| Active as of 2026-08-22 | *Computable Name*:MII_PR_Onko_Tod |

 
Tumorbedingter Tod 

This profile describes whether and when a patient died as a result of the tumor. It is part of the oBDS cancer registry dataset.

The date of death can also be represented in the MII core dataset via the Patient resource, but was additionally added here as an Observation for reasons of data structure and data cohesion.

Since the version MII-Patient(2024), a cause of death is also present directly in the Patient resource. Unlike the oBDS cause of death, which is recorded using ICD-10-GM, the MII-Patient cause of death refers to ICD-10-WHO.

It contains:

* a reference to Patient
*  

| | |
| :--- | :--- |
| the Observation code "184305005 | Cause of death (observable entity)" (SNOMED-CT) |

 
* the exact date of death
* a coding of the cause of death per ICD-10 GM
* an interpretation of the relationship between the tumor disease and the cause of death

In the oBDS, the death report is transmitted as an independent entity. Because there should be only one death report per patient, the FHIR profiling therefore does not hold a direct link to the primary diagnosis or to the individual follow-up stagings, but exclusively to the patient.

### Search parameters

The following search parameters are relevant for the Onkologie module, also in combination:

1. The search parameter `_id` SHALL be supported:Examples:`GET [base]/Observation?_id=1234`Usage notes: further information on searching by "_id" can be found in the [FHIR base specification, section "Parameters for all resources"](http://hl7.org/fhir/R4/search.html#all).
1. The search parameter "_profile" SHALL be supported:Examples:`GET [base]/Observation?_profile=https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-tod`Usage notes: further information on searching by "_profile" can be found in the [FHIR base specification, section "token"](http://hl7.org/fhir/R4/search.html#all).
1. The search parameter "code" SHALL be supported:Examples:`GET [base]/Observation?code=http://fhir.de/CodeSystem/sct|184305005`Usage notes: further information on searching by "code" can be found in the FHIR base specification, section "token".
1. The search parameter "subject" SHALL be supported:Examples:`GET [base]/Observation?subject=Patient/example`Usage notes: further information on searching by "subject" can be found in the FHIR base specification, section "reference".
1. The search parameter "focus" SHALL be supported:Examples:`GET [base]/Observation?focus=Condition/example`Usage notes: further information on searching by "focus" can be found in the FHIR base specification, section "reference".
1. The search parameter "encounter" SHALL be supported:Examples:`GET [base]/Observation?encounter=Encounter/example`Usage notes: further information on searching by "encounter" can be found in the FHIR base specification, section "reference".
1. The search parameter "date" SHALL be supported:Examples:`GET [base]/Observation?date=2024-02-08`Usage notes: further information on searching by "date" can be found in the FHIR base specification, section "date".
1. The search parameter "interpretation" SHALL be supported:Examples:`GET [base]/Observation?interpretation=http://fhir.de/CodeSystem/icd10gm|C44.3`Usage notes: further information on searching by "interpretation" can be found in the FHIR base specification, section "token".
1. The search parameter "derived-from" SHALL be supported:Examples:`GET [base]/Observation?derived-from=Observation/example`Usage notes: further information on searching by "derived-from" can be found in the FHIR base specification, section "reference".

### Examples

> **Written during migration - review before release.** Three instances in this guide illustrate the profile: `mii-exa-onko-tod-j`, `mii-exa-onko-tod-n` and `mii-exa-onko-tod-u` - one per code (J, N, U) of `mii-cs-onko-tod`, i.e. per interpretation of the relationship between the tumor disease and the cause of death.

**Usages:**

* Examples for this Profile: [Observation/mii-exa-onko-tod-j](Observation-mii-exa-onko-tod-j.md), [Observation/mii-exa-onko-tod-n](Observation-mii-exa-onko-tod-n.md) and [Observation/mii-exa-onko-tod-u](Observation-mii-exa-onko-tod-u.md)
* CapabilityStatements using this Profile: [MII CPS Onkology CapabilityStatement](CapabilityStatement-mii-cps-onko-capabilitystatement.md)

You can also check for [usages in the FHIR IG Statistics](https://packages2.fhir.org/xig/resource/de.medizininformatikinitiative.kerndatensatz.onkologie|current/StructureDefinition/StructureDefinition-mii-pr-onko-tod.json)

### Formal Views of Profile Content

 [Description of Profiles, Differentials, Snapshots, and their representations](http://build.fhir.org/ig/FHIR/ig-guidance/readingIgs.html#structure-definitions). 

 

Other representations of profile: [CSV](../StructureDefinition-mii-pr-onko-tod.csv), [Excel](../StructureDefinition-mii-pr-onko-tod.xlsx), [Schematron](../StructureDefinition-mii-pr-onko-tod.sch) 



## Resource Content

```json
{
  "resourceType" : "StructureDefinition",
  "id" : "mii-pr-onko-tod",
  "url" : "https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-tod",
  "version" : "2026.0.3",
  "name" : "MII_PR_Onko_Tod",
  "title" : "MII PR Onkologie Tod",
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
  "description" : "Tumorbedingter Tod",
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
  },
  {
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
      "mustSupport" : true
    },
    {
      "id" : "Observation.code.coding",
      "path" : "Observation.code.coding",
      "patternCoding" : {
        "system" : "http://snomed.info/sct",
        "code" : "184305005"
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
      "type" : [{
        "code" : "Reference",
        "targetProfile" : ["https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-diagnose-primaertumor"]
      }],
      "mustSupport" : true
    },
    {
      "id" : "Observation.encounter",
      "path" : "Observation.encounter",
      "mustSupport" : true
    },
    {
      "id" : "Observation.effective[x]",
      "path" : "Observation.effective[x]",
      "short" : "Sterbedatum",
      "_short" : {
        "extension" : [{
          "extension" : [{
            "url" : "lang",
            "valueCode" : "de-DE"
          },
          {
            "url" : "content",
            "valueString" : "Sterbedatum"
          }],
          "url" : "http://hl7.org/fhir/StructureDefinition/translation"
        }]
      },
      "definition" : "Sterbedatum gemäß 20.1 oBDS 2021",
      "_definition" : {
        "extension" : [{
          "extension" : [{
            "url" : "lang",
            "valueCode" : "de-DE"
          },
          {
            "url" : "content",
            "valueString" : "Sterbedatum gemäß 20.1 oBDS 2021"
          }],
          "url" : "http://hl7.org/fhir/StructureDefinition/translation"
        }]
      },
      "type" : [{
        "code" : "dateTime"
      }],
      "mustSupport" : true,
      "mapping" : [{
        "identity" : "oBDS",
        "map" : "20.1",
        "comment" : "Sterbedatum"
      }]
    },
    {
      "id" : "Observation.value[x]",
      "path" : "Observation.value[x]",
      "type" : [{
        "code" : "CodeableConcept"
      }],
      "mustSupport" : true,
      "binding" : {
        "strength" : "required",
        "valueSet" : "https://www.medizininformatik-initiative.de/fhir/core/modul-diagnose/ValueSet/mii-vs-diagnose-icd10gm"
      }
    },
    {
      "id" : "Observation.value[x].coding",
      "path" : "Observation.value[x].coding",
      "short" : "Todesursache ICD-10",
      "_short" : {
        "extension" : [{
          "extension" : [{
            "url" : "lang",
            "valueCode" : "de-DE"
          },
          {
            "url" : "content",
            "valueString" : "Todesursache ICD-10"
          }],
          "url" : "http://hl7.org/fhir/StructureDefinition/translation"
        }]
      },
      "definition" : "Todesursache ICD-10 gemäß 20.3 oBDS 2021",
      "_definition" : {
        "extension" : [{
          "extension" : [{
            "url" : "lang",
            "valueCode" : "de-DE"
          },
          {
            "url" : "content",
            "valueString" : "Todesursache ICD-10 gemäß 20.3 oBDS 2021"
          }],
          "url" : "http://hl7.org/fhir/StructureDefinition/translation"
        }]
      }
    },
    {
      "id" : "Observation.value[x].coding.system",
      "path" : "Observation.value[x].coding.system",
      "min" : 1,
      "patternUri" : "http://fhir.de/CodeSystem/bfarm/icd-10-gm",
      "mustSupport" : true
    },
    {
      "id" : "Observation.value[x].coding.version",
      "path" : "Observation.value[x].coding.version",
      "min" : 1,
      "mustSupport" : true,
      "mapping" : [{
        "identity" : "oBDS",
        "map" : "20.4",
        "comment" : "Todesursache ICD-Version "
      }]
    },
    {
      "id" : "Observation.value[x].coding.code",
      "path" : "Observation.value[x].coding.code",
      "min" : 1,
      "mustSupport" : true,
      "mapping" : [{
        "identity" : "oBDS",
        "map" : "20.3",
        "comment" : "Todesursache ICD "
      }]
    },
    {
      "id" : "Observation.interpretation",
      "path" : "Observation.interpretation",
      "mustSupport" : true
    },
    {
      "id" : "Observation.interpretation.coding",
      "path" : "Observation.interpretation.coding",
      "short" : "Sterbedatum",
      "_short" : {
        "extension" : [{
          "extension" : [{
            "url" : "lang",
            "valueCode" : "de-DE"
          },
          {
            "url" : "content",
            "valueString" : "Tod tumorbedingt"
          }],
          "url" : "http://hl7.org/fhir/StructureDefinition/translation"
        }]
      },
      "definition" : "Sterbedatum gemäß 20.1 oBDS 2021",
      "_definition" : {
        "extension" : [{
          "extension" : [{
            "url" : "lang",
            "valueCode" : "de-DE"
          },
          {
            "url" : "content",
            "valueString" : "Tod tumorbedingt gemäß 20.2 oBDS 2021"
          }],
          "url" : "http://hl7.org/fhir/StructureDefinition/translation"
        }]
      },
      "binding" : {
        "strength" : "required",
        "valueSet" : "https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/ValueSet/mii-vs-onko-tod"
      }
    },
    {
      "id" : "Observation.interpretation.coding.system",
      "path" : "Observation.interpretation.coding.system",
      "patternUri" : "https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/CodeSystem/mii-cs-onko-tod",
      "mustSupport" : true
    },
    {
      "id" : "Observation.interpretation.coding.code",
      "path" : "Observation.interpretation.coding.code",
      "mustSupport" : true,
      "mapping" : [{
        "identity" : "oBDS",
        "map" : "20.2",
        "comment" : "Tod tumorbedingt"
      }]
    }]
  }
}

```
