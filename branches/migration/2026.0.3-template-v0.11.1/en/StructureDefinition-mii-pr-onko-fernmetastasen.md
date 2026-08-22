# MII PR Onkologie Fernmetastasen - MII IG Kerndatensatz-Modul Onkologie v2026.0.3

* [**Table of Contents**](toc.md)
* [**Artifacts Summary**](artifacts.md)
* **MII PR Onkologie Fernmetastasen**

## Resource Profile: MII PR Onkologie Fernmetastasen 

| | |
| :--- | :--- |
| *Official URL*:https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-fernmetastasen | *Version*:2026.0.3 |
| Active as of 2026-08-22 | *Computable Name*:MII_PR_Onko_Fernmetastasen |

 
OBDS Beschreibung von Fernmetastasen (Lokalisation und Datum) 

This profile describes distant metastases (Fernmetastasen) as they are recorded within the oBDS in oncology for the report to the cancer registries. For each metastasis the following data fields are to be given individually:

* date of the determination
* location based on the oBDS's own coding

In the FHIR profiling, each distant metastasis **SHOULD** be created as an individual resource. The oBDS does not provide for stating non-invasive diagnostic procedures. Nor does the oBDS require the degree of diagnostic certainty (clinical, radiological, histological) to be recorded. Where needed, a distant metastasis **MAY** reference the corresponding diagnostic procedures.

This profile is conformant to the [Patho-Finding profile of the MII pathology report](https://simplifier.net/guide/mii-ig-pathologie/Befund-TechnischeImplementierung-FHIRProfile-MII-PR-Patho-Finding?version=current) and can therefore be embedded as an Observation into a pathology report.

### Search parameters

The following search parameters are relevant for the Onkologie module, also in combination:

* The search parameter `_id` MUST be supported: `GET [base]/Observation?_id=1234`
* The search parameter `_profile` MUST be supported: `GET [base]/Observation?_profile=https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-allgemeiner-leistungszustand`
* The search parameter `code` MUST be supported: `GET [base]/Observation?code=http://fhir.de/CodeSystem/sct|184305005`
* The search parameter `subject` MUST be supported: `GET [base]/Observation?subject=Patient/example`
* The search parameter `focus` MUST be supported: `GET [base]/Observation?focus=Condition/example`
* The search parameter `encounter` MUST be supported: `GET [base]/Observation?encounter=Encounter/example`
* The search parameter `date` MUST be supported: `GET [base]/Observation?date=2024-02-08`
* The search parameter `body-site` MUST be supported: `GET [base]/Observation?body-site=http://snomed.info/sct|258332000`
* The search parameter `derived-from` MUST be supported: `GET [base]/Observation?derived-from=Observation/example`

**Usages:**

* Refer to this Profile: [MII PR Onkologie TNM M-Kategorie](StructureDefinition-mii-pr-onko-tnm-m-kategorie.md)
* Examples for this Profile: [Observation/mii-exa-onko-fernmetastasen-1](Observation-mii-exa-onko-fernmetastasen-1.md)
* CapabilityStatements using this Profile: [MII CPS Onkology CapabilityStatement](CapabilityStatement-mii-cps-onko-capabilitystatement.md)

You can also check for [usages in the FHIR IG Statistics](https://packages2.fhir.org/xig/resource/de.medizininformatikinitiative.kerndatensatz.onkologie|current/StructureDefinition/StructureDefinition-mii-pr-onko-fernmetastasen.json)

### Formal Views of Profile Content

 [Description of Profiles, Differentials, Snapshots, and their representations](http://build.fhir.org/ig/FHIR/ig-guidance/readingIgs.html#structure-definitions). 

 

Other representations of profile: [CSV](../StructureDefinition-mii-pr-onko-fernmetastasen.csv), [Excel](../StructureDefinition-mii-pr-onko-fernmetastasen.xlsx), [Schematron](../StructureDefinition-mii-pr-onko-fernmetastasen.sch) 



## Resource Content

```json
{
  "resourceType" : "StructureDefinition",
  "id" : "mii-pr-onko-fernmetastasen",
  "url" : "https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-fernmetastasen",
  "version" : "2026.0.3",
  "name" : "MII_PR_Onko_Fernmetastasen",
  "title" : "MII PR Onkologie Fernmetastasen",
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
  "description" : "OBDS Beschreibung von Fernmetastasen (Lokalisation und Datum)",
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
      "mapping" : [{
        "identity" : "oBDS",
        "map" : "11",
        "comment" : "Fernmetastasen"
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
      "short" : "Lokalisation einer Fernmetastase laut oBDS",
      "definition" : "SCTID: 385421009 | Site of distant metastasis",
      "mustSupport" : true
    },
    {
      "id" : "Observation.code.coding",
      "path" : "Observation.code.coding",
      "patternCoding" : {
        "system" : "http://snomed.info/sct",
        "code" : "385421009"
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
      "short" : "Datum der diagnostischen Sicherung von Fernmetastasen",
      "_short" : {
        "extension" : [{
          "extension" : [{
            "url" : "lang",
            "valueCode" : "de-DE"
          },
          {
            "url" : "content",
            "valueString" : "Datum der diagnostischen Sicherung von Fernmetastasen"
          }],
          "url" : "http://hl7.org/fhir/StructureDefinition/translation"
        }]
      },
      "definition" : "Gibt an, wann die Fernmetastase festgestellt wurde.",
      "_definition" : {
        "extension" : [{
          "extension" : [{
            "url" : "lang",
            "valueCode" : "de-DE"
          },
          {
            "url" : "content",
            "valueString" : "Gibt an wann die Fernmetastase festgestellt wurde."
          }],
          "url" : "http://hl7.org/fhir/StructureDefinition/translation"
        }]
      },
      "min" : 1,
      "type" : [{
        "code" : "dateTime"
      }],
      "mustSupport" : true,
      "mapping" : [{
        "identity" : "oBDS",
        "map" : "11.2",
        "comment" : "Datum der diagnostischen Sicherung von Fernmetastasen"
      }]
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
      "short" : "Lokalisation der Fernmetastase laut oBDS/TNM-Kodierung",
      "_short" : {
        "extension" : [{
          "extension" : [{
            "url" : "lang",
            "valueCode" : "de-DE"
          },
          {
            "url" : "content",
            "valueString" : "Lokalisation der Fernmetastasen"
          }],
          "url" : "http://hl7.org/fhir/StructureDefinition/translation"
        }]
      },
      "definition" : "weitere Lokalisationen sind als einzelne Ressourcen zu kodieren",
      "_definition" : {
        "extension" : [{
          "extension" : [{
            "url" : "lang",
            "valueCode" : "de-DE"
          },
          {
            "url" : "content",
            "valueString" : "Lokalisation der Fernmetastasen laut 11.1 oBDS 2021 / TNM Kodierung"
          }],
          "url" : "http://hl7.org/fhir/StructureDefinition/translation"
        }]
      },
      "mustSupport" : true,
      "binding" : {
        "strength" : "required",
        "valueSet" : "https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/ValueSet/mii-vs-onko-fernmetastasen"
      }
    },
    {
      "id" : "Observation.value[x].coding.system",
      "path" : "Observation.value[x].coding.system",
      "mustSupport" : true
    },
    {
      "id" : "Observation.value[x].coding.code",
      "path" : "Observation.value[x].coding.code",
      "mustSupport" : true,
      "mapping" : [{
        "identity" : "oBDS",
        "map" : "11.1",
        "comment" : "Lokalisation von Fernmetastase(n)"
      }]
    }]
  }
}

```
