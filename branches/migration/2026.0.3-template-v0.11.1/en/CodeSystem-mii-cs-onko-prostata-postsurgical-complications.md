# MII CS Onkologie Prostata Postoperative Komplikationen - MII IG Kerndatensatz-Modul Onkologie v2026.0.3

* [**Table of Contents**](toc.md)
* [**Artifacts Summary**](artifacts.md)
* **MII CS Onkologie Prostata Postoperative Komplikationen**

## CodeSystem: MII CS Onkologie Prostata Postoperative Komplikationen 

| | |
| :--- | :--- |
| *Official URL*:https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/CodeSystem/mii-cs-onko-prostata-postsurgical-complications | *Version*:2026.0.3 |
| Active as of 2026-08-22 | *Computable Name*:MII_CS_Onko_Prostata_Postsurgical_Complications |

 
CodeSystem zur Darstellung des Vorhandenseins von postoperativen Komplikationen nach Prostatektomie in der Onkologie 

This Code system is referenced in the definition of the following value sets:

* [MII_VS_Onko_Prostata_Postsurgical_Complications](ValueSet-mii-vs-onko-prostata-postsurgical-complications.md)

-------

 [Description of the above table(s)](http://build.fhir.org/ig/FHIR/ig-guidance/readingIgs.html#terminology). 



## Resource Content

```json
{
  "resourceType" : "CodeSystem",
  "id" : "mii-cs-onko-prostata-postsurgical-complications",
  "meta" : {
    "profile" : ["http://hl7.org/fhir/StructureDefinition/shareablecodesystem"]
  },
  "url" : "https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/CodeSystem/mii-cs-onko-prostata-postsurgical-complications",
  "version" : "2026.0.3",
  "name" : "MII_CS_Onko_Prostata_Postsurgical_Complications",
  "title" : "MII CS Onkologie Prostata Postoperative Komplikationen",
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
  "description" : "CodeSystem zur Darstellung des Vorhandenseins von postoperativen Komplikationen nach Prostatektomie in der Onkologie",
  "jurisdiction" : [{
    "coding" : [{
      "system" : "urn:iso:std:iso:3166",
      "code" : "DE",
      "display" : "Germany"
    }]
  }],
  "caseSensitive" : true,
  "content" : "complete",
  "count" : 3,
  "concept" : [{
    "code" : "J",
    "display" : "Ja"
  },
  {
    "code" : "N",
    "display" : "keine oder höchstens Grad II"
  },
  {
    "code" : "U",
    "display" : "Unbekannt"
  }]
}

```
