# MII PR Onkologie Präoperative Markierung Mamma - MII IG Kerndatensatz-Modul Onkologie v2026.0.3

* [**Table of Contents**](toc.md)
* [**Artifacts Summary**](artifacts.md)
* **MII PR Onkologie Präoperative Markierung Mamma**

## Resource Profile: MII PR Onkologie Präoperative Markierung Mamma 

| | |
| :--- | :--- |
| *Official URL*:https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-mamma-praeoperative-markierung | *Version*:2026.0.3 |
| Active as of 2026-08-22 | *Computable Name*:MII_PR_Onko_Mamma_Praeoperative_Markierung |

 
Das vorliegende Profil beschreibt eine präoperativ durchgeführte Markierung von Tumorgewebe in der Brust. Dabei können verschiedene Markierungsmodalitäten gewählt werden, wie z.B. Drahtmarkierungen, Seed-Markierungen oder andere Lokalisationstechniken. 

The **Mamma-Präoperative Markierung profile** documents radiologically performed markings of tumour tissue in the breast prior to surgical interventions. The profile is based on the FHIR Procedure resource and records the various marking modalities used for the precise localisation of tumour tissue.

Pre-operative marking is an important component of breast-conserving therapy and allows surgeons to localise non-palpable lesions exactly and to remove them completely.

### Links to other resources

The profile is closely linked to the other oncology resources:

* references the superordinate operation (MII_PR_Onko_Operation) via `Procedure.partOf`
* references the patient (Patient resource) via `Procedure.subject`
* can be linked to a specific encounter via `Procedure.encounter`

### oBDS context

The profile implements **breast-specific marking procedures** as an extension of the general oBDS operation data set. Pre-operative marking is particularly relevant for:

**Clinical applications:**

* **Breast-conserving therapy**: precise localisation of non-palpable tumours
* **Multifocal tumours**: marking of several tumour foci
* **Re-excision**: marking in the case of R1 resections
* **Quality assurance**: documentation of the marking quality

**Marking modalities (currently in the ValueSet):**

* **Wire marking with ultrasound guidance**: SNOMED CT 433222002
* **Marker insertion with X-ray guidance**: SNOMED CT 836381000000102
* **Wire marking with MRI guidance**: SNOMED CT 911831000000104

**Further clinically relevant modalities (not yet in the ValueSet):**

* **Radioactive seed marking**: radioactive seeds for localisation
* **Magnetic seed marking**: modern wireless procedures (e.g. Magseed(R))
* **Clip marking**: metal clips for orientation

**Note: the current ValueSet focuses on imaging-guided wire and marker procedures. Modern seed-based procedures could be added in future versions.**

### Terminology binding

The profile uses an **extensible binding** for marking modalities directly on `Procedure.code`:

* ValueSet: MII VS Onko Mamma Präoperative Markierung Modalität

### Search parameters

The following search parameters are relevant for the Mamma-Präoperative Markierung profile, including in combination:

* The search parameter `_id` MUST be supported: `GET [base]/Procedure?_id=12345`
* The search parameter `_profile` MUST be supported: `GET [base]/Procedure?_profile=https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-mamma-praeoperative-markierung`
* The search parameter `code` MUST be supported: `GET [base]/Procedure?code=http://snomed.info/sct|392021009`
* The search parameter `subject` MUST be supported: `GET [base]/Procedure?subject=Patient/test`
* The search parameter `patient` MUST be supported: `GET [base]/Procedure?patient=Patient/test`
* The search parameter `part-of` MUST be supported: `GET [base]/Procedure?part-of=Procedure/hauptoperation`
* The search parameter `date` MUST be supported: `GET [base]/Procedure?date=2024-01-15`

**Usages:**

* Examples for this Profile: [Procedure/mii-exa-onko-mamma-praeoperative-markierung-1](Procedure-mii-exa-onko-mamma-praeoperative-markierung-1.md)
* CapabilityStatements using this Profile: [MII CPS Onkology CapabilityStatement](CapabilityStatement-mii-cps-onko-capabilitystatement.md)

You can also check for [usages in the FHIR IG Statistics](https://packages2.fhir.org/xig/resource/de.medizininformatikinitiative.kerndatensatz.onkologie|current/StructureDefinition/StructureDefinition-mii-pr-onko-mamma-praeoperative-markierung.json)

### Formal Views of Profile Content

 [Description of Profiles, Differentials, Snapshots, and their representations](http://build.fhir.org/ig/FHIR/ig-guidance/readingIgs.html#structure-definitions). 

 

Other representations of profile: [CSV](../StructureDefinition-mii-pr-onko-mamma-praeoperative-markierung.csv), [Excel](../StructureDefinition-mii-pr-onko-mamma-praeoperative-markierung.xlsx), [Schematron](../StructureDefinition-mii-pr-onko-mamma-praeoperative-markierung.sch) 



## Resource Content

```json
{
  "resourceType" : "StructureDefinition",
  "id" : "mii-pr-onko-mamma-praeoperative-markierung",
  "url" : "https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-mamma-praeoperative-markierung",
  "version" : "2026.0.3",
  "name" : "MII_PR_Onko_Mamma_Praeoperative_Markierung",
  "title" : "MII PR Onkologie Präoperative Markierung Mamma",
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
  "description" : "Das vorliegende Profil beschreibt eine präoperativ durchgeführte Markierung von Tumorgewebe in der Brust. Dabei können verschiedene Markierungsmodalitäten gewählt werden, wie z.B. Drahtmarkierungen, Seed-Markierungen oder andere Lokalisationstechniken.",
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
  "type" : "Procedure",
  "baseDefinition" : "http://hl7.org/fhir/StructureDefinition/Procedure",
  "derivation" : "constraint",
  "differential" : {
    "element" : [{
      "id" : "Procedure",
      "path" : "Procedure"
    },
    {
      "id" : "Procedure.meta.profile",
      "path" : "Procedure.meta.profile",
      "mustSupport" : true
    },
    {
      "id" : "Procedure.partOf",
      "path" : "Procedure.partOf",
      "type" : [{
        "code" : "Reference",
        "targetProfile" : ["https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-operation"]
      }],
      "mustSupport" : true
    },
    {
      "id" : "Procedure.status",
      "path" : "Procedure.status",
      "mustSupport" : true
    },
    {
      "id" : "Procedure.code",
      "path" : "Procedure.code",
      "short" : "Präoperative Tumormarkierung",
      "definition" : "Präoperative Markierung von Tumorgewebe in der Brust zur exakten Lokalisation während der Operation",
      "min" : 1,
      "mustSupport" : true
    },
    {
      "id" : "Procedure.code.coding",
      "path" : "Procedure.code.coding",
      "mustSupport" : true,
      "binding" : {
        "strength" : "extensible",
        "valueSet" : "https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/ValueSet/mii-vs-onko-mamma-praeoperative-markierung-modalitaet"
      }
    },
    {
      "id" : "Procedure.subject",
      "path" : "Procedure.subject",
      "type" : [{
        "code" : "Reference",
        "targetProfile" : ["http://hl7.org/fhir/StructureDefinition/Patient"]
      }],
      "mustSupport" : true
    },
    {
      "id" : "Procedure.encounter",
      "path" : "Procedure.encounter",
      "mustSupport" : true
    }]
  }
}

```
