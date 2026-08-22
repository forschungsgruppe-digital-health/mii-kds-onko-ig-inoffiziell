# Guidance for Implementers - MII IG Kerndatensatz-Modul Onkologie v2026.0.3

* [**Table of Contents**](toc.md)
* [**Guidance**](guidance.md)
* **Guidance for Implementers**

## Guidance for Implementers

Technical guidance for DIC implementers on implementing the profiles of the **Onkologie** module (ETL from primary systems, FHIR API, validation).

> [TODO: Describe the technical implementation steps for your module.]

### Technical implementation

> **Written during migration - review before release.** The source guide opened its technical-implementation chapter with a page left blank on purpose. The four sections below carry that chapter's content: how the profiles inherit and which oBDS data fields they map, how the resources reference one another, why the module uses extensions and which alternatives were weighed, and the current state of FHIR validation. The terminologies are described on [Code Systems](code-systems.md) and [Value Sets](value-sets.md), the required server capabilities on [Capability Statements](capability-statements.md).

### Profile - content and inheritance

The following presents the profiles in a simplified form. This presentation puts particular emphasis on a clear overview of:

* inheritance from other profiles
* the mapping of the oBDS data fields onto the corresponding FHIR elements.

The image files can be viewed and downloaded individually [here (Github)](https://github.com/medizininformatik-initiative/kerndatensatzmodul-onkologie/tree/refs/heads/dev/implementation-guides/ImplementationGuide-2026.x-DE/Images) for a better view (provided as `.png` and `.svg`).

#### Diagnose

The diagnosis carries information on the primary diagnosis itself as well as on the histology and the site of the primary tumour.

#### Histologie

#### TNM-Klassifikation

#### Further classifications, residual status, general health status, distant metastases

#### Procedures, medication and adverse events

#### Course of disease, tumour board, death and genetic variant

### Profile - relationships and references

The following overview presents the references of the resources among one another.

The image files can be viewed and downloaded individually [here (Github)](https://github.com/medizininformatik-initiative/kerndatensatzmodul-onkologie/tree/refs/heads/dev/implementation-guides/ImplementationGuide-2026.x-DE/Images) for a better view (provided as `.png` and `.svg`).

#### Envisaged future integration of the Biobank, MolGen-Befundbericht and Pathologiebefund modules

### Use of extensions

The oBDS is implemented using extensions. This has to do in particular with the oBDS data structure and the oBDS-specific code systems, and with the attempt to represent them with modules from the MII Core Dataset.

The extensions presented here were designed with a focus on integration into the MII Core Dataset and on the secondary use of cancer-registry data through the FDPG.

Since the use of extensions is to be avoided where possible in a FHIR context — at least as long as there are sensible alternatives within the existing FHIR data model — implementation alternatives are set out and discussed below.

#### Prozeduren-Extension (Intention, Stellung)

**Intention**

* Necessity of the extension: 
* the FHIR R4 Procedure contains no element that can adequately represent the treatment intention.
* the MII Procedure therefore contains an extension [Durchführungsabsicht](https://www.medizininformatik-initiative.de/fhir/core/modul-prozedur/StructureDefinition/Durchfuehrungsabsicht)
* CarePlan contains the element intent; this, however, describes the strength of the intention of the resource (how binding the resource is, that is plan, option, order etc.) and can therefore not be used to code the treatment intention in the sense of the oBDS
 
* Alternative proposal 
* A consented SNOMED mapping may possibly achieve a match, so that the treatment intention is recorded directly in SNOMED CT and can thus be carried out by means of the extension [Durchführungsabsicht](https://www.medizininformatik-initiative.de/fhir/core/modul-prozedur/StructureDefinition/Durchfuehrungsabsicht).
 

**Stellung**

* The Stellung of a radiotherapy or systemic therapy cannot be represented through the existing FHIR procedures. Representing it through another resource (e.g. in CarePlan as part of the tumour board) was discussed, but judged not to be more advantageous.

#### Strahlentherapie-Bestrahlungs-Extension

* Necessity of the extension: representing the complex oBDS Bestrahlung type through traditional FHIR resources is currently only possible to a limited extent.
* Representing the individual irradiations as MII is not possible, because mandatory OPS codes or SNOMED CT codes have to be given in each case, which are not available for all oBDS data fields.
* Alternative proposal 
* Strahlentherapie remains an MII_Prozedur
* define Bestrahlung as an R4 Procedure 
* bodySite for the Zielgebiet, with a laterality extension
* code as the Applikationsart
* method as a slice for the Strahlenart
* dose and boost still represented through extensions
 
 

#### TNM (c/p, itc, sn) extensions

Alternative implementations:

* as individual observations with the existing TNM grouper logic 
* advantage: behaves exactly like the other categories and symbols
* disadvantage: does not occur on its own, tight coupling to the T/N/M classification profiles required
 
* as part of the T/N/M categories (e.g. component)

### QA and validation

> **Written during migration - review before release.** The counts, filter statistics and error lists in this section are the snapshot the source guide recorded on 2025-12-16 for package version 2026.0.0, and every repository link below points at the upstream `kerndatensatzmodul-onkologie` repository they were taken from. Re-measure them against this guide's own build, and re-target the links, before release.

This page documents the current state of FHIR validation for the MII Modul Onkologie.

#### Validierungsübersicht

The module is continuously validated against the FHIR R4 standard and the defined profiles. Since Simplifier does not provide a public QA report the way classic FHIR IG Publisher builds do, we document the validation status transparently here.

**Current statistics** (as of 2025-12-16, version 2026.0.0):

* **Actionable errors**: 9
* **Filtered messages**: ~700+ (via advisor.json)

Most of the original messages are suppressed by filters in `advisor.json`, because they concern false positives or external dependencies.

#### Terminology server and validation configuration

The validation in question concerns the current package version **2026.0.0**.

**MII Terminology Server**: [https://termserv.mii.medizininformatik-initiative.de/fhir](https://termserv.mii.medizininformatik-initiative.de/fhir)

**Validation configuration**: [`advisor.json`](https://github.com/medizininformatik-initiative/kerndatensatzmodul-onkologie/blob/dev/advisor.json)

#### Filtered validation messages

These messages are suppressed by `advisor.json`. The table shows the estimated number of occurrences and the reason for the filter:

| | | | |
| :--- | :--- | :--- | :--- |
| `Terminology_TX_NoValid_16` | ~310 | lines 3, 10-12 | Concerns ImplementationGuide parameters and all StructureDefinitions/ValueSets/CodeSystems. External terminology-server limitation. |
| `MSG_DRAFT` | ~14 | line 4 | Expected warning during the development phase. Resolves at the final release. |
| `dom-6` | ? | line 5 | FHIR base rule for DomainResource. Known validator artefact. |
| `eld-20` | ~294 | line 6 | ElementDefinition constraint. Structural validator limitation. |
| `UNABLE_TO_INFER_CODESYSTEM` | ~100 | lines 7-9 | The system URI cannot be inferred for certain codes (concerns StructureDefinition, ValueSet, CodeSystem). |

**Total suppressions**: ~700+ messages are filtered

#### Remaining active validation issues

These errors are **not** filtered and should be fixed:

##### Current errors (as of 2025-12-16)

| | | | |
| :--- | :--- | :--- | :--- |
| **Unknown_Code** | 3 | HER2 status, receptor status estrogen/progesterone | 🟡 TODO: check code bindings |
| **Reference_Not_Found** | 1 | AdverseEvent (MedDRA) | 🔵 EXTERNAL: MedDRA proprietary |
| **Profile-Match** | 1 | KRK bundle (operation) | 🟡 TODO: correct the bundle structure |
| **TX-Server** | 2 | Mamma bundle, MRT fascia | 🔵 EXTERNAL: terminology-server limitation |
| **Other** | 2 | KRK observation, Mamma HER2 | 🟡 TODO: review |

##### Affected files

* `Bundle-mii-exa-onko-mamma-example-bundle-1.json` (2 errors)
* `AdverseEvent-mii-pr-onko-nebenwirkung-0.json` (1 error)
* `Bundle-mii-exa-onko-krk-bundle.json` (1 error)
* `Observation-mii-exa-onko-krk-abstand-mesorektale-fascie.json` (1 error)
* `Observation-mii-exa-onko-mamma-her2neu-status.json` (1 error)
* `Observation-mii-exa-onko-mamma-rezeptorstatus-estrogen-1.json` (1 error)
* `Observation-mii-exa-onko-mamma-rezeptorstatus-progesteron-1.json` (1 error)
* `StructureDefinition-mii-pr-onko-krk-mrt-mesorektale-faszie.json` (1 error)

##### External dependencies (EXTERNAL)

| | | |
| :--- | :--- | :--- |
| **MedDRA** | Proprietary terminology, not publicly validatable | Adverse events cannot be fully validated |
| **ICD-O-3** | Morphology codes are only available to a limited extent on FHIR TX servers | Histology coding partly not validatable |
| **OPS versions** | Multiple OPS versions lead to warnings | Procedure validation shows warnings on a version mix |

#### Status legend

| | | |
| :--- | :--- | :--- |
| 🔴 | **TODO** | Errors to be fixed actively |
| 🟡 | **MONITOR** | Observe, action may be required |
| 🔵 | **EXTERNAL** | External issue, resolves through updates of the dependencies |
| ⚪ | **FILTERED** | Filtered by advisor.json |

#### Continuous integration

The FHIR validation runs automatically on every push via GitHub Actions:

* **JAVA_FHIR_VALIDATION**: HL7 FHIR Validator (official)
* **DOTNET_FHIR_VALIDATION**: Firely .NET Validator (alternative)

🔗 [Show the current CI runs](https://github.com/medizininformatik-initiative/kerndatensatzmodul-onkologie/actions)

The validation results are available directly in the repository:

* [`validation.html`](https://github.com/medizininformatik-initiative/kerndatensatzmodul-onkologie/blob/dev/validation.html) - HTML report
* [`validation.json`](https://github.com/medizininformatik-initiative/kerndatensatzmodul-onkologie/blob/dev/validation.json) - machine-readable results

#### How can I help?

If you would like to contribute to improving the validation:

1. **Check**the TODO-marked errors above
1. **Download**the validation artefacts from the[CI runs](https://github.com/medizininformatik-initiative/kerndatensatzmodul-onkologie/actions)
1. **Create**an issue or pull request in the[GitHub repository](https://github.com/medizininformatik-initiative/kerndatensatzmodul-onkologie)

**Note**: This page is maintained manually. For the most up-to-date technical state, see the CI runs in the repository.

