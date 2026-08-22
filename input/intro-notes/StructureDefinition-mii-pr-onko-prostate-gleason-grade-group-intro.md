<!-- source: TechnischeImplementierung/FHIR-Profile/Organspezifische-Module/Prostata/Prostata-Gleason-Score-Grade-Group-Observation.page.md -->
This profile describes the Gleason score and the corresponding Grade Group in the histopathological grading of prostate cancer. The Gleason score is the sum of the primary and the secondary Gleason pattern, while the Grade Group (1-5) is an international standard classification.

The profile is based on a FHIR Observation resource and uses LOINC for coding. The Grade Group is documented as a component of the Observation.

### Links to other resources

The Gleason score is a central histopathological assessment:
- references the primary diagnosis (MII_PR_Onko_Diagnose_Primaertumor) via `Observation.focus`
- references the patient (Patient resource) via `Observation.subject`
- can be linked to a specific encounter via `Observation.encounter`
- can be linked to the corresponding biopsy procedure via `Observation.partOf`
- can reference the individual Gleason pattern observations via `Observation.hasMember`

### oBDS context

According to oBDS P3, the Gleason score is documented as the sum of the primary and the secondary pattern. The Grade Group is a modern international classification that is standard in current oncological practice.

### Terminology binding

The ValueSet for Gleason score codes is bound as **required**. The Grade Group codes are likewise bound as **required**, because they are internationally standardised.

- ValueSet: MII VS Onko Prostata Gleason Score

### Search parameters

The following search parameters are relevant for the Prostata-Gleason-Score-Grade-Group profile, including in combination:

- The search parameter `_id` MUST be supported: `GET [base]/Observation?_id=12345`
- The search parameter `_profile` MUST be supported: `GET [base]/Observation?_profile=https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-prostate-gleason-grade-group`
- The search parameter `code` MUST be supported: `GET [base]/Observation?code=http://loinc.org|44642-7`
- The search parameter `subject` MUST be supported: `GET [base]/Observation?subject=Patient/test`
- The search parameter `focus` MUST be supported: `GET [base]/Observation?focus=Condition/primaertumor`
- The search parameter `value-concept` MUST be supported: `GET [base]/Observation?value-concept=http://snomed.info/sct|369771007`
- The search parameter `component-code` MUST be supported: `GET [base]/Observation?component-code=http://loinc.org|79892-6` - for searching the Grade Group component.
