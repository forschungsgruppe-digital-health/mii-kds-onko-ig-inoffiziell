# MII EX Onko Operation Urgency - MII IG Kerndatensatz-Modul Onkologie v2026.0.3

* [**Table of Contents**](toc.md)
* [**Artifacts Summary**](artifacts.md)
* **MII EX Onko Operation Urgency**

## Extension: MII EX Onko Operation Urgency 

| | |
| :--- | :--- |
| *Official URL*:https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-ex-onko-operation-urgency | *Version*:2026.0.3 |
| Active as of 2026-08-22 | *Computable Name*:MII_EX_Onko_Operation_Urgency |

Modalität der Eingriffsdurchführung (Art des Eingriffs) im Rahmen des oBDS (KR6)

**Context of Use**

This extension captures the **modality under which the intervention was performed** (Art des Eingriffs) and distinguishes between elective and emergency interventions.

### Origin and scope

This data point originally comes from the organ-specific module **Kolorektales Karzinom (KRK 6)** as per oBDS 2021. Since the distinction between elective and emergency interventions is, however, clinically relevant for all surgical procedures, the extension was integrated into the general Operation profile and can be **applied universally to all oncological surgeries**.

### Clinical relevance

Recording the intervention modality is important for several reasons:

* **Quality assurance**: emergency interventions often show different complication rates than planned interventions
* **Risk stratification**: urgency influences perioperative morbidity and mortality
* **Statistical analyses**: fair comparisons between centres require the share of emergencies to be taken into account
* **Resource planning**: distinction between plannable and unplanned interventions

### Value range

The values come from the CodeSystem `mii-cs-onko-operation-urgency`:

* **E**: Elektiveingriff (planned intervention)
* **N**: Notfalleingriff (emergency intervention)
* **U**: Unbekannt (unknown)

### Mapping

Mapping [Einheitlicher onkologischer Basisdatensatz (oBDS)](https://basisdatensatz.de/basisdatensatz) to FHIR

This extension maps to the **KRK module** field:

* **KR6**: Art des Eingriffs (modality under which the intervention was performed)

### Related profiles

* Operation: `mii-pr-onko-operation`
* Extension Intention: `mii-ex-onko-operation-intention`

**Usage info**

**Usages:**

* Use this Extension: [MII PR Onkologie Operation](StructureDefinition-mii-pr-onko-operation.md)

You can also check for [usages in the FHIR IG Statistics](https://packages2.fhir.org/xig/resource/de.medizininformatikinitiative.kerndatensatz.onkologie|current/StructureDefinition/StructureDefinition-mii-ex-onko-operation-urgency.json)

### Formal Views of Extension Content

 [Description of Profiles, Differentials, Snapshots, and their representations](http://build.fhir.org/ig/FHIR/ig-guidance/readingIgs.html#structure-definitions). 

 

Other representations of profile: [CSV](../StructureDefinition-mii-ex-onko-operation-urgency.csv), [Excel](../StructureDefinition-mii-ex-onko-operation-urgency.xlsx), [Schematron](../StructureDefinition-mii-ex-onko-operation-urgency.sch) 



## Resource Content

```json
{
  "resourceType" : "StructureDefinition",
  "id" : "mii-ex-onko-operation-urgency",
  "url" : "https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-ex-onko-operation-urgency",
  "version" : "2026.0.3",
  "name" : "MII_EX_Onko_Operation_Urgency",
  "title" : "MII EX Onko Operation Urgency",
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
  "description" : "Modalität der Eingriffsdurchführung (Art des Eingriffs) im Rahmen des oBDS (KR6)",
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
  }],
  "kind" : "complex-type",
  "abstract" : false,
  "context" : [{
    "type" : "element",
    "expression" : "Procedure"
  }],
  "type" : "Extension",
  "baseDefinition" : "http://hl7.org/fhir/StructureDefinition/Extension",
  "derivation" : "constraint",
  "differential" : {
    "element" : [{
      "id" : "Extension",
      "path" : "Extension",
      "short" : "MII EX Onko Operation Urgency",
      "definition" : "Modalität der Eingriffsdurchführung (Art des Eingriffs) im Rahmen des oBDS (KR6)"
    },
    {
      "id" : "Extension.extension",
      "path" : "Extension.extension",
      "max" : "0"
    },
    {
      "id" : "Extension.url",
      "path" : "Extension.url",
      "fixedUri" : "https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-ex-onko-operation-urgency"
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
        "valueSet" : "https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/ValueSet/mii-vs-onko-operation-urgency"
      },
      "mapping" : [{
        "identity" : "oBDS",
        "map" : "KR6",
        "comment" : "Art des Eingriffs (Modalität der Eingriffsdurchführung: E=Elektiveingriff, N=Notfalleingriff, U=Unbekannt)"
      }]
    },
    {
      "id" : "Extension.value[x].coding.system",
      "path" : "Extension.value[x].coding.system",
      "min" : 1,
      "fixedUri" : "https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/CodeSystem/mii-cs-onko-operation-urgency"
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
