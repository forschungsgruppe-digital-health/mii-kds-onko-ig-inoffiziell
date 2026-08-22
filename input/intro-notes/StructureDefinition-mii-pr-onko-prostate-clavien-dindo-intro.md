<!-- source: TechnischeImplementierung/FHIR-Profile/Organspezifische-Module/Prostata/Prostata-Clavien-Dindo-Observation.page.md -->
This profile describes the Clavien-Dindo score for prostatectomy in oncology. The Clavien-Dindo classification is a standardised system for assessing post-operative complications on the basis of their severity and of the treatment they require.

The profile is based on a FHIR Observation resource and uses SNOMED CT to code the assessment procedure. It supports both the SNOMED CT Clavien-Dindo grades and the oBDS-specific codings for post-operative complications.

### Links to other resources

The Clavien-Dindo score is an important post-operative observation:
- references the primary diagnosis (MII_PR_Onko_Diagnose_Primaertumor) via `Observation.focus[Diagnose]`
- references the operation performed (MII_PR_Onko_Operation) via `Observation.focus[Operation]`
- references the patient (Patient resource) via `Observation.subject`
- can be linked to a specific encounter via `Observation.encounter`
- can be linked to the corresponding tissue specimens via `Observation.specimen`

### oBDS context

According to oBDS, post-operative complications after prostatectomy are recorded systematically. The Clavien-Dindo classification complements the oBDS coding with an internationally standardised assessment of the complication severity.

### Terminology binding

The profile uses **required** bindings for both coding systems:

#### Assessment method
- **SNOMED CT**: 789278003 "Clavien-Dindo classification (assessment scale)"

#### Observation code
- **SNOMED CT**: 789279006 "Clavien-Dindo classification grade (observable entity)"

#### Clavien-Dindo ValueSet
The ValueSet covers the SNOMED CT codes for all Clavien-Dindo grades: MII VS Onko Prostata Clavien-Dindo.

#### oBDS post-operative complications ValueSet
In addition, oBDS-specific codes for post-operative complications are supported: MII VS Onko Prostata Postsurgical Complications.

### Search parameters

The following search parameters are relevant for the Prostata-Clavien-Dindo profile, including in combination:

- The search parameter `_id` MUST be supported: `GET [base]/Observation?_id=12345`
- The search parameter `_profile` MUST be supported: `GET [base]/Observation?_profile=https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-prostate-clavien-dindo`
- The search parameter `code` MUST be supported: `GET [base]/Observation?code=http://snomed.info/sct|789279006`
- The search parameter `subject` MUST be supported: `GET [base]/Observation?subject=Patient/test`
- The search parameter `focus` MUST be supported: `GET [base]/Observation?focus=Condition/primaertumor`, `GET [base]/Observation?focus=Procedure/prostatektomie`
- The search parameter `method` MUST be supported: `GET [base]/Observation?method=http://snomed.info/sct|789278003`
- The search parameter `value-concept` MUST be supported: `GET [base]/Observation?value-concept=http://snomed.info/sct|1367521005`
