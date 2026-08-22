# MII PR Onkologie Mamma Operation - MII IG Kerndatensatz-Modul Onkologie v2026.0.3

* [**Table of Contents**](toc.md)
* [**Artifacts Summary**](artifacts.md)
* **MII PR Onkologie Mamma Operation**

## Resource Profile: MII PR Onkologie Mamma Operation 

| | |
| :--- | :--- |
| *Official URL*:https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-mamma-operation | *Version*:2026.0.3 |
| Active as of 2026-08-22 | *Computable Name*:MII_PR_Onko_Mamma_Operation |

 
Das vorliegende Profil beschreibt operative Eingriffe an der Brust im Rahmen der Mammakarzinom-Behandlung. Es erweitert das allgemeine Operationsprofil um Mamma-spezifische Aspekte und ermöglicht die detaillierte Erfassung von brustchirurgischen Verfahren. 

The **Mamma-Operation profile** documents surgical interventions on the breast as part of breast cancer treatment. This profile extends the general MII_PR_Onko_Operation profile with breast-specific aspects and allows breast surgery procedures to be recorded in detail.

The profile supports breast-conserving therapies as well as mastectomies, together with accompanying procedures such as lymph node removal and the use of intraoperative aids.

**Comment note**: it is open for discussion whether pre-operative marking should be modelled as a separate additional resource (as currently implemented) or simply as usedCode with pre-operative and intraoperative slices.

> **Written during migration - review before release.** The source page declared its subject as the canonical `.../StructureDefinition/mii-pr-onko-mamma-intraoperatives-imaging-specimen`, which does not exist as an artefact in this guide. Its content describes the breast surgery Procedure profile, so this note was attached to [MII_PR_Onko_Mamma_Operation](StructureDefinition-mii-pr-onko-mamma-operation.md) and the `_profile` search example below was re-pointed to that canonical. Please confirm the intended profile.

### Links to other resources

The profile is closely linked to the other oncology resources:

* references the primary diagnosis (MII_PR_Onko_Diagnose_Primaertumor) via `Procedure.reasonReference`
* references the patient (Patient resource) via `Procedure.subject`
* can be linked to superordinate operations via `Procedure.partOf`
* can be linked to a specific encounter via `Procedure.encounter`

### oBDS context

The profile implements **breast-specific surgical data** as an extension of the general oBDS operation data set (section 13). Breast surgery covers several procedures:

**Surgical procedures:**

* **Breast-conserving therapy (BET)**: lumpectomy, segmental resection, quadrantectomy
* **Mastectomy**: simple, modified radical, radical mastectomy
* **Lymph node surgery**: sentinel lymph node biopsy, axillary dissection
* **Reconstructive procedures**: immediate reconstruction, secondary reconstruction

**Intraoperative aids:**

* **Wire markings**: pre-operative localisation of non-palpable tumours
* **Seed markings**: radioactive marking for tumour localisation
* **Marker clips**: orientation aids for follow-up
* **Intraoperative imaging**: specimen radiography, ultrasound

### Terminology binding

The profile uses a **dual coding strategy** with SNOMED CT and OPS:

* ValueSet: MII VS Onko Mamma Operation SNOMED CT
* ValueSet: MII VS Onko Mamma Operation OPS

### Search parameters

The following search parameters are relevant for the Mamma-Operation profile, including in combination:

* The search parameter `_id` MUST be supported: `GET [base]/Procedure?_id=12345`
* The search parameter `_profile` MUST be supported: `GET [base]/Procedure?_profile=https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-mamma-operation`
* The search parameter `code` MUST be supported: `GET [base]/Procedure?code=http://snomed.info/sct|392090004`
* The search parameter `subject` MUST be supported: `GET [base]/Procedure?subject=Patient/test`
* The search parameter `patient` MUST be supported: `GET [base]/Procedure?patient=Patient/test`
* The search parameter `reason-reference` MUST be supported: `GET [base]/Procedure?reason-reference=Condition/primaertumor`
* The search parameter `part-of` MUST be supported: `GET [base]/Procedure?part-of=Procedure/hauptoperation`
* The search parameter `date` MUST be supported: `GET [base]/Procedure?date=2024-01-15`

**Usages:**

* CapabilityStatements using this Profile: [MII CPS Onkology CapabilityStatement](CapabilityStatement-mii-cps-onko-capabilitystatement.md)
* This Profile is not used by any profiles in this Specification

You can also check for [usages in the FHIR IG Statistics](https://packages2.fhir.org/xig/resource/de.medizininformatikinitiative.kerndatensatz.onkologie|current/StructureDefinition/StructureDefinition-mii-pr-onko-mamma-operation.json)

### Formal Views of Profile Content

 [Description of Profiles, Differentials, Snapshots, and their representations](http://build.fhir.org/ig/FHIR/ig-guidance/readingIgs.html#structure-definitions). 

 

Other representations of profile: [CSV](../StructureDefinition-mii-pr-onko-mamma-operation.csv), [Excel](../StructureDefinition-mii-pr-onko-mamma-operation.xlsx), [Schematron](../StructureDefinition-mii-pr-onko-mamma-operation.sch) 



## Resource Content

```json
{
  "resourceType" : "StructureDefinition",
  "id" : "mii-pr-onko-mamma-operation",
  "extension" : [{
    "url" : "http://hl7.org/fhir/StructureDefinition/artifact-versionAlgorithm",
    "valueCoding" : {
      "system" : "http://hl7.org/fhir/version-algorithm",
      "code" : "semver",
      "display" : "SemVer"
    }
  },
  {
    "url" : "http://hl7.org/fhir/StructureDefinition/cqf-knowledgeCapability",
    "valueCode" : "shareable"
  },
  {
    "url" : "http://hl7.org/fhir/StructureDefinition/cqf-knowledgeCapability",
    "valueCode" : "publishable"
  },
  {
    "url" : "http://hl7.org/fhir/StructureDefinition/artifact-versionPolicy",
    "valueCodeableConcept" : {
      "coding" : [{
        "system" : "http://terminology.hl7.org/CodeSystem/artifact-version-policy-codes",
        "code" : "package",
        "display" : "Package"
      }]
    }
  },
  {
    "url" : "http://hl7.org/fhir/StructureDefinition/artifact-usage",
    "valueMarkdown" : "Use this profile as the technical FHIR representation of the corresponding Medical Informatics Initiative logical model. The profile constrains a base FHIR resource for the MII module context by specifying how elements are used, which elements are required or not used, which extensions and terminology bindings apply, and how the resource maps to the module-specific content model. Implementers should produce and consume resource instances that conform to this profile when exchanging data for the corresponding MII module."
  },
  {
    "url" : "http://hl7.org/fhir/StructureDefinition/artifact-topic",
    "valueCodeableConcept" : {
      "coding" : [{
        "system" : "http://ncicb.nci.nih.gov/xml/owl/EVS/Thesaurus.owl",
        "code" : "C25218"
      }]
    }
  },
  {
    "url" : "http://hl7.org/fhir/StructureDefinition/artifact-author",
    "valueContactDetail" : {
      "telecom" : [{
        "system" : "email",
        "value" : "julian.sass@charite.de"
      }]
    }
  },
  {
    "url" : "http://hl7.org/fhir/StructureDefinition/artifact-editor",
    "valueContactDetail" : {
      "name" : "Taskforce Core Data Set"
    }
  },
  {
    "url" : "http://hl7.org/fhir/StructureDefinition/artifact-reviewer",
    "valueContactDetail" : {
      "name" : "Interoperability Working Group",
      "telecom" : [{
        "system" : "url",
        "value" : "https://www.medizininformatik-initiative.de/en/collaboration/interoperability-working-group"
      }]
    }
  },
  {
    "url" : "http://hl7.org/fhir/StructureDefinition/artifact-reviewer",
    "valueContactDetail" : {
      "name" : "National Steering Committee",
      "telecom" : [{
        "system" : "url",
        "value" : "https://www.medizininformatik-initiative.de/en/collaboration/national-steering-committee"
      }]
    }
  },
  {
    "url" : "http://hl7.org/fhir/StructureDefinition/artifact-endorser",
    "valueContactDetail" : {
      "name" : "Interoperability Working Group",
      "telecom" : [{
        "system" : "url",
        "value" : "https://www.medizininformatik-initiative.de/en/collaboration/interoperability-working-group"
      }]
    }
  },
  {
    "url" : "http://hl7.org/fhir/StructureDefinition/artifact-endorser",
    "valueContactDetail" : {
      "name" : "National Steering Committee",
      "telecom" : [{
        "system" : "url",
        "value" : "https://www.medizininformatik-initiative.de/en/collaboration/national-steering-committee"
      }]
    }
  },
  {
    "url" : "http://hl7.org/fhir/StructureDefinition/resource-approvalDate",
    "valueDate" : "2024-03-07"
  },
  {
    "url" : "http://hl7.org/fhir/StructureDefinition/resource-effectivePeriod",
    "valuePeriod" : {
      "start" : "2026"
    }
  }],
  "url" : "https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-mamma-operation",
  "version" : "2026.0.3",
  "name" : "MII_PR_Onko_Mamma_Operation",
  "title" : "MII PR Onkologie Mamma Operation",
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
  "description" : "Das vorliegende Profil beschreibt operative Eingriffe an der Brust im Rahmen der Mammakarzinom-Behandlung. Es erweitert das allgemeine Operationsprofil um Mamma-spezifische Aspekte und ermöglicht die detaillierte Erfassung von brustchirurgischen Verfahren.",
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
  "baseDefinition" : "https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-operation",
  "derivation" : "constraint",
  "differential" : {
    "element" : [{
      "id" : "Procedure",
      "path" : "Procedure"
    },
    {
      "id" : "Procedure.partOf",
      "path" : "Procedure.partOf",
      "type" : [{
        "code" : "Reference",
        "targetProfile" : ["https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-operation"]
      }]
    },
    {
      "id" : "Procedure.code",
      "path" : "Procedure.code",
      "short" : "Operation der Brust",
      "definition" : "Operation der Brust, z.B. Exzision eines Tumors, Entfernung eines Lymphknotens"
    },
    {
      "id" : "Procedure.code.coding:ops",
      "path" : "Procedure.code.coding",
      "sliceName" : "ops",
      "binding" : {
        "strength" : "required",
        "valueSet" : "https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/ValueSet/mii-vs-onko-mamma-operation-ops"
      }
    },
    {
      "id" : "Procedure.code.coding:sct",
      "path" : "Procedure.code.coding",
      "sliceName" : "sct",
      "binding" : {
        "strength" : "required",
        "valueSet" : "https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/ValueSet/mii-vs-onko-mamma-operation-sct"
      }
    },
    {
      "id" : "Procedure.reasonReference",
      "path" : "Procedure.reasonReference",
      "type" : [{
        "code" : "Reference",
        "targetProfile" : ["https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-diagnose-primaertumor"]
      }]
    },
    {
      "id" : "Procedure.usedCode",
      "path" : "Procedure.usedCode",
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
      "id" : "Procedure.usedCode:IntraoperativesImaging",
      "path" : "Procedure.usedCode",
      "sliceName" : "IntraoperativesImaging",
      "short" : "Intraoperatives Präparateröntgen/Sonografie",
      "definition" : "Bildgebende Verfahren zur intraoperativen Beurteilung des Resektats (Mammografie, Sonografie, etc.)",
      "min" : 0,
      "max" : "*",
      "mustSupport" : true
    },
    {
      "id" : "Procedure.usedCode:IntraoperativesImaging.coding",
      "path" : "Procedure.usedCode.coding",
      "binding" : {
        "strength" : "extensible",
        "valueSet" : "https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/ValueSet/mii-vs-onko-mamma-intraoperatives-imaging-praeparat"
      }
    },
    {
      "id" : "Procedure.usedCode:PraeoperativeMarkierung",
      "path" : "Procedure.usedCode",
      "sliceName" : "PraeoperativeMarkierung",
      "short" : "Präoperative Markierung",
      "definition" : "Modalität der präoperativen Markierung (Drahtmarkierung, Markierungsclips, Seed-Markierung)",
      "min" : 0,
      "max" : "*",
      "mustSupport" : true
    },
    {
      "id" : "Procedure.usedCode:PraeoperativeMarkierung.coding",
      "path" : "Procedure.usedCode.coding",
      "binding" : {
        "strength" : "extensible",
        "valueSet" : "https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/ValueSet/mii-vs-onko-mamma-praeoperative-markierung-modalitaet"
      }
    }]
  }
}

```
