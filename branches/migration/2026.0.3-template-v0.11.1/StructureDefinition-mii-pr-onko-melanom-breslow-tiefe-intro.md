<!-- source: TechnischeImplementierung/FHIR-Profile/Organspezifische-Module/MalignesMelanom/Melanom-Breslow-Tiefe-Observation.page.md -->
This profile describes the Breslow tumour thickness in malignant melanoma of the skin according to oBDS MM2 "Breslow". The Breslow depth is the most important prognostic factor in primary melanoma and describes the vertical tumour thickness in millimetres, from the granular layer of the epidermis to the deepest point of tumour invasion.

The profile is based on a FHIR Observation resource and uses SNOMED CT for the standardised coding of the Breslow measurement. The tumour thickness is given as a Quantity value in millimetres.

### Links to other resources

The Breslow depth is a central histopathological observation in melanoma:
- references the primary diagnosis (MII_PR_Onko_Diagnose_Primaertumor) via `Observation.focus`
- references the patient (Patient resource) via `Observation.subject`
- can be linked to a specific encounter via `Observation.encounter`

### oBDS context

The Breslow depth corresponds to the oBDS data field "Breslow" MM2 for the tumour thickness in malignant melanoma and is documented in millimetres. This measurement is the most important prognostic factor and influences the staging as well as the therapeutic approach.

### Terminology binding

The profile uses SNOMED CT code 106243009 "Breslow depth staging for melanoma of skin (observable entity)" for the standardised coding of the Breslow measurement. The value is given as a UCUM-conformant Quantity in millimetres.

### Search parameters

The following search parameters are relevant for the Melanom-Breslow-Tiefe profile, including in combination:

- The search parameter `_id` MUST be supported: `GET [base]/Observation?_id=12345`
- The search parameter `_profile` MUST be supported: `GET [base]/Observation?_profile=https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-melanom-breslow-tiefe`
- The search parameter `code` MUST be supported: `GET [base]/Observation?code=http://snomed.info/sct|106243009`
- The search parameter `subject` MUST be supported: `GET [base]/Observation?subject=Patient/test`
- The search parameter `focus` MUST be supported: `GET [base]/Observation?focus=Condition/primaertumor`
- The search parameter `value-quantity` MUST be supported: `GET [base]/Observation?value-quantity=2.1|http://unitsofmeasure.org|mm`
