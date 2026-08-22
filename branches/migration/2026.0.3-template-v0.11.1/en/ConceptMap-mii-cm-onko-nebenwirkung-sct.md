# MII CM Onko Nebenwirkung SNOMED Mapping - MII IG Kerndatensatz-Modul Onkologie v2026.0.3

* [**Table of Contents**](toc.md)
* [**Artifacts Summary**](artifacts.md)
* **MII CM Onko Nebenwirkung SNOMED Mapping**

## ConceptMap: MII CM Onko Nebenwirkung SNOMED Mapping 

| | |
| :--- | :--- |
| *Official URL*:https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/ConceptMap/mii-cm-onko-nebenwirkung-sct | *Version*:2026.0.3 |
| Active as of 2024-04-10 | *Computable Name*:MII CM Onko Nebenwirkung SCT Mapping |

 
Mapping Nebenwirkung CTCAE Codes zu SNOMED-CT 

The CTCAE severity grade of adverse events can be represented well in SNOMED.



## Resource Content

```json
{
  "resourceType" : "ConceptMap",
  "id" : "mii-cm-onko-nebenwirkung-sct",
  "url" : "https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/ConceptMap/mii-cm-onko-nebenwirkung-sct",
  "version" : "2026.0.3",
  "name" : "MII CM Onko Nebenwirkung SCT Mapping",
  "title" : "MII CM Onko Nebenwirkung SNOMED Mapping",
  "status" : "active",
  "experimental" : false,
  "date" : "2024-04-10",
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
  "description" : "Mapping Nebenwirkung CTCAE Codes zu SNOMED-CT",
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
    "source" : "https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/CodeSystem/mii-cs-onko-nebenwirkung-ctcae-grad",
    "target" : "http://snomed.info/sct/900000000000207008/version/20240401",
    "element" : [{
      "code" : "K",
      "display" : "keine",
      "target" : [{
        "code" : "260413007",
        "display" : "None (qualifier value)",
        "equivalence" : "equivalent"
      }]
    },
    {
      "code" : "1",
      "display" : "mild",
      "target" : [{
        "code" : "255604002",
        "display" : "Mild (qualifier value)",
        "equivalence" : "equivalent"
      }]
    },
    {
      "code" : "2",
      "display" : "moderat",
      "target" : [{
        "code" : "1255665007",
        "display" : "Moderate (qualifier value)",
        "equivalence" : "equivalent"
      }]
    },
    {
      "code" : "3",
      "display" : "schwerwiegend",
      "target" : [{
        "code" : "24484000",
        "display" : "Severe (severity modifier) (qualifier value)",
        "equivalence" : "equivalent"
      }]
    },
    {
      "code" : "4",
      "display" : "lebensbedrohlich",
      "target" : [{
        "code" : "442452003",
        "display" : "Life threatening severity (qualifier value)",
        "equivalence" : "equivalent"
      }]
    },
    {
      "code" : "5",
      "display" : "tödlich",
      "target" : [{
        "code" : "399166001",
        "display" : "Fatal (qualifier value)",
        "equivalence" : "equivalent"
      }]
    },
    {
      "code" : "U",
      "display" : "unbekannt",
      "target" : [{
        "code" : "261665006",
        "display" : "Unknown (qualifier value)",
        "equivalence" : "equivalent"
      }]
    }]
  }]
}

```
