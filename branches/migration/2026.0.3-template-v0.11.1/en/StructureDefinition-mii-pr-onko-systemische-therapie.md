# MII PR Onkologie Systemische Therapie - MII IG Kerndatensatz-Modul Onkologie v2026.0.3

* [**Table of Contents**](toc.md)
* [**Artifacts Summary**](artifacts.md)
* **MII PR Onkologie Systemische Therapie**

## Resource Profile: MII PR Onkologie Systemische Therapie 

| | |
| :--- | :--- |
| *Official URL*:https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-systemische-therapie | *Version*:2026.0.3 |
| Active as of 2026-08-22 | *Computable Name*:MII_PR_Onko_Systemische_Therapie |

 
Systemische Therapie. Dieses Profil beschreibt eine Systemische Therapie für den oBDS. Da die Granularität der Anforderungen des oBDS nicht deckungsgleich mit den FHIR-Profilen für Medikation sind, wurde die Systemische Therapie als Prozedur umgesetzt 

This profile describes a systemic or watchful-waiting therapy in oncology.

### Description

The oBDS maps several clinical concepts within Systemische Therapie

* Systemic therapies 
* Chemotherapie
* Immuntherapie
* Targeted Therapy
* combination therapies of the therapies listed above
* Hormontherapie
* stem cell and bone marrow transplantation
 
* Watchful-waiting therapies 
* Watchful Waiting
* Active Surveillance
* Wait and see
 

For these individual therapies the oBDS records further data elements, which are represented here, among them:

* start and end date of the therapy
* relation to surgery and intention of the therapy
* the reason the therapy ended (whether successful or not)
* the therapy protocol used, with its substance combinations (as per the oBDS Umsetzungsleitfaden).

#### Category

* The MII Prozedur used here recommends representing the **category** by means of the OPS main categories transferred into SNOMED (https://www.medizininformatik-initiative.de/fhir/core/modul-prozedur/ValueSet/procedures-category-sct)
* The category used here, SNOMED `277132007 | Therapeutic procedure`, which corresponds to OPS category 8 ("Nicht-operative therapeutische Maßnahmen"), covers radiotherapy as well as nuclear medicine therapy and certain systemic therapies (e.g. chemotherapy and immunotherapy), while other systemic drug therapies (e.g. hormone therapy, targeted therapy) may also be coded under category 6 "Medikamente". It is therefore unspecific and not suitable for, say, filtering specifically for nuclear medicine therapies within a research question.

#### Code

* As the **code**, the MII Prozedur requires an OPS code or a SNOMED code.
* The medication-based systemic therapies are coded through different OPS categories depending on the kind of therapy.
* For the watchful-waiting therapies there are no OPS codes in the current catalogue.
* In the MII Prozedur, exactly one coding (OPS or SNOMED CT) SHOULD be used for exactly one therapy. Additional procedures are represented as individual Procedure resources.

#### Therapy protocol

* The specific therapy protocols used in the systemic therapy are documented as **usedCode**.
* The protocols are based on the [oBDS Umsetzungsleitfaden](https://plattform65c.atlassian.net/wiki/spaces/UMK/pages/15532385/Systemische+Therapie+SYST+Protokolle) and contain standardised substance combinations.
* Each protocol is documented with its characteristic designation (e.g. "FOLFOX", "R-CHOP", "AC") and the active substances it contains.
* Coding is done via the **MII CodeSystem Systemische Therapie Protokolle**, which covers all common oncological therapy protocols.
* Protocols that are not included can still be documented - here, however, harmonisation across the sites is decisive. Please therefore submit new protocols via [GitHub Issues](https://github.com/medizininformatik-initiative/kerndatensatzmodul-onkologie/issues).

#### Implementation recommendation

The points above result in the following coding recommendation for the systemic / watchful-waiting therapy from the oBDS:

* Category as a SNOMED code 
* Category for systemic therapies `18629005 | Administration of drug or medicament (procedure)`
* Category for watchful-waiting therapies: none (no suitable parent concept; searching directly via the coding is recommended)
 
* Coding 
* Systemic therapy via OPS as follows. Note that the exact active substance is coded via ATC as part of the MedicationStatement resource. An additional documentation of the medication via 
* chemotherapy via OPS `8-54` or more specific
* immunotherapy via OPS `8-54` or more specific (additional statement of )
* stem cell therapy via OPS `8-86` or more specific
* hormone therapy via OPS `6-xxx.y` (e.g. `6-009.0` for olaparib, oral, in prostate carcinoma)
 
* Watchful-waiting therapy via SNOMED CT as follows 
* Watchful Waiting: SNOMED CT `373818007 | No anti-cancer treatment - watchful waiting (finding)`
* Active Surveillance: SNOMED CT `424313000 | Active surveillance (regime/therapy)`
* Wait and see: SNOMED CT `310341009 | Follow-up (wait and see) (finding)`
 
 

> **Written during migration - review before release.** Two statements in the coding recommendation break off incomplete in the source page: "Eine zusätzliche Dokumentation der Medikation über" ends without a continuation, and the parenthesis for immunotherapy is empty ("Zusatzangabe von )"). The wording was carried over unchanged; both places need to be completed before release.

### Conformance

This profiling is compatible with the procedure profile of the ISiK Basismodule Stufe 4. https://simplifier.net/isik-basis-v4/isikprozedur

> **Written during migration - review before release.** The source page listed every search parameter individually with an example query and a link into the FHIR base specification. Condensed here: mandatory (MUSS) are `_id`, `_profile`, `status`, `category`, `code`, `date`, `subject`, `patient`, `bodySite`, `dokumentationsdatum`, `durchfuehrungsabsicht`, `outcome` and `extension-intention`; `used-code` SHOULD be supported.

**Usages:**

* Refer to this Profile: [MII PR Onkologie Systemische Therapie Medikation](StructureDefinition-mii-pr-onko-systemische-therapie-medikation.md)
* Examples for this Profile: [Procedure/PatientKimMusterperson-SystemicTherapy-1](Procedure-PatientKimMusterperson-SystemicTherapy-1.md), [Procedure/PatientKimMusterperson-SystemicTherapy-2](Procedure-PatientKimMusterperson-SystemicTherapy-2.md), [Procedure/PatientKimMusterperson-SystemicTherapy-3](Procedure-PatientKimMusterperson-SystemicTherapy-3.md), [Procedure/mii-exa-onko-folfox-phase1](Procedure-mii-exa-onko-folfox-phase1.md)... Show 6 more, [Procedure/mii-exa-onko-folfox-procedure](Procedure-mii-exa-onko-folfox-procedure.md), [Procedure/mii-exa-onko-lv5fu2-phase2](Procedure-mii-exa-onko-lv5fu2-phase2.md), [Procedure/mii-exa-onko-palbociclib-therapie](Procedure-mii-exa-onko-palbociclib-therapie.md), [Procedure/mii-exa-onko-pertuzumab-therapie](Procedure-mii-exa-onko-pertuzumab-therapie.md), [Procedure/mii-exa-onko-systemische-therapie-1](Procedure-mii-exa-onko-systemische-therapie-1.md) and [Procedure/mii-exa-onko-trastuzumab-therapie](Procedure-mii-exa-onko-trastuzumab-therapie.md)
* CapabilityStatements using this Profile: [MII CPS Onkology CapabilityStatement](CapabilityStatement-mii-cps-onko-capabilitystatement.md)

You can also check for [usages in the FHIR IG Statistics](https://packages2.fhir.org/xig/resource/de.medizininformatikinitiative.kerndatensatz.onkologie|current/StructureDefinition/StructureDefinition-mii-pr-onko-systemische-therapie.json)

### Formal Views of Profile Content

 [Description of Profiles, Differentials, Snapshots, and their representations](http://build.fhir.org/ig/FHIR/ig-guidance/readingIgs.html#structure-definitions). 

 

Other representations of profile: [CSV](../StructureDefinition-mii-pr-onko-systemische-therapie.csv), [Excel](../StructureDefinition-mii-pr-onko-systemische-therapie.xlsx), [Schematron](../StructureDefinition-mii-pr-onko-systemische-therapie.sch) 



## Resource Content

```json
{
  "resourceType" : "StructureDefinition",
  "id" : "mii-pr-onko-systemische-therapie",
  "extension" : [{
    "url" : "http://hl7.org/fhir/StructureDefinition/artifact-versionAlgorithm",
    "valueCoding" : {
      "system" : "http://hl7.org/fhir/version-algorithm",
      "code" : "semver",
      "display" : "SemVer"
    }
  },
  {
    "url" : "http://hl7.org/fhir/StructureDefinition/cqf-knowledgeCapability",
    "valueCode" : "shareable"
  },
  {
    "url" : "http://hl7.org/fhir/StructureDefinition/cqf-knowledgeCapability",
    "valueCode" : "publishable"
  },
  {
    "url" : "http://hl7.org/fhir/StructureDefinition/artifact-versionPolicy",
    "valueCodeableConcept" : {
      "coding" : [{
        "system" : "http://terminology.hl7.org/CodeSystem/artifact-version-policy-codes",
        "code" : "package",
        "display" : "Package"
      }]
    }
  },
  {
    "url" : "http://hl7.org/fhir/StructureDefinition/artifact-usage",
    "valueMarkdown" : "Use this profile as the technical FHIR representation of the corresponding Medical Informatics Initiative logical model. The profile constrains a base FHIR resource for the MII module context by specifying how elements are used, which elements are required or not used, which extensions and terminology bindings apply, and how the resource maps to the module-specific content model. Implementers should produce and consume resource instances that conform to this profile when exchanging data for the corresponding MII module."
  },
  {
    "url" : "http://hl7.org/fhir/StructureDefinition/artifact-topic",
    "valueCodeableConcept" : {
      "coding" : [{
        "system" : "http://ncicb.nci.nih.gov/xml/owl/EVS/Thesaurus.owl",
        "code" : "C25218"
      }]
    }
  },
  {
    "url" : "http://hl7.org/fhir/StructureDefinition/artifact-author",
    "valueContactDetail" : {
      "telecom" : [{
        "system" : "email",
        "value" : "julian.sass@charite.de"
      }]
    }
  },
  {
    "url" : "http://hl7.org/fhir/StructureDefinition/artifact-editor",
    "valueContactDetail" : {
      "name" : "Taskforce Core Data Set"
    }
  },
  {
    "url" : "http://hl7.org/fhir/StructureDefinition/artifact-reviewer",
    "valueContactDetail" : {
      "name" : "Interoperability Working Group",
      "telecom" : [{
        "system" : "url",
        "value" : "https://www.medizininformatik-initiative.de/en/collaboration/interoperability-working-group"
      }]
    }
  },
  {
    "url" : "http://hl7.org/fhir/StructureDefinition/artifact-reviewer",
    "valueContactDetail" : {
      "name" : "National Steering Committee",
      "telecom" : [{
        "system" : "url",
        "value" : "https://www.medizininformatik-initiative.de/en/collaboration/national-steering-committee"
      }]
    }
  },
  {
    "url" : "http://hl7.org/fhir/StructureDefinition/artifact-endorser",
    "valueContactDetail" : {
      "name" : "Interoperability Working Group",
      "telecom" : [{
        "system" : "url",
        "value" : "https://www.medizininformatik-initiative.de/en/collaboration/interoperability-working-group"
      }]
    }
  },
  {
    "url" : "http://hl7.org/fhir/StructureDefinition/artifact-endorser",
    "valueContactDetail" : {
      "name" : "National Steering Committee",
      "telecom" : [{
        "system" : "url",
        "value" : "https://www.medizininformatik-initiative.de/en/collaboration/national-steering-committee"
      }]
    }
  },
  {
    "url" : "http://hl7.org/fhir/StructureDefinition/resource-approvalDate",
    "valueDate" : "2024-03-07"
  },
  {
    "url" : "http://hl7.org/fhir/StructureDefinition/resource-effectivePeriod",
    "valuePeriod" : {
      "start" : "2026"
    }
  }],
  "url" : "https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-systemische-therapie",
  "version" : "2026.0.3",
  "name" : "MII_PR_Onko_Systemische_Therapie",
  "title" : "MII PR Onkologie Systemische Therapie",
  "status" : "active",
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
  "description" : "Systemische Therapie. Dieses Profil beschreibt eine Systemische Therapie für den oBDS. Da die Granularität der Anforderungen des oBDS nicht deckungsgleich mit den FHIR-Profilen für Medikation sind, wurde die Systemische Therapie als Prozedur umgesetzt",
  "jurisdiction" : [{
    "coding" : [{
      "system" : "urn:iso:std:iso:3166",
      "code" : "DE",
      "display" : "Germany"
    }]
  }],
  "fhirVersion" : "4.0.1",
  "mapping" : [{
    "identity" : "oBDS",
    "name" : "Mapping FHIR zu oBDS"
  },
  {
    "identity" : "workflow",
    "uri" : "http://hl7.org/fhir/workflow",
    "name" : "Workflow Pattern"
  },
  {
    "identity" : "w5",
    "uri" : "http://hl7.org/fhir/fivews",
    "name" : "FiveWs Pattern Mapping"
  },
  {
    "identity" : "v2",
    "uri" : "http://hl7.org/v2",
    "name" : "HL7 v2 Mapping"
  }],
  "kind" : "resource",
  "abstract" : false,
  "type" : "Procedure",
  "baseDefinition" : "https://www.medizininformatik-initiative.de/fhir/core/modul-prozedur/StructureDefinition/Procedure",
  "derivation" : "constraint",
  "differential" : {
    "element" : [{
      "id" : "Procedure",
      "path" : "Procedure",
      "mapping" : [{
        "identity" : "oBDS",
        "map" : "16",
        "comment" : "Systemische Therapie"
      }]
    },
    {
      "id" : "Procedure.extension",
      "path" : "Procedure.extension",
      "min" : 1
    },
    {
      "id" : "Procedure.extension:Intention",
      "path" : "Procedure.extension",
      "sliceName" : "Intention",
      "min" : 1,
      "max" : "1",
      "type" : [{
        "code" : "Extension",
        "profile" : ["https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-ex-onko-systemische-therapie-intention"]
      }],
      "mustSupport" : true
    },
    {
      "id" : "Procedure.extension:Intention.value[x].coding",
      "path" : "Procedure.extension.value[x].coding",
      "short" : "Intention der systemischen oder abwartenden Therapie",
      "_short" : {
        "extension" : [{
          "extension" : [{
            "url" : "lang",
            "valueCode" : "de-DE"
          },
          {
            "url" : "content",
            "valueString" : "Intention der systemischen oder abwartenden Therapie"
          }],
          "url" : "http://hl7.org/fhir/StructureDefinition/translation"
        }]
      },
      "definition" : "Intention der systemischen oder abwartenden Therapie gemäß 16.1 oBDS 2021.",
      "_definition" : {
        "extension" : [{
          "extension" : [{
            "url" : "lang",
            "valueCode" : "de-DE"
          },
          {
            "url" : "content",
            "valueString" : "Intention der systemischen oder abwartenden Therapie gemäß 16.1 oBDS 2021."
          }],
          "url" : "http://hl7.org/fhir/StructureDefinition/translation"
        }]
      }
    },
    {
      "id" : "Procedure.extension:Intention.value[x].coding.code",
      "path" : "Procedure.extension.value[x].coding.code",
      "mapping" : [{
        "identity" : "oBDS",
        "map" : "16.1",
        "comment" : "Intention der systemischen Therapie"
      }]
    },
    {
      "id" : "Procedure.extension:StellungZurOp",
      "path" : "Procedure.extension",
      "sliceName" : "StellungZurOp",
      "min" : 0,
      "max" : "*",
      "type" : [{
        "code" : "Extension",
        "profile" : ["https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-ex-onko-systemische-therapie-stellungzurop"]
      }],
      "mustSupport" : true
    },
    {
      "id" : "Procedure.extension:StellungZurOp.value[x].coding",
      "path" : "Procedure.extension.value[x].coding",
      "short" : "Stellung der systemischen Therapie zu einer Operation",
      "_short" : {
        "extension" : [{
          "extension" : [{
            "url" : "lang",
            "valueCode" : "de-DE"
          },
          {
            "url" : "content",
            "valueString" : "Stellung der systemischen Therapie zu einer Operation"
          }],
          "url" : "http://hl7.org/fhir/StructureDefinition/translation"
        }]
      },
      "definition" : "Stellung der systemischen Therapie zu einer Operation gemäß 16.2 oBDS 2021.",
      "_definition" : {
        "extension" : [{
          "extension" : [{
            "url" : "lang",
            "valueCode" : "de-DE"
          },
          {
            "url" : "content",
            "valueString" : "Stellung der systemischen Therapie zu einer Operation gemäß 16.2 oBDS 2021."
          }],
          "url" : "http://hl7.org/fhir/StructureDefinition/translation"
        }]
      }
    },
    {
      "id" : "Procedure.extension:StellungZurOp.value[x].coding.code",
      "path" : "Procedure.extension.value[x].coding.code",
      "mapping" : [{
        "identity" : "oBDS",
        "map" : "16.2",
        "comment" : "Systemische Therapie Stellung zu operativer Therapie"
      }]
    },
    {
      "id" : "Procedure.basedOn",
      "path" : "Procedure.basedOn",
      "type" : [{
        "code" : "Reference",
        "targetProfile" : ["http://hl7.org/fhir/StructureDefinition/CarePlan"]
      }],
      "mustSupport" : true
    },
    {
      "id" : "Procedure.partOf",
      "path" : "Procedure.partOf",
      "mustSupport" : true
    },
    {
      "id" : "Procedure.code",
      "path" : "Procedure.code",
      "definition" : "Enthält den Code, der neben der oBDS-spezifischen Kodierungden optional mit Codings für OPS und SNOMED annotiert werden kann",
      "comment" : "Primäre Befüllung aus den oBDS / Tumordokumentatiosndaten. Beim Zusammenführen mit Daten aus KIS und anderen Quellen können hier ebenfalls OPS- und SNOMED-CT-Codings hinterlegt werden"
    },
    {
      "id" : "Procedure.code.coding",
      "path" : "Procedure.code.coding"
    },
    {
      "id" : "Procedure.code.coding.code",
      "path" : "Procedure.code.coding.code",
      "mapping" : [{
        "identity" : "oBDS",
        "map" : "16.3",
        "comment" : "Art der systemischen oder abwartenden Therapie"
      }]
    },
    {
      "id" : "Procedure.code.coding:systemische_therapie_art",
      "path" : "Procedure.code.coding",
      "sliceName" : "systemische_therapie_art",
      "short" : "Art der systemischen oder abwartenden Therapie",
      "_short" : {
        "extension" : [{
          "extension" : [{
            "url" : "lang",
            "valueCode" : "de-DE"
          },
          {
            "url" : "content",
            "valueString" : "Art der systemischen oder abwartenden Therapie"
          }],
          "url" : "http://hl7.org/fhir/StructureDefinition/translation"
        }]
      },
      "definition" : "Art der systemischen oder abwartenden Therapie gemäß 16.3 oBDS 2021.",
      "_definition" : {
        "extension" : [{
          "extension" : [{
            "url" : "lang",
            "valueCode" : "de-DE"
          },
          {
            "url" : "content",
            "valueString" : "Art der systemischen oder abwartenden Therapie gemäß 16.3 oBDS 2021."
          }],
          "url" : "http://hl7.org/fhir/StructureDefinition/translation"
        }]
      },
      "min" : 0,
      "max" : "1",
      "binding" : {
        "strength" : "required",
        "valueSet" : "https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/ValueSet/mii-vs-onko-systemische-therapie-art"
      }
    },
    {
      "id" : "Procedure.code.coding:systemische_therapie_art.system",
      "path" : "Procedure.code.coding.system",
      "min" : 1
    },
    {
      "id" : "Procedure.code.coding:systemische_therapie_art.code",
      "path" : "Procedure.code.coding.code",
      "min" : 1
    },
    {
      "id" : "Procedure.subject",
      "path" : "Procedure.subject",
      "type" : [{
        "code" : "Reference",
        "targetProfile" : ["http://hl7.org/fhir/StructureDefinition/Patient"]
      }]
    },
    {
      "id" : "Procedure.performed[x]",
      "path" : "Procedure.performed[x]",
      "type" : [{
        "code" : "Period"
      }]
    },
    {
      "id" : "Procedure.performed[x].start",
      "path" : "Procedure.performed[x].start",
      "mapping" : [{
        "identity" : "oBDS",
        "map" : "16.6",
        "comment" : "Systemische Therapie Beginn"
      }]
    },
    {
      "id" : "Procedure.performed[x].end",
      "path" : "Procedure.performed[x].end",
      "mapping" : [{
        "identity" : "oBDS",
        "map" : "16.8",
        "comment" : "Systemische Therapie Ende"
      }]
    },
    {
      "id" : "Procedure.performed[x]:performedPeriod",
      "path" : "Procedure.performed[x]",
      "sliceName" : "performedPeriod",
      "type" : [{
        "code" : "Period"
      }]
    },
    {
      "id" : "Procedure.performed[x]:performedPeriod.start",
      "path" : "Procedure.performed[x].start",
      "short" : "Startdatum der systemischen oder abwartenden Therapie",
      "_short" : {
        "extension" : [{
          "extension" : [{
            "url" : "lang",
            "valueCode" : "de-DE"
          },
          {
            "url" : "content",
            "valueString" : "Startdatum der systemischen oder abwartenden Therapie"
          }],
          "url" : "http://hl7.org/fhir/StructureDefinition/translation"
        }]
      },
      "definition" : "Startdatum der systemischen oder abwartenden Therapie gemäß 16.6 oBDS 2021.",
      "_definition" : {
        "extension" : [{
          "extension" : [{
            "url" : "lang",
            "valueCode" : "de-DE"
          },
          {
            "url" : "content",
            "valueString" : "Startdatum der systemischen oder abwartenden Therapie gemäß 16.6 oBDS 2021."
          }],
          "url" : "http://hl7.org/fhir/StructureDefinition/translation"
        }]
      },
      "min" : 1,
      "mustSupport" : true
    },
    {
      "id" : "Procedure.performed[x]:performedPeriod.end",
      "path" : "Procedure.performed[x].end",
      "short" : "Enddatum der systemischen oder abwartenden Therapie",
      "_short" : {
        "extension" : [{
          "extension" : [{
            "url" : "lang",
            "valueCode" : "de-DE"
          },
          {
            "url" : "content",
            "valueString" : "Enddatum der systemischen oder abwartenden Therapie"
          }],
          "url" : "http://hl7.org/fhir/StructureDefinition/translation"
        }]
      },
      "definition" : "Enddatum der systemischen oder abwartenden Therapie gemäß 16.8 oBDS 2021.",
      "_definition" : {
        "extension" : [{
          "extension" : [{
            "url" : "lang",
            "valueCode" : "de-DE"
          },
          {
            "url" : "content",
            "valueString" : "Enddatum der systemischen oder abwartenden Therapie - wenn vorhanden -  gemäß 16.8 oBDS 2021."
          }],
          "url" : "http://hl7.org/fhir/StructureDefinition/translation"
        }]
      },
      "mustSupport" : true
    },
    {
      "id" : "Procedure.reasonReference",
      "path" : "Procedure.reasonReference",
      "type" : [{
        "code" : "Reference",
        "targetProfile" : ["https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-diagnose-primaertumor",
        "http://hl7.org/fhir/StructureDefinition/Condition"]
      }],
      "mustSupport" : true
    },
    {
      "id" : "Procedure.outcome",
      "path" : "Procedure.outcome",
      "mustSupport" : true,
      "binding" : {
        "strength" : "required",
        "valueSet" : "https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/ValueSet/mii-vs-systemische-therapie-ende-grund"
      }
    },
    {
      "id" : "Procedure.outcome.coding",
      "path" : "Procedure.outcome.coding",
      "short" : "Grund für Ende der systemischen oder abwartenden Therapie",
      "_short" : {
        "extension" : [{
          "extension" : [{
            "url" : "lang",
            "valueCode" : "de-DE"
          },
          {
            "url" : "content",
            "valueString" : "Grund für Ende der systemischen oder abwartenden Therapie"
          }],
          "url" : "http://hl7.org/fhir/StructureDefinition/translation"
        }]
      },
      "definition" : "Grund für Ende der systemischen oder abwartenden Therapie gemäß 16.7 oBDS 2021.",
      "_definition" : {
        "extension" : [{
          "extension" : [{
            "url" : "lang",
            "valueCode" : "de-DE"
          },
          {
            "url" : "content",
            "valueString" : "Grund für Ende der systemischen oder abwartenden Therapie gemäß 16.7 oBDS 2021."
          }],
          "url" : "http://hl7.org/fhir/StructureDefinition/translation"
        }]
      }
    },
    {
      "id" : "Procedure.outcome.coding.system",
      "path" : "Procedure.outcome.coding.system",
      "patternUri" : "https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/CodeSystem/mii-cs-onko-therapie-ende-grund"
    },
    {
      "id" : "Procedure.outcome.coding.code",
      "path" : "Procedure.outcome.coding.code",
      "mustSupport" : true,
      "mapping" : [{
        "identity" : "oBDS",
        "map" : "16.7",
        "comment" : "Systemische Therapie Ende Grund"
      }]
    },
    {
      "id" : "Procedure.usedCode",
      "path" : "Procedure.usedCode",
      "mustSupport" : true,
      "binding" : {
        "strength" : "extensible",
        "valueSet" : "https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/ValueSet/mii-vs-onko-systemische-therapie-protokolle"
      }
    },
    {
      "id" : "Procedure.usedCode.coding",
      "path" : "Procedure.usedCode.coding",
      "short" : "Protokoll der systemischen Therapie",
      "_short" : {
        "extension" : [{
          "extension" : [{
            "url" : "lang",
            "valueCode" : "de-DE"
          },
          {
            "url" : "content",
            "valueString" : "Protokoll der systemischen Therapie"
          }],
          "url" : "http://hl7.org/fhir/StructureDefinition/translation"
        }]
      },
      "definition" : "Protokoll der systemischen Therapie gemäß oBDS Umsetzungsleitfaden.",
      "_definition" : {
        "extension" : [{
          "extension" : [{
            "url" : "lang",
            "valueCode" : "de-DE"
          },
          {
            "url" : "content",
            "valueString" : "Protokoll der systemischen Therapie gemäß oBDS Umsetzungsleitfaden mit Substanzkombinationen."
          }],
          "url" : "http://hl7.org/fhir/StructureDefinition/translation"
        }]
      }
    },
    {
      "id" : "Procedure.usedCode.coding.system",
      "path" : "Procedure.usedCode.coding.system",
      "min" : 1,
      "mustSupport" : true
    },
    {
      "id" : "Procedure.usedCode.coding.code",
      "path" : "Procedure.usedCode.coding.code",
      "min" : 1,
      "mustSupport" : true,
      "mapping" : [{
        "identity" : "oBDS",
        "map" : "16.4",
        "comment" : "Protokoll der systemischen Therapie"
      }]
    }]
  }
}

```
