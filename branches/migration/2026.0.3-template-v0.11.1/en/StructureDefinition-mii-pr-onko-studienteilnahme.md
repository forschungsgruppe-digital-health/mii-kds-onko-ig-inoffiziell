# MII PR Onkologie Studienteilnahme - MII IG Kerndatensatz-Modul Onkologie v2026.0.3

* [**Table of Contents**](toc.md)
* [**Artifacts Summary**](artifacts.md)
* **MII PR Onkologie Studienteilnahme**

## Resource Profile: MII PR Onkologie Studienteilnahme 

| | |
| :--- | :--- |
| *Official URL*:https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-studienteilnahme | *Version*:2026.0.3 |
| Active as of 2026-08-22 | *Computable Name*:MII_PR_Onko_Studienteilnahme |

 
Dieses Profil beschreibt Studienteilnahmen in der Onkologie 

This profile describes whether and when a patient took part in a study.

It contains:

* a reference to Patient
* a reference to the primary diagnosis
*  

| | |
| :--- | :--- |
| the Observation code "709491003 | Enrollment in clinical trial (procedure)" (SNOMED-CT) |

 
* the exact date of first enrolment into a study with an ethics vote
* the status of the study participation (yes, no, unknown)

In the case of a pharmacological study, there SHOULD ideally be a reference to a Procedure / Systemische Therapie, either via Observation.partOf = Reference (SystemischeTherapie), Observation.basedOn = Reference (MedicationRequest); or Procedure.basedOn.

### Referencing studies

Information about the specific study (organization, study ID, study phase, etc.) MAY be provided via the element `Observation.focus[studie]` with a reference to a ResearchStudy resource from the [MII Modul Studie](https://simplifier.net/medizininformatikinitiative-modul-studie).

The ResearchStudy resource enables the structured recording of:

* study identifiers (DRKS, ClinicalTrials.gov, EudraCT, Innovationsfonds project number)
* study type and phase
* primary study objectives
* study context and indication
* study status

A complete example can be found in the PRO-B study participation, which references a ResearchStudy with a DRKS registration (DRKS00024015) and an Innovationsfonds project number (01NVF19013).

### Search parameters

The following search parameters are relevant for the Onkologie module, also in combination:

1. The search parameter `_id` SHALL be supported:Examples:`GET [base]/Observation?_id=1234`Usage notes: further information on searching by "_id" can be found in the [FHIR base specification, section "Parameters for all resources"](http://hl7.org/fhir/R4/search.html#all).
1. The search parameter "_profile" SHALL be supported:Examples:`GET [base]/Observation?_profile=https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-studienteilnahme`Usage notes: further information on searching by "_profile" can be found in the [FHIR base specification, section "token"](http://hl7.org/fhir/R4/search.html#all).
1. The search parameter "code" SHALL be supported:Examples:`GET [base]/Observation?code=http://fhir.de/CodeSystem/sct|709491003`Usage notes: further information on searching by "code" can be found in the FHIR base specification, section "token".
1. The search parameter "subject" SHALL be supported:Examples:`GET [base]/Observation?subject=Patient/example`Usage notes: further information on searching by "subject" can be found in the FHIR base specification, section "reference".
1. The search parameter "focus" SHALL be supported:Examples:`GET [base]/Observation?focus=Condition/example`Usage notes: further information on searching by "focus" can be found in the FHIR base specification, section "reference".
1. The search parameter "encounter" SHALL be supported:Examples:`GET [base]/Observation?encounter=Encounter/example`Usage notes: further information on searching by "encounter" can be found in the FHIR base specification, section "reference".
1. The search parameter "date" SHALL be supported:Examples:`GET [base]/Observation?date=2024-02-08`Usage notes: further information on searching by "date" can be found in the FHIR base specification, section "date".
1. The search parameter "derived-from" SHALL be supported:Examples:`GET [base]/Observation?derived-from=Observation/example`Usage notes: further information on searching by "derived-from" can be found in the FHIR base specification, section "reference".

### Examples

Example 1: simple study participation

Example 2: study participation with a ResearchStudy reference (PRO-B study)

This example shows the documentation of a study participation with a reference to a ResearchStudy resource that contains detailed study information including the DRKS registration and the Innovationsfonds project number.

> **Written during migration - review before release.** The instances behind the two examples are `mii-exa-onko-studienteilnahme` (example 1) and `mii-exa-onko-studienteilnahme-prob` (example 2); the ResearchStudy resource referenced by example 2 is `mii-exa-onko-studie-prob`.

**Usages:**

* Examples for this Profile: [Observation/mii-exa-onko-studienteilnahme-prob](Observation-mii-exa-onko-studienteilnahme-prob.md) and [Observation/mii-exa-onko-studienteilnahme](Observation-mii-exa-onko-studienteilnahme.md)
* CapabilityStatements using this Profile: [MII CPS Onkology CapabilityStatement](CapabilityStatement-mii-cps-onko-capabilitystatement.md)

You can also check for [usages in the FHIR IG Statistics](https://packages2.fhir.org/xig/resource/de.medizininformatikinitiative.kerndatensatz.onkologie|current/StructureDefinition/StructureDefinition-mii-pr-onko-studienteilnahme.json)

### Formal Views of Profile Content

 [Description of Profiles, Differentials, Snapshots, and their representations](http://build.fhir.org/ig/FHIR/ig-guidance/readingIgs.html#structure-definitions). 

 

Other representations of profile: [CSV](../StructureDefinition-mii-pr-onko-studienteilnahme.csv), [Excel](../StructureDefinition-mii-pr-onko-studienteilnahme.xlsx), [Schematron](../StructureDefinition-mii-pr-onko-studienteilnahme.sch) 



## Resource Content

```json
{
  "resourceType" : "StructureDefinition",
  "id" : "mii-pr-onko-studienteilnahme",
  "url" : "https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-studienteilnahme",
  "version" : "2026.0.3",
  "name" : "MII_PR_Onko_Studienteilnahme",
  "title" : "MII PR Onkologie Studienteilnahme",
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
  "description" : "Dieses Profil beschreibt Studienteilnahmen in der Onkologie",
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
        "map" : "24",
        "comment" : "Studienteilnahme"
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
      "short" : "Studienteilnahme laut oBDS",
      "definition" : "SCTID: 709491003 | Enrollment in clinical trial (procedure)",
      "mustSupport" : true
    },
    {
      "id" : "Observation.code.coding",
      "path" : "Observation.code.coding",
      "patternCoding" : {
        "system" : "http://snomed.info/sct",
        "code" : "709491003"
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
      "slicing" : {
        "discriminator" : [{
          "type" : "type",
          "path" : "$this.resolve()"
        }],
        "rules" : "open"
      },
      "mustSupport" : true
    },
    {
      "id" : "Observation.focus:primaertumor",
      "path" : "Observation.focus",
      "sliceName" : "primaertumor",
      "short" : "Referenz zum Primärtumor",
      "definition" : "Referenz zur Primärtumordiagnose, auf die sich die Studienteilnahme bezieht",
      "min" : 0,
      "max" : "1",
      "type" : [{
        "code" : "Reference",
        "targetProfile" : ["https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-diagnose-primaertumor"]
      }],
      "mustSupport" : true
    },
    {
      "id" : "Observation.focus:studie",
      "path" : "Observation.focus",
      "sliceName" : "studie",
      "short" : "Referenz zur Studie",
      "definition" : "Referenz zur konkreten Studie (ResearchStudy), an der der Patient teilnimmt",
      "min" : 0,
      "max" : "1",
      "type" : [{
        "code" : "Reference",
        "targetProfile" : ["http://hl7.org/fhir/StructureDefinition/ResearchStudy"]
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
      "short" : "Studienteilnahme Datum",
      "_short" : {
        "extension" : [{
          "extension" : [{
            "url" : "lang",
            "valueCode" : "de-DE"
          },
          {
            "url" : "content",
            "valueString" : "Studienteilnahme Datum"
          }],
          "url" : "http://hl7.org/fhir/StructureDefinition/translation"
        }]
      },
      "definition" : "Studienteilnahme Datum gemäß 24.2 oBDS 2021",
      "_definition" : {
        "extension" : [{
          "extension" : [{
            "url" : "lang",
            "valueCode" : "de-DE"
          },
          {
            "url" : "content",
            "valueString" : "Studienteilnahme Datum gemäß 24.2 oBDS 2021"
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
        "map" : "24.2",
        "comment" : "Studienteilnahme Datum"
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
        "valueSet" : "https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/ValueSet/mii-vs-onko-studienteilnahme"
      }
    },
    {
      "id" : "Observation.value[x].coding",
      "path" : "Observation.value[x].coding",
      "short" : "Studienteilnahme",
      "_short" : {
        "extension" : [{
          "extension" : [{
            "url" : "lang",
            "valueCode" : "de-DE"
          },
          {
            "url" : "content",
            "valueString" : "Studienteilnahme"
          }],
          "url" : "http://hl7.org/fhir/StructureDefinition/translation"
        }]
      },
      "definition" : "Studienteilnahme gemäß 24.1 oBDS 2021",
      "_definition" : {
        "extension" : [{
          "extension" : [{
            "url" : "lang",
            "valueCode" : "de-DE"
          },
          {
            "url" : "content",
            "valueString" : "Studienteilnahme gemäß 24.1 oBDS 2021"
          }],
          "url" : "http://hl7.org/fhir/StructureDefinition/translation"
        }]
      }
    },
    {
      "id" : "Observation.value[x].coding.system",
      "path" : "Observation.value[x].coding.system",
      "patternUri" : "https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/CodeSystem/mii-cs-onko-studienteilnahme"
    },
    {
      "id" : "Observation.value[x].coding.code",
      "path" : "Observation.value[x].coding.code",
      "min" : 1,
      "mustSupport" : true,
      "mapping" : [{
        "identity" : "oBDS",
        "map" : "24.1",
        "comment" : "Studienteilnahme Status"
      }]
    }]
  }
}

```
