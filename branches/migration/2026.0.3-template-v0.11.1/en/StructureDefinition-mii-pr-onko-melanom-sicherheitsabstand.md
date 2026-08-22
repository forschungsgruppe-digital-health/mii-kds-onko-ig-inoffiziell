# MII PR Onkologie Melanom Sicherheitsabstand - MII IG Kerndatensatz-Modul Onkologie v2026.0.3

* [**Table of Contents**](toc.md)
* [**Artifacts Summary**](artifacts.md)
* **MII PR Onkologie Melanom Sicherheitsabstand**

## Resource Profile: MII PR Onkologie Melanom Sicherheitsabstand 

| | |
| :--- | :--- |
| *Official URL*:https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-melanom-sicherheitsabstand | *Version*:2026.0.3 |
| Active as of 2026-08-22 | *Computable Name*:MII_PR_Onko_Melanom_Sicherheitsabstand |

 
Dieses Profil beschreibt den minimalen Sicherheitsabstand zum Primärtumor beim Malignen Melanom basierend auf oBDS Feld MM1. Bei nicht beurteilbaren Fällen (oBDS Wert -1) wird dataAbsentReason verwendet statt valueQuantity. 

This profile describes the minimum safety margin to the primary tumour in malignant melanoma according to oBDS MM1. This measurement is taken after the definitive surgical intervention and gives the minimum distance from the melanoma to the nearest lateral surgical resection margin in the excision specimen. A value of 0 corresponds to a local R1 or R2 resection status.

The profile is based on a FHIR Observation resource and uses SNOMED CT for the standardised coding of the safety margin measurement. The distance is given as a Quantity value in millimetres (mm).

### Links to other resources

The safety margin measurement is an important surgical observation in melanoma:

* references the primary diagnosis (MII_PR_Onko_Diagnose_Primaertumor) via `Observation.focus`
* references the patient (Patient resource) via `Observation.subject`
* can be linked to a specific encounter via `Observation.encounter`

### oBDS context

The safety margin measurement corresponds to the oBDS data field MM1 "Minimaler Sicherheitsabstand zum Primärtumor" and is documented in millimetres. This measurement is essential for assessing the completeness of the tumour resection and the prognosis in melanoma.

**Note on coding cases that cannot be assessed:** According to oBDS, the safety margin can take the following values:

* **-1**: cannot be assessed -> in FHIR, `dataAbsentReason` is used (e.g. "unknown" or "not-asked") instead of `valueQuantity`
* **0**: no safety margin (R1/R2 resection) -> `valueQuantity.value = 0`
* **n**: safety margin in mm -> `valueQuantity.value = n`

The profile contains an invariant which ensures that either `valueQuantity` or `dataAbsentReason` must be present.

### Terminology binding

The profile uses SNOMED CT code 396511007 "Distance of in situ melanoma from closest lateral surgical margin in excised specimen of skin (observable entity)" for the standardised coding of the safety margin measurement. The value is given as a UCUM-conformant Quantity in millimetres (mm).

### Search parameters

The following search parameters are relevant for the Melanom-Sicherheitsabstand profile, including in combination:

* The search parameter `_id` MUST be supported: `GET [base]/Observation?_id=12345`
* The search parameter `_profile` MUST be supported: `GET [base]/Observation?_profile=https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-melanom-sicherheitsabstand`
* The search parameter `code` MUST be supported: `GET [base]/Observation?code=http://snomed.info/sct|396511007`
* The search parameter `subject` MUST be supported: `GET [base]/Observation?subject=Patient/test`
* The search parameter `focus` MUST be supported: `GET [base]/Observation?focus=Condition/primaertumor`
* The search parameter `value-quantity` MUST be supported: `GET [base]/Observation?value-quantity=5|http://unitsofmeasure.org|mm`

**Usages:**

* Examples for this Profile: [Observation/mii-exa-onko-melanom-sicherheitsabstand](Observation-mii-exa-onko-melanom-sicherheitsabstand.md)
* CapabilityStatements using this Profile: [MII CPS Onkology CapabilityStatement](CapabilityStatement-mii-cps-onko-capabilitystatement.md)

You can also check for [usages in the FHIR IG Statistics](https://packages2.fhir.org/xig/resource/de.medizininformatikinitiative.kerndatensatz.onkologie|current/StructureDefinition/StructureDefinition-mii-pr-onko-melanom-sicherheitsabstand.json)

### Formal Views of Profile Content

 [Description of Profiles, Differentials, Snapshots, and their representations](http://build.fhir.org/ig/FHIR/ig-guidance/readingIgs.html#structure-definitions). 

 

Other representations of profile: [CSV](../StructureDefinition-mii-pr-onko-melanom-sicherheitsabstand.csv), [Excel](../StructureDefinition-mii-pr-onko-melanom-sicherheitsabstand.xlsx), [Schematron](../StructureDefinition-mii-pr-onko-melanom-sicherheitsabstand.sch) 



## Resource Content

```json
{
  "resourceType" : "StructureDefinition",
  "id" : "mii-pr-onko-melanom-sicherheitsabstand",
  "url" : "https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-melanom-sicherheitsabstand",
  "version" : "2026.0.3",
  "name" : "MII_PR_Onko_Melanom_Sicherheitsabstand",
  "title" : "MII PR Onkologie Melanom Sicherheitsabstand",
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
  "description" : "Dieses Profil beschreibt den minimalen Sicherheitsabstand zum Primärtumor beim Malignen Melanom basierend auf oBDS Feld MM1. Bei nicht beurteilbaren Fällen (oBDS Wert -1) wird dataAbsentReason verwendet statt valueQuantity.",
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
      "path" : "Observation",
      "constraint" : [{
        "key" : "mii-onko-melanom-sicherheitsabstand-1",
        "severity" : "error",
        "human" : "Entweder muss valueQuantity oder dataAbsentReason vorhanden sein",
        "expression" : "valueQuantity.exists() or dataAbsentReason.exists()",
        "source" : "https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-melanom-sicherheitsabstand"
      }],
      "mapping" : [{
        "identity" : "oBDS",
        "map" : "MM1",
        "comment" : "Sicherheitsabstand Primärtumor"
      }]
    },
    {
      "id" : "Observation.meta.profile",
      "path" : "Observation.meta.profile",
      "mustSupport" : true
    },
    {
      "id" : "Observation.code",
      "path" : "Observation.code",
      "short" : "Sicherheitsabstand Primärtumor",
      "definition" : "Minimaler Sicherheitsabstand zum Primärtumor beim Malignen Melanom gemäß oBDS MM1",
      "mustSupport" : true
    },
    {
      "id" : "Observation.code.coding",
      "path" : "Observation.code.coding",
      "patternCoding" : {
        "system" : "http://snomed.info/sct",
        "code" : "396511007",
        "display" : "Distance of in situ melanoma from closest lateral surgical margin in excised specimen of skin (observable entity)"
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
      "short" : "Datum der Messung",
      "_short" : {
        "extension" : [{
          "extension" : [{
            "url" : "lang",
            "valueCode" : "de-DE"
          },
          {
            "url" : "content",
            "valueString" : "Datum der Messung"
          }],
          "url" : "http://hl7.org/fhir/StructureDefinition/translation"
        }]
      },
      "definition" : "Datum der Messung des Sicherheitsabstands",
      "_definition" : {
        "extension" : [{
          "extension" : [{
            "url" : "lang",
            "valueCode" : "de-DE"
          },
          {
            "url" : "content",
            "valueString" : "Datum der Messung des Sicherheitsabstands"
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
        "map" : "MM1",
        "comment" : "Datum der Messung des Sicherheitsabstands"
      }]
    },
    {
      "id" : "Observation.value[x]",
      "path" : "Observation.value[x]",
      "short" : "Sicherheitsabstand in mm",
      "_short" : {
        "extension" : [{
          "extension" : [{
            "url" : "lang",
            "valueCode" : "de-DE"
          },
          {
            "url" : "content",
            "valueString" : "Sicherheitsabstand in mm"
          }],
          "url" : "http://hl7.org/fhir/StructureDefinition/translation"
        }]
      },
      "definition" : "Minimaler Sicherheitsabstand zum Primärtumor in mm gemäß oBDS MM1",
      "_definition" : {
        "extension" : [{
          "extension" : [{
            "url" : "lang",
            "valueCode" : "de-DE"
          },
          {
            "url" : "content",
            "valueString" : "Minimaler Sicherheitsabstand zum Primärtumor in mm nach definitivem operativem Eingriff gemäß oBDS MM1. Wert 0 entspricht lokal R1 oder R2 bzw. marginal"
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
      "mustSupport" : true,
      "mapping" : [{
        "identity" : "oBDS",
        "map" : "MM1",
        "comment" : "Minimaler Sicherheitsabstand in mm"
      }]
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
    },
    {
      "id" : "Observation.dataAbsentReason",
      "path" : "Observation.dataAbsentReason",
      "short" : "Grund für fehlende Messung",
      "definition" : "Grund warum der Sicherheitsabstand nicht bestimmt werden konnte (z.B. nicht beurteilbar). Wird verwendet wenn oBDS Wert -1 (nicht beurteilbar) vorliegt.",
      "mustSupport" : true
    }]
  }
}

```
