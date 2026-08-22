<!-- markdownlint-disable MD041 -->
<!-- Migrated from Therapieempfehlung-Kombinationstherapie-RequestGroup.page.md
     (MII IG Modul Onkologie, Simplifier). Simplifier/FQL directives (page title,
     tree/XML/JSON/link tabs, FQL query blocks for profile metadata, the value-set
     listing and the oBDS mapping) were removed - the IG Publisher renders all of that
     on this artifact page. The two example directives of the source page pointed at
     instances that this module does not (yet) generate, so no example is named here.
     German mirror: input/translations/de/intro-notes/StructureDefinition-mii-pr-onko-therapieempfehlung-kombinationstherapie-intro.md -->

This profile describes structured **therapy recommendations for combination therapies** by means of a
RequestGroup. It enables the detailed representation of multi-agent protocols and alternative therapy
options for molecular tumor boards.

### Content

The RequestGroup profile acts as a "protocol coordinator" between **CarePlan recommendations** and
**specific therapy resources** (SystemischeTherapie, MedicationRequest, etc.).

### Use cases

#### **Multi-agent therapy protocols**

- **Anti-HER2 combination**: Trastuzumab + Pertuzumab
- **CDK4/6 + hormone therapy**: Palbociclib + Letrozol
- **Triplet therapies**: Tucatinib + Trastuzumab + Capecitabine

#### **Alternative therapy options**

- **Line therapy**: first-, second-, third-line options based on resistance
- **Biomarker-based**: different options depending on the mutation status
- **Class-based**: "any CDK4/6 inhibitor" vs. a specific selection

### Technical architecture

#### **RequestGroup as protocol coordinator**

```
CarePlan.activity.reference → RequestGroup
├── code: oBDS-Therapietyp (ZS, CZ, IM, etc.)
├── basedOn: Reference(CarePlan) [Rückverfolgbarkeit]
└── action[].resource: Reference(SystemischeTherapie)
```

#### **Therapy type classification**

The **RequestGroup.code** element carries the **oBDS therapy type classification**:

- **ZS**: Zielgerichtete Substanzen
- **CZ**: Chemotherapie + zielgerichtete Substanzen
- **IM**: Immun-/Antikörpertherapie
- **CI**: Chemo- + Immun-/Antikörpertherapie
- **CIZ**: Chemo- + Immun-/Antikörpertherapie + zielgerichtete Substanzen

**Important**: this classification was originally in `CarePlan.activity.detail.code` (oBDS 19.1), but
is moved into the RequestGroup because of FHIR invariants.

### Implementation options

#### **Option 1: pharmaceutical classes**

For **class-based recommendations** (e.g. "any CDK4/6 inhibitor"):

```
RequestGroup
├── code: "CZ" (Chemotherapie + zielgerichtete Substanzen)
└── action[0].resource: Reference(SystemischeTherapie)
    └── code.text: "CDK4/6 Inhibitor (Klasse L01XE) - Palbociclib, Ribociclib oder Abemaciclib"
```

**Application**: when a molecular tumor board recommends a **drug class** and leaves the final
selection to the treating physician.

#### **Option 2: specific drug selection**

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

**Application**: when a molecular tumor board recommends **specific alternatives** with clear
preferences based on resistance patterns or the clinical situation.

### FHIR invariant conformance

**Problem**: a FHIR R4 invariant prevents the simultaneous use of `code` and `action.resource`
**Solution**: this profile **accepts both approaches**, depending on the use case:

- **Option 1**: uses `code` for the therapy type and `action.resource` for the class-level therapy
- **Option 2**: uses `code` for the therapy type and nested `action.action.resource` for specific
  options with `selectionBehavior`

### oBDS context

#### **Mapping to oBDS 19.1**

```
RequestGroup.code → "19.1" "Tumorkonferenz Therapieempfehlung Typ"
```

**Data fields**:

- **CH**: Chemotherapie
- **HO**: Hormontherapie
- **IM**: Immun-/Antikörpertherapie
- **ZS**: Zielgerichtete Substanzen
- **SZ**: Stammzelltransplantation
- **Combinations**: CI, CZ, CIZ, IZ
- **Others**: OP, ST, WW, AS, SO

#### **Extended structuring**

While the oBDS only records the **therapy type**, the RequestGroup additionally enables:

- **Specific drugs** per recommendation
- **Alternative options** with priorities
- **Combination logic** for multi-agent protocols

### Terminology binding

**RequestGroup.code**:

- **ValueSet**: `mii-vs-onko-therapieempfehlung-typ`
- **Binding**: Preferred
- **Source**: oBDS therapy types from `mii-cs-onko-therapie-typ`

### Search parameters

1. The search parameter ```_id``` SHALL be supported:
    ```GET [base]/RequestGroup?_id=1234```

2. The search parameter "_profile" SHALL be supported:
    ```GET [base]/RequestGroup?_profile=https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-therapieempfehlung-kombinationstherapie```

3. The search parameter "subject" SHALL be supported:
    ```GET [base]/RequestGroup?subject=Patient/example```

4. The search parameter "code" SHOULD be supported:
    ```GET [base]/RequestGroup?code=ZS```

5. The search parameter "based-on" SHOULD be supported:
    ```GET [base]/RequestGroup?based-on=CarePlan/tumorkonferenz-example```
