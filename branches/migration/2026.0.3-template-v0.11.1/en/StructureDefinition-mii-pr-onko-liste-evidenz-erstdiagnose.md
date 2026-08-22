# MII PR Onkologie Evidenz Diagnose Primärtumor - MII IG Kerndatensatz-Modul Onkologie v2026.0.3

* [**Table of Contents**](toc.md)
* [**Artifacts Summary**](artifacts.md)
* **MII PR Onkologie Evidenz Diagnose Primärtumor**

## Resource Profile: MII PR Onkologie Evidenz Diagnose Primärtumor 

| | |
| :--- | :--- |
| *Official URL*:https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-liste-evidenz-erstdiagnose | *Version*:2026.0.3 |
| Active as of 2026-08-22 | *Computable Name*:MII_PR_Onko_Liste_Evidenz_Erstdiagnose |

 
Dieses Profil beschreibt eine Liste, die alle Observationen und Berichte enthält, die für eine Erstdiagnostik relevant waren. (synchrone Observationen im Sinne der Krebsregister) 

The List resource is a flat collection of resources and offers functions for managing the collection. In this case the resource serves as the collection of the observations and diagnostic reports that are known at the time of the initial oncological diagnosis. These include, for example, a TNM classification as well as further diagnostically relevant classifications, distant metastases, histologies etc.

The evidence list itself is not part of the oBDS; it is intended to permanently record the state at the time of the initial diagnosis.

* The list **SHOULD** be created on the basis of the content that was known before or at the time the initial diagnosis was established.
* For this, the entries **MAY** be taken directly from the Diagnosemeldung.

**Search parameters**

The following search parameters are relevant for the Onkologie module, also in combination:

1. The search parameter `_id` SHALL be supported:Examples:`GET [base]/Condition?_id=1234`Usage notes: Further information on searching by "_id" is available in the [FHIR base specification — section "Parameters for all resources"](http://hl7.org/fhir/R4/search.html#all).
1. The search parameter "_profile" SHALL be supported:Examples:`GET [base]/Condition?_profile=https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-diagnose`Usage notes: Further information on searching by "_profile" is available in the [FHIR base specification — section "token"](http://hl7.org/fhir/R4/search.html#all).

**Usages:**

* Refer to this Profile: [MII PR Onkologie Diagnose Primärtumor](StructureDefinition-mii-pr-onko-diagnose-primaertumor.md)
* Examples for this Profile: [List/mii-exa-onko-liste-evidenz-erstdiagnose-1](List-mii-exa-onko-liste-evidenz-erstdiagnose-1.md)
* CapabilityStatements using this Profile: [MII CPS Onkology CapabilityStatement](CapabilityStatement-mii-cps-onko-capabilitystatement.md)

You can also check for [usages in the FHIR IG Statistics](https://packages2.fhir.org/xig/resource/de.medizininformatikinitiative.kerndatensatz.onkologie|current/StructureDefinition/StructureDefinition-mii-pr-onko-liste-evidenz-erstdiagnose.json)

### Formal Views of Profile Content

 [Description of Profiles, Differentials, Snapshots, and their representations](http://build.fhir.org/ig/FHIR/ig-guidance/readingIgs.html#structure-definitions). 

 

Other representations of profile: [CSV](../StructureDefinition-mii-pr-onko-liste-evidenz-erstdiagnose.csv), [Excel](../StructureDefinition-mii-pr-onko-liste-evidenz-erstdiagnose.xlsx), [Schematron](../StructureDefinition-mii-pr-onko-liste-evidenz-erstdiagnose.sch) 



## Resource Content

```json
{
  "resourceType" : "StructureDefinition",
  "id" : "mii-pr-onko-liste-evidenz-erstdiagnose",
  "url" : "https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-liste-evidenz-erstdiagnose",
  "version" : "2026.0.3",
  "name" : "MII_PR_Onko_Liste_Evidenz_Erstdiagnose",
  "title" : "MII PR Onkologie Evidenz Diagnose Primärtumor",
  "status" : "active",
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
  "description" : "Dieses Profil beschreibt eine Liste, die alle Observationen und Berichte enthält, die für eine Erstdiagnostik relevant waren.  (synchrone Observationen im Sinne der Krebsregister)",
  "jurisdiction" : [{
    "coding" : [{
      "system" : "urn:iso:std:iso:3166",
      "code" : "DE",
      "display" : "Germany"
    }]
  }],
  "fhirVersion" : "4.0.1",
  "mapping" : [{
    "identity" : "w5",
    "uri" : "http://hl7.org/fhir/fivews",
    "name" : "FiveWs Pattern Mapping"
  }],
  "kind" : "resource",
  "abstract" : false,
  "type" : "List",
  "baseDefinition" : "http://hl7.org/fhir/StructureDefinition/List",
  "derivation" : "constraint",
  "differential" : {
    "element" : [{
      "id" : "List",
      "path" : "List"
    },
    {
      "id" : "List.meta.profile",
      "path" : "List.meta.profile",
      "mustSupport" : true
    },
    {
      "id" : "List.status",
      "path" : "List.status",
      "patternCode" : "current",
      "mustSupport" : true
    },
    {
      "id" : "List.mode",
      "path" : "List.mode",
      "patternCode" : "snapshot",
      "mustSupport" : true
    },
    {
      "id" : "List.title",
      "path" : "List.title",
      "min" : 1,
      "patternString" : "Liste der Evidenz zum Erstdiagnosezeitpunkt",
      "mustSupport" : true
    },
    {
      "id" : "List.subject",
      "path" : "List.subject",
      "min" : 1,
      "type" : [{
        "code" : "Reference",
        "targetProfile" : ["http://hl7.org/fhir/StructureDefinition/Patient"]
      }],
      "mustSupport" : true
    },
    {
      "id" : "List.encounter",
      "path" : "List.encounter",
      "mustSupport" : true
    },
    {
      "id" : "List.entry",
      "path" : "List.entry",
      "min" : 1,
      "mustSupport" : true
    },
    {
      "id" : "List.entry.flag",
      "path" : "List.entry.flag",
      "mustSupport" : true
    },
    {
      "id" : "List.entry.item",
      "path" : "List.entry.item",
      "type" : [{
        "code" : "Reference",
        "targetProfile" : ["http://hl7.org/fhir/StructureDefinition/Observation",
        "http://hl7.org/fhir/StructureDefinition/DiagnosticReport"]
      }],
      "mustSupport" : true
    }]
  }
}

```
