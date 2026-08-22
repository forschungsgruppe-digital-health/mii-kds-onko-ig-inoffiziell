# MII PR Onkologie TNM-Klassifikation - MII IG Kerndatensatz-Modul Onkologie v2026.0.3

* [**Inhaltsverzeichnis**](toc.md)
* [**Artefaktübersicht**](artifacts.md)
* **MII PR Onkologie TNM-Klassifikation**

## Ressourcenprofil: MII PR Onkologie TNM-Klassifikation 

| | |
| :--- | :--- |
| *Offizielle URL*:https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-tnm-klassifikation | *Version*:2026.0.3 |
| Active Stand: 2026-08-22 | *Maschinenlesbarer Name*:MII_PR_Onko_TNM_Klassifikation |

 
TNM-Klassifikation: Grouper-Profil für Komponenten der TNM-Klassifikation. 

Dieses Profil ist das Gruppierungsprofil für eine TNM-Klassifikation in der Onkologie.

Das Profil enthält das Referenzdatum und dient als Ankerpunkt für alle weiteren TNM-Einzelbeobachtungen zu diesem Zeitpunkt. Das Element `hasMember` enthält Referenzen zu allen verbundenen TNM-Einzelbeobachtungen.

Außerdem wird im Element `value` das UICC-Staging kodiert, dass von den untergeordneten TNM-Beobachtungen abgeleitet ist.

> **Written during migration - review before release.** Verdichtet aus der Suchparameter-Liste der Quellseite (je Parameter ein nummerierter Eintrag mit Beispielabfrage): Für dieses Profil MÜSSEN die Suchparameter `_id`, `_profile`, `status`, `code`, `subject`, `focus`, `encounter`, `date`, `method`, `has-member` und `derived-from` unterstützt werden, auch in Kombination. Die Quellseite rendert außerdem die Mappings dieses Profils auf das Logische Modell Onkologie und auf den [Einheitlichen onkologischen Basisdatensatz (oBDS)](https://basisdatensatz.de/basisdatensatz); diese Mappings sind Bestandteil des Profils.

**Usages:**

* Examples for this Profile: [Observation/TNM-Klassifikation-Observation-2](Observation-TNM-Klassifikation-Observation-2.md), [Observation/mii-exa-onko-ascending-colon-tnm](Observation-mii-exa-onko-ascending-colon-tnm.md), [Observation/mii-exa-onko-colorectal-tnm](Observation-mii-exa-onko-colorectal-tnm.md), [Observation/mii-exa-onko-tnm-klassifikation-TisN0M0](Observation-mii-exa-onko-tnm-klassifikation-TisN0M0.md) and [Observation/mii-exa-onko-tnm-klassifikation-uT2a2pN0023i-sncM1](Observation-mii-exa-onko-tnm-klassifikation-uT2a2pN0023i-sncM1.md)
* CapabilityStatements using this Profile: [MII CPS Onkology CapabilityStatement](CapabilityStatement-mii-cps-onko-capabilitystatement.md)

You can also check for [usages in the FHIR IG Statistics](https://packages2.fhir.org/xig/resource/de.medizininformatikinitiative.kerndatensatz.onkologie|current/StructureDefinition/StructureDefinition-mii-pr-onko-tnm-klassifikation.json)

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

#### Constraints

#### Terminology Bindings

#### Constraints

Diese Struktur ist abgeleitet von [Observation](http://hl7.org/fhir/R4/observation.html) 

** Summary **

Mandatory: 1 element(2 nested mandatory elements)
 Must-Support: 13 elements

**Structures**

This structure refers to these other structures:

* [MII PR Onkologie Diagnose Primärtumor (https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-diagnose-primaertumor)](StructureDefinition-mii-pr-onko-diagnose-primaertumor.md)
* [MII PR Onkologie Specimen (https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-specimen)](StructureDefinition-mii-pr-onko-specimen.md)
* [MII PR Onkologie TNM L-Kategorie (https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-tnm-l-kategorie)](StructureDefinition-mii-pr-onko-tnm-l-kategorie.md)
* [MII PR Onkologie TNM M-Kategorie (https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-tnm-m-kategorie)](StructureDefinition-mii-pr-onko-tnm-m-kategorie.md)
* [MII PR Onkologie TNM m-Symbol (https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-tnm-m-symbol)](StructureDefinition-mii-pr-onko-tnm-m-symbol.md)
* [MII PR Onkologie TNM N-Kategorie (https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-tnm-n-kategorie)](StructureDefinition-mii-pr-onko-tnm-n-kategorie.md)
* [MII PR Onkologie TNM T-Kategorie (https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-tnm-t-kategorie)](StructureDefinition-mii-pr-onko-tnm-t-kategorie.md)
* [MII PR Onkologie TNM Pn-Kategorie (https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-tnm-pn-kategorie)](StructureDefinition-mii-pr-onko-tnm-pn-kategorie.md)
* [MII PR Onkologie TNM S-Kategorie (https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-tnm-s-kategorie)](StructureDefinition-mii-pr-onko-tnm-s-kategorie.md)
* [MII PR Onkologie TNM V-Kategorie (https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-tnm-v-kategorie)](StructureDefinition-mii-pr-onko-tnm-v-kategorie.md)
* [MII PR Onkologie TNM a-Symbol (https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-tnm-a-symbol)](StructureDefinition-mii-pr-onko-tnm-a-symbol.md)
* [MII PR Onkologie TNM r-Symbol (https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-tnm-r-symbol)](StructureDefinition-mii-pr-onko-tnm-r-symbol.md)
* [MII PR Onkologie TNM y-Symbol (https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-tnm-y-symbol)](StructureDefinition-mii-pr-onko-tnm-y-symbol.md)

 **Schlüsselelemente-Ansicht** 

#### Terminology Bindings

#### Constraints

 **Differential-Ansicht** 

Diese Struktur ist abgeleitet von [Observation](http://hl7.org/fhir/R4/observation.html) 

#### Terminology Bindings (Differential)

#### Constraints

 **Snapshot-AnsichtView** 

#### Terminology Bindings

#### Constraints

Diese Struktur ist abgeleitet von [Observation](http://hl7.org/fhir/R4/observation.html) 

** Summary **

Mandatory: 1 element(2 nested mandatory elements)
 Must-Support: 13 elements

**Structures**

This structure refers to these other structures:

* [MII PR Onkologie Diagnose Primärtumor (https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-diagnose-primaertumor)](StructureDefinition-mii-pr-onko-diagnose-primaertumor.md)
* [MII PR Onkologie Specimen (https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-specimen)](StructureDefinition-mii-pr-onko-specimen.md)
* [MII PR Onkologie TNM L-Kategorie (https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-tnm-l-kategorie)](StructureDefinition-mii-pr-onko-tnm-l-kategorie.md)
* [MII PR Onkologie TNM M-Kategorie (https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-tnm-m-kategorie)](StructureDefinition-mii-pr-onko-tnm-m-kategorie.md)
* [MII PR Onkologie TNM m-Symbol (https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-tnm-m-symbol)](StructureDefinition-mii-pr-onko-tnm-m-symbol.md)
* [MII PR Onkologie TNM N-Kategorie (https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-tnm-n-kategorie)](StructureDefinition-mii-pr-onko-tnm-n-kategorie.md)
* [MII PR Onkologie TNM T-Kategorie (https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-tnm-t-kategorie)](StructureDefinition-mii-pr-onko-tnm-t-kategorie.md)
* [MII PR Onkologie TNM Pn-Kategorie (https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-tnm-pn-kategorie)](StructureDefinition-mii-pr-onko-tnm-pn-kategorie.md)
* [MII PR Onkologie TNM S-Kategorie (https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-tnm-s-kategorie)](StructureDefinition-mii-pr-onko-tnm-s-kategorie.md)
* [MII PR Onkologie TNM V-Kategorie (https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-tnm-v-kategorie)](StructureDefinition-mii-pr-onko-tnm-v-kategorie.md)
* [MII PR Onkologie TNM a-Symbol (https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-tnm-a-symbol)](StructureDefinition-mii-pr-onko-tnm-a-symbol.md)
* [MII PR Onkologie TNM r-Symbol (https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-tnm-r-symbol)](StructureDefinition-mii-pr-onko-tnm-r-symbol.md)
* [MII PR Onkologie TNM y-Symbol (https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-tnm-y-symbol)](StructureDefinition-mii-pr-onko-tnm-y-symbol.md)

 

Weitere Repräsentationen des Profils: [CSV](../StructureDefinition-mii-pr-onko-tnm-klassifikation.csv), [Excel](../StructureDefinition-mii-pr-onko-tnm-klassifikation.xlsx), [Schematron](../StructureDefinition-mii-pr-onko-tnm-klassifikation.sch) 



## Resource Content

```json
{
  "resourceType" : "StructureDefinition",
  "id" : "mii-pr-onko-tnm-klassifikation",
  "url" : "https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-tnm-klassifikation",
  "version" : "2026.0.3",
  "name" : "MII_PR_Onko_TNM_Klassifikation",
  "title" : "MII PR Onkologie TNM-Klassifikation",
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
  "description" : "TNM-Klassifikation: Grouper-Profil für Komponenten der TNM-Klassifikation.",
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
      "path" : "Observation"
    },
    {
      "id" : "Observation.meta.profile",
      "path" : "Observation.meta.profile",
      "mustSupport" : true
    },
    {
      "id" : "Observation.status",
      "path" : "Observation.status",
      "mustSupport" : true
    },
    {
      "id" : "Observation.code",
      "path" : "Observation.code",
      "mustSupport" : true,
      "binding" : {
        "strength" : "required",
        "valueSet" : "https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/ValueSet/mii-vs-onko-tnm-klassifikation-typ"
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
      "short" : "TNM-Datum",
      "_short" : {
        "extension" : [{
          "extension" : [{
            "url" : "lang",
            "valueCode" : "de-DE"
          },
          {
            "url" : "content",
            "valueString" : "TNM-Datum"
          }],
          "url" : "http://hl7.org/fhir/StructureDefinition/translation"
        }]
      },
      "definition" : "Datum der TNM-Klassifikation nach 8.1 oBDS 2021",
      "_definition" : {
        "extension" : [{
          "extension" : [{
            "url" : "lang",
            "valueCode" : "de-DE"
          },
          {
            "url" : "content",
            "valueString" : "Datum der TNM-Klassifikation nach 8.1 oBDS 2021"
          }],
          "url" : "http://hl7.org/fhir/StructureDefinition/translation"
        }]
      },
      "type" : [{
        "code" : "dateTime"
      }],
      "constraint" : [{
        "key" : "tnm-datum",
        "severity" : "error",
        "human" : "TNM Datum: Ein exaktes (taggenaues) Datum ist anzugeben.",
        "expression" : "$this.toString().length() >= 8",
        "source" : "https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-tnm-klassifikation"
      }],
      "mustSupport" : true,
      "mapping" : [{
        "identity" : "oBDS",
        "map" : "8.1",
        "comment" : "TNM Datum"
      }]
    },
    {
      "id" : "Observation.value[x]",
      "path" : "Observation.value[x]",
      "type" : [{
        "code" : "CodeableConcept"
      }],
      "mustSupport" : true,
      "binding" : {
        "strength" : "required",
        "valueSet" : "https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/ValueSet/mii-vs-onko-tnm-uicc-stadium"
      }
    },
    {
      "id" : "Observation.value[x].coding",
      "path" : "Observation.value[x].coding",
      "short" : "UICC Stadium",
      "_short" : {
        "extension" : [{
          "extension" : [{
            "url" : "lang",
            "valueCode" : "de-DE"
          },
          {
            "url" : "content",
            "valueString" : "UICC-Staging"
          }],
          "url" : "http://hl7.org/fhir/StructureDefinition/translation"
        }]
      },
      "definition" : "Stadium nach aktuell gültiger TNM-Klassifikation.",
      "_definition" : {
        "extension" : [{
          "extension" : [{
            "url" : "lang",
            "valueCode" : "de-DE"
          },
          {
            "url" : "content",
            "valueString" : "UICC-Staging nach 8.17 oBDS 2021"
          }],
          "url" : "http://hl7.org/fhir/StructureDefinition/translation"
        }]
      }
    },
    {
      "id" : "Observation.value[x].coding.system",
      "path" : "Observation.value[x].coding.system",
      "min" : 1,
      "mustSupport" : true
    },
    {
      "id" : "Observation.value[x].coding.code",
      "path" : "Observation.value[x].coding.code",
      "min" : 1,
      "mustSupport" : true,
      "mapping" : [{
        "identity" : "oBDS",
        "map" : "8.17",
        "comment" : "UICC Stadium"
      }]
    },
    {
      "id" : "Observation.method",
      "path" : "Observation.method",
      "short" : "TNM Version",
      "definition" : "Gibt an, nach welcher Version des TNM klassifiziert wurde.",
      "mustSupport" : true,
      "binding" : {
        "strength" : "required",
        "valueSet" : "https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/ValueSet/mii-vs-onko-tnm-version"
      },
      "mapping" : [{
        "identity" : "oBDS",
        "map" : "8.2",
        "comment" : "TNM Version"
      }]
    },
    {
      "id" : "Observation.method.coding",
      "path" : "Observation.method.coding",
      "short" : "TNM-Version",
      "_short" : {
        "extension" : [{
          "extension" : [{
            "url" : "lang",
            "valueCode" : "de-DE"
          },
          {
            "url" : "content",
            "valueString" : "TNM-Version"
          }],
          "url" : "http://hl7.org/fhir/StructureDefinition/translation"
        }]
      },
      "definition" : "TNM-Version nach 8.5 oBDS 2021",
      "_definition" : {
        "extension" : [{
          "extension" : [{
            "url" : "lang",
            "valueCode" : "de-DE"
          },
          {
            "url" : "content",
            "valueString" : "TNM-Version nach 8.5 oBDS 2021"
          }],
          "url" : "http://hl7.org/fhir/StructureDefinition/translation"
        }]
      }
    },
    {
      "id" : "Observation.specimen",
      "path" : "Observation.specimen",
      "type" : [{
        "code" : "Reference",
        "targetProfile" : ["https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-specimen",
        "http://hl7.org/fhir/StructureDefinition/Specimen"]
      }],
      "mustSupport" : true
    },
    {
      "id" : "Observation.hasMember",
      "path" : "Observation.hasMember",
      "type" : [{
        "code" : "Reference",
        "targetProfile" : ["https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-tnm-l-kategorie",
        "https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-tnm-m-kategorie",
        "https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-tnm-m-symbol",
        "https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-tnm-n-kategorie",
        "https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-tnm-t-kategorie",
        "https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-tnm-pn-kategorie",
        "https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-tnm-s-kategorie",
        "https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-tnm-v-kategorie",
        "https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-tnm-a-symbol",
        "https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-tnm-r-symbol",
        "https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-tnm-y-symbol"]
      }],
      "mustSupport" : true
    }]
  }
}

```
