<!-- source: TechnischeImplementierung/FHIR-Profile/Organspezifische-Module/Prostata/Prostata-Anzahl-Stanzen-Observation.page.md -->
This profile describes the total number of biopsy cores taken during a prostate biopsy. This information is important for assessing how representative the biopsy is and for interpreting the findings.

The profile is based on a FHIR Observation resource and uses LOINC for coding. The value is given as a Quantity with the unit "Stück" (pieces).

### Links to other resources

The number of cores is an important biopsy parameter:
- references the primary diagnosis (MII_PR_Onko_Diagnose_Primaertumor) via `Observation.focus`
- references the patient (Patient resource) via `Observation.subject`
- can be linked to the corresponding biopsy procedure via `Observation.partOf`

### oBDS context

According to oBDS P4.1, the total number of biopsy cores taken is documented. This information is essential for judging the adequacy of the specimen collection.

### Terminology binding

The LOINC code for the number of cores is bound as **required**.

### Search parameters

The following search parameters are relevant for the Prostata-Anzahl-Stanzen profile:

- The search parameter `_id` MUST be supported: `GET [base]/Observation?_id=12345`
- The search parameter `_profile` MUST be supported: `GET [base]/Observation?_profile=https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-prostate-anzahl-stanzen`
- The search parameter `code` MUST be supported: `GET [base]/Observation?code=http://loinc.org|33747-0`
- The search parameter `value-quantity` MUST be supported: `GET [base]/Observation?value-quantity=gt10`
