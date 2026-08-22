# MII PR Onkologie Grading - MII IG Kerndatensatz-Modul Onkologie v2026.0.3

* [**Table of Contents**](toc.md)
* [**Artifacts Summary**](artifacts.md)
* **MII PR Onkologie Grading**

## Resource Profile: MII PR Onkologie Grading 

| | |
| :--- | :--- |
| *Official URL*:https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-grading | *Version*:2026.0.3 |
| Active as of 2026-08-22 | *Computable Name*:MII_PR_Onko_Grading |

 
Histologie: Tumor Grading. Gibt den Differenzierungsgrad des Tumors entsprechend der aktuellen TNM-Auflage an. 

This profile describes a histology grading in oncology. It assesses in particular the morphological dedifferentiation of the tissue.

**Search parameters**

The following search parameters are relevant for the Onkologie module, also in combination:

1. The search parameter `_id` SHALL be supported:Examples:`GET [base]/Observation?_id=1234`Usage notes: Further information on searching by "_id" is available in the [FHIR base specification — section "Parameters for all resources"](http://hl7.org/fhir/R4/search.html#all).
1. The search parameter "_profile" SHALL be supported:Examples:`GET [base]/Observation?_profile=https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-grading`Usage notes: Further information on searching by "_profile" is available in the [FHIR base specification — section "token"](http://hl7.org/fhir/R4/search.html#all).
1. The search parameter "category" SHALL be supported:Examples:`GET [base]/Observation?category=http://terminology.hl7.org/CodeSystem/observation-category|laboratory`Usage notes: Further information on searching by "category" is available in the FHIR base specification — section "token".
1. The search parameter "code" SHALL be supported:Examples:`GET [base]/Observation?code=http://fhir.de/CodeSystem/sct|184305005`Usage notes: Further information on searching by "code" is available in the FHIR base specification — section "token".
1. The search parameter "subject" SHALL be supported:Examples:`GET [base]/Observation?subject=Patient/example`Usage notes: Further information on searching by "subject" is available in the FHIR base specification — section "reference".
1. The search parameter "focus" SHALL be supported:Examples:`GET [base]/Observation?focus=Condition/example`Usage notes: Further information on searching by "focus" is available in the FHIR base specification — section "reference".
1. The search parameter "encounter" SHALL be supported:Examples:`GET [base]/Observation?encounter=Encounter/example`Usage notes: Further information on searching by "encounter" is available in the FHIR base specification — section "reference".
1. The search parameter "date" SHALL be supported:Examples:`GET [base]/Observation?date=2024-02-08`Usage notes: Further information on searching by "date" is available in the FHIR base specification — section "date".
1. The search parameter "derived-from" SHALL be supported:Examples:`GET [base]/Observation?derived-from=Observation/example`Usage notes: Further information on searching by "derived-from" is available in the FHIR base specification — section "reference".

**Usages:**

* Examples for this Profile: [Observation/mii-exa-onko-grading-1](Observation-mii-exa-onko-grading-1.md)
* CapabilityStatements using this Profile: [MII CPS Onkology CapabilityStatement](CapabilityStatement-mii-cps-onko-capabilitystatement.md)

You can also check for [usages in the FHIR IG Statistics](https://packages2.fhir.org/xig/resource/de.medizininformatikinitiative.kerndatensatz.onkologie|current/StructureDefinition/StructureDefinition-mii-pr-onko-grading.json)

### Formal Views of Profile Content

 [Description of Profiles, Differentials, Snapshots, and their representations](http://build.fhir.org/ig/FHIR/ig-guidance/readingIgs.html#structure-definitions). 

 

Other representations of profile: [CSV](../StructureDefinition-mii-pr-onko-grading.csv), [Excel](../StructureDefinition-mii-pr-onko-grading.xlsx), [Schematron](../StructureDefinition-mii-pr-onko-grading.sch) 



## Resource Content

```json
{
  "resourceType" : "StructureDefinition",
  "id" : "mii-pr-onko-grading",
  "url" : "https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-grading",
  "version" : "2026.0.3",
  "name" : "MII_PR_Onko_Grading",
  "title" : "MII PR Onkologie Grading",
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
  "description" : "Histologie: Tumor Grading. Gibt den Differenzierungsgrad des Tumors entsprechend der aktuellen TNM-Auflage an.",
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
      "id" : "Observation.category",
      "path" : "Observation.category",
      "slicing" : {
        "discriminator" : [{
          "type" : "pattern",
          "path" : "$this"
        }],
        "rules" : "open"
      },
      "min" : 1,
      "mustSupport" : true
    },
    {
      "id" : "Observation.category:laboratory",
      "path" : "Observation.category",
      "sliceName" : "laboratory",
      "min" : 1,
      "max" : "*",
      "patternCodeableConcept" : {
        "coding" : [{
          "system" : "http://terminology.hl7.org/CodeSystem/observation-category",
          "code" : "laboratory"
        }]
      },
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
      "slicing" : {
        "discriminator" : [{
          "type" : "pattern",
          "path" : "$this"
        }],
        "rules" : "open"
      },
      "min" : 1,
      "mustSupport" : true
    },
    {
      "id" : "Observation.code.coding:loinc",
      "path" : "Observation.code.coding",
      "sliceName" : "loinc",
      "min" : 1,
      "max" : "*",
      "patternCoding" : {
        "system" : "http://loinc.org",
        "code" : "33732-9"
      },
      "mustSupport" : true
    },
    {
      "id" : "Observation.code.coding:loinc.system",
      "path" : "Observation.code.coding.system",
      "min" : 1,
      "mustSupport" : true
    },
    {
      "id" : "Observation.code.coding:loinc.code",
      "path" : "Observation.code.coding.code",
      "min" : 1,
      "mustSupport" : true
    },
    {
      "id" : "Observation.code.coding:snomed",
      "path" : "Observation.code.coding",
      "sliceName" : "snomed",
      "min" : 0,
      "max" : "*",
      "patternCoding" : {
        "system" : "http://snomed.info/sct",
        "code" : "371469007"
      }
    },
    {
      "id" : "Observation.code.coding:snomed.system",
      "path" : "Observation.code.coding.system",
      "min" : 1
    },
    {
      "id" : "Observation.code.coding:snomed.code",
      "path" : "Observation.code.coding.code",
      "min" : 1
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
      "min" : 1,
      "type" : [{
        "code" : "dateTime"
      }],
      "mustSupport" : true
    },
    {
      "id" : "Observation.value[x]",
      "path" : "Observation.value[x]",
      "min" : 1,
      "type" : [{
        "code" : "CodeableConcept"
      }],
      "mustSupport" : true,
      "binding" : {
        "strength" : "required",
        "valueSet" : "https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/ValueSet/mii-vs-onko-grading"
      }
    },
    {
      "id" : "Observation.value[x].coding",
      "path" : "Observation.value[x].coding",
      "short" : "Histologisches Grading",
      "_short" : {
        "extension" : [{
          "extension" : [{
            "url" : "lang",
            "valueCode" : "de-DE"
          },
          {
            "url" : "content",
            "valueString" : "Histologisches Grading"
          }],
          "url" : "http://hl7.org/fhir/StructureDefinition/translation"
        }]
      },
      "definition" : "Histologisches Grading nach 6.6 oBDS 2021",
      "_definition" : {
        "extension" : [{
          "extension" : [{
            "url" : "lang",
            "valueCode" : "de-DE"
          },
          {
            "url" : "content",
            "valueString" : "Histologisches Grading nach 6.6 oBDS 2021"
          }],
          "url" : "http://hl7.org/fhir/StructureDefinition/translation"
        }]
      }
    },
    {
      "id" : "Observation.value[x].coding.system",
      "path" : "Observation.value[x].coding.system",
      "min" : 1,
      "mustSupport" : true
    },
    {
      "id" : "Observation.value[x].coding.code",
      "path" : "Observation.value[x].coding.code",
      "min" : 1,
      "mustSupport" : true,
      "mapping" : [{
        "identity" : "oBDS",
        "map" : "6.6",
        "comment" : "Grading"
      }]
    }]
  }
}

```
