# MII_CS_Onko_KRK_MRT_Mesorektale_Faszie_Status - MII IG Kerndatensatz-Modul Onkologie v2026.0.3

* [**Table of Contents**](toc.md)
* [**Artifacts Summary**](artifacts.md)
* **MII_CS_Onko_KRK_MRT_Mesorektale_Faszie_Status**

## CodeSystem: MII_CS_Onko_KRK_MRT_Mesorektale_Faszie_Status (Experimental) 

| | |
| :--- | :--- |
| *Official URL*:https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/CodeSystem/mii-cs-onko-krk-mrt-mesorektale-faszie-status | *Version*:2026.0.3 |
| Active as of 2026-08-22 | *Computable Name*:MII_CS_Onko_KRK_MRT_Mesorektale_Faszie_Status |

 
oBDS-basiertes Codesystem für den Status der MRT/CT Untersuchung zur mesorektalen Faszie beim Kolorektalen Karzinom (KR5) 

This Code system is referenced in the definition of the following value sets:

* [MII_VS_Onko_KRK_MRT_Mesorektale_Faszie_Status](ValueSet-mii-vs-onko-krk-mrt-mesorektale-faszie-status.md)

-------

 [Description of the above table(s)](http://build.fhir.org/ig/FHIR/ig-guidance/readingIgs.html#terminology). 



## Resource Content

```json
{
  "resourceType" : "CodeSystem",
  "id" : "mii-cs-onko-krk-mrt-mesorektale-faszie-status",
  "meta" : {
    "profile" : ["http://hl7.org/fhir/StructureDefinition/shareablecodesystem"]
  },
  "url" : "https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/CodeSystem/mii-cs-onko-krk-mrt-mesorektale-faszie-status",
  "version" : "2026.0.3",
  "name" : "MII_CS_Onko_KRK_MRT_Mesorektale_Faszie_Status",
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
  "description" : "oBDS-basiertes Codesystem für den Status der MRT/CT Untersuchung zur mesorektalen Faszie beim Kolorektalen Karzinom (KR5)",
  "jurisdiction" : [{
    "coding" : [{
      "system" : "urn:iso:std:iso:3166",
      "code" : "DE",
      "display" : "Germany"
    }]
  }],
  "caseSensitive" : true,
  "valueSet" : "https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/ValueSet/mii-vs-onko-krk-mrt-mesorektale-faszie-status",
  "content" : "complete",
  "count" : 3,
  "concept" : [{
    "code" : "D",
    "display" : "Durchgeführt, aber Abstand nicht angegeben",
    "definition" : "MRT oder Dünnschicht-CT wurde durchgeführt, aber der Abstand zur mesorektalen Faszie wurde nicht angegeben"
  },
  {
    "code" : "N",
    "display" : "Nein (MRT/CT nicht durchgeführt)",
    "definition" : "MRT oder Dünnschicht-CT wurde nicht durchgeführt"
  },
  {
    "code" : "U",
    "display" : "Unbekannt",
    "definition" : "Es ist unbekannt, ob eine MRT oder Dünnschicht-CT durchgeführt wurde"
  }]
}

```
