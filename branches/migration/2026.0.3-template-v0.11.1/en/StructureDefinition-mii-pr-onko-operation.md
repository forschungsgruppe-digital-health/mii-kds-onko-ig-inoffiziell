# MII PR Onkologie Operation - MII IG Kerndatensatz-Modul Onkologie v2026.0.3

* [**Table of Contents**](toc.md)
* [**Artifacts Summary**](artifacts.md)
* **MII PR Onkologie Operation**

## Resource Profile: MII PR Onkologie Operation 

| | |
| :--- | :--- |
| *Official URL*:https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-operation | *Version*:2026.0.3 |
| Active as of 2026-08-22 | *Computable Name*:MII_PR_Onko_Operation |

 
Operation nach OPS inklusive Intention, Datum und Komplikationen: 

This profile describes a surgical procedure (Operation) in oncology.

* The oncology surgery profile is derived from the MII Prozedur module and additionally specialised for oBDS content. https://simplifier.net/guide/mii-ig-modul-prozedur-2024-de/MIIIGModulProzedur/TechnischeImplementierung/FHIRProfile/Prozedur-Procedure.page.md?version=current

### Category and code

* The MII Prozedur recommends representing the category by means of the OPS main categories transferred into SNOMED (https://www.medizininformatik-initiative.de/fhir/core/modul-prozedur/ValueSet/procedures-category-sct), where the SNOMED code `38771300` corresponds to OPS category "5 - Operationen". According to the oBDS, however, a different coding may be entered here in justified cases (e.g. `103693007` for "1 - Diagnostische Maßnahmen"). For that reason the category is not constrained further.
* The exact kind of procedure is coded in the field `Procedure.code`. **IMPORTANT**: every Procedure MUST have a code - either OPS or SNOMED CT.
* An OPS code SHOULD be used primarily. If no suitable OPS code exists, a SNOMED CT code MUST be chosen.
* At most one OPS value SHOULD be coded per Procedure resource. Additional procedures are represented as individual Procedure resources.
* Note: within the KDS module Onkologie the overarching MII Prozedur is also used to represent radiotherapy and systemic/watchful-waiting therapy. For the particularities of their categories and codes, see the profiles Strahlentherapie (`mii-pr-onko-strahlentherapie`) and Systemische Therapie (`mii-pr-onko-systemische-therapie`).

### Multi-part interventions and related surgeries

In complex oncological interventions, several operative procedures are frequently performed in one session. Because only one OPS code should be coded per Procedure resource, two modelling approaches are supported:

#### Approach 1: overarching Procedure with a general code

**IMPORTANT**: a Procedure MUST have either an OPS code OR a SNOMED CT code. If no suitable OPS code exists for the overarching Procedure, a suitable SNOMED CT code MUST be chosen.

1. **Overarching Procedure**: a main Procedure with a general SNOMED CT code for the location/kind of the intervention
* `Procedure.code`: SNOMED CT code (e.g. 86481000 "Laparotomy (procedure)")
* `Procedure.code.coding[ops]`: stays empty, because no specific OPS code exists
* This Procedure SHOULD satisfy the MII_PR_Onko_Operation profile
* **Note**: the SNOMED CT code must be chosen from the available SNOMED CT concepts

1. **Detailed part Procedures**: individual Procedure resources for each specific OPS code
* Linked to the overarching Procedure via `Procedure.partOf`
* Each with its specific OPS code

**Example:**

```
Procedure/haupteingriff (SNOMED: 176282005 "Resektion des Rektums")
├── Procedure/teileingriff1 (partOf → haupteingriff) 
│   └── OPS: 5-484.35 "Rektumresektion mit Anastomose"
└── Procedure/teileingriff2 (partOf → haupteingriff)
    └── OPS: 5-469.21 "Andere Operationen am Darm"

```

#### Approach 2: Procedures of equal rank

For complex tumour surgeries where the hierarchy is not unambiguous:

1. **All Procedures of equal rank**: each Procedure represents one OPS code
1. **Common overarching Procedure optional**: can serve as a grouping
1. **Alternative**: choose one of the Procedures as the "main Procedure" (the decision can be arbitrary)

**Note on harmonisation**: deciding which Procedure counts as the "main Procedure" can be difficult for complex tumour surgeries and is hard to harmonise post hoc.

#### Common aspects of multi-part interventions:

* **Point in time**: all linked procedures should have the same `performedDateTime` if they were performed in one session
* **Intention**: the extension for the surgical intention should be consistent across all linked procedures
* **Complications**: can be documented on the affected individual procedure or on the overarching Procedure
* **Residual status**: the local residual status is documented on the resecting procedure
* **References**: all Procedures should reference the same primary diagnosis (`reasonReference`) and, where applicable, the tumour board recommendation (`basedOn`)

#### Visualisation using the example of Kim Musterperson

![](https://raw.githubusercontent.com/medizininformatik-initiative/kerndatensatzmodul-onkologie/dev/implementation-guides/ImplementationGuide-2026.x-DE/Images/MII_Onko_MultiPartSurgery_Example/MII_Onko_MultiPartSurgery_Example.png)

### Extensions

#### Intention

The MII Prozedur module already has a [Durchführungsabsicht](https://www.medizininformatik-initiative.de/fhir/core/modul-prozedur/StructureDefinition/Durchfuehrungsabsicht) extension bound to SNOMED CT codes. Since the intention of the surgery is, however, captured in the oBDS through an oBDS-specific answer set, the procedure was extended by an additional element "Intention". Existing extensions of the MII Prozedur module are optional and not directly relevant for mapping from the oBDS.

Further information: see the extension `mii-ex-onko-operation-intention`.

#### Urgency (Art des Eingriffs)

The "Urgency" extension captures the modality under which the intervention was performed. This data point originally comes from the organ-specific module Kolorektales Karzinom (KRK 6, oBDS 2021), but is **universally applicable to all Procedures** and was therefore integrated into the general Operation profile.

The extension distinguishes between:

* **E**: Elektiveingriff (planned intervention)
* **N**: Notfalleingriff (emergency intervention)
* **U**: Unbekannt (unknown)

This extension is particularly relevant for quality assurance and statistical analyses, because emergency interventions often show different outcomes and complication rates than planned interventions. Although originally defined for colorectal interventions, the distinction between elective and emergency interventions is clinically relevant for all surgical procedures.

**Use:**

```
* extension[urgency].valueCodeableConcept = $mii-cs-onko-operation-urgency#E "Elektiveingriff"

```

Further information: see the extension `mii-ex-onko-operation-urgency`.

### Residual status and further observations

The oBDS provides for recording the R status when tumour tissue is resected. Depending on the procedure performed, the assessment of the residual status is to be made **locally** or **globally**. The oBDS records these as two different data points. In the FHIR profiling at hand, the local residual status (where applicable) is coded under Procedure.outcome. The global residual status is recorded through its own Observation (see Residualstatus: Observation.)

Besides the residual status there are further data points that can reference a surgery and that are reported together with it in the oBDS. These include the histological examinations (lymph nodes, grading) as well as ICD-O morphology, TNM and/or, where applicable, further classifications.

#### References to other profiles

A surgery recorded and reported within the cancer registries is frequently based on a therapy recommendation of a tumour board. In that case the elements should be linked via `Procedure.basedOn(Reference(CarePlan))`. The surgery furthermore references the primary diagnosis via `Procedure.reasonReference`.

### Conformance

This profiling is compatible with the procedure profile of the ISiK Basismodule Stufe 4. https://simplifier.net/isik-basis-v4/isikprozedur

> **Written during migration - review before release.** The source page listed every search parameter individually with an example query and a link into the FHIR base specification. Condensed here to the parameter names the source page declares as mandatory (MUSS): `_id`, `_profile`, `status`, `category`, `code`, `date`, `subject`, `patient`, `bodySite`, `dokumentationsdatum`, `durchfuehrungsabsicht`, `outcome` and `extension-intention`.

**Usages:**

* Derived from this Profile: [MII PR Onkologie Präoperative Drahtmarkierung Mamma](StructureDefinition-mii-pr-onko-krk-operation.md), [MII PR Onkologie Mamma Operation](StructureDefinition-mii-pr-onko-mamma-operation.md), [MII PR Onkologie Präoperative Drahtmarkierung Mamma](StructureDefinition-mii-pr-onko-mamma-sozialdienst.md), [MII PR Onko Melanom Exzision](StructureDefinition-mii-pr-onko-melanom-exzision.md) and [MII PR Onko Prostata Operation](StructureDefinition-mii-pr-onko-prostata-operation.md)
* Refer to this Profile: [MII PR Onkologie Präoperative Drahtmarkierung Mamma](StructureDefinition-mii-pr-onko-krk-operation.md), [MII PR Onkologie Mamma Operation](StructureDefinition-mii-pr-onko-mamma-operation.md), [MII PR Onkologie Präoperative Markierung Mamma](StructureDefinition-mii-pr-onko-mamma-praeoperative-markierung.md) and [MII PR Onkologie Clavien Dindo](StructureDefinition-mii-pr-onko-prostate-clavien-dindo.md)
* Examples for this Profile: [Procedure/PatientKimMusterperson-Procedure-4](Procedure-PatientKimMusterperson-Procedure-4.md), [Procedure/mii-exa-onko-operation-1](Procedure-mii-exa-onko-operation-1.md), [Procedure/mii-exa-onko-prostata-surgery-1](Procedure-mii-exa-onko-prostata-surgery-1.md), [Procedure/mii-exa-onko-prostata-surgery-2](Procedure-mii-exa-onko-prostata-surgery-2.md)... Show 5 more, [Procedure/mii-exa-onko-right-hemicolectomy](Procedure-mii-exa-onko-right-hemicolectomy.md), [Procedure/mii-exa-onko-sigmoid-resection-part1](Procedure-mii-exa-onko-sigmoid-resection-part1.md), [Procedure/mii-exa-onko-sigmoid-resection-part2](Procedure-mii-exa-onko-sigmoid-resection-part2.md), [Procedure/mii-exa-onko-sigmoid-resection-part3](Procedure-mii-exa-onko-sigmoid-resection-part3.md) and [Procedure/mii-exa-onko-sigmoid-resection](Procedure-mii-exa-onko-sigmoid-resection.md)
* CapabilityStatements using this Profile: [MII CPS Onkology CapabilityStatement](CapabilityStatement-mii-cps-onko-capabilitystatement.md)

You can also check for [usages in the FHIR IG Statistics](https://packages2.fhir.org/xig/resource/de.medizininformatikinitiative.kerndatensatz.onkologie|current/StructureDefinition/StructureDefinition-mii-pr-onko-operation.json)

### Formal Views of Profile Content

 [Description of Profiles, Differentials, Snapshots, and their representations](http://build.fhir.org/ig/FHIR/ig-guidance/readingIgs.html#structure-definitions). 

 

Other representations of profile: [CSV](../StructureDefinition-mii-pr-onko-operation.csv), [Excel](../StructureDefinition-mii-pr-onko-operation.xlsx), [Schematron](../StructureDefinition-mii-pr-onko-operation.sch) 



## Resource Content

```json
{
  "resourceType" : "StructureDefinition",
  "id" : "mii-pr-onko-operation",
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
  "url" : "https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-operation",
  "version" : "2026.0.3",
  "name" : "MII_PR_Onko_Operation",
  "title" : "MII PR Onkologie Operation",
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
  "description" : "Operation nach OPS inklusive Intention, Datum und Komplikationen:",
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
        "map" : "13",
        "comment" : "Operation"
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
      "short" : "Intention der OP",
      "_short" : {
        "extension" : [{
          "extension" : [{
            "url" : "lang",
            "valueCode" : "de-DE"
          },
          {
            "url" : "content",
            "valueString" : "Intention der OP"
          }],
          "url" : "http://hl7.org/fhir/StructureDefinition/translation"
        }]
      },
      "definition" : "Intention der OP gemäß 13.1 oBDS 2021",
      "_definition" : {
        "extension" : [{
          "extension" : [{
            "url" : "lang",
            "valueCode" : "de-DE"
          },
          {
            "url" : "content",
            "valueString" : "Intention der OP gemäß 13.1 oBDS 2021"
          }],
          "url" : "http://hl7.org/fhir/StructureDefinition/translation"
        }]
      },
      "min" : 1,
      "max" : "1",
      "type" : [{
        "code" : "Extension",
        "profile" : ["https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-ex-onko-operation-intention"]
      }],
      "mustSupport" : true
    },
    {
      "id" : "Procedure.extension:Intention.value[x].coding.code",
      "path" : "Procedure.extension.value[x].coding.code",
      "mapping" : [{
        "identity" : "oBDS",
        "map" : "13.1",
        "comment" : "Intention der Operation"
      }]
    },
    {
      "id" : "Procedure.extension:Urgency",
      "path" : "Procedure.extension",
      "sliceName" : "Urgency",
      "short" : "Art des Eingriffs",
      "_short" : {
        "extension" : [{
          "extension" : [{
            "url" : "lang",
            "valueCode" : "de-DE"
          },
          {
            "url" : "content",
            "valueString" : "Art des Eingriffs"
          }],
          "url" : "http://hl7.org/fhir/StructureDefinition/translation"
        }]
      },
      "definition" : "Modalität der Eingriffsdurchführung gemäß KR6 oBDS 2021",
      "_definition" : {
        "extension" : [{
          "extension" : [{
            "url" : "lang",
            "valueCode" : "de-DE"
          },
          {
            "url" : "content",
            "valueString" : "Modalität der Eingriffsdurchführung - Elektiveingriff vs. Notfalleingriff - gemäß KR6 oBDS 2021"
          }],
          "url" : "http://hl7.org/fhir/StructureDefinition/translation"
        }]
      },
      "min" : 0,
      "max" : "1",
      "type" : [{
        "code" : "Extension",
        "profile" : ["https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-ex-onko-operation-urgency"]
      }],
      "mustSupport" : true
    },
    {
      "id" : "Procedure.extension:Urgency.value[x].coding.code",
      "path" : "Procedure.extension.value[x].coding.code",
      "mapping" : [{
        "identity" : "oBDS",
        "map" : "KR6",
        "comment" : "Art des Eingriffs (Modalität der Eingriffsdurchführung)"
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
      "type" : [{
        "code" : "Reference",
        "targetProfile" : ["http://hl7.org/fhir/StructureDefinition/Observation",
        "http://hl7.org/fhir/StructureDefinition/Procedure"]
      }],
      "mustSupport" : true
    },
    {
      "id" : "Procedure.code.coding:ops",
      "path" : "Procedure.code.coding",
      "sliceName" : "ops",
      "short" : "OPS-Kode der Operation",
      "_short" : {
        "extension" : [{
          "extension" : [{
            "url" : "lang",
            "valueCode" : "de-DE"
          },
          {
            "url" : "content",
            "valueString" : "OPS-Kode der Operation"
          }],
          "url" : "http://hl7.org/fhir/StructureDefinition/translation"
        },
        {
          "extension" : [{
            "url" : "lang",
            "valueCode" : "en-US"
          },
          {
            "url" : "content",
            "valueString" : "OPS code"
          }],
          "url" : "http://hl7.org/fhir/StructureDefinition/translation"
        }]
      },
      "definition" : "OPS-Kode der Operation gemäß 13.3 oBDS 2021",
      "_definition" : {
        "extension" : [{
          "extension" : [{
            "url" : "lang",
            "valueCode" : "de-DE"
          },
          {
            "url" : "content",
            "valueString" : "OPS-Kode der Operation gemäß 13.3 oBDS 2021"
          }],
          "url" : "http://hl7.org/fhir/StructureDefinition/translation"
        },
        {
          "extension" : [{
            "url" : "lang",
            "valueCode" : "en-US"
          },
          {
            "url" : "content",
            "valueString" : "A reference to a code defined by the German Procedure Classification OPS"
          }],
          "url" : "http://hl7.org/fhir/StructureDefinition/translation"
        }]
      }
    },
    {
      "id" : "Procedure.code.coding:ops.version",
      "path" : "Procedure.code.coding.version",
      "mapping" : [{
        "identity" : "oBDS",
        "map" : "13.4",
        "comment" : "OPS Version"
      }]
    },
    {
      "id" : "Procedure.code.coding:ops.code",
      "path" : "Procedure.code.coding.code",
      "mapping" : [{
        "identity" : "oBDS",
        "map" : "13.3",
        "comment" : "OPS"
      }]
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
        "code" : "dateTime"
      }]
    },
    {
      "id" : "Procedure.performed[x]:performedDateTime",
      "path" : "Procedure.performed[x]",
      "sliceName" : "performedDateTime",
      "type" : [{
        "code" : "dateTime"
      }],
      "mapping" : [{
        "identity" : "oBDS",
        "map" : "13.2",
        "comment" : "OP Datum"
      }]
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
        "valueSet" : "https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/ValueSet/mii-vs-onko-beurteilung-lokaler-residualstatus"
      },
      "mapping" : [{
        "identity" : "oBDS",
        "map" : "10.1",
        "comment" : "Beurteilung des lokalen Residualstatus nach Abschluss der Operation"
      }]
    },
    {
      "id" : "Procedure.outcome.coding",
      "path" : "Procedure.outcome.coding",
      "short" : "Lokaler Residualstatus",
      "_short" : {
        "extension" : [{
          "extension" : [{
            "url" : "lang",
            "valueCode" : "de-DE"
          },
          {
            "url" : "content",
            "valueString" : "Lokaler Residualstatus"
          }],
          "url" : "http://hl7.org/fhir/StructureDefinition/translation"
        }]
      },
      "definition" : "Lokaler Residualstatus der OP gemäß 10.1 oBDS 2021. Globaler Residualstatus wird prozedurenunabhängig als eigenständige Observation kodiert.",
      "_definition" : {
        "extension" : [{
          "extension" : [{
            "url" : "lang",
            "valueCode" : "de-DE"
          },
          {
            "url" : "content",
            "valueString" : "Lokaler Residualstatus der OP gemäß 10.1 oBDS 2021. Globaler Residualstatus wird prozedurenunabhängig als eigenständige Observation kodiert."
          }],
          "url" : "http://hl7.org/fhir/StructureDefinition/translation"
        }]
      }
    },
    {
      "id" : "Procedure.outcome.coding.system",
      "path" : "Procedure.outcome.coding.system",
      "patternUri" : "https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/CodeSystem/mii-cs-onko-residualstatus",
      "mustSupport" : true
    },
    {
      "id" : "Procedure.outcome.coding.code",
      "path" : "Procedure.outcome.coding.code",
      "mustSupport" : true
    },
    {
      "id" : "Procedure.complication",
      "path" : "Procedure.complication",
      "slicing" : {
        "discriminator" : [{
          "type" : "pattern",
          "path" : "$this"
        }],
        "rules" : "open"
      },
      "mustSupport" : true,
      "mapping" : [{
        "identity" : "oBDS",
        "map" : "13.5",
        "comment" : "OP Komplikationen "
      }]
    },
    {
      "id" : "Procedure.complication:compl_obds",
      "path" : "Procedure.complication",
      "sliceName" : "compl_obds",
      "min" : 0,
      "max" : "*",
      "mustSupport" : true,
      "binding" : {
        "strength" : "required",
        "valueSet" : "https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/ValueSet/mii-vs-onko-operation-komplikation"
      }
    },
    {
      "id" : "Procedure.complication:compl_obds.coding",
      "path" : "Procedure.complication.coding",
      "short" : "Komplikation der OP laut oBDS",
      "_short" : {
        "extension" : [{
          "extension" : [{
            "url" : "lang",
            "valueCode" : "de-DE"
          },
          {
            "url" : "content",
            "valueString" : "Komplikation der OP laut oBDS"
          }],
          "url" : "http://hl7.org/fhir/StructureDefinition/translation"
        }]
      },
      "definition" : "Komplikation der OP gemäß 13.5 oBDS 2021",
      "_definition" : {
        "extension" : [{
          "extension" : [{
            "url" : "lang",
            "valueCode" : "de-DE"
          },
          {
            "url" : "content",
            "valueString" : "Komplikation der OP gemäß 13.5 oBDS 2021"
          }],
          "url" : "http://hl7.org/fhir/StructureDefinition/translation"
        }]
      }
    },
    {
      "id" : "Procedure.complication:compl_obds.coding.system",
      "path" : "Procedure.complication.coding.system",
      "patternUri" : "https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/CodeSystem/mii-cs-onko-operation-komplikation"
    },
    {
      "id" : "Procedure.complication:compl_obds.coding.code",
      "path" : "Procedure.complication.coding.code",
      "min" : 1,
      "mustSupport" : true
    },
    {
      "id" : "Procedure.complication:compl_icd10",
      "path" : "Procedure.complication",
      "sliceName" : "compl_icd10",
      "min" : 0,
      "max" : "*",
      "mustSupport" : true,
      "binding" : {
        "strength" : "required",
        "valueSet" : "http://fhir.de/ValueSet/bfarm/icd-10-gm"
      }
    },
    {
      "id" : "Procedure.complication:compl_icd10.coding",
      "path" : "Procedure.complication.coding",
      "short" : "Komplikation der OP Sonstige ICD-10",
      "_short" : {
        "extension" : [{
          "extension" : [{
            "url" : "lang",
            "valueCode" : "de-DE"
          },
          {
            "url" : "content",
            "valueString" : "Komplikation der OP Sonstige ICD-10"
          }],
          "url" : "http://hl7.org/fhir/StructureDefinition/translation"
        }]
      },
      "definition" : "Komplikation der OP - soweit nicht in 13.1 oBDS 2021 enthalten - als ICD-10-GM",
      "_definition" : {
        "extension" : [{
          "extension" : [{
            "url" : "lang",
            "valueCode" : "de-DE"
          },
          {
            "url" : "content",
            "valueString" : "Komplikation der OP - soweit nicht in 13.1 oBDS 2021 enthalten - als ICD-10-GM"
          }],
          "url" : "http://hl7.org/fhir/StructureDefinition/translation"
        }]
      }
    },
    {
      "id" : "Procedure.complication:compl_icd10.coding.system",
      "path" : "Procedure.complication.coding.system",
      "min" : 1,
      "patternUri" : "http://fhir.de/CodeSystem/bfarm/icd-10-gm"
    },
    {
      "id" : "Procedure.complication:compl_icd10.coding.code",
      "path" : "Procedure.complication.coding.code",
      "min" : 1
    }]
  }
}

```
