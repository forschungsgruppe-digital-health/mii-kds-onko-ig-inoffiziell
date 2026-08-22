# mii-sp-onko-ext-strahlentherapie-stellungzurop - MII IG Kerndatensatz-Modul Onkologie v2026.0.3

* [**Inhaltsverzeichnis**](toc.md)
* [**Artefaktübersicht**](artifacts.md)
* **mii-sp-onko-ext-strahlentherapie-stellungzurop**

## SearchParameter: mii-sp-onko-ext-strahlentherapie-stellungzurop (Experimentell) 

| | |
| :--- | :--- |
| *Offizielle URL*:https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/SearchParameter/mii-sp-onko-ext-strahlentherapie-stellungzurop | *Version*:2026.0.3 |
| Active Stand: 2024-04-15 | *Maschinenlesbarer Name*:MII_SP_Procedure_Extension_Strahlentherapie_StellungZurOp |

 
SearchParameter for Procedure.extension[StellungZurOp] 



## Resource Content

```json
{
  "resourceType" : "SearchParameter",
  "id" : "mii-sp-onko-ext-strahlentherapie-stellungzurop",
  "url" : "https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/SearchParameter/mii-sp-onko-ext-strahlentherapie-stellungzurop",
  "version" : "2026.0.3",
  "name" : "MII_SP_Procedure_Extension_Strahlentherapie_StellungZurOp",
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
  "description" : "SearchParameter for Procedure.extension[StellungZurOp]",
  "jurisdiction" : [{
    "coding" : [{
      "system" : "urn:iso:std:iso:3166",
      "code" : "DE",
      "display" : "Germany"
    }]
  }],
  "code" : "strahlentherapie-stellungzurop",
  "base" : ["Procedure"],
  "type" : "token",
  "expression" : "Procedure.extension.where(url='https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-ex-onko-strahlentherapie-stellungzurop').value"
}

```
