# MII PR Onkologie Abstand Circumferelle Resektionsebene - MII IG Kerndatensatz-Modul Onkologie v2026.0.3

* [**Table of Contents**](toc.md)
* [**Artifacts Summary**](artifacts.md)
* **MII PR Onkologie Abstand Circumferelle Resektionsebene**

## Resource Profile: MII PR Onkologie Abstand Circumferelle Resektionsebene 

| | |
| :--- | :--- |
| *Official URL*:https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-krk-abstand-circumferelle-resektionsebene | *Version*:2026.0.3 |
| Active as of 2026-08-22 | *Computable Name*:MII_PR_Onko_KRK_Abstand_Circumferelle_Resektionsebene |

 
Dieses Profil beschreibt den minimalen Abstand des Tumorrandes zur circumferellen Dissektionlinie beim Kolorektalen Karzinom 

This profile describes the minimum distance from the tumour margin to the circumferential resection plane in colorectal cancer according to oBDS KR3. This measurement is an important prognostic factor and is determined both macroscopically and microscopically. A small circumferential resection margin is associated with an increased risk of local recurrence.

The profile is based on a FHIR Observation resource and uses a dedicated ValueSet to distinguish between macroscopic and microscopic assessment. The distance is given as a Quantity value in millimetres.

### Links to other resources

The circumferential resection margin measurement is an important pathological observation:

* references the primary diagnosis (MII_PR_Onko_Diagnose_Primaertumor) via `Observation.focus`
* references the patient (Patient resource) via `Observation.subject`
* can be linked to a specific encounter via `Observation.encounter`

### oBDS context

The distance measurement corresponds to the oBDS data field KR3 "Minimaler Abstand des Tumorrandes zur circumferellen Resektionsebene" and is documented in millimetres. The distinction between macroscopic and microscopic assessment is represented by the corresponding ValueSet.

### Terminology binding

The ValueSet for the circumferential resection plane is bound as **extensible** and distinguishes between the macroscopic and the microscopic assessment of the resection margins.

* ValueSet: MII VS Onko KRK Abstand Circumferelle Resektionsrand

### Search parameters

The following search parameters are relevant for the KRK-Circumferelle-Resektionsebene profile, including in combination:

* The search parameter `_id` MUST be supported: `GET [base]/Observation?_id=12345`
* The search parameter `_profile` MUST be supported: `GET [base]/Observation?_profile=https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-krk-abstand-circumferelle-resektionsebene`
* The search parameter `code` MUST be supported: `GET [base]/Observation?code=https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/CodeSystem/mii-cs-onko-krk-abstand-circumferelle-resektionsebene|makroskopisch`
* The search parameter `subject` MUST be supported: `GET [base]/Observation?subject=Patient/test`
* The search parameter `focus` MUST be supported: `GET [base]/Observation?focus=Condition/primaertumor`
* The search parameter `value-quantity` MUST be supported: `GET [base]/Observation?value-quantity=2|http://unitsofmeasure.org|mm`

**Usages:**

* Examples for this Profile: [Observation/mii-exa-onko-krk-abstand-circumferelle-resektionsebene](Observation-mii-exa-onko-krk-abstand-circumferelle-resektionsebene.md)
* CapabilityStatements using this Profile: [MII CPS Onkology CapabilityStatement](CapabilityStatement-mii-cps-onko-capabilitystatement.md)

You can also check for [usages in the FHIR IG Statistics](https://packages2.fhir.org/xig/resource/de.medizininformatikinitiative.kerndatensatz.onkologie|current/StructureDefinition/StructureDefinition-mii-pr-onko-krk-abstand-circumferelle-resektionsebene.json)

### Formal Views of Profile Content

 [Description of Profiles, Differentials, Snapshots, and their representations](http://build.fhir.org/ig/FHIR/ig-guidance/readingIgs.html#structure-definitions). 

 

Other representations of profile: [CSV](../StructureDefinition-mii-pr-onko-krk-abstand-circumferelle-resektionsebene.csv), [Excel](../StructureDefinition-mii-pr-onko-krk-abstand-circumferelle-resektionsebene.xlsx), [Schematron](../StructureDefinition-mii-pr-onko-krk-abstand-circumferelle-resektionsebene.sch) 



## Resource Content

```json
{
  "resourceType" : "StructureDefinition",
  "id" : "mii-pr-onko-krk-abstand-circumferelle-resektionsebene",
  "url" : "https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-krk-abstand-circumferelle-resektionsebene",
  "version" : "2026.0.3",
  "name" : "MII_PR_Onko_KRK_Abstand_Circumferelle_Resektionsebene",
  "title" : "MII PR Onkologie Abstand Circumferelle Resektionsebene",
  "status" : "active",
  "date" : "2026-08-22T22:31:14+00:00",
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
  "description" : "Dieses Profil beschreibt den minimalen Abstand des Tumorrandes zur circumferellen Dissektionlinie beim Kolorektalen Karzinom",
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
      "short" : "Minimaler Abstand Tumorrand circumferell - makroskopisch oder mikroskopisch",
      "definition" : "Minimaler Abstand des Tumorrandes zum circumferellen Resektionsrand in mm., gemäß oBDS 2021 KR3 - makroskopisch oder mikroskopisch",
      "mustSupport" : true
    },
    {
      "id" : "Observation.code.coding",
      "path" : "Observation.code.coding",
      "binding" : {
        "strength" : "extensible",
        "valueSet" : "https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/ValueSet/mii-vs-onko-krk-abstand-circumferelle-resektionsrand"
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
      "short" : "Datum der Untersuchung",
      "_short" : {
        "extension" : [{
          "extension" : [{
            "url" : "lang",
            "valueCode" : "de-DE"
          },
          {
            "url" : "content",
            "valueString" : "Datum der Untersuchung"
          }],
          "url" : "http://hl7.org/fhir/StructureDefinition/translation"
        }]
      },
      "definition" : "Datum der Untersuchung",
      "_definition" : {
        "extension" : [{
          "extension" : [{
            "url" : "lang",
            "valueCode" : "de-DE"
          },
          {
            "url" : "content",
            "valueString" : "Datum der Untersuchung"
          }],
          "url" : "http://hl7.org/fhir/StructureDefinition/translation"
        }]
      },
      "type" : [{
        "code" : "dateTime"
      }],
      "mustSupport" : true
    },
    {
      "id" : "Observation.value[x]",
      "path" : "Observation.value[x]",
      "short" : "Minimaler Abstand Tumorrand aboral",
      "_short" : {
        "extension" : [{
          "extension" : [{
            "url" : "lang",
            "valueCode" : "de-DE"
          },
          {
            "url" : "content",
            "valueString" : "Minimaler Abstand Tumorrand circumferell"
          }],
          "url" : "http://hl7.org/fhir/StructureDefinition/translation"
        }]
      },
      "definition" : "Minimaler Abstand des aboralen Tumorrandes zum aboralen Resektionsrand in mm. gemäß oBDS 2021 KR2",
      "_definition" : {
        "extension" : [{
          "extension" : [{
            "url" : "lang",
            "valueCode" : "de-DE"
          },
          {
            "url" : "content",
            "valueString" : "Minimaler Abstand des aboralen Tumorrandes zum aboralen Resektionsrand in mm. gemäß oBDS 2021 KR2"
          }],
          "url" : "http://hl7.org/fhir/StructureDefinition/translation"
        }]
      },
      "type" : [{
        "code" : "Quantity"
      }],
      "mustSupport" : true
    },
    {
      "id" : "Observation.value[x].value",
      "path" : "Observation.value[x].value",
      "min" : 1,
      "mustSupport" : true
    },
    {
      "id" : "Observation.value[x].unit",
      "path" : "Observation.value[x].unit",
      "min" : 1,
      "patternString" : "mm",
      "mustSupport" : true
    },
    {
      "id" : "Observation.value[x].system",
      "path" : "Observation.value[x].system",
      "min" : 1,
      "fixedUri" : "http://unitsofmeasure.org",
      "mustSupport" : true
    },
    {
      "id" : "Observation.value[x].code",
      "path" : "Observation.value[x].code",
      "min" : 1,
      "patternCode" : "mm",
      "mustSupport" : true
    }]
  }
}

```
