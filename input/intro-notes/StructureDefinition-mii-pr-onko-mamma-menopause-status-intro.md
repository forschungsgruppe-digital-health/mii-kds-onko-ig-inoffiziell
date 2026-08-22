<!-- source: TechnischeImplementierung/FHIR-Profile/Organspezifische-Module/Mamma/Mamma-Menopause-Status-Observation.page.md -->
This profile describes the (pre-therapeutic) menopausal status of a patient with breast cancer in oncology. The menopausal status is an important prognostic factor for treatment planning and therapy selection in breast cancer.

The profile is based on a FHIR Observation resource and uses SNOMED CT to code the observed characteristic (menopause function). The specific expressions of the menopausal status are defined via a dedicated ValueSet.

### Links to other resources

The menopausal status is an important tumour-specific observation:
- references the primary diagnosis (MII_PR_Onko_Diagnose_Primaertumor) via `Observation.focus`
- references the patient (Patient resource) via `Observation.subject`
- can be linked to a specific encounter via `Observation.encounter`

### oBDS context

According to the current oBDS version 2021, the perimenopausal status is implicitly subsumed under premenopausal. This convention is represented in the FHIR profiling by the corresponding ValueSet.

### Terminology binding

The ValueSet for the menopausal status is bound as **extensible**. This means that the codes from the defined ValueSet SHOULD preferably be used, but that other suitable codes MAY be used where needed if the predefined values are not sufficient.

- ValueSet: MII VS Onko Mamma Menopause Status

### Search parameters

The following search parameters are relevant for the Mamma-Menopause-Status profile, including in combination:

- The search parameter `_id` MUST be supported: `GET [base]/Observation?_id=12345`
- The search parameter `_profile` MUST be supported: `GET [base]/Observation?_profile=https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-mamma-menopause-status`
- The search parameter `code` MUST be supported: `GET [base]/Observation?code=http://snomed.info/sct|161712005`
- The search parameter `subject` MUST be supported: `GET [base]/Observation?subject=Patient/test`
- The search parameter `focus` MUST be supported: `GET [base]/Observation?focus=Condition/primaertumor`
- The search parameter `value-concept` MUST be supported: `GET [base]/Observation?value-concept=http://snomed.info/sct|76498008`
