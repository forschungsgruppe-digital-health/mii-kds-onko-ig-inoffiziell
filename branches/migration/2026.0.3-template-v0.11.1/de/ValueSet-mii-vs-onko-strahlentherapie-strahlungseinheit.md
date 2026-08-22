# MII VS Onkologie Strahlentherapie Strahlungseinheit - MII IG Kerndatensatz-Modul Onkologie v2026.0.3

* [**Inhaltsverzeichnis**](toc.md)
* [**Artefaktübersicht**](artifacts.md)
* **MII VS Onkologie Strahlentherapie Strahlungseinheit**

## ValueSet: MII VS Onkologie Strahlentherapie Strahlungseinheit 

| | |
| :--- | :--- |
| *Offizielle URL*:https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/ValueSet/mii-vs-strahlentherapie-strahlungseinheit | *Version*:2026.0.3 |
| Active Stand: 2026-08-22 | *Maschinenlesbarer Name*:MII_VS_Onko_Strahlentherapie_Strahlungseinheit |

 
oBDS-spezifisches ValueSet für Strahlungseinheit en für Strahlen- und Nuklearmedizinische Therapie 

 **References** 

* [MII EX Onko Strahlentherapie Bestrahlung Einzeldosis](StructureDefinition-mii-ex-onko-strahlentherapie-bestrahlung-einzeldosis.md)
* [MII EX Onko Strahlentherapie Bestrahlung Gesamtdosis](StructureDefinition-mii-ex-onko-strahlentherapie-bestrahlung-gesamtdosis.md)

### Logical Definition (CLD)

 

### Expansion

No Expansion for this valueset (Unsupported Code System Version)

-------

 [Beschreibung der obigen Tabelle(n)](http://build.fhir.org/ig/FHIR/ig-guidance/readingIgs.html#terminology). 



## Resource Content

```json
{
  "resourceType" : "ValueSet",
  "id" : "mii-vs-onko-strahlentherapie-strahlungseinheit",
  "meta" : {
    "profile" : ["http://hl7.org/fhir/StructureDefinition/shareablevalueset"]
  },
  "url" : "https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/ValueSet/mii-vs-strahlentherapie-strahlungseinheit",
  "version" : "2026.0.3",
  "name" : "MII_VS_Onko_Strahlentherapie_Strahlungseinheit",
  "title" : "MII VS Onkologie Strahlentherapie Strahlungseinheit",
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
  "description" : "oBDS-spezifisches ValueSet für Strahlungseinheit en für Strahlen- und Nuklearmedizinische Therapie",
  "jurisdiction" : [{
    "coding" : [{
      "system" : "urn:iso:std:iso:3166",
      "code" : "DE",
      "display" : "Germany"
    }]
  }],
  "compose" : {
    "include" : [{
      "system" : "http://unitsofmeasure.org",
      "concept" : [{
        "code" : "Gy",
        "display" : "Gy"
      },
      {
        "code" : "kBq",
        "display" : "kBq"
      },
      {
        "code" : "MBq",
        "display" : "MBq"
      },
      {
        "code" : "GBq",
        "display" : "GBq"
      }]
    }]
  }
}

```
