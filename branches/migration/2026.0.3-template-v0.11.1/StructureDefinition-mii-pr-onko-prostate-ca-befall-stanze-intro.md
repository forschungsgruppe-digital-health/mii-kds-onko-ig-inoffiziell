<!-- source: TechnischeImplementierung/FHIR-Profile/Organspezifische-Module/Prostata/Prostata-Karzinom-Befall-Stanze-Observation.page.md -->
This profile describes the percentage involvement of the most heavily involved core of a prostate biopsy or of a prostate excision specimen in oncology. This value is an important histopathological parameter for assessing the tumour extent and aggressiveness in prostate cancer.

The profile is based on a FHIR Observation resource and uses LOINC to code the observed parameter. The value is given as a percentage and refers to the most heavily involved core of the biopsy.

### Links to other resources

The carcinoma involvement of the core is an important histopathological observation:
- references the primary diagnosis (MII_PR_Onko_Diagnose_Primaertumor) via `Observation.focus`
- references the patient (Patient resource) via `Observation.subject`
- can be linked to a specific encounter via `Observation.encounter`
- can be linked to the corresponding tissue specimen via `Observation.specimen`

### oBDS context

According to oBDS P4.3, the percentage carcinoma involvement of the most heavily involved core of a prostate biopsy is documented. This is an important parameter for the histopathological assessment of the tumour extent.

### Terminology binding

The profile uses a **required** LOINC code for the unambiguous identification of the observation:

#### Carcinoma involvement code
- **LOINC**: 44654-2 "Tissue involved by tumor in Prostate tumor"

### Search parameters

The following search parameters are relevant for the Prostata-Karzinom-Befall-Stanze profile, including in combination:

- The search parameter `_id` MUST be supported: `GET [base]/Observation?_id=12345`
- The search parameter `_profile` MUST be supported: `GET [base]/Observation?_profile=https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-prostate-ca-befall-stanze`
- The search parameter `code` MUST be supported: `GET [base]/Observation?code=http://loinc.org|44654-2`
- The search parameter `subject` MUST be supported: `GET [base]/Observation?subject=Patient/test`
- The search parameter `focus` MUST be supported: `GET [base]/Observation?focus=Condition/primaertumor`
- The search parameter `value-quantity` MUST be supported: `GET [base]/Observation?value-quantity=gt50`
