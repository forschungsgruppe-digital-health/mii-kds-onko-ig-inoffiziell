# MII CM Onko Strahlentherapie Boost SNOMED Mapping - MII IG Kerndatensatz-Modul Onkologie v2026.0.3

* [**Table of Contents**](toc.md)
* [**Artifacts Summary**](artifacts.md)
* **MII CM Onko Strahlentherapie Boost SNOMED Mapping**

## ConceptMap: MII CM Onko Strahlentherapie Boost SNOMED Mapping 

| | |
| :--- | :--- |
| *Official URL*:https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/ConceptMap/mii-cm-onko-strahlentherapie-boost-sct | *Version*:2026.0.3 |
| Active as of 2024-04-11 | *Computable Name*:MII CM Onko Strahlentherapie Boost SCT Mapping |

 
Mapping Strahlentherapie Boost Codes zu SNOMED-CT 

For every irradiation it is to be stated whether a boost was carried out or not. The temporal integration cannot be represented in SNOMED.



## Resource Content

```json
{
  "resourceType" : "ConceptMap",
  "id" : "mii-cm-onko-strahlentherapie-boost-sct",
  "url" : "https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/ConceptMap/mii-cm-onko-strahlentherapie-boost-sct",
  "version" : "2026.0.3",
  "name" : "MII CM Onko Strahlentherapie Boost SCT Mapping",
  "title" : "MII CM Onko Strahlentherapie Boost SNOMED Mapping",
  "status" : "active",
  "experimental" : false,
  "date" : "2024-04-11",
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
  "description" : "Mapping Strahlentherapie Boost Codes zu SNOMED-CT",
  "jurisdiction" : [{
    "coding" : [{
      "system" : "urn:iso:std:iso:3166",
      "code" : "DE",
      "display" : "Germany"
    }]
  }],
  "purpose" : "Technical mapping to transform oBDS-Data into SNOMED",
  "sourceUri" : "https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/",
  "targetUri" : "http://snomed.info/sct/900000000000207008/version/20240401",
  "group" : [{
    "source" : "https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/CodeSystem/mii-cs-onko-strahlentherapie-boost",
    "target" : "http://snomed.info/sct/900000000000207008/version/20240401",
    "element" : [{
      "code" : "J",
      "display" : "ja, mit Boost o. n. A.",
      "target" : [{
        "code" : "445232009",
        "display" : "Boost radiation therapy (procedure)",
        "equivalence" : "equivalent"
      }]
    },
    {
      "code" : "SIB",
      "display" : "simultan integrierter Boost",
      "target" : [{
        "code" : "445232009",
        "display" : "Boost radiation therapy (procedure)",
        "equivalence" : "wider"
      }]
    },
    {
      "code" : "SEQ",
      "display" : "sequentieller Boost",
      "target" : [{
        "code" : "445232009",
        "display" : "Boost radiation therapy (procedure)",
        "equivalence" : "wider"
      }]
    },
    {
      "code" : "KON",
      "display" : "konkomitanter Boost",
      "target" : [{
        "code" : "445232009",
        "display" : "Boost radiation therapy (procedure)",
        "equivalence" : "wider"
      }]
    },
    {
      "code" : "N",
      "display" : "nein, ohne Boost",
      "target" : [{
        "code" : "373067005",
        "display" : "No (qualifier value)",
        "equivalence" : "equivalent"
      }]
    }]
  }]
}

```
