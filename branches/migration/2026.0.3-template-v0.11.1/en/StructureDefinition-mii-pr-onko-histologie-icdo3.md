# MII PR Onkologie Histologie ICD-O-3 - MII IG Kerndatensatz-Modul Onkologie v2026.0.3

* [**Table of Contents**](toc.md)
* [**Artifacts Summary**](artifacts.md)
* **MII PR Onkologie Histologie ICD-O-3**

## Resource Profile: MII PR Onkologie Histologie ICD-O-3 

| | |
| :--- | :--- |
| *Official URL*:https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-histologie-icdo3 | *Version*:2026.0.3 |
| Active as of 2026-08-22 | *Computable Name*:MII_PR_Onko_Histologie_ICDO3 |

 
Histologie-Kodierung nach ICD-0 für die Verwendung von Folgediagnostik. Bei der histologischen Beurteilung des Primärtumors sind die histologischen Informationen direkt über die Condition-Ressource abzubilden. 

This profile describes a histological examination in oncology.

For histologies used to establish the primary diagnosis, the ICD-O-3 codings SHOULD be recorded directly in the primary diagnosis. The present profile is reserved for the case that an ICD-O-3 is determined in a histology in the course of the disease. Possible scenarios for this are the histological confirmation of distant metastases or a histological follow-up of known tumour sites. Examinations that lead to new cancer diagnoses SHOULD be coded directly as part of the new diagnosis.

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
1. The search parameter "body-site" SHALL be supported:Examples:`GET [base]/Observation?bodysite=http://fhir.de/CodeSystem/icd-o-3|C00.4`Usage notes: Further information on searching by "derived-from" is available in the FHIR base specification — section "reference".

**Usages:**

* Examples for this Profile: [Observation/mii-exa-onko-histologie-icdo3](Observation-mii-exa-onko-histologie-icdo3.md)
* CapabilityStatements using this Profile: [MII CPS Onkology CapabilityStatement](CapabilityStatement-mii-cps-onko-capabilitystatement.md)

You can also check for [usages in the FHIR IG Statistics](https://packages2.fhir.org/xig/resource/de.medizininformatikinitiative.kerndatensatz.onkologie|current/StructureDefinition/StructureDefinition-mii-pr-onko-histologie-icdo3.json)

### Formal Views of Profile Content

 [Description of Profiles, Differentials, Snapshots, and their representations](http://build.fhir.org/ig/FHIR/ig-guidance/readingIgs.html#structure-definitions). 

 

Other representations of profile: [CSV](../StructureDefinition-mii-pr-onko-histologie-icdo3.csv), [Excel](../StructureDefinition-mii-pr-onko-histologie-icdo3.xlsx), [Schematron](../StructureDefinition-mii-pr-onko-histologie-icdo3.sch) 



## Resource Content

```json
{
  "resourceType" : "StructureDefinition",
  "id" : "mii-pr-onko-histologie-icdo3",
  "url" : "https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-histologie-icdo3",
  "version" : "2026.0.3",
  "name" : "MII_PR_Onko_Histologie_ICDO3",
  "title" : "MII PR Onkologie Histologie ICD-O-3",
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
  "description" : "Histologie-Kodierung nach ICD-0 für die Verwendung von Folgediagnostik. Bei der histologischen Beurteilung des Primärtumors sind die histologischen Informationen direkt über die Condition-Ressource abzubilden.",
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
      "short" : "Histologische Bewertung nach ICD-0-3",
      "mustSupport" : true
    },
    {
      "id" : "Observation.code.coding",
      "path" : "Observation.code.coding",
      "patternCoding" : {
        "system" : "http://loinc.org",
        "code" : "59847-4"
      },
      "mustSupport" : true
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
      "short" : "Datum der histologischen Untersuchung",
      "_short" : {
        "extension" : [{
          "extension" : [{
            "url" : "lang",
            "valueCode" : "de-DE"
          },
          {
            "url" : "content",
            "valueString" : "Datum der histologischen Untersuchung"
          }],
          "url" : "http://hl7.org/fhir/StructureDefinition/translation"
        }]
      },
      "definition" : "Datum der histologischen Untersuchung im Krankheitsverlauf",
      "_definition" : {
        "extension" : [{
          "extension" : [{
            "url" : "lang",
            "valueCode" : "de-DE"
          },
          {
            "url" : "content",
            "valueString" : "Datum der histologischen Untersuchung im Krankheitsverlauf"
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
        "map" : "6.1",
        "comment" : "Datum der histologischen Untersuchung (oBDS 6.1 'Tumor Histologiedatum' = Probenentnahme ist im Specimen.collection.collectedDateTime abgebildet)"
      }]
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
        "valueSet" : "https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/ValueSet/mii-vs-onko-icdo3-morphologie"
      }
    },
    {
      "id" : "Observation.value[x].coding",
      "path" : "Observation.value[x].coding",
      "max" : "1",
      "mustSupport" : true
    },
    {
      "id" : "Observation.value[x].coding.version",
      "path" : "Observation.value[x].coding.version",
      "short" : "Morphologie-Kode-Version",
      "_short" : {
        "extension" : [{
          "extension" : [{
            "url" : "lang",
            "valueCode" : "de-DE"
          },
          {
            "url" : "content",
            "valueString" : "Morphologie-Kode-Version"
          }],
          "url" : "http://hl7.org/fhir/StructureDefinition/translation"
        }]
      },
      "definition" : "Version der ICD-O-3 bzw. Blue Book nach 6.4 oBDS 2021",
      "_definition" : {
        "extension" : [{
          "extension" : [{
            "url" : "lang",
            "valueCode" : "de-DE"
          },
          {
            "url" : "content",
            "valueString" : "Version der ICD-O-3 bzw. Blue Book nach 6.4 oBDS 2021"
          }],
          "url" : "http://hl7.org/fhir/StructureDefinition/translation"
        }]
      },
      "mapping" : [{
        "identity" : "oBDS",
        "map" : "6.4",
        "comment" : "Morphologie ICD-O/Blue Book Version"
      }]
    },
    {
      "id" : "Observation.value[x].coding.code",
      "path" : "Observation.value[x].coding.code",
      "short" : "Morphologie-Kode",
      "_short" : {
        "extension" : [{
          "extension" : [{
            "url" : "lang",
            "valueCode" : "de-DE"
          },
          {
            "url" : "content",
            "valueString" : "Morphologie-Kode"
          }],
          "url" : "http://hl7.org/fhir/StructureDefinition/translation"
        }]
      },
      "definition" : "Morphologie als ICD-O-3 nach 6.3 oBDS 2021",
      "_definition" : {
        "extension" : [{
          "extension" : [{
            "url" : "lang",
            "valueCode" : "de-DE"
          },
          {
            "url" : "content",
            "valueString" : "Morphologie als ICD-O-3 nach 6.3 oBDS 2021"
          }],
          "url" : "http://hl7.org/fhir/StructureDefinition/translation"
        }]
      },
      "mapping" : [{
        "identity" : "oBDS",
        "map" : "6.3",
        "comment" : "Morphologie-Code"
      }]
    },
    {
      "id" : "Observation.value[x].text",
      "path" : "Observation.value[x].text",
      "mustSupport" : true,
      "mapping" : [{
        "identity" : "oBDS",
        "map" : "6.5",
        "comment" : "Morphologie Freitext"
      }]
    },
    {
      "id" : "Observation.bodySite.coding",
      "path" : "Observation.bodySite.coding",
      "slicing" : {
        "discriminator" : [{
          "type" : "pattern",
          "path" : "$this"
        }],
        "rules" : "open"
      },
      "mustSupport" : true
    },
    {
      "id" : "Observation.bodySite.coding:Seitenlokalisation",
      "path" : "Observation.bodySite.coding",
      "sliceName" : "Seitenlokalisation",
      "short" : "Seitenlokalisation",
      "_short" : {
        "extension" : [{
          "extension" : [{
            "url" : "lang",
            "valueCode" : "de-DE"
          },
          {
            "url" : "content",
            "valueString" : "Seitenlokalisation"
          }],
          "url" : "http://hl7.org/fhir/StructureDefinition/translation"
        }]
      },
      "definition" : "Seitenlokalisation bei paarigen Organen",
      "_definition" : {
        "extension" : [{
          "extension" : [{
            "url" : "lang",
            "valueCode" : "de-DE"
          },
          {
            "url" : "content",
            "valueString" : "Seitenlokalisation bei paarigen Organen"
          }],
          "url" : "http://hl7.org/fhir/StructureDefinition/translation"
        }]
      },
      "min" : 0,
      "max" : "1",
      "patternCoding" : {
        "system" : "https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/CodeSystem/mii-cs-onko-seitenlokalisation"
      },
      "mustSupport" : true,
      "binding" : {
        "strength" : "required",
        "valueSet" : "https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/ValueSet/mii-vs-onko-seitenlokalisation"
      }
    },
    {
      "id" : "Observation.bodySite.coding:Seitenlokalisation.system",
      "path" : "Observation.bodySite.coding.system",
      "min" : 1,
      "mustSupport" : true
    },
    {
      "id" : "Observation.bodySite.coding:Seitenlokalisation.code",
      "path" : "Observation.bodySite.coding.code",
      "min" : 1,
      "mustSupport" : true
    },
    {
      "id" : "Observation.bodySite.coding:icd-o-3",
      "path" : "Observation.bodySite.coding",
      "sliceName" : "icd-o-3",
      "short" : "ICD-O-3 Topographie",
      "_short" : {
        "extension" : [{
          "extension" : [{
            "url" : "lang",
            "valueCode" : "de-DE"
          },
          {
            "url" : "content",
            "valueString" : "ICD-O-3 Topographie"
          }],
          "url" : "http://hl7.org/fhir/StructureDefinition/translation"
        }]
      },
      "definition" : "ICD-O-3 Topographie bei vom Primärtumor abweichender Lokalisation in der Verlaufsbeschreibung",
      "_definition" : {
        "extension" : [{
          "extension" : [{
            "url" : "lang",
            "valueCode" : "de-DE"
          },
          {
            "url" : "content",
            "valueString" : "ICD-O-3 Topographie bei vom Primärtumor abweichender Lokalisation in der Verlaufsbeschreibung"
          }],
          "url" : "http://hl7.org/fhir/StructureDefinition/translation"
        }]
      },
      "min" : 0,
      "max" : "1",
      "patternCoding" : {
        "system" : "http://terminology.hl7.org/CodeSystem/icd-o-3"
      },
      "mustSupport" : true
    },
    {
      "id" : "Observation.bodySite.coding:icd-o-3.system",
      "path" : "Observation.bodySite.coding.system",
      "min" : 1,
      "mustSupport" : true
    },
    {
      "id" : "Observation.bodySite.coding:icd-o-3.code",
      "path" : "Observation.bodySite.coding.code",
      "min" : 1,
      "mustSupport" : true,
      "binding" : {
        "strength" : "required",
        "valueSet" : "https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/ValueSet/mii-vs-onko-icdo3-topographie"
      }
    },
    {
      "id" : "Observation.specimen",
      "path" : "Observation.specimen",
      "min" : 1,
      "type" : [{
        "code" : "Reference",
        "targetProfile" : ["https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-specimen"]
      }],
      "mustSupport" : true,
      "mapping" : [{
        "identity" : "oBDS",
        "map" : "6.1",
        "comment" : "Tumor Histologiedatum = Datum der Probenentnahme (siehe Specimen.collection.collectedDateTime)"
      }]
    }]
  }
}

```
