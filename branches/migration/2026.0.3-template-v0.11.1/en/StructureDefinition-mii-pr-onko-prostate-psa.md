# MII PR Onkologie PSA-Wert - MII IG Kerndatensatz-Modul Onkologie v2026.0.3

* [**Table of Contents**](toc.md)
* [**Artifacts Summary**](artifacts.md)
* **MII PR Onkologie PSA-Wert**

## Resource Profile: MII PR Onkologie PSA-Wert 

| | |
| :--- | :--- |
| *Official URL*:https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-prostate-psa | *Version*:2026.0.3 |
| Active as of 2026-08-22 | *Computable Name*:MII_PR_Onko_Prostata_PSA |

 
Dieses Profil beschreibt den PSA-Wert sowohl beim Monitoring als auch in der Verlaufskontrolle in der Onkologie 

This profile describes the PSA value (prostate-specific antigen) in patients with prostate cancer in oncology. The PSA value is a central tumour marker for diagnosis, follow-up and therapy monitoring in prostate cancer.

The profile is based on a FHIR Observation resource and uses LOINC to code the observed parameter. PSA values can be documented both as total PSA and as free PSA.

### Links to other resources

The PSA value is an important tumour-specific observation:

* references the primary diagnosis (MII_PR_Onko_Diagnose_Primaertumor) via `Observation.focus`
* references the patient (Patient resource) via `Observation.subject`
* can be linked to a specific encounter via `Observation.encounter`

### oBDS context

According to oBDS P1, the PSA value is documented as a tumour marker for diagnosis and follow-up. Both diagnostic and follow-up PSA values can be recorded.

### Terminology binding

The ValueSet for PSA codes is bound as **required**, because LOINC codes for PSA determinations are standardised and unambiguously defined.

#### PSA codes

* **Free PSA**: LOINC 10886-0 "Prostate specific antigen Free [Mass/volume] in Serum or Plasma"

### Search parameters

The following search parameters are relevant for the Prostata-PSA profile, including in combination:

* The search parameter `_id` MUST be supported: `GET [base]/Observation?_id=12345`
* The search parameter `_profile` MUST be supported: `GET [base]/Observation?_profile=https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-prostate-psa`
* The search parameter `code` MUST be supported: `GET [base]/Observation?code=http://loinc.org|2857-1`
* The search parameter `subject` MUST be supported: `GET [base]/Observation?subject=Patient/test`
* The search parameter `focus` MUST be supported: `GET [base]/Observation?focus=Condition/primaertumor`
* The search parameter `value-quantity` MUST be supported: `GET [base]/Observation?value-quantity=gt5.0`

**Usages:**

* Examples for this Profile: [Observation/mii-exa-onko-prostata-psa-diagnose-1](Observation-mii-exa-onko-prostata-psa-diagnose-1.md) and [Observation/mii-exa-onko-prostata-psa-verlauf-1](Observation-mii-exa-onko-prostata-psa-verlauf-1.md)
* CapabilityStatements using this Profile: [MII CPS Onkology CapabilityStatement](CapabilityStatement-mii-cps-onko-capabilitystatement.md)

You can also check for [usages in the FHIR IG Statistics](https://packages2.fhir.org/xig/resource/de.medizininformatikinitiative.kerndatensatz.onkologie|current/StructureDefinition/StructureDefinition-mii-pr-onko-prostate-psa.json)

### Formal Views of Profile Content

 [Description of Profiles, Differentials, Snapshots, and their representations](http://build.fhir.org/ig/FHIR/ig-guidance/readingIgs.html#structure-definitions). 

 

Other representations of profile: [CSV](../StructureDefinition-mii-pr-onko-prostate-psa.csv), [Excel](../StructureDefinition-mii-pr-onko-prostate-psa.xlsx), [Schematron](../StructureDefinition-mii-pr-onko-prostate-psa.sch) 



## Resource Content

```json
{
  "resourceType" : "StructureDefinition",
  "id" : "mii-pr-onko-prostate-psa",
  "url" : "https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-prostate-psa",
  "version" : "2026.0.3",
  "name" : "MII_PR_Onko_Prostata_PSA",
  "title" : "MII PR Onkologie PSA-Wert",
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
  "description" : "Dieses Profil beschreibt den PSA-Wert sowohl beim Monitoring als auch in der Verlaufskontrolle in der Onkologie",
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
        "map" : "P7",
        "comment" : "PSA-Wert"
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
      "short" : "PSA-Wert",
      "definition" : "PSA-Wert wie im oBDS definiert. Der PSA-Wert ist ein Tumormarker, der bei der Diagnostik und Verlaufskontrolle von Prostatakrebs verwendet wird. Er wird in ng/ml gemessen. Bei Vorliegen kann dieser Datenpunkt auch durch eine Observation aus dem Labormodul abgebildet werden. ",
      "mustSupport" : true
    },
    {
      "id" : "Observation.code.coding",
      "path" : "Observation.code.coding",
      "binding" : {
        "strength" : "required",
        "valueSet" : "https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/ValueSet/mii-vs-onko-prostata-psa-loinc"
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
      "slicing" : {
        "discriminator" : [{
          "type" : "type",
          "path" : "$this"
        }],
        "ordered" : false,
        "rules" : "open"
      }
    },
    {
      "id" : "Observation.effective[x]:effectiveDateTime",
      "path" : "Observation.effective[x]",
      "sliceName" : "effectiveDateTime",
      "min" : 0,
      "max" : "1",
      "type" : [{
        "code" : "dateTime"
      }],
      "mapping" : [{
        "identity" : "oBDS",
        "map" : "P8",
        "comment" : "Datum PSA-Wert (oBDS 238)"
      }]
    },
    {
      "id" : "Observation.value[x]",
      "path" : "Observation.value[x]",
      "short" : "PSA-Wert",
      "_short" : {
        "extension" : [{
          "extension" : [{
            "url" : "lang",
            "valueCode" : "de-DE"
          },
          {
            "url" : "content",
            "valueString" : "PSA-Wert"
          }],
          "url" : "http://hl7.org/fhir/StructureDefinition/translation"
        }]
      },
      "definition" : "PSA-Wert aus Blut/Plasma in ng/ml",
      "_definition" : {
        "extension" : [{
          "extension" : [{
            "url" : "lang",
            "valueCode" : "de-DE"
          },
          {
            "url" : "content",
            "valueString" : "PSA-Wert aus Blut/Plasma in ng/ml"
          }],
          "url" : "http://hl7.org/fhir/StructureDefinition/translation"
        }]
      },
      "min" : 1,
      "type" : [{
        "code" : "Quantity"
      }],
      "mustSupport" : true
    },
    {
      "id" : "Observation.value[x].value",
      "path" : "Observation.value[x].value",
      "min" : 1,
      "mapping" : [{
        "identity" : "oBDS",
        "map" : "P7",
        "comment" : "PSA-Wert (oBDS 237)"
      }]
    },
    {
      "id" : "Observation.value[x].unit",
      "path" : "Observation.value[x].unit",
      "patternString" : "ng/ml"
    },
    {
      "id" : "Observation.value[x].system",
      "path" : "Observation.value[x].system",
      "patternUri" : "http://unitsofmeasure.org"
    },
    {
      "id" : "Observation.value[x].code",
      "path" : "Observation.value[x].code",
      "patternCode" : "ng/mL"
    }]
  }
}

```
