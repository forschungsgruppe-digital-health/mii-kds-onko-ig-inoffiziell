<!-- source: TechnischeImplementierung/FHIR-Profile/Organspezifische-Module/MalignesMelanom/Melanom-Sicherheitsabstand-Observation.page.md -->
This profile describes the minimum safety margin to the primary tumour in malignant melanoma according to oBDS MM1. This measurement is taken after the definitive surgical intervention and gives the minimum distance from the melanoma to the nearest lateral surgical resection margin in the excision specimen. A value of 0 corresponds to a local R1 or R2 resection status.

The profile is based on a FHIR Observation resource and uses SNOMED CT for the standardised coding of the safety margin measurement. The distance is given as a Quantity value in millimetres (mm).

### Links to other resources

The safety margin measurement is an important surgical observation in melanoma:
- references the primary diagnosis (MII_PR_Onko_Diagnose_Primaertumor) via `Observation.focus`
- references the patient (Patient resource) via `Observation.subject`
- can be linked to a specific encounter via `Observation.encounter`

### oBDS context

The safety margin measurement corresponds to the oBDS data field MM1 "Minimaler Sicherheitsabstand zum Primärtumor" and is documented in millimetres. This measurement is essential for assessing the completeness of the tumour resection and the prognosis in melanoma.

**Note on coding cases that cannot be assessed:**
According to oBDS, the safety margin can take the following values:
- **-1**: cannot be assessed -> in FHIR, `dataAbsentReason` is used (e.g. "unknown" or "not-asked") instead of `valueQuantity`
- **0**: no safety margin (R1/R2 resection) -> `valueQuantity.value = 0`
- **n**: safety margin in mm -> `valueQuantity.value = n`

The profile contains an invariant which ensures that either `valueQuantity` or `dataAbsentReason` must be present.

### Terminology binding

The profile uses SNOMED CT code 396511007 "Distance of in situ melanoma from closest lateral surgical margin in excised specimen of skin (observable entity)" for the standardised coding of the safety margin measurement. The value is given as a UCUM-conformant Quantity in millimetres (mm).

### Search parameters

The following search parameters are relevant for the Melanom-Sicherheitsabstand profile, including in combination:

- The search parameter `_id` MUST be supported: `GET [base]/Observation?_id=12345`
- The search parameter `_profile` MUST be supported: `GET [base]/Observation?_profile=https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-melanom-sicherheitsabstand`
- The search parameter `code` MUST be supported: `GET [base]/Observation?code=http://snomed.info/sct|396511007`
- The search parameter `subject` MUST be supported: `GET [base]/Observation?subject=Patient/test`
- The search parameter `focus` MUST be supported: `GET [base]/Observation?focus=Condition/primaertumor`
- The search parameter `value-quantity` MUST be supported: `GET [base]/Observation?value-quantity=5|http://unitsofmeasure.org|mm`
