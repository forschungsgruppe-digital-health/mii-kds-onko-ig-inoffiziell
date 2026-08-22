<!-- source: TechnischeImplementierung/FHIR-Profile/Organspezifische-Module/KolorektalesKarzinom/KRK-Abstand-Circumferelle-Resektionsebene-Observation.page.md -->
This profile describes the minimum distance from the tumour margin to the circumferential resection plane in colorectal cancer according to oBDS KR3. This measurement is an important prognostic factor and is determined both macroscopically and microscopically. A small circumferential resection margin is associated with an increased risk of local recurrence.

The profile is based on a FHIR Observation resource and uses a dedicated ValueSet to distinguish between macroscopic and microscopic assessment. The distance is given as a Quantity value in millimetres.

### Links to other resources

The circumferential resection margin measurement is an important pathological observation:
- references the primary diagnosis (MII_PR_Onko_Diagnose_Primaertumor) via `Observation.focus`
- references the patient (Patient resource) via `Observation.subject`
- can be linked to a specific encounter via `Observation.encounter`

### oBDS context

The distance measurement corresponds to the oBDS data field KR3 "Minimaler Abstand des Tumorrandes zur circumferellen Resektionsebene" and is documented in millimetres. The distinction between macroscopic and microscopic assessment is represented by the corresponding ValueSet.

### Terminology binding

The ValueSet for the circumferential resection plane is bound as **extensible** and distinguishes between the macroscopic and the microscopic assessment of the resection margins.

- ValueSet: MII VS Onko KRK Abstand Circumferelle Resektionsrand

### Search parameters

The following search parameters are relevant for the KRK-Circumferelle-Resektionsebene profile, including in combination:

- The search parameter `_id` MUST be supported: `GET [base]/Observation?_id=12345`
- The search parameter `_profile` MUST be supported: `GET [base]/Observation?_profile=https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-krk-abstand-circumferelle-resektionsebene`
- The search parameter `code` MUST be supported: `GET [base]/Observation?code=https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/CodeSystem/mii-cs-onko-krk-abstand-circumferelle-resektionsebene|makroskopisch`
- The search parameter `subject` MUST be supported: `GET [base]/Observation?subject=Patient/test`
- The search parameter `focus` MUST be supported: `GET [base]/Observation?focus=Condition/primaertumor`
- The search parameter `value-quantity` MUST be supported: `GET [base]/Observation?value-quantity=2|http://unitsofmeasure.org|mm`
