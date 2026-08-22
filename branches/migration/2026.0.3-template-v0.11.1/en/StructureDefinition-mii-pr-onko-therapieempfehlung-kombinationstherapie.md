# MII PR Onkologie Therapieempfehlung Kombinationstherapie - MII IG Kerndatensatz-Modul Onkologie v2026.0.3

* [**Table of Contents**](toc.md)
* [**Artifacts Summary**](artifacts.md)
* **MII PR Onkologie Therapieempfehlung Kombinationstherapie**

## Resource Profile: MII PR Onkologie Therapieempfehlung Kombinationstherapie 

| | |
| :--- | :--- |
| *Official URL*:https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-therapieempfehlung-kombinationstherapie | *Version*:2026.0.3 |
| Active as of 2026-08-22 | *Computable Name*:MII_PR_Onko_Therapieempfehlung_Kombinationstherapie |

 
Dieses Profil beschreibt eine Empfehlung für eine Kombinationstherapie im Rahmen der Tumorkonferenz 

This profile describes structured **therapy recommendations for combination therapies** by means of a RequestGroup. It enables the detailed representation of multi-agent protocols and alternative therapy options for molecular tumor boards.

### Content

The RequestGroup profile acts as a "protocol coordinator" between **CarePlan recommendations** and **specific therapy resources** (SystemischeTherapie, MedicationRequest, etc.).

### Use cases

#### Multi-agent therapy protocols

* **Anti-HER2 combination**: Trastuzumab + Pertuzumab
* **CDK4/6 + hormone therapy**: Palbociclib + Letrozol
* **Triplet therapies**: Tucatinib + Trastuzumab + Capecitabine

#### Alternative therapy options

* **Line therapy**: first-, second-, third-line options based on resistance
* **Biomarker-based**: different options depending on the mutation status
* **Class-based**: "any CDK4/6 inhibitor" vs. a specific selection

### Technical architecture

#### RequestGroup as protocol coordinator

```
CarePlan.activity.reference → RequestGroup
├── code: oBDS-Therapietyp (ZS, CZ, IM, etc.)
├── basedOn: Reference(CarePlan) [Rückverfolgbarkeit]
└── action[].resource: Reference(SystemischeTherapie)

```

#### Therapy type classification

The **RequestGroup.code** element carries the **oBDS therapy type classification**:

* **ZS**: Zielgerichtete Substanzen
* **CZ**: Chemotherapie + zielgerichtete Substanzen
* **IM**: Immun-/Antikörpertherapie
* **CI**: Chemo- + Immun-/Antikörpertherapie
* **CIZ**: Chemo- + Immun-/Antikörpertherapie + zielgerichtete Substanzen

**Important**: this classification was originally in `CarePlan.activity.detail.code` (oBDS 19.1), but is moved into the RequestGroup because of FHIR invariants.

### Implementation options

#### Option 1: pharmaceutical classes

For **class-based recommendations** (e.g. "any CDK4/6 inhibitor"):

```
RequestGroup
├── code: "CZ" (Chemotherapie + zielgerichtete Substanzen)
└── action[0].resource: Reference(SystemischeTherapie)
    └── code.text: "CDK4/6 Inhibitor (Klasse L01XE) - Palbociclib, Ribociclib oder Abemaciclib"

```

**Application**: when a molecular tumor board recommends a **drug class** and leaves the final selection to the treating physician.

#### Option 2: specific drug selection

For **specific options** with selection logic:

```
RequestGroup
├── code: "ZS" (Zielgerichtete Substanzen)
├── action[0].selectionBehavior: #any
├── action[0].requiredBehavior: #must
├── action[0].action[0]: Reference(Trastuzumab) [priority: routine]
├── action[0].action[1]: Reference(T-DM1) [priority: asap]
└── action[0].action[2]: Reference(Tucatinib) [priority: stat]

```

**Application**: when a molecular tumor board recommends **specific alternatives** with clear preferences based on resistance patterns or the clinical situation.

### FHIR invariant conformance

**Problem**: a FHIR R4 invariant prevents the simultaneous use of `code` and `action.resource` **Solution**: this profile **accepts both approaches**, depending on the use case:

* **Option 1**: uses `code` for the therapy type and `action.resource` for the class-level therapy
* **Option 2**: uses `code` for the therapy type and nested `action.action.resource` for specific options with `selectionBehavior`

### oBDS context

#### Mapping to oBDS 19.1

```
RequestGroup.code → "19.1" "Tumorkonferenz Therapieempfehlung Typ"

```

**Data fields**:

* **CH**: Chemotherapie
* **HO**: Hormontherapie
* **IM**: Immun-/Antikörpertherapie
* **ZS**: Zielgerichtete Substanzen
* **SZ**: Stammzelltransplantation
* **Combinations**: CI, CZ, CIZ, IZ
* **Others**: OP, ST, WW, AS, SO

#### Extended structuring

While the oBDS only records the **therapy type**, the RequestGroup additionally enables:

* **Specific drugs** per recommendation
* **Alternative options** with priorities
* **Combination logic** for multi-agent protocols

### Terminology binding

**RequestGroup.code**:

* **ValueSet**: `mii-vs-onko-therapieempfehlung-typ`
* **Binding**: Preferred
* **Source**: oBDS therapy types from `mii-cs-onko-therapie-typ`

### Search parameters

1. The search parameter `_id` SHALL be supported: `GET [base]/RequestGroup?_id=1234`
1. The search parameter "_profile" SHALL be supported: `GET [base]/RequestGroup?_profile=https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-therapieempfehlung-kombinationstherapie`
1. The search parameter "subject" SHALL be supported: `GET [base]/RequestGroup?subject=Patient/example`
1. The search parameter "code" SHOULD be supported: `GET [base]/RequestGroup?code=ZS`
1. The search parameter "based-on" SHOULD be supported: `GET [base]/RequestGroup?based-on=CarePlan/tumorkonferenz-example`

**Usages:**

* Refer to this Profile: [MII PR Onkologie Tumorkonferenz](StructureDefinition-mii-pr-onko-tumorkonferenz.md)
* Examples for this Profile: [RequestGroup/mii-exa-onko-folfox-requestgroup-modification](RequestGroup-mii-exa-onko-folfox-requestgroup-modification.md), [RequestGroup/mii-exa-onko-folfox-requestgroup](RequestGroup-mii-exa-onko-folfox-requestgroup.md), [RequestGroup/mii-exa-onko-molecular-cdk46-protocol](RequestGroup-mii-exa-onko-molecular-cdk46-protocol.md) and [RequestGroup/mii-exa-onko-molecular-her2-alternatives](RequestGroup-mii-exa-onko-molecular-her2-alternatives.md)
* CapabilityStatements using this Profile: [MII CPS Onkology CapabilityStatement](CapabilityStatement-mii-cps-onko-capabilitystatement.md)

You can also check for [usages in the FHIR IG Statistics](https://packages2.fhir.org/xig/resource/de.medizininformatikinitiative.kerndatensatz.onkologie|current/StructureDefinition/StructureDefinition-mii-pr-onko-therapieempfehlung-kombinationstherapie.json)

### Formal Views of Profile Content

 [Description of Profiles, Differentials, Snapshots, and their representations](http://build.fhir.org/ig/FHIR/ig-guidance/readingIgs.html#structure-definitions). 

 

Other representations of profile: [CSV](../StructureDefinition-mii-pr-onko-therapieempfehlung-kombinationstherapie.csv), [Excel](../StructureDefinition-mii-pr-onko-therapieempfehlung-kombinationstherapie.xlsx), [Schematron](../StructureDefinition-mii-pr-onko-therapieempfehlung-kombinationstherapie.sch) 



## Resource Content

```json
{
  "resourceType" : "StructureDefinition",
  "id" : "mii-pr-onko-therapieempfehlung-kombinationstherapie",
  "url" : "https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-therapieempfehlung-kombinationstherapie",
  "version" : "2026.0.3",
  "name" : "MII_PR_Onko_Therapieempfehlung_Kombinationstherapie",
  "title" : "MII PR Onkologie Therapieempfehlung Kombinationstherapie",
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
  "description" : "Dieses Profil beschreibt eine Empfehlung für eine Kombinationstherapie im Rahmen der Tumorkonferenz",
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
  }],
  "kind" : "resource",
  "abstract" : false,
  "type" : "RequestGroup",
  "baseDefinition" : "http://hl7.org/fhir/StructureDefinition/RequestGroup",
  "derivation" : "constraint",
  "differential" : {
    "element" : [{
      "id" : "RequestGroup",
      "path" : "RequestGroup"
    },
    {
      "id" : "RequestGroup.meta.profile",
      "path" : "RequestGroup.meta.profile",
      "mustSupport" : true
    },
    {
      "id" : "RequestGroup.identifier",
      "path" : "RequestGroup.identifier",
      "mustSupport" : true
    },
    {
      "id" : "RequestGroup.status",
      "path" : "RequestGroup.status",
      "mustSupport" : true
    },
    {
      "id" : "RequestGroup.intent",
      "path" : "RequestGroup.intent",
      "patternCode" : "proposal",
      "mustSupport" : true
    },
    {
      "id" : "RequestGroup.code",
      "path" : "RequestGroup.code",
      "short" : "Type of therapy recommendation",
      "definition" : "Classification of the therapy recommendation using oBDS therapy types (CH, HO, IM, ZS, etc.) to specify the kind of therapy being recommended.",
      "mustSupport" : true,
      "binding" : {
        "strength" : "preferred",
        "valueSet" : "https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/ValueSet/mii-vs-onko-therapieempfehlung-typ"
      }
    },
    {
      "id" : "RequestGroup.subject",
      "path" : "RequestGroup.subject",
      "min" : 1,
      "type" : [{
        "code" : "Reference",
        "targetProfile" : ["http://hl7.org/fhir/StructureDefinition/Patient"]
      }],
      "mustSupport" : true
    },
    {
      "id" : "RequestGroup.encounter",
      "path" : "RequestGroup.encounter",
      "mustSupport" : true
    },
    {
      "id" : "RequestGroup.authoredOn",
      "path" : "RequestGroup.authoredOn",
      "min" : 1,
      "mustSupport" : true
    },
    {
      "id" : "RequestGroup.reasonReference",
      "path" : "RequestGroup.reasonReference",
      "type" : [{
        "code" : "Reference",
        "targetProfile" : ["https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-diagnose-primaertumor"]
      }],
      "mustSupport" : true
    },
    {
      "id" : "RequestGroup.action",
      "path" : "RequestGroup.action",
      "mustSupport" : true
    },
    {
      "id" : "RequestGroup.action.code",
      "path" : "RequestGroup.action.code",
      "short" : "Empfohlenes Therapieprotokoll",
      "_short" : {
        "extension" : [{
          "extension" : [{
            "url" : "lang",
            "valueCode" : "de-DE"
          },
          {
            "url" : "content",
            "valueString" : "Empfohlenes Therapieprotokoll"
          }],
          "url" : "http://hl7.org/fhir/StructureDefinition/translation"
        }]
      },
      "definition" : "Empfohlenes Therapieprotokoll gemäß Tumorkonferenz",
      "_definition" : {
        "extension" : [{
          "extension" : [{
            "url" : "lang",
            "valueCode" : "de-DE"
          },
          {
            "url" : "content",
            "valueString" : "Spezifisches Therapieprotokoll empfohlen durch Tumorkonferenz. Bei Kombinationstherapien repräsentiert dies das Gesamtprotokoll mit einzelnen Medikamenten als Sub-Actions."
          }],
          "url" : "http://hl7.org/fhir/StructureDefinition/translation"
        }]
      },
      "mustSupport" : true,
      "binding" : {
        "strength" : "extensible",
        "valueSet" : "https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/ValueSet/mii-vs-onko-systemische-therapie-protokolle"
      }
    },
    {
      "id" : "RequestGroup.action.action",
      "path" : "RequestGroup.action.action",
      "short" : "Individual medications in protocol",
      "definition" : "For combination therapy protocols, each sub-action references an individual MedicationRequest with ATC/UNII coding",
      "type" : [{
        "code" : "BackboneElement"
      }],
      "mustSupport" : true
    },
    {
      "id" : "RequestGroup.action.action.resource",
      "path" : "RequestGroup.action.action.resource",
      "type" : [{
        "code" : "Reference",
        "targetProfile" : ["https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-therapieempfehlung-medikation"]
      }],
      "mustSupport" : true
    }]
  }
}

```
