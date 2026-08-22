<!-- source: TechnischeImplementierung/FHIR-Profile/Organspezifische-Module/Mamma/Mamma-Her2neu-Status-Observation.page.md -->
The **Her2neu status profile** documents the diagnostic Her2neu status of a pathologically examined specimen in breast cancer. Her2neu (also HER2 or ERBB2) is an important prognostic and predictive biomarker that decides whether a patient is eligible for anti-HER2-directed therapy.

The Her2neu status is based on **immunohistochemical (IHC) staining** and, for certain findings, additionally on **in-situ hybridisation (ISH, e.g. FISH or CISH)**. The determination follows the ASCO/CAP guidelines and the requirements of the S3 guideline for breast cancer.

### Clinical background

Determining Her2neu is essential for treatment planning in breast cancer:

- **HER2-positive tumours** (approx. 15-20% of breast cancers) benefit from anti-HER2 therapies such as trastuzumab, pertuzumab or T-DM1
- **HER2-low tumours** show low HER2 expression and can benefit from newer therapies such as trastuzumab deruxtecan (based on the DESTINY-Breast04/06 trials)
- **HER2-negative tumours** do not receive anti-HER2-directed therapy

### Her2neu determination according to ASCO/CAP

Her2neu is determined in several steps.

#### IHC scores:
- **3+**: strong, complete membrane staining in >10% of the tumour cells -> HER2-positive
- **2+**: weak to moderate, complete membrane staining in >10% of the tumour cells -> ISH testing required
- **1+**: weak, incomplete membrane staining in >10% of the tumour cells -> HER2-low (if ISH-negative or without ISH)
- **0**: no staining, or membrane staining in <=10% of the tumour cells

#### ISH testing (FISH, CISH, etc.):
- **Positive**: HER2/CEP17 ratio >=2.0 or HER2 copy number >=6.0 per cell
- **Negative**: HER2/CEP17 ratio <2.0 and HER2 copy number <4.0 per cell
- **Equivocal**: borderline findings that require re-testing

The Molekulares Tumorboard module offers more fine-grained profiles for representing the IHC and ISH data points within a molecular pathology report.

### Links to other resources

The profile is closely linked to the other oncology resources:
- references the primary diagnosis (MII_PR_Onko_Diagnose_Primaertumor) via `Observation.focus`
- references the patient (Patient resource) via `Observation.subject`
- can be linked to a specific encounter via `Observation.encounter`

### oBDS context and dual coding

The profile implements the **oBDS data fields for the Her2neu status** (field M4, no. 243) in breast cancer. A **dual coding strategy** is used in order to satisfy both the frozen oBDS specification and the newer S3 guidelines and ASCO/CAP guidelines.

#### oBDS definition (based on the guideline 3.0 specification):
The oBDS coding uses letter codes that correspond exactly to the published specification:
- **P** = positive (IHC 3+, or IHC 2+ and ISH positive)
- **N** = negative
- **U** = unknown

#### S3 guideline / ASCO-CAP definition (current guideline version 5.1):
The modern classification additionally takes the **HER2-low** and **HER2-ultralow** categories into account:
- **HER2-positive**: IHC 3+, or IHC 2+ and ISH-positive
- **HER2-low**: IHC 1+, or IHC 2+ and ISH-negative
- **HER2-ultralow**: IHC 0 with membrane staining
- **HER2-negative**: IHC 0 without membrane staining
- **Equivocal**: borderline, further testing required

This dual coding enables **backward compatibility** with existing oBDS registry data and at the same time **forward compatibility** with newer therapeutic developments (e.g. trastuzumab deruxtecan for HER2-low).

### Terminology binding

The profile uses a **dual coding strategy** with an **extensible** binding for `valueCodeableConcept`. This means that codes from both ValueSets MAY be used in parallel.

- ValueSet: MII VS Onko Mamma Her2neu Status oBDS
- ValueSet: MII VS Onko Mamma Her2neu Status Leitlinie

### Search parameters

The following search parameters are relevant for the Mamma-Her2neu-Status profile, including in combination:

- The search parameter `_id` MUST be supported: `GET [base]/Observation?_id=12345`
- The search parameter `_profile` MUST be supported: `GET [base]/Observation?_profile=https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-mamma-her2neu-status`
- The search parameter `code` MUST be supported: `GET [base]/Observation?code=http://loinc.org|48676-1`
- The search parameter `subject` MUST be supported: `GET [base]/Observation?subject=Patient/test`
- The search parameter `patient` MUST be supported: `GET [base]/Observation?patient=Patient/test`
- The search parameter `focus` MUST be supported: `GET [base]/Observation?focus=Condition/primaertumor`
- The search parameter `value-concept` MUST be supported: `GET [base]/Observation?value-concept=https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/CodeSystem/mii-cs-onko-mamma-her2neu-status-obds|P`
- The search parameter `component-code` MUST be supported: `GET [base]/Observation?component-code=http://loinc.org|85319-2`
