# MII VS Onko Prostata Operation SNOMED CT - MII IG Kerndatensatz-Modul Onkologie v2026.0.3

* [**Inhaltsverzeichnis**](toc.md)
* [**Artefaktübersicht**](artifacts.md)
* **MII VS Onko Prostata Operation SNOMED CT**

## ValueSet: MII VS Onko Prostata Operation SNOMED CT 

| | |
| :--- | :--- |
| *Offizielle URL*:https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/ValueSet/mii-vs-onko-prostata-operation-snomedct | *Version*:2026.0.3 |
| Active Stand: 2026-08-22 | *Maschinenlesbarer Name*:MII_VS_Onko_Prostata_Operation_SNOMEDCT |

 

| | |
| :--- | :--- |
| Value Set für Prostata-spezifische Operationen basierend auf SNOMED CT. Enthält alle Kinder von 118877007 | Procedure on prostate (procedure) |

 

 **References** 

* [MII PR Onko Prostata Operation](StructureDefinition-mii-pr-onko-prostata-operation.md)

### Logical Definition (CLD)

 

### Expansion

No Expansion for this valueset (Unsupported Code System Version)

-------

 [Beschreibung der obigen Tabelle(n)](http://build.fhir.org/ig/FHIR/ig-guidance/readingIgs.html#terminology). 



## Resource Content

```json
{
  "resourceType" : "ValueSet",
  "id" : "mii-vs-onko-prostata-operation-snomedct",
  "meta" : {
    "profile" : ["http://hl7.org/fhir/StructureDefinition/shareablevalueset"]
  },
  "url" : "https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/ValueSet/mii-vs-onko-prostata-operation-snomedct",
  "version" : "2026.0.3",
  "name" : "MII_VS_Onko_Prostata_Operation_SNOMEDCT",
  "title" : "MII VS Onko Prostata Operation SNOMED CT",
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
  "description" : "Value Set für Prostata-spezifische Operationen basierend auf SNOMED CT. Enthält alle Kinder von 118877007 |Procedure on prostate (procedure)|",
  "jurisdiction" : [{
    "coding" : [{
      "system" : "urn:iso:std:iso:3166",
      "code" : "DE",
      "display" : "Germany"
    }]
  }],
  "compose" : {
    "include" : [{
      "system" : "http://snomed.info/sct",
      "filter" : [{
        "property" : "concept",
        "op" : "descendent-of",
        "value" : "118877007"
      }]
    }]
  }
}

```
