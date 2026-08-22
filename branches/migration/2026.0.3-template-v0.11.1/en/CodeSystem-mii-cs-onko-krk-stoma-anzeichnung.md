# MII_CS_Onko_KRK_Stoma_Anzeichnung - MII IG Kerndatensatz-Modul Onkologie v2026.0.3

* [**Table of Contents**](toc.md)
* [**Artifacts Summary**](artifacts.md)
* **MII_CS_Onko_KRK_Stoma_Anzeichnung**

## CodeSystem: MII_CS_Onko_KRK_Stoma_Anzeichnung (Experimental) 

| | |
| :--- | :--- |
| *Official URL*:https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/CodeSystem/mii-cs-onko-krk-stoma-anzeichnung | *Version*:2026.0.3 |
| Active as of 2026-08-22 | *Computable Name*:MII_CS_Onko_KRK_Stoma_Anzeichnung |

 
oBDS-basiertes Codesystem für die präoperative Anzeichnung der Stoma-Position beim Rektumkarzinom 

This Code system is referenced in the definition of the following value sets:

* [MII_VS_Onko_KRK_Stoma_Anzeichnung](ValueSet-mii-vs-onko-krk-stoma-anzeichnung.md)

-------

 [Description of the above table(s)](http://build.fhir.org/ig/FHIR/ig-guidance/readingIgs.html#terminology). 



## Resource Content

```json
{
  "resourceType" : "CodeSystem",
  "id" : "mii-cs-onko-krk-stoma-anzeichnung",
  "meta" : {
    "profile" : ["http://hl7.org/fhir/StructureDefinition/shareablecodesystem"]
  },
  "url" : "https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/CodeSystem/mii-cs-onko-krk-stoma-anzeichnung",
  "version" : "2026.0.3",
  "name" : "MII_CS_Onko_KRK_Stoma_Anzeichnung",
  "status" : "active",
  "experimental" : true,
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
  "description" : "oBDS-basiertes Codesystem für die präoperative Anzeichnung der Stoma-Position beim Rektumkarzinom",
  "jurisdiction" : [{
    "coding" : [{
      "system" : "urn:iso:std:iso:3166",
      "code" : "DE",
      "display" : "Germany"
    }]
  }],
  "caseSensitive" : true,
  "valueSet" : "https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/ValueSet/mii-vs-onko-krk-stoma-anzeichnung",
  "content" : "complete",
  "count" : 5,
  "concept" : [{
    "code" : "D",
    "display" : "Anzeichnung durchgeführt",
    "definition" : "Präoperative Anzeichnung der Stoma-Position wurde durchgeführt"
  },
  {
    "code" : "N",
    "display" : "Anzeichnung nicht durchgeführt",
    "definition" : "Präoperative Anzeichnung der Stoma-Position wurde nicht durchgeführt"
  },
  {
    "code" : "K",
    "display" : "Kein Stoma",
    "definition" : "Kein Stoma geplant oder erforderlich"
  },
  {
    "code" : "S",
    "display" : "Stoma angelegt, Anzeichnungsstatus unbekannt",
    "definition" : "Stoma wurde angelegt, aber der Status der präoperativen Anzeichnung ist unbekannt"
  },
  {
    "code" : "U",
    "display" : "Unbekannt",
    "definition" : "Status der präoperativen Stoma-Anzeichnung ist unbekannt"
  }]
}

```
