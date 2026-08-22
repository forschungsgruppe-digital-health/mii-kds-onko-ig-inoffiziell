# MII PR Onkologie Menopausenstatus Mamma - MII IG Kerndatensatz-Modul Onkologie v2026.0.3

* [**Table of Contents**](toc.md)
* [**Artifacts Summary**](artifacts.md)
* **MII PR Onkologie Menopausenstatus Mamma**

## Resource Profile: MII PR Onkologie Menopausenstatus Mamma 

| | |
| :--- | :--- |
| *Official URL*:https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-mamma-menopause-status | *Version*:2026.0.3 |
| Active as of 2026-08-22 | *Computable Name*:MII_PR_Onko_Mamma_Menopausenstatus |

 
Dieses Profil beschreibt den (prätherapeutischen) Menopausenstatus einer Patientin mit Mamma-Karzinom in der Onkologie 

This profile describes the (pre-therapeutic) menopausal status of a patient with breast cancer in oncology. The menopausal status is an important prognostic factor for treatment planning and therapy selection in breast cancer.

The profile is based on a FHIR Observation resource and uses SNOMED CT to code the observed characteristic (menopause function). The specific expressions of the menopausal status are defined via a dedicated ValueSet.

### Links to other resources

The menopausal status is an important tumour-specific observation:

* references the primary diagnosis (MII_PR_Onko_Diagnose_Primaertumor) via `Observation.focus`
* references the patient (Patient resource) via `Observation.subject`
* can be linked to a specific encounter via `Observation.encounter`

### oBDS context

According to the current oBDS version 2021, the perimenopausal status is implicitly subsumed under premenopausal. This convention is represented in the FHIR profiling by the corresponding ValueSet.

### Terminology binding

The ValueSet for the menopausal status is bound as **extensible**. This means that the codes from the defined ValueSet SHOULD preferably be used, but that other suitable codes MAY be used where needed if the predefined values are not sufficient.

* ValueSet: MII VS Onko Mamma Menopause Status

### Search parameters

The following search parameters are relevant for the Mamma-Menopause-Status profile, including in combination:

* The search parameter `_id` MUST be supported: `GET [base]/Observation?_id=12345`
* The search parameter `_profile` MUST be supported: `GET [base]/Observation?_profile=https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-mamma-menopause-status`
* The search parameter `code` MUST be supported: `GET [base]/Observation?code=http://snomed.info/sct|161712005`
* The search parameter `subject` MUST be supported: `GET [base]/Observation?subject=Patient/test`
* The search parameter `focus` MUST be supported: `GET [base]/Observation?focus=Condition/primaertumor`
* The search parameter `value-concept` MUST be supported: `GET [base]/Observation?value-concept=http://snomed.info/sct|76498008`

**Usages:**

* Examples for this Profile: [Observation/mii-exa-onko-mamma-menopause-status-1](Observation-mii-exa-onko-mamma-menopause-status-1.md)
* CapabilityStatements using this Profile: [MII CPS Onkology CapabilityStatement](CapabilityStatement-mii-cps-onko-capabilitystatement.md)

You can also check for [usages in the FHIR IG Statistics](https://packages2.fhir.org/xig/resource/de.medizininformatikinitiative.kerndatensatz.onkologie|current/StructureDefinition/StructureDefinition-mii-pr-onko-mamma-menopause-status.json)

### Formal Views of Profile Content

 [Description of Profiles, Differentials, Snapshots, and their representations](http://build.fhir.org/ig/FHIR/ig-guidance/readingIgs.html#structure-definitions). 

 

Other representations of profile: [CSV](../StructureDefinition-mii-pr-onko-mamma-menopause-status.csv), [Excel](../StructureDefinition-mii-pr-onko-mamma-menopause-status.xlsx), [Schematron](../StructureDefinition-mii-pr-onko-mamma-menopause-status.sch) 



## Resource Content

```json
{
  "resourceType" : "StructureDefinition",
  "id" : "mii-pr-onko-mamma-menopause-status",
  "url" : "https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-mamma-menopause-status",
  "version" : "2026.0.3",
  "name" : "MII_PR_Onko_Mamma_Menopausenstatus",
  "title" : "MII PR Onkologie Menopausenstatus Mamma",
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
  "description" : "Dieses Profil beschreibt den (prätherapeutischen) Menopausenstatus einer Patientin mit Mamma-Karzinom in der Onkologie",
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
      "short" : "Status der Menopause",
      "definition" : "Prätherapeutischer Menopausenstatus einer Patientin mit Mamma-Karzinom",
      "mustSupport" : true
    },
    {
      "id" : "Observation.code.coding",
      "path" : "Observation.code.coding",
      "patternCoding" : {
        "system" : "http://snomed.info/sct",
        "code" : "161712005",
        "display" : "Menopause, function (observable entity)"
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
      "id" : "Observation.value[x]",
      "path" : "Observation.value[x]",
      "min" : 1,
      "type" : [{
        "code" : "CodeableConcept"
      }],
      "mustSupport" : true,
      "binding" : {
        "strength" : "extensible",
        "valueSet" : "https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/ValueSet/mii-vs-onko-mamma-menopause-status"
      }
    },
    {
      "id" : "Observation.value[x].coding.code",
      "path" : "Observation.value[x].coding.code",
      "min" : 1,
      "mustSupport" : true
    }]
  }
}

```
