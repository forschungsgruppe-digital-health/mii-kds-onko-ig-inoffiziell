<!-- source: TechnischeImplementierung/FHIR-Profile/Organspezifische-Module/KolorektalesKarzinom/KRK-Abstand-Resektionsrand-Aboral-Observation.page.md -->
This profile describes the minimum distance from the aboral tumour margin to the aboral resection margin in colorectal cancer according to oBDS KR2. This measurement is decisive for assessing the R classification and the risk of local recurrence in rectal cancer.

The profile is based on a FHIR Observation resource and uses a dedicated ValueSet to specify the aboral resection plane. The distance is given as a Quantity value in millimetres.

### Links to other resources

The aboral resection margin measurement is an important pathological observation:
- references the primary diagnosis (MII_PR_Onko_Diagnose_Primaertumor) via `Observation.focus`
- references the patient (Patient resource) via `Observation.subject`
- can be linked to a specific encounter via `Observation.encounter`

### oBDS context

The distance measurement corresponds to the oBDS data field KR2 "Minimaler Abstand des aboralen Tumorrandes zum aboralen Resektionsrand" and is documented in millimetres. This measurement is of particular prognostic significance in rectal cancer.

### Terminology binding

The ValueSet for the aboral resection line is bound as **extensible** and specifies the various aspects of determining the aboral resection margin.

- ValueSet: MII VS Onko KRK Abstand Resektionslinie Aboral

### Search parameters

The following search parameters are relevant for the KRK-Abstand-Aboral profile, including in combination:

- The search parameter `_id` MUST be supported: `GET [base]/Observation?_id=12345`
- The search parameter `_profile` MUST be supported: `GET [base]/Observation?_profile=https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-krk-abstand-aboral`
- The search parameter `code` MUST be supported: `GET [base]/Observation?code=https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/CodeSystem/mii-cs-onko-krk-abstand-resektionslinie-aboral|aboral`
- The search parameter `subject` MUST be supported: `GET [base]/Observation?subject=Patient/test`
- The search parameter `focus` MUST be supported: `GET [base]/Observation?focus=Condition/primaertumor`
- The search parameter `value-quantity` MUST be supported: `GET [base]/Observation?value-quantity=3|http://unitsofmeasure.org|mm`
