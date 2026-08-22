# MII EX Onko Histology Morphology Behavior ICDO3 - MII IG Kerndatensatz-Modul Onkologie v2026.0.3

* [**Table of Contents**](toc.md)
* [**Artifacts Summary**](artifacts.md)
* **MII EX Onko Histology Morphology Behavior ICDO3**

## Extension: MII EX Onko Histology Morphology Behavior ICDO3 

| | |
| :--- | :--- |
| *Official URL*:https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-ex-onko-histology-morphology-behavior-icdo3 | *Version*:2026.0.3 |
| Active as of 2026-08-22 | *Computable Name*:MII_EX_Onko_Histology_Morphology_Behavior_ICDO3 |

Extension zur Erfassung von ICDO3 da Morphology nicht als Condition.code. Orientiert sich an mcode-stu3.0.

**Context of Use**

* This extension replaces the previous ICD-O-3 slice in the MII-Diagnose.
* The original profiling built on the ICD-O-3 slice of the `Condition.code` element. At the same time the `Condition.code` field also carries the ICD-10 coding of the oncological diagnosis. During the commenting phase it was noted, however, that an ICD-O-3 morphology describes a clinically different concept than an ICD-10-coded diagnosis. Representing both in the same CodeableConcept therefore contradicts common FHIR modelling conventions. For that reason a modelling as an extension, comparable to mCODE, was chosen. The representation of the ICD-O-3 topography via `Condition.bodySite` is not affected by this. Further histologies carried out as part of a follow-up shall continue to be represented via the Verlaufshistologie profile (Observation.bodySite and Observation.valueCodeableConcept); the present extension is not used there.

**Usage info**

**Usages:**

* Use this Extension: [MII PR Onkologie Diagnose Primärtumor](StructureDefinition-mii-pr-onko-diagnose-primaertumor.md) and [MII PR Onkologie Frühere Tumorerkrankung](StructureDefinition-mii-pr-onko-fruehere-tumorerkrankung.md)
* Examples for this Extension: [Condition/mii-exa-onko-diagnose](Condition-mii-exa-onko-diagnose.md)

You can also check for [usages in the FHIR IG Statistics](https://packages2.fhir.org/xig/resource/de.medizininformatikinitiative.kerndatensatz.onkologie|current/StructureDefinition/StructureDefinition-mii-ex-onko-histology-morphology-behavior-icdo3.json)

### Formal Views of Extension Content

 [Description of Profiles, Differentials, Snapshots, and their representations](http://build.fhir.org/ig/FHIR/ig-guidance/readingIgs.html#structure-definitions). 

 

Other representations of profile: [CSV](../StructureDefinition-mii-ex-onko-histology-morphology-behavior-icdo3.csv), [Excel](../StructureDefinition-mii-ex-onko-histology-morphology-behavior-icdo3.xlsx), [Schematron](../StructureDefinition-mii-ex-onko-histology-morphology-behavior-icdo3.sch) 



## Resource Content

```json
{
  "resourceType" : "StructureDefinition",
  "id" : "mii-ex-onko-histology-morphology-behavior-icdo3",
  "url" : "https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-ex-onko-histology-morphology-behavior-icdo3",
  "version" : "2026.0.3",
  "name" : "MII_EX_Onko_Histology_Morphology_Behavior_ICDO3",
  "title" : "MII EX Onko Histology Morphology Behavior ICDO3",
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
  "description" : "Extension zur Erfassung von ICDO3 da Morphology nicht als Condition.code. Orientiert sich an mcode-stu3.0.",
  "jurisdiction" : [{
    "coding" : [{
      "system" : "urn:iso:std:iso:3166",
      "code" : "DE",
      "display" : "Germany"
    }]
  }],
  "fhirVersion" : "4.0.1",
  "kind" : "complex-type",
  "abstract" : false,
  "context" : [{
    "type" : "element",
    "expression" : "Condition"
  }],
  "type" : "Extension",
  "baseDefinition" : "http://hl7.org/fhir/StructureDefinition/Extension",
  "derivation" : "constraint",
  "differential" : {
    "element" : [{
      "id" : "Extension",
      "path" : "Extension",
      "short" : "MII EX Onko Histology Morphology Behavior ICDO3",
      "definition" : "Extension zur Erfassung von ICDO3 da Morphology nicht als Condition.code. Orientiert sich an mcode-stu3.0."
    },
    {
      "id" : "Extension.extension",
      "path" : "Extension.extension",
      "max" : "0"
    },
    {
      "id" : "Extension.url",
      "path" : "Extension.url",
      "fixedUri" : "https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-ex-onko-histology-morphology-behavior-icdo3"
    },
    {
      "id" : "Extension.value[x]",
      "path" : "Extension.value[x]",
      "min" : 1,
      "type" : [{
        "code" : "CodeableConcept"
      }],
      "binding" : {
        "strength" : "required",
        "valueSet" : "https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/ValueSet/mii-vs-onko-icdo3-morphologie"
      }
    },
    {
      "id" : "Extension.value[x].coding.system",
      "path" : "Extension.value[x].coding.system",
      "min" : 1,
      "fixedUri" : "http://terminology.hl7.org/CodeSystem/icd-o-3"
    },
    {
      "id" : "Extension.value[x].coding.code",
      "path" : "Extension.value[x].coding.code",
      "min" : 1
    },
    {
      "id" : "Extension.value[x].text",
      "path" : "Extension.value[x].text",
      "mustSupport" : true
    }]
  }
}

```
