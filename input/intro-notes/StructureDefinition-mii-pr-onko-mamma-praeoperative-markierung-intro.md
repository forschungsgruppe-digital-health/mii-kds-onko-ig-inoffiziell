<!-- source: TechnischeImplementierung/FHIR-Profile/Organspezifische-Module/Mamma/Mamma-Praeoperative-Markierung-Procedure.page.md -->
The **Mamma-Präoperative Markierung profile** documents radiologically performed markings of tumour tissue in the breast prior to surgical interventions. The profile is based on the FHIR Procedure resource and records the various marking modalities used for the precise localisation of tumour tissue.

Pre-operative marking is an important component of breast-conserving therapy and allows surgeons to localise non-palpable lesions exactly and to remove them completely.

### Links to other resources

The profile is closely linked to the other oncology resources:
- references the superordinate operation (MII_PR_Onko_Operation) via `Procedure.partOf`
- references the patient (Patient resource) via `Procedure.subject`
- can be linked to a specific encounter via `Procedure.encounter`

### oBDS context

The profile implements **breast-specific marking procedures** as an extension of the general oBDS operation data set. Pre-operative marking is particularly relevant for:

**Clinical applications:**
- **Breast-conserving therapy**: precise localisation of non-palpable tumours
- **Multifocal tumours**: marking of several tumour foci
- **Re-excision**: marking in the case of R1 resections
- **Quality assurance**: documentation of the marking quality

**Marking modalities (currently in the ValueSet):**
- **Wire marking with ultrasound guidance**: SNOMED CT 433222002
- **Marker insertion with X-ray guidance**: SNOMED CT 836381000000102
- **Wire marking with MRI guidance**: SNOMED CT 911831000000104

**Further clinically relevant modalities (not yet in the ValueSet):**
- **Radioactive seed marking**: radioactive seeds for localisation
- **Magnetic seed marking**: modern wireless procedures (e.g. Magseed(R))
- **Clip marking**: metal clips for orientation

*Note: the current ValueSet focuses on imaging-guided wire and marker procedures. Modern seed-based procedures could be added in future versions.*

### Terminology binding

The profile uses an **extensible binding** for marking modalities directly on `Procedure.code`:

- ValueSet: MII VS Onko Mamma Präoperative Markierung Modalität

### Search parameters

The following search parameters are relevant for the Mamma-Präoperative Markierung profile, including in combination:

- The search parameter `_id` MUST be supported: `GET [base]/Procedure?_id=12345`
- The search parameter `_profile` MUST be supported: `GET [base]/Procedure?_profile=https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-mamma-praeoperative-markierung`
- The search parameter `code` MUST be supported: `GET [base]/Procedure?code=http://snomed.info/sct|392021009`
- The search parameter `subject` MUST be supported: `GET [base]/Procedure?subject=Patient/test`
- The search parameter `patient` MUST be supported: `GET [base]/Procedure?patient=Patient/test`
- The search parameter `part-of` MUST be supported: `GET [base]/Procedure?part-of=Procedure/hauptoperation`
- The search parameter `date` MUST be supported: `GET [base]/Procedure?date=2024-01-15`
