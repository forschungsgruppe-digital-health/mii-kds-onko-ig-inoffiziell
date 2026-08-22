# MII CM Onko Therapie Stellung SNOMED Mapping - MII IG Kerndatensatz-Modul Onkologie v2026.0.3

* [**Table of Contents**](toc.md)
* [**Artifacts Summary**](artifacts.md)
* **MII CM Onko Therapie Stellung SNOMED Mapping**

## ConceptMap: MII CM Onko Therapie Stellung SNOMED Mapping 

| | |
| :--- | :--- |
| *Official URL*:https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/ConceptMap/mii-cm-onko-therapie-stellung-sct | *Version*:2026.0.3 |
| Active as of 2024-04-11 | *Computable Name*:MII CM Onko Therapie Stellung SNOMED Mapping |

 
Mapping Therapie Stellung Codes zu SNOMED-CT 

The relation to a surgical therapy is stated both for radiotherapy and for systemic therapy.



## Resource Content

```json
{
  "resourceType" : "ConceptMap",
  "id" : "mii-cm-onko-therapie-stellung-sct",
  "url" : "https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/ConceptMap/mii-cm-onko-therapie-stellung-sct",
  "version" : "2026.0.3",
  "name" : "MII CM Onko Therapie Stellung SNOMED Mapping",
  "title" : "MII CM Onko Therapie Stellung SNOMED Mapping",
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
  "description" : "Mapping Therapie Stellung Codes zu SNOMED-CT",
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
    "source" : "https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/CodeSystem/mii-cs-onko-therapie-stellungzurop",
    "target" : "http://snomed.info/sct/900000000000207008/version/20240401",
    "element" : [{
      "code" : "O",
      "display" : "ohne Bezug zur operativen Therapie",
      "target" : [{
        "equivalence" : "unmatched"
      }]
    },
    {
      "code" : "A",
      "display" : "adjuvant",
      "target" : [{
        "code" : "373846009",
        "display" : "Adjuvant - intent (qualifier value)",
        "equivalence" : "equivalent"
      }]
    },
    {
      "code" : "N",
      "display" : "neoadjuvant",
      "target" : [{
        "code" : "373847000",
        "display" : "Neo-adjuvant - intent (qualifier value)",
        "equivalence" : "equivalent"
      }]
    },
    {
      "code" : "I",
      "display" : "intraoperativ",
      "target" : [{
        "code" : "277671009",
        "display" : "Intraoperative (qualifier value)",
        "equivalence" : "equivalent"
      }]
    },
    {
      "code" : "Z",
      "display" : "additiv",
      "target" : [{
        "code" : "260364009",
        "display" : "Additive (qualifier value)",
        "equivalence" : "equivalent"
      }]
    },
    {
      "code" : "S",
      "display" : "Sonstiges",
      "target" : [{
        "code" : "74964007",
        "display" : "Other (qualifier value)",
        "equivalence" : "equivalent"
      }]
    }]
  }]
}

```
