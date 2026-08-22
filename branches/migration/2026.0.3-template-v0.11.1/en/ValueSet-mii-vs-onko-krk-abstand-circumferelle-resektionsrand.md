# MII_VS_Onko_KRK_Abstand_Circumferelle_Resektionsrand - MII IG Kerndatensatz-Modul Onkologie v2026.0.3

* [**Table of Contents**](toc.md)
* [**Artifacts Summary**](artifacts.md)
* **MII_VS_Onko_KRK_Abstand_Circumferelle_Resektionsrand**

## ValueSet: (Experimental) 

| | |
| :--- | :--- |
| *Official URL*:https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/ValueSet/mii-vs-onko-krk-abstand-circumferelle-resektionsrand | *Version*:2026.0.3 |
| Active as of 2026-08-22 | *Computable Name*:MII_VS_Onko_KRK_Abstand_Circumferelle_Resektionsrand |

 
Value Set für semantische Kodierung des oBDS-Abstand des Tumorrandes zur circumferellen Resektionsrand im Kolorektalen Karzinom 

 **References** 

* [MII PR Onkologie Abstand Circumferelle Resektionsebene](StructureDefinition-mii-pr-onko-krk-abstand-circumferelle-resektionsebene.md)

### Logical Definition (CLD)

 

### Expansion

-------

 [Description of the above table(s)](http://build.fhir.org/ig/FHIR/ig-guidance/readingIgs.html#terminology). 



## Resource Content

```json
{
  "resourceType" : "ValueSet",
  "id" : "mii-vs-onko-krk-abstand-circumferelle-resektionsrand",
  "meta" : {
    "profile" : ["http://hl7.org/fhir/StructureDefinition/shareablevalueset"]
  },
  "url" : "https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/ValueSet/mii-vs-onko-krk-abstand-circumferelle-resektionsrand",
  "version" : "2026.0.3",
  "name" : "MII_VS_Onko_KRK_Abstand_Circumferelle_Resektionsrand",
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
  "description" : "Value Set für semantische Kodierung des oBDS-Abstand des Tumorrandes zur circumferellen Resektionsrand im Kolorektalen Karzinom",
  "jurisdiction" : [{
    "coding" : [{
      "system" : "urn:iso:std:iso:3166",
      "code" : "DE",
      "display" : "Germany"
    }]
  }],
  "compose" : {
    "include" : [{
      "system" : "http://loinc.org",
      "concept" : [{
        "code" : "81176-0",
        "display" : "Distance of tumor from circumferential resection margin [Length] in Specimen by Macroscopy"
      },
      {
        "code" : "81184-4",
        "display" : "Distance of tumor from circumferential resection margin [Length] by Microscopy"
      }]
    }]
  }
}

```
