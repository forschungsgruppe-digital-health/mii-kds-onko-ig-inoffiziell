# MII PR Onkologie Specimen - MII IG Kerndatensatz-Modul Onkologie v2026.0.3

* [**Table of Contents**](toc.md)
* [**Artifacts Summary**](artifacts.md)
* **MII PR Onkologie Specimen**

## Resource Profile: MII PR Onkologie Specimen 

| | |
| :--- | :--- |
| *Official URL*:https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-krk-specimen | *Version*:2026.0.3 |
| Active as of 2026-08-22 | *Computable Name*:MII_PR_Onko_KRK_Specimen |

 
Histologie: Dieses Profil beschreibt eine Gewebeprobe in der Onkologie. 

This profile describes tissue specimens in colorectal cancer that are taken during surgical interventions. It covers the characterisation of the tissue as well as specific pathological aspects such as the TME quality (total mesorectal excision) in rectal cancer.

The profile is based on a FHIR Specimen resource and establishes the link between the surgical removal and the pathological work-up.

### Links to other resources

The KRK specimen is an important link in the diagnostic chain:

* references the patient (Patient resource) via `Specimen.subject`
* relates to the collection procedure via `Specimen.collection.procedure`
* can be linked to pathological observations (e.g. histology, grading)
* serves as the basis for determining the resection margins and the TNM classification

### oBDS context

The KRK specimen is the basis for various oBDS assessments:

* pathological assessment of the resection specimen
* TME quality in rectal cancer (KR4)
* histopathological characteristics of the tumour
* assessment of the resection margins

### Terminology binding

The profile uses specialised ValueSets for colorectal specimens, in particular for assessing the TME quality and other pathological parameters.

* ValueSet: MII VS Onko KRK TME Qualität

### Search parameters

The following search parameters are relevant for the KRK-Specimen profile, including in combination:

* The search parameter `_id` MUST be supported: `GET [base]/Specimen?_id=12345`
* The search parameter `_profile` MUST be supported: `GET [base]/Specimen?_profile=https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-krk-specimen`
* The search parameter `subject` MUST be supported: `GET [base]/Specimen?subject=Patient/test`
* The search parameter `type` MUST be supported: `GET [base]/Specimen?type=http://snomed.info/sct|119376003`
* The search parameter `status` MUST be supported: `GET [base]/Specimen?status=available`

**Usages:**

* Examples for this Profile: [Specimen/mii-exa-onko-krk-specimen](Specimen-mii-exa-onko-krk-specimen.md)
* CapabilityStatements using this Profile: [MII CPS Onkology CapabilityStatement](CapabilityStatement-mii-cps-onko-capabilitystatement.md)

You can also check for [usages in the FHIR IG Statistics](https://packages2.fhir.org/xig/resource/de.medizininformatikinitiative.kerndatensatz.onkologie|current/StructureDefinition/StructureDefinition-mii-pr-onko-krk-specimen.json)

### Formal Views of Profile Content

 [Description of Profiles, Differentials, Snapshots, and their representations](http://build.fhir.org/ig/FHIR/ig-guidance/readingIgs.html#structure-definitions). 

 

Other representations of profile: [CSV](../StructureDefinition-mii-pr-onko-krk-specimen.csv), [Excel](../StructureDefinition-mii-pr-onko-krk-specimen.xlsx), [Schematron](../StructureDefinition-mii-pr-onko-krk-specimen.sch) 



## Resource Content

```json
{
  "resourceType" : "StructureDefinition",
  "id" : "mii-pr-onko-krk-specimen",
  "url" : "https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-krk-specimen",
  "version" : "2026.0.3",
  "name" : "MII_PR_Onko_KRK_Specimen",
  "title" : "MII PR Onkologie Specimen",
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
  "description" : "Histologie: Dieses Profil beschreibt eine Gewebeprobe in der Onkologie.",
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
    "identity" : "w5",
    "uri" : "http://hl7.org/fhir/fivews",
    "name" : "FiveWs Pattern Mapping"
  },
  {
    "identity" : "v2",
    "uri" : "http://hl7.org/v2",
    "name" : "HL7 v2 Mapping"
  }],
  "kind" : "resource",
  "abstract" : false,
  "type" : "Specimen",
  "baseDefinition" : "https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-specimen",
  "derivation" : "constraint",
  "differential" : {
    "element" : [{
      "id" : "Specimen",
      "path" : "Specimen",
      "mapping" : [{
        "identity" : "oBDS",
        "map" : "6",
        "comment" : "Histologie"
      }]
    },
    {
      "id" : "Specimen.accessionIdentifier.value",
      "path" : "Specimen.accessionIdentifier.value",
      "mapping" : [{
        "identity" : "oBDS",
        "map" : "6.2",
        "comment" : "Histologie-Einsendenummer"
      }]
    },
    {
      "id" : "Specimen.collection.collected[x]:collectedDateTime",
      "path" : "Specimen.collection.collected[x]",
      "sliceName" : "collectedDateTime",
      "short" : "Tumor Histologiedatum",
      "_short" : {
        "extension" : [{
          "extension" : [{
            "url" : "lang",
            "valueCode" : "de-DE"
          },
          {
            "url" : "content",
            "valueString" : "Tumor Histologiedatum"
          }],
          "url" : "http://hl7.org/fhir/StructureDefinition/translation"
        }]
      },
      "definition" : "Histologiedatum nach 6.1 oBDS 2021",
      "_definition" : {
        "extension" : [{
          "extension" : [{
            "url" : "lang",
            "valueCode" : "de-DE"
          },
          {
            "url" : "content",
            "valueString" : "Histologiedatum nach 6.1 oBDS 2021"
          }],
          "url" : "http://hl7.org/fhir/StructureDefinition/translation"
        }]
      },
      "type" : [{
        "code" : "dateTime"
      }],
      "mapping" : [{
        "identity" : "oBDS",
        "map" : "6.1",
        "comment" : "Tumor Histologiedatum"
      }]
    },
    {
      "id" : "Specimen.condition",
      "path" : "Specimen.condition",
      "mustSupport" : true,
      "binding" : {
        "strength" : "extensible",
        "valueSet" : "https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/ValueSet/mii-vs-onko-krk-tme-qualitaet"
      }
    }]
  }
}

```
