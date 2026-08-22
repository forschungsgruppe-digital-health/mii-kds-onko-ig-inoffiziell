# MII VS Onkologie Beurteilung des lokalen Residualstatus - MII IG Kerndatensatz-Modul Onkologie v2026.0.3

* [**Inhaltsverzeichnis**](toc.md)
* [**Artefaktübersicht**](artifacts.md)
* **MII VS Onkologie Beurteilung des lokalen Residualstatus**

## ValueSet: MII VS Onkologie Beurteilung des lokalen Residualstatus 

| | |
| :--- | :--- |
| *Offizielle URL*:https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/ValueSet/mii-vs-onko-beurteilung-lokaler-residualstatus | *Version*:2026.0.3 |
| Active Stand: 2026-08-22 | *Maschinenlesbarer Name*:MII_VS_Onko_Beurteilung_Lokaler_Residualstatus |

 
Value Set für oBDS-Codes für die Beurteilung des lokalen Residualstatus 

 **References** 

* [MII PR Onkologie Operation](StructureDefinition-mii-pr-onko-operation.md)

### Logical Definition (CLD)

 

### Expansion

-------

 [Beschreibung der obigen Tabelle(n)](http://build.fhir.org/ig/FHIR/ig-guidance/readingIgs.html#terminology). 



## Resource Content

```json
{
  "resourceType" : "ValueSet",
  "id" : "mii-vs-onko-beurteilung-lokaler-residualstatus",
  "meta" : {
    "profile" : ["http://hl7.org/fhir/StructureDefinition/shareablevalueset"]
  },
  "url" : "https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/ValueSet/mii-vs-onko-beurteilung-lokaler-residualstatus",
  "version" : "2026.0.3",
  "name" : "MII_VS_Onko_Beurteilung_Lokaler_Residualstatus",
  "title" : "MII VS Onkologie Beurteilung des lokalen Residualstatus",
  "status" : "active",
  "experimental" : false,
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
  "description" : "Value Set für oBDS-Codes für die Beurteilung des lokalen Residualstatus",
  "jurisdiction" : [{
    "coding" : [{
      "system" : "urn:iso:std:iso:3166",
      "code" : "DE",
      "display" : "Germany"
    }]
  }],
  "compose" : {
    "include" : [{
      "system" : "https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/CodeSystem/mii-cs-onko-residualstatus"
    }]
  }
}

```
