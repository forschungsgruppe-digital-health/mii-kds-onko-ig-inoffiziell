# MII PR Onkologie Frühere Tumorerkrankung - MII IG Kerndatensatz-Modul Onkologie v2026.0.3

* [**Table of Contents**](toc.md)
* [**Artifacts Summary**](artifacts.md)
* **MII PR Onkologie Frühere Tumorerkrankung**

## Resource Profile: MII PR Onkologie Frühere Tumorerkrankung 

| | |
| :--- | :--- |
| *Official URL*:https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-fruehere-tumorerkrankung | *Version*:2026.0.3 |
| Active as of 2026-08-22 | *Computable Name*:MII_PR_Onko_Fruehere_Tumorerkrankung |

 
Dieses Profil beschreibt frühere Tumorerkrankungen, die in der Anamnese zu einem früheren Zeitpunkt diagnostiziert/behandelt wurden. Basiert auf FHIR Condition, da historische Daten oft nur als Freitext vorliegen. 

This profile describes previous tumour diseases that were diagnosed or treated at an earlier point in the patient history. It is based on the FHIR Condition resource, because historical anamnestic data are frequently available as free text only.

### Distinction from the primary tumour diagnosis

In contrast to the profile "Diagnose Primärtumor" (MII_PR_Onko_Diagnose_Primaertumor), which describes the current oncological disease, this profile serves to record **previous** tumour diseases from the patient history.

**Key differences:**

* **Data source**: previous tumour diseases often originate from free-text entries in the patient history, whereas the primary tumour diagnosis is based on current diagnostic findings
* **Coding requirements**: code.text is mandatory, ICD-10-GM coding is optional (mandatory for the primary tumour)
* **Base profile**: based on FHIR Condition (not on MII Diagnose), in order to allow flexible free-text recording
* **Level of detail**: reduced requirements regarding diagnostic confirmation, topography and further details

### Usage notes

#### Mandatory data

* **code.text**: textual description of the previous tumour disease (e.g. "Hautkrebs am Rücken, ca. 2010")
* **category**: categorisation as an oncological diagnosis (SNOMED CT: 394593009 "Medical oncology")
* **subject**: reference to the patient

#### Optional data

* **code.coding[icd10-gm]**: ICD-10-GM coding, if it can be determined retrospectively
* **bodySite.coding[icd-o-3]**: ICD-O-3 topography, if known
* **extension[assertedDate]**: date of diagnosis of the previous tumour disease
* **clinicalStatus**: current clinical status (e.g. resolved, remission)
* **verificationStatus**: verification status (e.g. confirmed, unconfirmed)
* **note**: additional information on the previous tumour disease

### Mapping to oBDS 5.9

The profile represents the oBDS requirement for "Frühere Tumorerkrankungen" (section 5.9):

| | | |
| :--- | :--- | :--- |
| Frühere Tumorerkrankung Beschreibung | code.text | Mandatory field |
| Frühere Tumorerkrankung ICD-10-GM Code | code.coding[icd10-gm].code | Optional |
| Frühere Tumorerkrankung ICD-10-GM Version | code.coding[icd10-gm].version | Optional |
| Frühere Tumorerkrankung Diagnosedatum | extension[assertedDate].valueDateTime | Optional |
| Frühere Tumorerkrankung ICD-O-3 Topographie | bodySite.coding[icd-o-3].code | Optional |

### Examples

**Example 1: with ICD-10-GM coding**

```
Code.text: "Mamma-Ca, links"
Code.coding[icd10-gm]: C50.9 (ICD-10-GM 2013)
BodySite.coding[icd-o-3]: C50.9 "Breast, NOS"
Extension[assertedDate]: 2013
ClinicalStatus: resolved

```

**Example 2: free text only (typical anamnestic entry)**

```
Code.text: "Hautkrebs am Rücken, ca. 2010"
Extension[assertedDate]: 2010
ClinicalStatus: resolved
Note: "Patient berichtet von operativ entferntem Hautkrebs vor ca. 14 Jahren"

```

Complete examples are available in the instances:

* `mii-exa-onko-fruehere-tumorerkrankung-cervix` - Cervix-Ca in situ
* `mii-exa-onko-fruehere-tumorerkrankung-mamma` - Mammakarzinom
* `mii-exa-onko-fruehere-tumorerkrankung-prostata` - Prostatakarzinom
* `mii-exa-onko-fruehere-tumorerkrankung-freetext` - free text only, without ICD coding

### Conformance

The profile is compatible with the FHIR Condition resource R4.

**Search parameters**

The following search parameters are relevant for the profile Frühere Tumorerkrankung, also in combination:

1. The search parameter "_id" SHALL be supported:Examples:`GET [base]/Condition?_id=12345`Usage notes: Further information on searching by "_id" is available in the [FHIR base specification — section "Parameters for all resources"](http://hl7.org/fhir/R4/search.html#all).
1. The search parameter "_profile" SHALL be supported:Examples:`GET [base]/Condition?_profile=https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-fruehere-tumorerkrankung`Usage notes: Further information on searching by "_profile" is available in the [FHIR base specification — section "Parameters for all resources"](http://hl7.org/fhir/R4/search.html#all).
1. The search parameter "code" SHALL be supported:Examples:`GET [base]/Condition?code=http://fhir.de/CodeSystem/bfarm/icd-10-gm|C50.9`Usage notes: Further information on searching by "Condition.code" is available in the [FHIR base specification — section "Token Search"](http://hl7.org/fhir/R4/search.html#token).
1. The search parameter "subject" SHALL be supported:Examples:`GET [base]/Condition?subject=Patient/test`Usage notes: Further information on searching by "Condition.subject" is available in the [FHIR base specification — section "reference"](http://hl7.org/fhir/R4/search.html#reference).
1. The search parameter "patient" SHALL be supported:Examples:`GET [base]/Condition?patient=Patient/test`Usage notes: Further information on searching by "Condition.subject" is available in the [FHIR base specification — section "reference"](http://hl7.org/fhir/R4/search.html#reference).
1. The search parameter "body-site" SHALL be supported:Examples:`GET [base]/Condition?body-site=http://terminology.hl7.org/CodeSystem/icd-o-3|C50.9`Usage notes: Further information on searching by "Condition.bodySite" is available in the [FHIR base specification — section "token"](http://hl7.org/fhir/R4/search.html#token).
1. The search parameter "clinical-status" SHALL be supported:Examples:`GET [base]/Condition?clinical-status=resolved`Usage notes: Further information on searching by "Condition.clinicalStatus" is available in the [FHIR base specification — section "token"](http://hl7.org/fhir/R4/search.html#token).

**Usages:**

* Refer to this Profile: [MII PR Onkologie Diagnose Primärtumor](StructureDefinition-mii-pr-onko-diagnose-primaertumor.md)
* Examples for this Profile: [Condition/mii-exa-onko-fruehere-tumorerkrankung-cervix](Condition-mii-exa-onko-fruehere-tumorerkrankung-cervix.md), [Condition/mii-exa-onko-fruehere-tumorerkrankung-freetext](Condition-mii-exa-onko-fruehere-tumorerkrankung-freetext.md), [Condition/mii-exa-onko-fruehere-tumorerkrankung-mamma](Condition-mii-exa-onko-fruehere-tumorerkrankung-mamma.md) and [Condition/mii-exa-onko-fruehere-tumorerkrankung-prostata](Condition-mii-exa-onko-fruehere-tumorerkrankung-prostata.md)
* CapabilityStatements using this Profile: [MII CPS Onkology CapabilityStatement](CapabilityStatement-mii-cps-onko-capabilitystatement.md)

You can also check for [usages in the FHIR IG Statistics](https://packages2.fhir.org/xig/resource/de.medizininformatikinitiative.kerndatensatz.onkologie|current/StructureDefinition/StructureDefinition-mii-pr-onko-fruehere-tumorerkrankung.json)

### Formal Views of Profile Content

 [Description of Profiles, Differentials, Snapshots, and their representations](http://build.fhir.org/ig/FHIR/ig-guidance/readingIgs.html#structure-definitions). 

 

Other representations of profile: [CSV](../StructureDefinition-mii-pr-onko-fruehere-tumorerkrankung.csv), [Excel](../StructureDefinition-mii-pr-onko-fruehere-tumorerkrankung.xlsx), [Schematron](../StructureDefinition-mii-pr-onko-fruehere-tumorerkrankung.sch) 



## Resource Content

```json
{
  "resourceType" : "StructureDefinition",
  "id" : "mii-pr-onko-fruehere-tumorerkrankung",
  "url" : "https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-fruehere-tumorerkrankung",
  "version" : "2026.0.3",
  "name" : "MII_PR_Onko_Fruehere_Tumorerkrankung",
  "title" : "MII PR Onkologie Frühere Tumorerkrankung",
  "_title" : {
    "extension" : [{
      "extension" : [{
        "url" : "lang",
        "valueCode" : "de-DE"
      },
      {
        "url" : "content",
        "valueString" : "Frühere Tumorerkrankung"
      }],
      "url" : "http://hl7.org/fhir/StructureDefinition/translation"
    }]
  },
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
  "description" : "Dieses Profil beschreibt frühere Tumorerkrankungen, die in der Anamnese zu einem früheren Zeitpunkt diagnostiziert/behandelt wurden. Basiert auf FHIR Condition, da historische Daten oft nur als Freitext vorliegen.",
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
  "type" : "Condition",
  "baseDefinition" : "http://hl7.org/fhir/StructureDefinition/Condition",
  "derivation" : "constraint",
  "differential" : {
    "element" : [{
      "id" : "Condition",
      "path" : "Condition",
      "mapping" : [{
        "identity" : "oBDS",
        "map" : "5.9",
        "comment" : "Frühere Tumorerkrankungen"
      }]
    },
    {
      "id" : "Condition.meta.profile",
      "path" : "Condition.meta.profile",
      "mustSupport" : true
    },
    {
      "id" : "Condition.extension",
      "path" : "Condition.extension",
      "slicing" : {
        "discriminator" : [{
          "type" : "value",
          "path" : "url"
        }],
        "rules" : "open"
      },
      "mustSupport" : true
    },
    {
      "id" : "Condition.extension:assertedDate",
      "path" : "Condition.extension",
      "sliceName" : "assertedDate",
      "short" : "Diagnosedatum der früheren Tumorerkrankung",
      "definition" : "Datum der früheren Tumorerkrankung",
      "min" : 0,
      "max" : "1",
      "type" : [{
        "code" : "Extension",
        "profile" : ["http://hl7.org/fhir/StructureDefinition/condition-assertedDate"]
      }],
      "mustSupport" : true
    },
    {
      "id" : "Condition.extension:assertedDate.value[x]",
      "path" : "Condition.extension.value[x]",
      "mapping" : [{
        "identity" : "oBDS",
        "map" : "5.9",
        "comment" : "Frühere Tumorerkrankung Diagnosedatum"
      }]
    },
    {
      "id" : "Condition.extension:morphology-behavior-icdo3",
      "path" : "Condition.extension",
      "sliceName" : "morphology-behavior-icdo3",
      "short" : "ICD-O-Morphologie",
      "definition" : "Morphologie der früheren Tumorerkrankung nach ICD-O-3",
      "min" : 0,
      "max" : "1",
      "type" : [{
        "code" : "Extension",
        "profile" : ["https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-ex-onko-histology-morphology-behavior-icdo3"]
      }],
      "mustSupport" : true
    },
    {
      "id" : "Condition.clinicalStatus",
      "path" : "Condition.clinicalStatus",
      "mustSupport" : true,
      "binding" : {
        "strength" : "required",
        "valueSet" : "http://hl7.org/fhir/ValueSet/condition-clinical"
      }
    },
    {
      "id" : "Condition.verificationStatus",
      "path" : "Condition.verificationStatus",
      "mustSupport" : true,
      "binding" : {
        "strength" : "required",
        "valueSet" : "http://hl7.org/fhir/ValueSet/condition-ver-status"
      }
    },
    {
      "id" : "Condition.category",
      "path" : "Condition.category",
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
      "id" : "Condition.category:oncology",
      "path" : "Condition.category",
      "sliceName" : "oncology",
      "short" : "Kategorisierung als onkologische Diagnose",
      "_short" : {
        "extension" : [{
          "extension" : [{
            "url" : "lang",
            "valueCode" : "de-DE"
          },
          {
            "url" : "content",
            "valueString" : "Kategorisierung als onkologische Diagnose"
          }],
          "url" : "http://hl7.org/fhir/StructureDefinition/translation"
        }]
      },
      "min" : 1,
      "max" : "1",
      "patternCodeableConcept" : {
        "coding" : [{
          "system" : "http://snomed.info/sct",
          "code" : "394593009",
          "display" : "Medical oncology (qualifier value)"
        }]
      },
      "mustSupport" : true
    },
    {
      "id" : "Condition.code",
      "path" : "Condition.code",
      "min" : 1,
      "mustSupport" : true
    },
    {
      "id" : "Condition.code.coding",
      "path" : "Condition.code.coding",
      "slicing" : {
        "discriminator" : [{
          "type" : "pattern",
          "path" : "system"
        }],
        "rules" : "open"
      }
    },
    {
      "id" : "Condition.code.coding:icd10-gm",
      "path" : "Condition.code.coding",
      "sliceName" : "icd10-gm",
      "short" : "ICD-10-GM Kodierung (optional)",
      "definition" : "ICD-10-GM Kodierung der früheren Tumorerkrankung, falls verfügbar",
      "min" : 0,
      "max" : "1",
      "mustSupport" : true
    },
    {
      "id" : "Condition.code.coding:icd10-gm.system",
      "path" : "Condition.code.coding.system",
      "min" : 1,
      "patternUri" : "http://fhir.de/CodeSystem/bfarm/icd-10-gm",
      "mustSupport" : true
    },
    {
      "id" : "Condition.code.coding:icd10-gm.version",
      "path" : "Condition.code.coding.version",
      "min" : 1,
      "mustSupport" : true,
      "mapping" : [{
        "identity" : "oBDS",
        "map" : "5.9",
        "comment" : "Frühere Tumorerkrankung ICD-10-GM Version"
      }]
    },
    {
      "id" : "Condition.code.coding:icd10-gm.code",
      "path" : "Condition.code.coding.code",
      "min" : 1,
      "mustSupport" : true,
      "mapping" : [{
        "identity" : "oBDS",
        "map" : "5.9",
        "comment" : "Frühere Tumorerkrankung ICD-10-GM Code"
      }]
    },
    {
      "id" : "Condition.code.text",
      "path" : "Condition.code.text",
      "short" : "Textuelle Beschreibung der früheren Tumorerkrankung (Pflichtfeld)",
      "definition" : "Freitextbeschreibung der früheren Tumorerkrankung",
      "min" : 1,
      "mustSupport" : true,
      "mapping" : [{
        "identity" : "oBDS",
        "map" : "5.9",
        "comment" : "Frühere Tumorerkrankung Beschreibung"
      }]
    },
    {
      "id" : "Condition.bodySite",
      "path" : "Condition.bodySite",
      "max" : "1",
      "mustSupport" : true
    },
    {
      "id" : "Condition.bodySite.coding",
      "path" : "Condition.bodySite.coding",
      "slicing" : {
        "discriminator" : [{
          "type" : "pattern",
          "path" : "system"
        }],
        "rules" : "open"
      }
    },
    {
      "id" : "Condition.bodySite.coding:icd-o-3",
      "path" : "Condition.bodySite.coding",
      "sliceName" : "icd-o-3",
      "short" : "ICD-O-3 Topographie",
      "definition" : "Anatomische Lokalisation nach ICD-O-3",
      "min" : 0,
      "max" : "1",
      "mustSupport" : true
    },
    {
      "id" : "Condition.bodySite.coding:icd-o-3.system",
      "path" : "Condition.bodySite.coding.system",
      "min" : 1,
      "patternUri" : "http://terminology.hl7.org/CodeSystem/icd-o-3",
      "mustSupport" : true
    },
    {
      "id" : "Condition.bodySite.coding:icd-o-3.code",
      "path" : "Condition.bodySite.coding.code",
      "min" : 1,
      "mustSupport" : true,
      "binding" : {
        "strength" : "required",
        "valueSet" : "https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/ValueSet/mii-vs-onko-icdo3-topographie"
      },
      "mapping" : [{
        "identity" : "oBDS",
        "map" : "5.9",
        "comment" : "Frühere Tumorerkrankung ICD-O-3 Topographie"
      }]
    },
    {
      "id" : "Condition.subject",
      "path" : "Condition.subject",
      "type" : [{
        "code" : "Reference",
        "targetProfile" : ["http://hl7.org/fhir/StructureDefinition/Patient"]
      }],
      "mustSupport" : true
    },
    {
      "id" : "Condition.encounter",
      "path" : "Condition.encounter",
      "mustSupport" : true
    },
    {
      "id" : "Condition.recordedDate",
      "path" : "Condition.recordedDate",
      "mustSupport" : true
    },
    {
      "id" : "Condition.note",
      "path" : "Condition.note",
      "mustSupport" : true
    }]
  }
}

```
