# MII CM Onko Allgemeiner Leistungszustand SNOMED Mapping - MII IG Kerndatensatz-Modul Onkologie v2026.0.3

* [**Table of Contents**](toc.md)
* [**Artifacts Summary**](artifacts.md)
* **MII CM Onko Allgemeiner Leistungszustand SNOMED Mapping**

## ConceptMap: MII CM Onko Allgemeiner Leistungszustand SNOMED Mapping 

| | |
| :--- | :--- |
| *Official URL*:https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/ConceptMap/mii-cm-onko-allgemeiner-leistungszustand-sct | *Version*:2026.0.3 |
| Active as of 2024-04-11 | *Computable Name*:mii-cm-onko-allgemeiner-leistungszustand-sct |

 
Mapping Allgemeiner Leistungszustand Codes zu SNOMED-CT 

> **Written during migration - review before release.** This ConceptMap maps the oBDS answer list for the general performance status (ECOG, codes 0 to 4 and U) onto SNOMED-CT.



## Resource Content

```json
{
  "resourceType" : "ConceptMap",
  "id" : "mii-cm-onko-allgemeiner-leistungszustand-sct",
  "url" : "https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/ConceptMap/mii-cm-onko-allgemeiner-leistungszustand-sct",
  "version" : "2026.0.3",
  "name" : "mii-cm-onko-allgemeiner-leistungszustand-sct",
  "title" : "MII CM Onko Allgemeiner Leistungszustand SNOMED Mapping",
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
  "description" : "Mapping Allgemeiner Leistungszustand Codes zu SNOMED-CT",
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
    "source" : "https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/CodeSystem/mii-cs-onko-allgemeiner-leistungszustand-ecog",
    "target" : "http://snomed.info/sct/900000000000207008/version/20240401",
    "element" : [{
      "code" : "0",
      "display" : "Normale, uneingeschränkte Aktivität wie vor der Erkrankung (90 - 100 % nach Karnofsky)",
      "target" : [{
        "code" : "425389002",
        "display" : "Eastern Cooperative Oncology Group performance status - grade 0 (finding)",
        "equivalence" : "equivalent"
      }]
    },
    {
      "code" : "1",
      "display" : "Einschränkung bei körperlicher Anstrengung, aber gehfähig; leichte körperliche Arbeit bzw. Arbeit im Sitzen (z. B. leichte Hausarbeit oder Büroarbeit) möglich (70 - 80 % nach Karnofsky)",
      "target" : [{
        "code" : "422512005",
        "display" : "Eastern Cooperative Oncology Group performance status - grade 1 (finding)",
        "equivalence" : "equivalent"
      }]
    },
    {
      "code" : "2",
      "display" : "Gehfähig, Selbstversorgung möglich, aber nicht arbeitsfähig; kann mehr als 50 % der Wachzeit aufstehen (50 - 60 % nach Karnofsky)",
      "target" : [{
        "code" : "422894000",
        "display" : "Eastern Cooperative Oncology Group performance status - grade 2 (finding)",
        "equivalence" : "equivalent"
      }]
    },
    {
      "code" : "3",
      "display" : "Nur begrenzte Selbstversorgung möglich; ist 50 % oder mehr der Wachzeit an Bett oder Stuhl gebunden (30  40 % nach Karnofsky)",
      "target" : [{
        "code" : "423053003",
        "display" : "Eastern Cooperative Oncology Group performance status - grade 3 (finding)",
        "equivalence" : "equivalent"
      }]
    },
    {
      "code" : "4",
      "display" : "Völlig pflegebedürftig, keinerlei Selbstversorgung möglich; völlig an Bett oder Stuhl gebunden (10 - 20 % nach Karnofsky)",
      "target" : [{
        "code" : "423237006",
        "display" : "Eastern Cooperative Oncology Group performance status - grade 4 (finding)",
        "equivalence" : "equivalent"
      }]
    },
    {
      "code" : "U",
      "display" : "Unbekannt",
      "target" : [{
        "code" : "261665006",
        "display" : "Unknown (qualifier value)",
        "equivalence" : "equivalent"
      }]
    }]
  }]
}

```
