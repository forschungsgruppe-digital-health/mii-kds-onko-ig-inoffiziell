<!-- source: TechnischeImplementierung/FHIR-Profile/Organspezifische-Module/Prostata/Prostata-Gleason-Patterns-Observation.page.md -->
This profile describes the individual Gleason patterns (primary, secondary, tertiary) in the histopathological grading of prostate cancer. The Gleason patterns are the basis for calculating the Gleason score and are decisive for estimating the prognosis.

The profile is based on a FHIR Observation resource and uses LOINC to code the different pattern types. Each pattern is scored with a value from 1 to 5, with patterns >=3 considered malignant.

### Links to other resources

The Gleason patterns are important histopathological observations:
- reference the primary diagnosis (MII_PR_Onko_Diagnose_Primaertumor) via `Observation.focus`
- reference the patient (Patient resource) via `Observation.subject`
- can be linked to a specific encounter via `Observation.encounter`
- can be linked to the corresponding biopsy procedure via `Observation.partOf`

### oBDS context

According to oBDS P2, Gleason patterns are documented as primary, secondary or tertiary pattern. The pattern values from 1 to 5 correspond to the international Gleason grading, with patterns from grade 3 upwards classified as malignant.

### Terminology binding

The ValueSet for Gleason pattern codes is bound as **required**, because the LOINC codes for Gleason patterns are standardised.

- ValueSet: MII VS Onko Prostata Gleason Patterns

### Search parameters

The following search parameters are relevant for the Prostata-Gleason-Patterns profile, including in combination:

- The search parameter `_id` MUST be supported: `GET [base]/Observation?_id=12345`
- The search parameter `_profile` MUST be supported: `GET [base]/Observation?_profile=https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-prostate-gleason-patterns`
- The search parameter `code` MUST be supported: `GET [base]/Observation?code=http://loinc.org|44641-9`
- The search parameter `subject` MUST be supported: `GET [base]/Observation?subject=Patient/test`
- The search parameter `focus` MUST be supported: `GET [base]/Observation?focus=Condition/primaertumor`
- The search parameter `value-concept` MUST be supported: `GET [base]/Observation?value-concept=http://snomed.info/sct|369771007`
