# MII PR Onkologie Her2neu Status - MII IG Kerndatensatz-Modul Onkologie v2026.0.3

* [**Table of Contents**](toc.md)
* [**Artifacts Summary**](artifacts.md)
* **MII PR Onkologie Her2neu Status**

## Resource Profile: MII PR Onkologie Her2neu Status 

| | |
| :--- | :--- |
| *Official URL*:https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-mamma-her2neu-status | *Version*:2026.0.3 |
| Active as of 2026-08-22 | *Computable Name*:MII_PR_Onko_Mamma_Her2neu_Status |

 
Dieses Profil beschreibt den Her2neu Status einer pathologisch untersuchten Probe beim Mamma-Karzinom in der Onkologie 

The **Her2neu status profile** documents the diagnostic Her2neu status of a pathologically examined specimen in breast cancer. Her2neu (also HER2 or ERBB2) is an important prognostic and predictive biomarker that decides whether a patient is eligible for anti-HER2-directed therapy.

The Her2neu status is based on **immunohistochemical (IHC) staining** and, for certain findings, additionally on **in-situ hybridisation (ISH, e.g. FISH or CISH)**. The determination follows the ASCO/CAP guidelines and the requirements of the S3 guideline for breast cancer.

### Clinical background

Determining Her2neu is essential for treatment planning in breast cancer:

* **HER2-positive tumours** (approx. 15-20% of breast cancers) benefit from anti-HER2 therapies such as trastuzumab, pertuzumab or T-DM1
* **HER2-low tumours** show low HER2 expression and can benefit from newer therapies such as trastuzumab deruxtecan (based on the DESTINY-Breast04/06 trials)
* **HER2-negative tumours** do not receive anti-HER2-directed therapy

### Her2neu determination according to ASCO/CAP

Her2neu is determined in several steps.

#### IHC scores:

* **3+**: strong, complete membrane staining in >10% of the tumour cells -> HER2-positive
* **2+**: weak to moderate, complete membrane staining in >10% of the tumour cells -> ISH testing required
* **1+**: weak, incomplete membrane staining in >10% of the tumour cells -> HER2-low (if ISH-negative or without ISH)
* **0**: no staining, or membrane staining in <=10% of the tumour cells

#### ISH testing (FISH, CISH, etc.):

* **Positive**: HER2/CEP17 ratio >=2.0 or HER2 copy number >=6.0 per cell
* **Negative**: HER2/CEP17 ratio <2.0 and HER2 copy number <4.0 per cell
* **Equivocal**: borderline findings that require re-testing

The Molekulares Tumorboard module offers more fine-grained profiles for representing the IHC and ISH data points within a molecular pathology report.

### Links to other resources

The profile is closely linked to the other oncology resources:

* references the primary diagnosis (MII_PR_Onko_Diagnose_Primaertumor) via `Observation.focus`
* references the patient (Patient resource) via `Observation.subject`
* can be linked to a specific encounter via `Observation.encounter`

### oBDS context and dual coding

The profile implements the **oBDS data fields for the Her2neu status** (field M4, no. 243) in breast cancer. A **dual coding strategy** is used in order to satisfy both the frozen oBDS specification and the newer S3 guidelines and ASCO/CAP guidelines.

#### oBDS definition (based on the guideline 3.0 specification):

The oBDS coding uses letter codes that correspond exactly to the published specification:

* **P** = positive (IHC 3+, or IHC 2+ and ISH positive)
* **N** = negative
* **U** = unknown

#### S3 guideline / ASCO-CAP definition (current guideline version 5.1):

The modern classification additionally takes the **HER2-low** and **HER2-ultralow** categories into account:

* **HER2-positive**: IHC 3+, or IHC 2+ and ISH-positive
* **HER2-low**: IHC 1+, or IHC 2+ and ISH-negative
* **HER2-ultralow**: IHC 0 with membrane staining
* **HER2-negative**: IHC 0 without membrane staining
* **Equivocal**: borderline, further testing required

This dual coding enables **backward compatibility** with existing oBDS registry data and at the same time **forward compatibility** with newer therapeutic developments (e.g. trastuzumab deruxtecan for HER2-low).

### Terminology binding

The profile uses a **dual coding strategy** with an **extensible** binding for `valueCodeableConcept`. This means that codes from both ValueSets MAY be used in parallel.

* ValueSet: MII VS Onko Mamma Her2neu Status oBDS
* ValueSet: MII VS Onko Mamma Her2neu Status Leitlinie

### Search parameters

The following search parameters are relevant for the Mamma-Her2neu-Status profile, including in combination:

* The search parameter `_id` MUST be supported: `GET [base]/Observation?_id=12345`
* The search parameter `_profile` MUST be supported: `GET [base]/Observation?_profile=https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-mamma-her2neu-status`
* The search parameter `code` MUST be supported: `GET [base]/Observation?code=http://loinc.org|48676-1`
* The search parameter `subject` MUST be supported: `GET [base]/Observation?subject=Patient/test`
* The search parameter `patient` MUST be supported: `GET [base]/Observation?patient=Patient/test`
* The search parameter `focus` MUST be supported: `GET [base]/Observation?focus=Condition/primaertumor`
* The search parameter `value-concept` MUST be supported: `GET [base]/Observation?value-concept=https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/CodeSystem/mii-cs-onko-mamma-her2neu-status-obds|P`
* The search parameter `component-code` MUST be supported: `GET [base]/Observation?component-code=http://loinc.org|85319-2`

**Usages:**

* Examples for this Profile: [Observation/mii-exa-onko-mamma-her2neu-status](Observation-mii-exa-onko-mamma-her2neu-status.md)
* CapabilityStatements using this Profile: [MII CPS Onkology CapabilityStatement](CapabilityStatement-mii-cps-onko-capabilitystatement.md)

You can also check for [usages in the FHIR IG Statistics](https://packages2.fhir.org/xig/resource/de.medizininformatikinitiative.kerndatensatz.onkologie|current/StructureDefinition/StructureDefinition-mii-pr-onko-mamma-her2neu-status.json)

### Formal Views of Profile Content

 [Description of Profiles, Differentials, Snapshots, and their representations](http://build.fhir.org/ig/FHIR/ig-guidance/readingIgs.html#structure-definitions). 

 

Other representations of profile: [CSV](../StructureDefinition-mii-pr-onko-mamma-her2neu-status.csv), [Excel](../StructureDefinition-mii-pr-onko-mamma-her2neu-status.xlsx), [Schematron](../StructureDefinition-mii-pr-onko-mamma-her2neu-status.sch) 



## Resource Content

```json
{
  "resourceType" : "StructureDefinition",
  "id" : "mii-pr-onko-mamma-her2neu-status",
  "url" : "https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-mamma-her2neu-status",
  "version" : "2026.0.3",
  "name" : "MII_PR_Onko_Mamma_Her2neu_Status",
  "title" : "MII PR Onkologie Her2neu Status",
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
  "description" : "Dieses Profil beschreibt den Her2neu Status einer pathologisch untersuchten Probe beim Mamma-Karzinom in der Onkologie",
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
        "map" : "M4",
        "comment" : "Her2neu Status"
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
      "short" : "Her2neu Status",
      "definition" : "Her2neu Status, abgeleitet aus der Immunhistochemie und ggf. In-situ-Hybridisierung der Mamma-Biopsie oder des Mamma-Exzisionspräparates",
      "mustSupport" : true
    },
    {
      "id" : "Observation.code.coding",
      "path" : "Observation.code.coding",
      "patternCoding" : {
        "system" : "http://loinc.org",
        "code" : "48676-1",
        "display" : "HER2 [Interpretation] in Tissue"
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
      "mustSupport" : true
    },
    {
      "id" : "Observation.value[x].coding",
      "path" : "Observation.value[x].coding",
      "slicing" : {
        "discriminator" : [{
          "type" : "value",
          "path" : "system"
        }],
        "description" : "Slicing für die unterschiedliche Definition von Her2neu Status im oBDS und in den S3-Leitlinien/ASCO-CAP Guidelines",
        "ordered" : false,
        "rules" : "open"
      },
      "mapping" : [{
        "identity" : "oBDS",
        "map" : "M4",
        "comment" : "Her2neu Status (oBDS 243)"
      }]
    },
    {
      "id" : "Observation.value[x].coding.code",
      "path" : "Observation.value[x].coding.code",
      "min" : 1,
      "mustSupport" : true
    },
    {
      "id" : "Observation.value[x].coding:DefinitionOBDS",
      "path" : "Observation.value[x].coding",
      "sliceName" : "DefinitionOBDS",
      "min" : 0,
      "max" : "1",
      "mustSupport" : true,
      "binding" : {
        "strength" : "extensible",
        "valueSet" : "https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/ValueSet/mii-vs-onko-mamma-her2neu-status-obds"
      }
    },
    {
      "id" : "Observation.value[x].coding:DefinitionOBDS.system",
      "path" : "Observation.value[x].coding.system",
      "min" : 1,
      "patternUri" : "https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/CodeSystem/mii-cs-onko-mamma-her2neu-status-obds"
    },
    {
      "id" : "Observation.value[x].coding:DefinitionOBDS.code",
      "path" : "Observation.value[x].coding.code",
      "min" : 1,
      "mustSupport" : true
    },
    {
      "id" : "Observation.value[x].coding:DefinitionLeitlinie",
      "path" : "Observation.value[x].coding",
      "sliceName" : "DefinitionLeitlinie",
      "min" : 0,
      "max" : "1",
      "mustSupport" : true,
      "binding" : {
        "strength" : "extensible",
        "valueSet" : "https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/ValueSet/mii-vs-onko-mamma-her2neu-status-leitlinie"
      }
    },
    {
      "id" : "Observation.value[x].coding:DefinitionLeitlinie.system",
      "path" : "Observation.value[x].coding.system",
      "min" : 1,
      "patternUri" : "https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/CodeSystem/mii-cs-onko-mamma-her2neu-status-leitlinie"
    },
    {
      "id" : "Observation.value[x].coding:DefinitionLeitlinie.code",
      "path" : "Observation.value[x].coding.code",
      "min" : 1,
      "mustSupport" : true
    },
    {
      "id" : "Observation.component",
      "path" : "Observation.component",
      "slicing" : {
        "discriminator" : [{
          "type" : "pattern",
          "path" : "code"
        }],
        "description" : "Slice for Her2neu primary data observations (IHC score and ISH result)",
        "ordered" : false,
        "rules" : "open"
      },
      "mustSupport" : true
    },
    {
      "id" : "Observation.component:IHCScore",
      "path" : "Observation.component",
      "sliceName" : "IHCScore",
      "min" : 0,
      "max" : "1",
      "mustSupport" : true
    },
    {
      "id" : "Observation.component:IHCScore.code",
      "path" : "Observation.component.code",
      "patternCodeableConcept" : {
        "coding" : [{
          "system" : "http://loinc.org",
          "code" : "85319-2",
          "display" : "HER2 [Presence] in Breast cancer specimen by Immune stain"
        }]
      }
    },
    {
      "id" : "Observation.component:IHCScore.value[x]",
      "path" : "Observation.component.value[x]",
      "type" : [{
        "code" : "CodeableConcept"
      }],
      "mustSupport" : true,
      "binding" : {
        "strength" : "extensible",
        "valueSet" : "http://loinc.org/vs/LL4396-9"
      }
    },
    {
      "id" : "Observation.component:ISHResult",
      "path" : "Observation.component",
      "sliceName" : "ISHResult",
      "min" : 0,
      "max" : "1",
      "mustSupport" : true
    },
    {
      "id" : "Observation.component:ISHResult.code",
      "path" : "Observation.component.code",
      "patternCodeableConcept" : {
        "coding" : [{
          "system" : "http://loinc.org",
          "code" : "96893-3",
          "display" : "ERBB2 gene duplication in Tumor by FISH"
        }]
      }
    },
    {
      "id" : "Observation.component:ISHResult.value[x]",
      "path" : "Observation.component.value[x]",
      "type" : [{
        "code" : "CodeableConcept"
      }],
      "mustSupport" : true,
      "binding" : {
        "strength" : "extensible",
        "valueSet" : "http://loinc.org/vs/LL4678-0"
      }
    }]
  }
}

```
