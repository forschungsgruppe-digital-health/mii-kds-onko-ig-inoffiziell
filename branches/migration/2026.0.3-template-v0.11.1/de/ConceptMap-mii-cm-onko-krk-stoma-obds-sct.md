# Mapping oBDS Stoma-Anzeichnung zu SNOMED CT - MII IG Kerndatensatz-Modul Onkologie v2026.0.3

* [**Inhaltsverzeichnis**](toc.md)
* [**Artefaktübersicht**](artifacts.md)
* **Mapping oBDS Stoma-Anzeichnung zu SNOMED CT**

## ConceptMap: Mapping oBDS Stoma-Anzeichnung zu SNOMED CT (Experimentell) 

| | |
| :--- | :--- |
| *Offizielle URL*:https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/ConceptMap/mii-cm-onko-krk-stoma-obds-sct | *Version*:2026.0.3 |
| Active Stand: 2026-08-22 | *Maschinenlesbarer Name*: |

 
Mapping der oBDS-Codes für präoperative Stoma-Anzeichnung zu SNOMED CT 



## Resource Content

```json
{
  "resourceType" : "ConceptMap",
  "id" : "mii-cm-onko-krk-stoma-obds-sct",
  "url" : "https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/ConceptMap/mii-cm-onko-krk-stoma-obds-sct",
  "version" : "2026.0.3",
  "title" : "Mapping oBDS Stoma-Anzeichnung zu SNOMED CT",
  "status" : "active",
  "experimental" : true,
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
  "description" : "Mapping der oBDS-Codes für präoperative Stoma-Anzeichnung zu SNOMED CT",
  "jurisdiction" : [{
    "coding" : [{
      "system" : "urn:iso:std:iso:3166",
      "code" : "DE",
      "display" : "Germany"
    }]
  }],
  "sourceCanonical" : "https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/ValueSet/mii-vs-onko-krk-stoma-anzeichnung",
  "group" : [{
    "source" : "https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/CodeSystem/mii-cs-onko-krk-stoma-anzeichnung",
    "target" : "http://snomed.info/sct",
    "targetVersion" : "http://snomed.info/sct/900000000000207008/version/20250701",
    "element" : [{
      "code" : "K",
      "display" : "Kein Stoma",
      "target" : [{
        "code" : "428119001",
        "display" : "Procedure not indicated (situation)",
        "equivalence" : "equivalent"
      }]
    },
    {
      "code" : "N",
      "display" : "Anzeichnung nicht durchgeführt",
      "target" : [{
        "code" : "262008008",
        "display" : "Not performed (qualifier value)",
        "equivalence" : "equivalent"
      }]
    },
    {
      "code" : "S",
      "display" : "Stoma angelegt, Anzeichnungsstatus unbekannt",
      "target" : [{
        "code" : "373068000",
        "display" : "Undetermined (qualifier value)",
        "equivalence" : "equivalent"
      }]
    },
    {
      "code" : "U",
      "display" : "Unbekannt",
      "target" : [{
        "code" : "261665006",
        "display" : "Unknown",
        "equivalence" : "equivalent"
      }]
    }]
  }]
}

```
