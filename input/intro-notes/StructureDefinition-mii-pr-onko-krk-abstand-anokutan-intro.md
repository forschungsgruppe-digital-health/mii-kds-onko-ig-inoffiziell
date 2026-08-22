<!-- source: TechnischeImplementierung/FHIR-Profile/Organspezifische-Module/KolorektalesKarzinom/KRK-Abstand-Tumor-Anokutanlinie-Observation.page.md -->
This profile describes the distance from the lower tumour margin to the anocutaneous line in colorectal cancer according to oBDS KR1. This measurement is particularly important for treatment planning in rectal cancer, because it influences the surgical strategy and the sphincter-preserving surgical procedure.

The profile is based on a FHIR Observation resource and uses LOINC for the standardised coding of the distance measurement. The distance is given as a Quantity value in centimetres.

### Links to other resources

The distance measurement to the anocutaneous line is an important diagnostic observation:
- references the primary diagnosis (MII_PR_Onko_Diagnose_Primaertumor) via `Observation.focus`
- references the patient (Patient resource) via `Observation.subject`
- can be linked to a specific encounter via `Observation.encounter`

### oBDS context

The distance measurement corresponds to the oBDS data field KR1 "Abstand des Tumorunterrandes zur Anokutanlinie" and is documented in centimetres. This measurement is specific to rectal cancer and serves the pre-operative planning.

### Terminology binding

The profile uses LOINC code 33748-5 "Distance from anal verge" for the standardised coding of the distance measurement. The value is given as a UCUM-conformant Quantity in centimetres.

### Search parameters

The following search parameters are relevant for the KRK-Abstand-Anokutanlinie profile, including in combination:

- The search parameter `_id` MUST be supported: `GET [base]/Observation?_id=12345`
- The search parameter `_profile` MUST be supported: `GET [base]/Observation?_profile=https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-krk-abstand-anokutan`
- The search parameter `code` MUST be supported: `GET [base]/Observation?code=http://loinc.org|33748-5`
- The search parameter `subject` MUST be supported: `GET [base]/Observation?subject=Patient/test`
- The search parameter `focus` MUST be supported: `GET [base]/Observation?focus=Condition/primaertumor`
- The search parameter `value-quantity` MUST be supported: `GET [base]/Observation?value-quantity=5|http://unitsofmeasure.org|cm`
