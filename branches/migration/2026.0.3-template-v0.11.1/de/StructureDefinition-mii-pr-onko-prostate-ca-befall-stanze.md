# MII PR Onkologie Ca-Befall Stanze - MII IG Kerndatensatz-Modul Onkologie v2026.0.3

* [**Inhaltsverzeichnis**](toc.md)
* [**Artefaktübersicht**](artifacts.md)
* **MII PR Onkologie Ca-Befall Stanze**

## Ressourcenprofil: MII PR Onkologie Ca-Befall Stanze 

| | |
| :--- | :--- |
| *Offizielle URL*:https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-prostate-ca-befall-stanze | *Version*:2026.0.3 |
| Active Stand: 2026-08-22 | *Maschinenlesbarer Name*:MII_PR_Onko_Prostata_CA_Befall_Stanze |

 
Dieses Profil beschreibt den prozentualen Befall der am stärksten befallenen Stanze einer Prostata-Biopsie oder eines Prostata-Exzisionspräparates in der Onkologie 

Dieses Profil beschreibt den prozentualen Befall der am stärksten befallenen Stanze einer Prostata-Biopsie oder eines Prostata-Exzisionspräparates in der Onkologie. Diese Angabe ist ein wichtiger histopathologischer Parameter zur Beurteilung der Tumorausdehnung und Aggressivität bei Prostatakarzinom.

Das Profil basiert auf einer FHIR Observation-Ressource und verwendet LOINC zur Kodierung des beobachteten Parameters. Der Wert wird als Prozentsatz angegeben und bezieht sich auf die am stärksten befallene Stanze der Biopsie.

### Verknüpfungen zu anderen Ressourcen

Der Karzinom-Befall der Stanze ist eine wichtige histopathologische Beobachtung:

* verweist über `Observation.focus` auf die Primärdiagnose (MII_PR_Onko_Diagnose_Primaertumor)
* verweist über `Observation.subject` auf den Patienten (Patient-Ressource)
* kann über `Observation.encounter` mit einem spezifischen Behandlungsfall verknüpft werden
* kann über `Observation.specimen` mit der entsprechenden Gewebeprobe verknüpft werden

### oBDS-Kontext

Gemäß oBDS P4.3 wird der prozentuale Karzinombefall der am stärksten befallenen Stanze einer Prostata-Biopsie dokumentiert. Dies ist ein wichtiger Parameter für die histopathologische Beurteilung der Tumorausdehnung.

### Terminologie-Binding

Das Profil verwendet einen **required** LOINC-Code für die eindeutige Identifikation der Beobachtung:

#### Karzinom-Befall Code

* **LOINC**: 44654-2 "Tissue involved by tumor in Prostate tumor"

### Suchparameter

Folgende Suchparameter sind für das Prostata-Karzinom-Befall-Stanze Profil relevant, auch in Kombination:

* Der Suchparameter `_id` MUSS unterstützt werden: `GET [base]/Observation?_id=12345`
* Der Suchparameter `_profile` MUSS unterstützt werden: `GET [base]/Observation?_profile=https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-prostate-ca-befall-stanze`
* Der Suchparameter `code` MUSS unterstützt werden: `GET [base]/Observation?code=http://loinc.org|44654-2`
* Der Suchparameter `subject` MUSS unterstützt werden: `GET [base]/Observation?subject=Patient/test`
* Der Suchparameter `focus` MUSS unterstützt werden: `GET [base]/Observation?focus=Condition/primaertumor`
* Der Suchparameter `value-quantity` MUSS unterstützt werden: `GET [base]/Observation?value-quantity=gt50`

**Usages:**

* Examples for this Profile: [Observation/mii-exa-onko-prostata-ca-befall-stanze-1](Observation-mii-exa-onko-prostata-ca-befall-stanze-1.md)
* CapabilityStatements using this Profile: [MII CPS Onkology CapabilityStatement](CapabilityStatement-mii-cps-onko-capabilitystatement.md)

You can also check for [usages in the FHIR IG Statistics](https://packages2.fhir.org/xig/resource/de.medizininformatikinitiative.kerndatensatz.onkologie|current/StructureDefinition/StructureDefinition-mii-pr-onko-prostate-ca-befall-stanze.json)

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

#### Terminology Bindings

#### Constraints

Diese Struktur ist abgeleitet von [Observation](http://hl7.org/fhir/R4/observation.html) 

** Summary **

Mandatory: 3 elements
 Must-Support: 7 elements

**Structures**

This structure refers to these other structures:

* [MII PR Onkologie Diagnose Primärtumor (https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-diagnose-primaertumor)](StructureDefinition-mii-pr-onko-diagnose-primaertumor.md)

 **Schlüsselelemente-Ansicht** 

#### Terminology Bindings

#### Constraints

 **Differential-Ansicht** 

Diese Struktur ist abgeleitet von [Observation](http://hl7.org/fhir/R4/observation.html) 

 **Snapshot-AnsichtView** 

#### Terminology Bindings

#### Constraints

Diese Struktur ist abgeleitet von [Observation](http://hl7.org/fhir/R4/observation.html) 

** Summary **

Mandatory: 3 elements
 Must-Support: 7 elements

**Structures**

This structure refers to these other structures:

* [MII PR Onkologie Diagnose Primärtumor (https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-diagnose-primaertumor)](StructureDefinition-mii-pr-onko-diagnose-primaertumor.md)

 

Weitere Repräsentationen des Profils: [CSV](../StructureDefinition-mii-pr-onko-prostate-ca-befall-stanze.csv), [Excel](../StructureDefinition-mii-pr-onko-prostate-ca-befall-stanze.xlsx), [Schematron](../StructureDefinition-mii-pr-onko-prostate-ca-befall-stanze.sch) 



## Resource Content

```json
{
  "resourceType" : "StructureDefinition",
  "id" : "mii-pr-onko-prostate-ca-befall-stanze",
  "url" : "https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-prostate-ca-befall-stanze",
  "version" : "2026.0.3",
  "name" : "MII_PR_Onko_Prostata_CA_Befall_Stanze",
  "title" : "MII PR Onkologie Ca-Befall Stanze",
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
  "description" : "Dieses Profil beschreibt den prozentualen Befall der am stärksten befallenen Stanze einer Prostata-Biopsie oder eines Prostata-Exzisionspräparates in der Onkologie",
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
      "short" : "Prozentualer Karzinombefall",
      "definition" : "Prozentualer Karzinombefall der am stärksten befallenen Stanze einer Prostata-Biopsie oder eines Prostata-Exzisionspräparates. ",
      "mustSupport" : true
    },
    {
      "id" : "Observation.code.coding",
      "path" : "Observation.code.coding",
      "patternCoding" : {
        "system" : "http://loinc.org",
        "code" : "44654-2",
        "display" : "Tissue involved by tumor in Prostate tumor"
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
      "short" : "Prozentualer Karzinombefall",
      "_short" : {
        "extension" : [{
          "extension" : [{
            "url" : "lang",
            "valueCode" : "de-DE"
          },
          {
            "url" : "content",
            "valueString" : "Prozentualer Karzinombefall"
          }],
          "url" : "http://hl7.org/fhir/StructureDefinition/translation"
        }]
      },
      "definition" : "Prozentualer Karzinombefall der am stärksten befallenen Stanze einer Prostata-Biopsie",
      "_definition" : {
        "extension" : [{
          "extension" : [{
            "url" : "lang",
            "valueCode" : "de-DE"
          },
          {
            "url" : "content",
            "valueString" : "Prozentualer Karzinombefall der am stärksten befallenen Stanze einer Prostata-Biopsie"
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
      "min" : 1
    },
    {
      "id" : "Observation.value[x].unit",
      "path" : "Observation.value[x].unit",
      "patternString" : "%"
    },
    {
      "id" : "Observation.value[x].system",
      "path" : "Observation.value[x].system",
      "patternUri" : "http://unitsofmeasure.org"
    },
    {
      "id" : "Observation.value[x].code",
      "path" : "Observation.value[x].code",
      "patternCode" : "%"
    },
    {
      "id" : "Observation.specimen",
      "path" : "Observation.specimen",
      "mustSupport" : true
    }]
  }
}

```
