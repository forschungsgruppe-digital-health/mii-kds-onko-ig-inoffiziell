# MII PR Onkologie Prostata Gleason Grade Group - MII IG Kerndatensatz-Modul Onkologie v2026.0.3

* [**Inhaltsverzeichnis**](toc.md)
* [**Artefaktübersicht**](artifacts.md)
* **MII PR Onkologie Prostata Gleason Grade Group**

## Ressourcenprofil: MII PR Onkologie Prostata Gleason Grade Group 

| | |
| :--- | :--- |
| *Offizielle URL*:https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-prostate-gleason-grade-group | *Version*:2026.0.3 |
| Active Stand: 2026-08-22 | *Maschinenlesbarer Name*:MII_PR_Onko_Prostata_Gleason_Grade_Group |

 
Dieses Profil beschreibt einen Gleasonscore in der Onkologie 

Dieses Profil beschreibt den Gleason Score und die entsprechende Grade Group bei der histopathologischen Graduierung des Prostatakarzinoms. Der Gleason Score ergibt sich aus der Summe des primären und sekundären Gleason Patterns, während die Grade Group (1-5) eine internationale Standardklassifikation darstellt.

Das Profil basiert auf einer FHIR Observation-Ressource und verwendet LOINC zur Kodierung. Die Grade Group wird als Komponente der Observation dokumentiert.

### Verknüpfungen zu anderen Ressourcen

Der Gleason Score ist eine zentrale histopathologische Bewertung:

* verweist über `Observation.focus` auf die Primärdiagnose (MII_PR_Onko_Diagnose_Primaertumor)
* verweist über `Observation.subject` auf den Patienten (Patient-Ressource)
* kann über `Observation.encounter` mit einem spezifischen Behandlungsfall verknüpft werden
* kann über `Observation.partOf` mit der entsprechenden Biopsie-Procedure verknüpft werden
* kann über `Observation.hasMember` die einzelnen Gleason Pattern-Observations referenzieren

### oBDS-Kontext

Gemäß oBDS P3 wird der Gleason Score als Summe aus primärem und sekundärem Pattern dokumentiert. Die Grade Group stellt eine moderne internationale Klassifikation dar, die in der aktuellen onkologischen Praxis Standard ist.

### Terminologie-Binding

Das ValueSet für Gleason Score-Codes ist **required** gebunden. Die Grade Group-Codes sind ebenfalls **required** gebunden, da sie international standardisiert sind.

* ValueSet: MII VS Onko Prostata Gleason Score

### Suchparameter

Folgende Suchparameter sind für das Prostata-Gleason-Score-Grade-Group Profil relevant, auch in Kombination:

* Der Suchparameter `_id` MUSS unterstützt werden: `GET [base]/Observation?_id=12345`
* Der Suchparameter `_profile` MUSS unterstützt werden: `GET [base]/Observation?_profile=https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-prostate-gleason-grade-group`
* Der Suchparameter `code` MUSS unterstützt werden: `GET [base]/Observation?code=http://loinc.org|44642-7`
* Der Suchparameter `subject` MUSS unterstützt werden: `GET [base]/Observation?subject=Patient/test`
* Der Suchparameter `focus` MUSS unterstützt werden: `GET [base]/Observation?focus=Condition/primaertumor`
* Der Suchparameter `value-concept` MUSS unterstützt werden: `GET [base]/Observation?value-concept=http://snomed.info/sct|369771007`
* Der Suchparameter `component-code` MUSS unterstützt werden: `GET [base]/Observation?component-code=http://loinc.org|79892-6` - Zur Suche nach der Grade Group Komponente.

**Usages:**

* Examples for this Profile: [Observation/mii-exa-onko-prostata-gleason-pattern-grade-group-1](Observation-mii-exa-onko-prostata-gleason-pattern-grade-group-1.md)
* CapabilityStatements using this Profile: [MII CPS Onkology CapabilityStatement](CapabilityStatement-mii-cps-onko-capabilitystatement.md)

You can also check for [usages in the FHIR IG Statistics](https://packages2.fhir.org/xig/resource/de.medizininformatikinitiative.kerndatensatz.onkologie|current/StructureDefinition/StructureDefinition-mii-pr-onko-prostate-gleason-grade-group.json)

### Formale Ansichten des Profilinhalts

 [Beschreibung von Profilen, Differentials, Snapshots und deren Repräsentationen](http://build.fhir.org/ig/FHIR/ig-guidance/readingIgs.html#structure-definitions). 

*  [Schlüsselelemente-Tabelle](#tabs-key) 
*  [Differential-Tabelle](#tabs-diff) 
*  [Snapshot-Tabelle](#tabs-snap) 
*  [Statistiken/Referenzen](#tabs-summ) 
*  [Alle](#tabs-all) 

#### Terminology Bindings

#### Constraints

Diese Struktur ist abgeleitet von [Observation](http://hl7.org/fhir/R4/observation.html) 

#### Terminology Bindings (Differential)

#### Terminology Bindings

#### Constraints

Diese Struktur ist abgeleitet von [Observation](http://hl7.org/fhir/R4/observation.html) 

** Summary **

Mandatory: 2 elements(1 nested mandatory element)
 Must-Support: 8 elements

**Structures**

This structure refers to these other structures:

* [MII PR Onkologie Diagnose Primärtumor (https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-diagnose-primaertumor)](StructureDefinition-mii-pr-onko-diagnose-primaertumor.md)

 **Schlüsselelemente-Ansicht** 

#### Terminology Bindings

#### Constraints

 **Differential-Ansicht** 

Diese Struktur ist abgeleitet von [Observation](http://hl7.org/fhir/R4/observation.html) 

#### Terminology Bindings (Differential)

 **Snapshot-AnsichtView** 

#### Terminology Bindings

#### Constraints

Diese Struktur ist abgeleitet von [Observation](http://hl7.org/fhir/R4/observation.html) 

** Summary **

Mandatory: 2 elements(1 nested mandatory element)
 Must-Support: 8 elements

**Structures**

This structure refers to these other structures:

* [MII PR Onkologie Diagnose Primärtumor (https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-diagnose-primaertumor)](StructureDefinition-mii-pr-onko-diagnose-primaertumor.md)

 

Weitere Repräsentationen des Profils: [CSV](../StructureDefinition-mii-pr-onko-prostate-gleason-grade-group.csv), [Excel](../StructureDefinition-mii-pr-onko-prostate-gleason-grade-group.xlsx), [Schematron](../StructureDefinition-mii-pr-onko-prostate-gleason-grade-group.sch) 



## Resource Content

```json
{
  "resourceType" : "StructureDefinition",
  "id" : "mii-pr-onko-prostate-gleason-grade-group",
  "url" : "https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-prostate-gleason-grade-group",
  "version" : "2026.0.3",
  "name" : "MII_PR_Onko_Prostata_Gleason_Grade_Group",
  "title" : "MII PR Onkologie Prostata Gleason Grade Group",
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
  "description" : "Dieses Profil beschreibt einen Gleasonscore in der Onkologie",
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
      "short" : "Gleason Grade Group",
      "definition" : "Gleason Grade Group. Die Gleason Grade Group ist aus dem Gleason Grade abgeleitet. Score ist ein histopathologisches Klassifikationssystem zur Beurteilung der Morphologie von Adenokarzinomen der Prostata und wird aus der Summe von primären und sekundärem Pattern berechnet.",
      "mustSupport" : true
    },
    {
      "id" : "Observation.code.coding",
      "path" : "Observation.code.coding",
      "patternCoding" : {
        "system" : "http://snomed.info/sct",
        "code" : "1812491000004107",
        "display" : "Histologic grade of primary malignant neoplasm of prostate by International Society of Urological Pathology technique (observable entity)"
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
      "short" : "Datum der Probenentnahme",
      "_short" : {
        "extension" : [{
          "extension" : [{
            "url" : "lang",
            "valueCode" : "de-DE"
          },
          {
            "url" : "content",
            "valueString" : "Datum der Probenentnahme"
          }],
          "url" : "http://hl7.org/fhir/StructureDefinition/translation"
        }]
      },
      "definition" : "Datum der Probenentnahme der Prostata-Biopise oder des Prostata-Exzisats",
      "_definition" : {
        "extension" : [{
          "extension" : [{
            "url" : "lang",
            "valueCode" : "de-DE"
          },
          {
            "url" : "content",
            "valueString" : "Datum der Probenentnahme der Prostata-Biopise oder des Prostata-Exzisats"
          }],
          "url" : "http://hl7.org/fhir/StructureDefinition/translation"
        }]
      },
      "type" : [{
        "code" : "dateTime"
      }],
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
        "valueSet" : "https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/ValueSet/mii-vs-onko-prostata-gleason-score"
      }
    },
    {
      "id" : "Observation.value[x].coding",
      "path" : "Observation.value[x].coding",
      "short" : "Gleason-Score und Grade Group",
      "_short" : {
        "extension" : [{
          "extension" : [{
            "url" : "lang",
            "valueCode" : "de-DE"
          },
          {
            "url" : "content",
            "valueString" : "Gleason-Score und Grade Group"
          }],
          "url" : "http://hl7.org/fhir/StructureDefinition/translation"
        }]
      },
      "definition" : "Gleason-Score und Grade Group einer Prostata-Biopsie oder Operation",
      "_definition" : {
        "extension" : [{
          "extension" : [{
            "url" : "lang",
            "valueCode" : "de-DE"
          },
          {
            "url" : "content",
            "valueString" : "Gleason-Score und Grade Gr einer Prostata-Biopsie oder Operation"
          }],
          "url" : "http://hl7.org/fhir/StructureDefinition/translation"
        }]
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
