<!-- source: TechnischeImplementierung/FHIR-Profile/Organspezifische-Module/Prostata/Prostata-Anzahl-Positive-Stanzen-Observation.page.md -->
This profile describes the number of tumour-positive cores in a prostate biopsy. This information is decisive for risk assessment and treatment planning, because it reflects the extent of the tumour spread within the prostate.

The profile is based on a FHIR Observation resource and uses LOINC for coding. The value is given as a Quantity with the unit "Stück" (pieces).

### Links to other resources

The number of positive cores is an important biopsy parameter:
- references the primary diagnosis (MII_PR_Onko_Diagnose_Primaertumor) via `Observation.focus`
- references the patient (Patient resource) via `Observation.subject`
- can be linked to the corresponding biopsy procedure via `Observation.partOf`
- relates to the total number of cores (separate Observation)

### oBDS context

According to oBDS P4.2, the number of tumour-positive cores is documented. Together with the total number of cores, this information is essential for assessing the tumour burden.

### Terminology binding

The LOINC code for the number of positive cores is bound as **required**.

### Search parameters

The following search parameters are relevant for the Prostata-Anzahl-Positive-Stanzen profile:

- The search parameter `_id` MUST be supported: `GET [base]/Observation?_id=12345`
- The search parameter `_profile` MUST be supported: `GET [base]/Observation?_profile=https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-prostate-anzahl-positive-stanzen`
- The search parameter `code` MUST be supported: `GET [base]/Observation?code=http://loinc.org|33746-2`
- The search parameter `value-quantity` MUST be supported: `GET [base]/Observation?value-quantity=gt3`
