# MII PR Onkologie Genetische Variante - MII IG Kerndatensatz-Modul Onkologie v2026.0.3

* [**Table of Contents**](toc.md)
* [**Artifacts Summary**](artifacts.md)
* **MII PR Onkologie Genetische Variante**

## Resource Profile: MII PR Onkologie Genetische Variante 

| | |
| :--- | :--- |
| *Official URL*:https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-genetische-variante | *Version*:2026.0.3 |
| Active as of 2026-08-22 | *Computable Name*:MII_PR_Onko_Genetische_Variante |

 
Genetische Variante wie im oBDS beschrieben 

### Context

Information on genetic variants has been recorded as part of the oBDS since the 2021 version. A variant is recorded via two data fields:

* 'Genetische Variante Name' as free text
* 'Genetische Variante Ausprägung' as oBDS-specific codes for the interpretation.

With the Molekulargenetischer Befundbericht (MolGenBB), the MII already offers a structure for the exchange of genetic findings. The MolGenBB is based on the GenomicReport (version STU2) of the international HL7 Clinical Genomics Working Group and uses international terminologies and nomenclatures such as:

* **HGNC** for the unambiguous description of gene names
* **HGVS** for the description of variants in the coding and non-coding DNA region as well as for proteins
* **ISCN** for the description of cytogenomic position and structural variants
* **Sequence Ontology** for the semantic annotation of the variants

It can be assumed that the genetic laboratories and bioinformatic pipelines work on the basis of these classifications or are able to map to them.

The coarse-grained recording of the variant data in the oBDS, however, makes a direct mapping to the terminologies and nomenclatures named above impossible.

### Conformance statements

Where possible, a more precise variant description **SHOULD** be done via the MII Variante.

An integration of these variants **SHOULD** be done by embedding them in the MII Molekulargenetischer Befundbericht `DiagnosticReport` and the MII Molekulargenetische Anforderung `ServiceRequest`.

In the event that these modules cannot be implemented at the DIZ sites at all, not yet, or only partially, a direct mapping of the oBDS fields onto the following fields **SHALL** be done:

* `Observation.note` for the variant name
* `Observation.interpretation` for the expression of the variant.

### Overview of the MII Variante

The variant profile of the Molekularer Befundbericht can be found here: https://simplifier.net/medizininformatikinitiative-modulomics/sdmiimolgenvariante

When using the MII Variante, the following data fields are mandatory for conformance:

* `subject`: reference to a Patient
* `code`: fixed LOINC code (69548-6) identifying it as an examination of a genetic variant
* `status`: HL7 status
* `category`: fixed HL7 code classifying it as a laboratory value

In addition, the following details can optionally be provided:

* `specimen`: reference to the biospecimen
* `method`: methodology of the examination
* `valueCodeableConcept`: variant assessment (present, not present, not called, indeterminate)
* `component`: all further details on the methodological execution and evaluation as well as variant information

### Search parameters

The following search parameters are relevant for the Onkologie module, also in combination:

1. The search parameter `_id` SHALL be supported:Examples:`GET [base]/Observation?_id=1234`Usage notes: further information on searching by "_id" can be found in the [FHIR base specification, section "Parameters for all resources"](http://hl7.org/fhir/R4/search.html#all).
1. The search parameter `_profile` SHALL be supported:Examples:`GET [base]/Observation?_profile=https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-genetische-variante`Usage notes: further information on searching by "_profile" can be found in the [FHIR base specification, section "token"](http://hl7.org/fhir/R4/search.html#all).
1. The search parameter "status" SHALL be supported:Examples:`GET [base]/Observation?status=final`Usage notes: further information on searching by "status" can be found in the FHIR base specification, section "token".
1. The search parameter "category" SHALL be supported:Examples:`GET [base]/Observation?category=http://terminology.hl7.org/CodeSystem/observation-category|laboratory`Usage notes: further information on searching by "category" can be found in the FHIR base specification, section "token".
1. The search parameter "code" SHALL be supported:Examples:`GET [base]/Observation?code=http://fhir.de/CodeSystem/sct|184305005`Usage notes: further information on searching by "code" can be found in the FHIR base specification, section "token".
1. The search parameter "subject" SHALL be supported:Examples:`GET [base]/Observation?subject=Patient/example`Usage notes: further information on searching by "subject" can be found in the FHIR base specification, section "reference".
1. The search parameter "focus" SHALL be supported:Examples:`GET [base]/Observation?focus=Condition/example`Usage notes: further information on searching by "focus" can be found in the FHIR base specification, section "reference".
1. The search parameter "encounter" SHALL be supported:Examples:`GET [base]/Observation?encounter=Encounter/example`Usage notes: further information on searching by "encounter" can be found in the FHIR base specification, section "reference".
1. The search parameter "interpretation" SHALL be supported:Examples:`GET [base]/Observation?interpretation=http://snomed.info/sct|55446002`Usage notes: further information on searching by "interpretation" can be found in the FHIR base specification, section "token".
1. The search parameter "method" SHALL be supported:Examples:`GET [base]/Observation?method=http://loinc.org|LA26398-0`Usage notes: further information on searching by "method" can be found in the FHIR base specification, section "token".
1. The search parameter "specimen" SHALL be supported:Examples:`GET [base]/Observation?specimen=Specimen/example`Usage notes: further information on searching by "specimen" can be found in the FHIR base specification, section "reference".
1. The search parameter "device" SHALL be supported:Examples:`GET [base]/Observation?device-from=Device/example`Usage notes: further information on searching by "device" can be found in the FHIR base specification, section "reference".
1. The search parameter "derived-from" SHALL be supported:Examples:`GET [base]/Observation?derived-from=Observation/example`Usage notes: further information on searching by "derived-from" can be found in the FHIR base specification, section "reference".

### Examples

> **Written during migration - review before release.** The instance `mii-exa-onko-genetische-variante-braf` in this guide illustrates the profile.

**Usages:**

* Examples for this Profile: [Observation/mii-exa-onko-genetische-variante-braf](Observation-mii-exa-onko-genetische-variante-braf.md)
* CapabilityStatements using this Profile: [MII CPS Onkology CapabilityStatement](CapabilityStatement-mii-cps-onko-capabilitystatement.md)

You can also check for [usages in the FHIR IG Statistics](https://packages2.fhir.org/xig/resource/de.medizininformatikinitiative.kerndatensatz.onkologie|current/StructureDefinition/StructureDefinition-mii-pr-onko-genetische-variante.json)

### Formal Views of Profile Content

 [Description of Profiles, Differentials, Snapshots, and their representations](http://build.fhir.org/ig/FHIR/ig-guidance/readingIgs.html#structure-definitions). 

 

Other representations of profile: [CSV](../StructureDefinition-mii-pr-onko-genetische-variante.csv), [Excel](../StructureDefinition-mii-pr-onko-genetische-variante.xlsx), [Schematron](../StructureDefinition-mii-pr-onko-genetische-variante.sch) 



## Resource Content

```json
{
  "resourceType" : "StructureDefinition",
  "id" : "mii-pr-onko-genetische-variante",
  "url" : "https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-genetische-variante",
  "version" : "2026.0.3",
  "name" : "MII_PR_Onko_Genetische_Variante",
  "title" : "MII PR Onkologie Genetische Variante",
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
  "description" : "Genetische Variante wie im oBDS beschrieben",
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
    "identity" : "MII-KDS",
    "name" : "MII KDS Mapping"
  }],
  "kind" : "resource",
  "abstract" : false,
  "type" : "Observation",
  "baseDefinition" : "https://www.medizininformatik-initiative.de/fhir/ext/modul-molgen/StructureDefinition/variante",
  "derivation" : "constraint",
  "differential" : {
    "element" : [{
      "id" : "Observation",
      "path" : "Observation",
      "mapping" : [{
        "identity" : "oBDS",
        "map" : "23",
        "comment" : "Genetische Variante"
      }]
    },
    {
      "id" : "Observation.meta.profile",
      "path" : "Observation.meta.profile",
      "mustSupport" : true
    },
    {
      "id" : "Observation.subject",
      "path" : "Observation.subject",
      "type" : [{
        "code" : "Reference",
        "targetProfile" : ["http://hl7.org/fhir/StructureDefinition/Patient"]
      }]
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
      "slicing" : {
        "discriminator" : [{
          "type" : "type",
          "path" : "$this"
        }],
        "ordered" : false,
        "rules" : "closed"
      },
      "type" : [{
        "code" : "CodeableConcept"
      }]
    },
    {
      "id" : "Observation.value[x]:valueCodeableConcept",
      "path" : "Observation.value[x]",
      "sliceName" : "valueCodeableConcept",
      "type" : [{
        "code" : "CodeableConcept"
      }],
      "mustSupport" : true
    },
    {
      "id" : "Observation.value[x]:valueCodeableConcept.coding.system",
      "path" : "Observation.value[x].coding.system",
      "mustSupport" : true
    },
    {
      "id" : "Observation.value[x]:valueCodeableConcept.coding.code",
      "path" : "Observation.value[x].coding.code",
      "mustSupport" : true
    },
    {
      "id" : "Observation.interpretation",
      "path" : "Observation.interpretation",
      "slicing" : {
        "discriminator" : [{
          "type" : "type",
          "path" : "$this"
        }],
        "rules" : "open"
      },
      "mustSupport" : true,
      "mapping" : [{
        "identity" : "oBDS",
        "map" : "23.2",
        "comment" : "Genetische Variante Ausprägung"
      }]
    },
    {
      "id" : "Observation.interpretation:oBDS",
      "path" : "Observation.interpretation",
      "sliceName" : "oBDS",
      "min" : 0,
      "max" : "1",
      "binding" : {
        "strength" : "required",
        "valueSet" : "https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/ValueSet/mii-vs-onko-genetische-variante-auspraegung"
      }
    },
    {
      "id" : "Observation.interpretation:oBDS.coding",
      "path" : "Observation.interpretation.coding",
      "short" : "Genetische Variante Ausprägung",
      "_short" : {
        "extension" : [{
          "extension" : [{
            "url" : "lang",
            "valueCode" : "de-DE"
          },
          {
            "url" : "content",
            "valueString" : "Genetische Variante Ausprägung"
          }],
          "url" : "http://hl7.org/fhir/StructureDefinition/translation"
        }]
      },
      "definition" : "Genetische Variante Ausprägung gemäß 23.1 oBDS 2021",
      "_definition" : {
        "extension" : [{
          "extension" : [{
            "url" : "lang",
            "valueCode" : "de-DE"
          },
          {
            "url" : "content",
            "valueString" : "Genetische Variante Ausprägung gemäß 23.2 oBDS 2021"
          }],
          "url" : "http://hl7.org/fhir/StructureDefinition/translation"
        }]
      }
    },
    {
      "id" : "Observation.interpretation:oBDS.coding.system",
      "path" : "Observation.interpretation.coding.system",
      "mustSupport" : true
    },
    {
      "id" : "Observation.interpretation:oBDS.coding.code",
      "path" : "Observation.interpretation.coding.code",
      "mustSupport" : true
    },
    {
      "id" : "Observation.note",
      "path" : "Observation.note",
      "mustSupport" : true,
      "mapping" : [{
        "identity" : "oBDS",
        "map" : "23.1",
        "comment" : "Genetische Variante Name"
      }]
    },
    {
      "id" : "Observation.note.text",
      "path" : "Observation.note.text",
      "short" : "Genetische Variante Name",
      "_short" : {
        "extension" : [{
          "extension" : [{
            "url" : "lang",
            "valueCode" : "de-DE"
          },
          {
            "url" : "content",
            "valueString" : "Genetische Variante Name"
          }],
          "url" : "http://hl7.org/fhir/StructureDefinition/translation"
        }]
      },
      "definition" : "Genetische Variante Name gemäß 23.1 oBDS 2021",
      "_definition" : {
        "extension" : [{
          "extension" : [{
            "url" : "lang",
            "valueCode" : "de-DE"
          },
          {
            "url" : "content",
            "valueString" : "Genetische Variante Name gemäß 23.1 oBDS 2021"
          }],
          "url" : "http://hl7.org/fhir/StructureDefinition/translation"
        }]
      },
      "mustSupport" : true
    },
    {
      "id" : "Observation.specimen",
      "path" : "Observation.specimen",
      "short" : "Tumor-Specimen aus dem die Variante bestimmt wurde",
      "definition" : "Referenz auf die Tumorprobe (Specimen), aus der die genetische Variante bestimmt wurde. Optional, da die Methodik auch über GenomicStudy abgebildet werden kann.",
      "type" : [{
        "code" : "Reference",
        "targetProfile" : ["https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-specimen"]
      }]
    }]
  }
}

```
