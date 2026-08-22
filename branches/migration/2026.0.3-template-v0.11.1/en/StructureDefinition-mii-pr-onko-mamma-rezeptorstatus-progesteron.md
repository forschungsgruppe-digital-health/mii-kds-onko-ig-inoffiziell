# MII PR Onkologie Rezeptorstatus Progesteron - MII IG Kerndatensatz-Modul Onkologie v2026.0.3

* [**Table of Contents**](toc.md)
* [**Artifacts Summary**](artifacts.md)
* **MII PR Onkologie Rezeptorstatus Progesteron**

## Resource Profile: MII PR Onkologie Rezeptorstatus Progesteron 

| | |
| :--- | :--- |
| *Official URL*:https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-mamma-rezeptorstatus-progesteron | *Version*:2026.0.3 |
| Active as of 2026-08-22 | *Computable Name*:MII_PR_Onko_Mamma_Rezeptorstatus_Progesteron |

 
Dieses Profil beschreibt den diagnostischen Progesteron-Rezeptorstatus eines pathologisch untersuchten Probe beim Mamma-Karzinom in der Onkologie 

The **progesterone receptor status profile** documents the diagnostic progesterone receptor status of a pathologically examined specimen in breast cancer. The profile allows both the quantitative measurements (proportion of positive cells, staining intensity) and the interpreted results according to the different definitions to be recorded in detail.

The progesterone receptor status is an important prognostic and predictive biomarker in breast cancer and complements the estrogen receptor status for treatment planning, in particular with regard to anti-hormonal therapy.

### Links to other resources

The profile is closely linked to the other oncology resources:

* references the primary diagnosis (MII_PR_Onko_Diagnose_Primaertumor) via `Observation.focus`
* references the patient (Patient resource) via `Observation.subject`
* can be linked to a specific encounter via `Observation.encounter`

### oBDS context

The profile implements the **oBDS data fields for the progesterone receptor status** in breast cancer. Note that the [oBDS Mamma was originally published in 2015](https://www.basisdatensatz.de/download/Brust.pdf) and that the methodology has undergone considerable change since then.

**Historical vs. current practice:**

* **IRS (Immunreactive Score)**: was still in use in 2015, but is no longer in broad clinical use today, although it remains relevant for registry data
* **Thresholds**: modern pathological practice already treats >1% positive cells as positive (instead of the historical 10% threshold)
* **Assessment approaches**: the current S3 guidelines use definitions other than the original oBDS

**Modelling compromise**: the profile proposed here is a compromise between older registry data, which the current registry framework requires, and the changes in clinical and pathological practice.

**Comment note**: it is open for discussion whether a separate profile for the IRS (Immunreactive Score) should be added in order to represent historical data completely.

### Terminology binding

The profile uses a **dual coding strategy** with an **extensible** binding. This means that the codes from the defined ValueSets SHOULD preferably be used, but that other suitable codes MAY be used where needed.

* ValueSet: MII VS Onko Mamma Rezeptorstatus oBDS
* ValueSet: MII VS Onko Mamma Rezeptorstatus Leitlinie

### Search parameters

The following search parameters are relevant for the Mamma-Progesteron-Rezeptorstatus profile, including in combination:

* The search parameter `_id` MUST be supported: `GET [base]/Observation?_id=12345`
* The search parameter `_profile` MUST be supported: `GET [base]/Observation?_profile=https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-mamma-rezeptorstatus-progesteron`
* The search parameter `code` MUST be supported: `GET [base]/Observation?code=http://loinc.org|85339-0`
* The search parameter `subject` MUST be supported: `GET [base]/Observation?subject=Patient/test`
* The search parameter `patient` MUST be supported: `GET [base]/Observation?patient=Patient/test`
* The search parameter `focus` MUST be supported: `GET [base]/Observation?focus=Condition/primaertumor`
* The search parameter `value-concept` MUST be supported: `GET [base]/Observation?value-concept=http://snomed.info/sct|416053008`
* The search parameter `component-code` MUST be supported: `GET [base]/Observation?component-code=http://snomed.info/sct|1234803000`
* The search parameter `component-value-quantity` MUST be supported: `GET [base]/Observation?component-value-quantity=gt50`

**Usages:**

* Examples for this Profile: [Observation/mii-exa-onko-mamma-rezeptorstatus-progesteron-1](Observation-mii-exa-onko-mamma-rezeptorstatus-progesteron-1.md)
* CapabilityStatements using this Profile: [MII CPS Onkology CapabilityStatement](CapabilityStatement-mii-cps-onko-capabilitystatement.md)

You can also check for [usages in the FHIR IG Statistics](https://packages2.fhir.org/xig/resource/de.medizininformatikinitiative.kerndatensatz.onkologie|current/StructureDefinition/StructureDefinition-mii-pr-onko-mamma-rezeptorstatus-progesteron.json)

### Formal Views of Profile Content

 [Description of Profiles, Differentials, Snapshots, and their representations](http://build.fhir.org/ig/FHIR/ig-guidance/readingIgs.html#structure-definitions). 

 

Other representations of profile: [CSV](../StructureDefinition-mii-pr-onko-mamma-rezeptorstatus-progesteron.csv), [Excel](../StructureDefinition-mii-pr-onko-mamma-rezeptorstatus-progesteron.xlsx), [Schematron](../StructureDefinition-mii-pr-onko-mamma-rezeptorstatus-progesteron.sch) 



## Resource Content

```json
{
  "resourceType" : "StructureDefinition",
  "id" : "mii-pr-onko-mamma-rezeptorstatus-progesteron",
  "url" : "https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-mamma-rezeptorstatus-progesteron",
  "version" : "2026.0.3",
  "name" : "MII_PR_Onko_Mamma_Rezeptorstatus_Progesteron",
  "title" : "MII PR Onkologie Rezeptorstatus Progesteron",
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
  "description" : "Dieses Profil beschreibt den diagnostischen Progesteron-Rezeptorstatus eines pathologisch untersuchten Probe beim Mamma-Karzinom in der Onkologie",
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
      "short" : "Rezeptorstatus Progesteron",
      "definition" : "Rezeptorstatus Progesteron, abgeleitet aus der Immunhistochemie der Mamma-Biopsie oder des Mamma-Exzisionspräparates, basierend auf Zahl der positiven Zellen und Färbeintensität",
      "mustSupport" : true
    },
    {
      "id" : "Observation.code.coding",
      "path" : "Observation.code.coding",
      "patternCoding" : {
        "system" : "http://loinc.org",
        "code" : "85339-0"
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
        "description" : "Slicing für die unterschiedliche Definition von Rezeptorstatus im oBDS und in den S3-Leitlinien",
        "ordered" : false,
        "rules" : "open"
      }
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
        "valueSet" : "https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/ValueSet/mii-vs-onko-mamma-rezeptorstatus-obds"
      }
    },
    {
      "id" : "Observation.value[x].coding:DefinitionOBDS.system",
      "path" : "Observation.value[x].coding.system",
      "min" : 1,
      "patternUri" : "http://loinc.org"
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
        "valueSet" : "https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/ValueSet/mii-vs-onko-mamma-rezeptorstatus-leitlinie"
      }
    },
    {
      "id" : "Observation.value[x].coding:DefinitionLeitlinie.system",
      "path" : "Observation.value[x].coding.system",
      "min" : 1,
      "patternUri" : "https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/CodeSystem/mii-cs-onko-mamma-rezeptorstatus-leitlinie"
    },
    {
      "id" : "Observation.component",
      "path" : "Observation.component",
      "slicing" : {
        "discriminator" : [{
          "type" : "value",
          "path" : "code.coding"
        }],
        "description" : "Slice for Receptor Status Progesteron primary data observations",
        "ordered" : false,
        "rules" : "open"
      },
      "mustSupport" : true
    },
    {
      "id" : "Observation.component:AnteilPositiveZellen",
      "path" : "Observation.component",
      "sliceName" : "AnteilPositiveZellen",
      "min" : 0,
      "max" : "1",
      "mustSupport" : true
    },
    {
      "id" : "Observation.component:AnteilPositiveZellen.code.coding",
      "path" : "Observation.component.code.coding",
      "min" : 1,
      "patternCoding" : {
        "system" : "http://snomed.info/sct",
        "code" : "1234803000",
        "display" : "Percent of cells with progesterone receptor in primary malignant neoplasm of breast by immunohistochemistry"
      }
    },
    {
      "id" : "Observation.component:AnteilPositiveZellen.value[x]",
      "path" : "Observation.component.value[x]",
      "type" : [{
        "code" : "Quantity"
      }],
      "mustSupport" : true
    },
    {
      "id" : "Observation.component:AnteilPositiveZellen.value[x].value",
      "path" : "Observation.component.value[x].value",
      "mustSupport" : true
    },
    {
      "id" : "Observation.component:AnteilPositiveZellen.value[x].unit",
      "path" : "Observation.component.value[x].unit",
      "patternString" : "%"
    },
    {
      "id" : "Observation.component:AnteilPositiveZellen.value[x].system",
      "path" : "Observation.component.value[x].system",
      "patternUri" : "http://unitsofmeasure.org"
    },
    {
      "id" : "Observation.component:AnteilPositiveZellen.value[x].code",
      "path" : "Observation.component.value[x].code",
      "patternCode" : "%"
    },
    {
      "id" : "Observation.component:Faerbeintensitaet",
      "path" : "Observation.component",
      "sliceName" : "Faerbeintensitaet",
      "min" : 0,
      "max" : "1",
      "mustSupport" : true
    },
    {
      "id" : "Observation.component:Faerbeintensitaet.code.coding",
      "path" : "Observation.component.code.coding",
      "min" : 1,
      "patternCoding" : {
        "system" : "http://snomed.info/sct",
        "code" : "1237278006",
        "display" : "Intensity of stain of progesterone receptor in primary malignant neoplasm of breast by immunohistochemistry (observable entity)"
      }
    },
    {
      "id" : "Observation.component:Faerbeintensitaet.value[x]",
      "path" : "Observation.component.value[x]",
      "type" : [{
        "code" : "CodeableConcept"
      }],
      "mustSupport" : true,
      "binding" : {
        "strength" : "extensible",
        "valueSet" : "http://loinc.org/vs/LL4358-9"
      }
    }]
  }
}

```
