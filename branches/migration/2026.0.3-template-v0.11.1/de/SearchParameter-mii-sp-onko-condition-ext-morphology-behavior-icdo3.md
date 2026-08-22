# mii-sp-onko-condition-ext-morphology-behavior-icdo3 - MII IG Kerndatensatz-Modul Onkologie v2026.0.3

* [**Inhaltsverzeichnis**](toc.md)
* [**Artefaktübersicht**](artifacts.md)
* **mii-sp-onko-condition-ext-morphology-behavior-icdo3**

## SearchParameter: mii-sp-onko-condition-ext-morphology-behavior-icdo3 (Experimentell) 

| | |
| :--- | :--- |
| *Offizielle URL*:https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/SearchParameter/mii-sp-onko-condition-ext-morphology-behavior-icdo3 | *Version*:2026.0.3 |
| Active Stand: 2024-04-15 | *Maschinenlesbarer Name*:MII_SP_Condition_Extension_Morphology_Behaviour_ICD-O-3 |

 
SearchParameter for Condition.extension[morphology-behaviour-icdo3] 



## Resource Content

```json
{
  "resourceType" : "SearchParameter",
  "id" : "mii-sp-onko-condition-ext-morphology-behavior-icdo3",
  "meta" : {
    "profile" : ["https://www.medizininformatik-initiative.de/fhir/modul-meta/StructureDefinition/mii-pr-meta-searchparameter"]
  },
  "extension" : [{
    "url" : "https://www.medizininformatik-initiative.de/fhir/modul-meta/StructureDefinition/mii-ex-meta-license-codeable",
    "valueCodeableConcept" : {
      "coding" : [{
        "system" : "http://hl7.org/fhir/spdx-license",
        "code" : "CC-BY-4.0",
        "display" : "Creative Commons Attribution 4.0 International"
      }]
    }
  }],
  "url" : "https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/SearchParameter/mii-sp-onko-condition-ext-morphology-behavior-icdo3",
  "version" : "2026.0.3",
  "name" : "MII_SP_Condition_Extension_Morphology_Behaviour_ICD-O-3",
  "status" : "active",
  "experimental" : true,
  "date" : "2024-04-15",
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
  "description" : "SearchParameter for Condition.extension[morphology-behaviour-icdo3]",
  "jurisdiction" : [{
    "coding" : [{
      "system" : "urn:iso:std:iso:3166",
      "code" : "DE",
      "display" : "Germany"
    }]
  }],
  "code" : "morphology-behavior-icdo3",
  "base" : ["Condition"],
  "type" : "token",
  "expression" : "Condition.extension.where(url='https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-ex-onko-histology-morphology-behavior-icdo3').value"
}

```
