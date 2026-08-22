<!-- source: TechnischeImplementierung/FHIR-Profile/Organspezifische-Module/Mamma/Mamma-Operation-Procedure.page.md -->
The **Mamma-Operation profile** documents surgical interventions on the breast as part of breast cancer treatment. This profile extends the general MII_PR_Onko_Operation profile with breast-specific aspects and allows breast surgery procedures to be recorded in detail.

The profile supports breast-conserving therapies as well as mastectomies, together with accompanying procedures such as lymph node removal and the use of intraoperative aids.

**Comment note**: it is open for discussion whether pre-operative marking should be modelled as a separate additional resource (as currently implemented) or simply as usedCode with pre-operative and intraoperative slices.

### Links to other resources

The profile is closely linked to the other oncology resources:
- references the primary diagnosis (MII_PR_Onko_Diagnose_Primaertumor) via `Procedure.reasonReference`
- references the patient (Patient resource) via `Procedure.subject`
- can be linked to superordinate operations via `Procedure.partOf`
- can be linked to a specific encounter via `Procedure.encounter`

### oBDS context

The profile implements **breast-specific surgical data** as an extension of the general oBDS operation data set (section 13). Breast surgery covers several procedures:

**Surgical procedures:**
- **Breast-conserving therapy (BET)**: lumpectomy, segmental resection, quadrantectomy
- **Mastectomy**: simple, modified radical, radical mastectomy
- **Lymph node surgery**: sentinel lymph node biopsy, axillary dissection
- **Reconstructive procedures**: immediate reconstruction, secondary reconstruction

**Intraoperative aids:**
- **Wire markings**: pre-operative localisation of non-palpable tumours
- **Seed markings**: radioactive marking for tumour localisation
- **Marker clips**: orientation aids for follow-up
- **Intraoperative imaging**: specimen radiography, ultrasound

### Terminology binding

The profile uses a **dual coding strategy** with SNOMED CT and OPS:

- ValueSet: MII VS Onko Mamma Operation SNOMED CT
- ValueSet: MII VS Onko Mamma Operation OPS

### Search parameters

The following search parameters are relevant for the Mamma-Operation profile, including in combination:

- The search parameter `_id` MUST be supported: `GET [base]/Procedure?_id=12345`
- The search parameter `_profile` MUST be supported: `GET [base]/Procedure?_profile=https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-mamma-operation`
- The search parameter `code` MUST be supported: `GET [base]/Procedure?code=http://snomed.info/sct|392090004`
- The search parameter `subject` MUST be supported: `GET [base]/Procedure?subject=Patient/test`
- The search parameter `patient` MUST be supported: `GET [base]/Procedure?patient=Patient/test`
- The search parameter `reason-reference` MUST be supported: `GET [base]/Procedure?reason-reference=Condition/primaertumor`
- The search parameter `part-of` MUST be supported: `GET [base]/Procedure?part-of=Procedure/hauptoperation`
- The search parameter `date` MUST be supported: `GET [base]/Procedure?date=2024-01-15`
