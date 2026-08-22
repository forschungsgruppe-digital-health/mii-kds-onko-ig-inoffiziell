# MII VS Onkologie Nebenwirkung nach CTCAE Art - MII IG Kerndatensatz-Modul Onkologie v2026.0.3

* [**Inhaltsverzeichnis**](toc.md)
* [**Artefaktübersicht**](artifacts.md)
* **MII VS Onkologie Nebenwirkung nach CTCAE Art**

## ValueSet: MII VS Onkologie Nebenwirkung nach CTCAE Art 

| | |
| :--- | :--- |
| *Offizielle URL*:https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/ValueSet/mii-vs-onko-nebenwirkung-art | *Version*:2026.0.3 |
| Active Stand: 2026-08-22 | *Maschinenlesbarer Name*:MII_VS_Onko_Nebenwirkung_Art |

 
oBDS-spezifisches ValueSet für Nebenwirkung nach CTCAE oder MedDRA code 

 **References** 

* [MII PR Onkologie Nebenwirkung von Strahlentherapie und systemische Therapie](StructureDefinition-mii-pr-onko-nebenwirkung-adverse-event.md)

### Logical Definition (CLD)

 

### Expansion

No Expansion for this valueset (Unknown Code System)

-------

 [Beschreibung der obigen Tabelle(n)](http://build.fhir.org/ig/FHIR/ig-guidance/readingIgs.html#terminology). 



## Resource Content

```json
{
  "resourceType" : "ValueSet",
  "id" : "mii-vs-onko-nebenwirkung-art",
  "meta" : {
    "profile" : ["http://hl7.org/fhir/StructureDefinition/shareablevalueset"]
  },
  "url" : "https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/ValueSet/mii-vs-onko-nebenwirkung-art",
  "version" : "2026.0.3",
  "name" : "MII_VS_Onko_Nebenwirkung_Art",
  "title" : "MII VS Onkologie Nebenwirkung nach CTCAE Art",
  "status" : "active",
  "experimental" : false,
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
  "description" : "oBDS-spezifisches ValueSet für Nebenwirkung nach CTCAE oder MedDRA code",
  "jurisdiction" : [{
    "coding" : [{
      "system" : "urn:iso:std:iso:3166",
      "code" : "DE",
      "display" : "Germany"
    }]
  }],
  "compose" : {
    "include" : [{
      "system" : "https://www.meddra.org"
    },
    {
      "system" : "https://www.meddra.org",
      "concept" : [{
        "code" : "10016256",
        "display" : "Fatigue"
      },
      {
        "code" : "10034620",
        "display" : "Peripheral sensory neuropathy"
      }]
    }]
  }
}

```
