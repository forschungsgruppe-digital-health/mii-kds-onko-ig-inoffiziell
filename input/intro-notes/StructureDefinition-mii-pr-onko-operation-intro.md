This profile describes a surgical procedure (Operation) in oncology.

- The oncology surgery profile is derived from the MII Prozedur module and additionally specialised for oBDS content. https://simplifier.net/guide/mii-ig-modul-prozedur-2024-de/MIIIGModulProzedur/TechnischeImplementierung/FHIRProfile/Prozedur-Procedure.page.md?version=current

### Category and code

- The MII Prozedur recommends representing the category by means of the OPS main categories transferred into SNOMED (https://www.medizininformatik-initiative.de/fhir/core/modul-prozedur/ValueSet/procedures-category-sct), where the SNOMED code `38771300` corresponds to OPS category "5 - Operationen". According to the oBDS, however, a different coding may be entered here in justified cases (e.g. `103693007` for "1 - Diagnostische Maßnahmen"). For that reason the category is not constrained further.
- The exact kind of procedure is coded in the field `Procedure.code`. **IMPORTANT**: every Procedure MUST have a code - either OPS or SNOMED CT.
- An OPS code SHOULD be used primarily. If no suitable OPS code exists, a SNOMED CT code MUST be chosen.
- At most one OPS value SHOULD be coded per Procedure resource. Additional procedures are represented as individual Procedure resources.
- Note: within the KDS module Onkologie the overarching MII Prozedur is also used to represent radiotherapy and systemic/watchful-waiting therapy. For the particularities of their categories and codes, see the profiles Strahlentherapie (`mii-pr-onko-strahlentherapie`) and Systemische Therapie (`mii-pr-onko-systemische-therapie`).

### Multi-part interventions and related surgeries

In complex oncological interventions, several operative procedures are frequently performed in one session. Because only one OPS code should be coded per Procedure resource, two modelling approaches are supported:

#### Approach 1: overarching Procedure with a general code

**IMPORTANT**: a Procedure MUST have either an OPS code OR a SNOMED CT code. If no suitable OPS code exists for the overarching Procedure, a suitable SNOMED CT code MUST be chosen.

1. **Overarching Procedure**: a main Procedure with a general SNOMED CT code for the location/kind of the intervention
   - `Procedure.code`: SNOMED CT code (e.g. 86481000 "Laparotomy (procedure)")
   - `Procedure.code.coding[ops]`: stays empty, because no specific OPS code exists
   - This Procedure SHOULD satisfy the MII_PR_Onko_Operation profile
   - **Note**: the SNOMED CT code must be chosen from the available SNOMED CT concepts

2. **Detailed part Procedures**: individual Procedure resources for each specific OPS code
   - Linked to the overarching Procedure via `Procedure.partOf`
   - Each with its specific OPS code

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
2. **Common overarching Procedure optional**: can serve as a grouping
3. **Alternative**: choose one of the Procedures as the "main Procedure" (the decision can be arbitrary)

**Note on harmonisation**: deciding which Procedure counts as the "main Procedure" can be difficult for complex tumour surgeries and is hard to harmonise post hoc.

#### Common aspects of multi-part interventions:

- **Point in time**: all linked procedures should have the same `performedDateTime` if they were performed in one session
- **Intention**: the extension for the surgical intention should be consistent across all linked procedures
- **Complications**: can be documented on the affected individual procedure or on the overarching Procedure
- **Residual status**: the local residual status is documented on the resecting procedure
- **References**: all Procedures should reference the same primary diagnosis (`reasonReference`) and, where applicable, the tumour board recommendation (`basedOn`)

#### Visualisation using the example of Kim Musterperson

<img src="https://raw.githubusercontent.com/medizininformatik-initiative/kerndatensatzmodul-onkologie/dev/implementation-guides/ImplementationGuide-2026.x-DE/Images/MII_Onko_MultiPartSurgery_Example/MII_Onko_MultiPartSurgery_Example.png" alt="Multi-Part Surgery Example: Kim Musterperson" style="max-width: 100%; height: auto;">

### Extensions

#### Intention

The MII Prozedur module already has a [Durchführungsabsicht](https://www.medizininformatik-initiative.de/fhir/core/modul-prozedur/StructureDefinition/Durchfuehrungsabsicht) extension bound to SNOMED CT codes. Since the intention of the surgery is, however, captured in the oBDS through an oBDS-specific answer set, the procedure was extended by an additional element "Intention". Existing extensions of the MII Prozedur module are optional and not directly relevant for mapping from the oBDS.

Further information: see the extension `mii-ex-onko-operation-intention`.

#### Urgency (Art des Eingriffs)

The "Urgency" extension captures the modality under which the intervention was performed. This data point originally comes from the organ-specific module Kolorektales Karzinom (KRK 6, oBDS 2021), but is **universally applicable to all Procedures** and was therefore integrated into the general Operation profile.

The extension distinguishes between:

- **E**: Elektiveingriff (planned intervention)
- **N**: Notfalleingriff (emergency intervention)
- **U**: Unbekannt (unknown)

This extension is particularly relevant for quality assurance and statistical analyses, because emergency interventions often show different outcomes and complication rates than planned interventions. Although originally defined for colorectal interventions, the distinction between elective and emergency interventions is clinically relevant for all surgical procedures.

**Use:**

```
* extension[urgency].valueCodeableConcept = $mii-cs-onko-operation-urgency#E "Elektiveingriff"
```

Further information: see the extension `mii-ex-onko-operation-urgency`.

### Residual status and further observations

The oBDS provides for recording the R status when tumour tissue is resected.
Depending on the procedure performed, the assessment of the residual status is to be made **locally** or **globally**. The oBDS records these as two different data points. In the FHIR profiling at hand, the local residual status (where applicable) is coded under Procedure.outcome. The global residual status is recorded through its own Observation (see Residualstatus: Observation.)

Besides the residual status there are further data points that can reference a surgery and that are reported together with it in the oBDS. These include the histological examinations (lymph nodes, grading) as well as ICD-O morphology, TNM and/or, where applicable, further classifications.

#### References to other profiles

A surgery recorded and reported within the cancer registries is frequently based on a therapy recommendation of a tumour board. In that case the elements should be linked via `Procedure.basedOn(Reference(CarePlan))`.
The surgery furthermore references the primary diagnosis via `Procedure.reasonReference`.

### Conformance

This profiling is compatible with the procedure profile of the ISiK Basismodule Stufe 4. https://simplifier.net/isik-basis-v4/isikprozedur

<!-- DERIVED:summary source=Operation-Procedure.page.md gate=B -->
> **Written during migration - review before release.** The source page listed every search parameter individually with an example query and a link into the FHIR base specification. Condensed here to the parameter names the source page declares as mandatory (MUSS): `_id`, `_profile`, `status`, `category`, `code`, `date`, `subject`, `patient`, `bodySite`, `dokumentationsdatum`, `durchfuehrungsabsicht`, `outcome` and `extension-intention`.
{: .ig-highlight .ig-highlight-blue}
