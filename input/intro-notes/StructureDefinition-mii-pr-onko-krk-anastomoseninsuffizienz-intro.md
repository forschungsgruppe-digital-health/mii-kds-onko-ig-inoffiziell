<!-- source: TechnischeImplementierung/FHIR-Profile/Organspezifische-Module/KolorektalesKarzinom/KRK-Anastomoseninsuffizienz-Observation.page.md -->
This profile describes the occurrence of an anastomotic leak (Anastomoseninsuffizienz) in colorectal cancer according to oBDS KR8. The anastomotic leak is an important post-operative complication after colorectal resections and affects the prognosis and the further treatment planning.

The profile is based on a FHIR Observation resource and uses a dedicated ValueSet to code the occurrence and the severity of the anastomotic leak.

### Links to other resources

The assessment of the anastomotic leak is an important post-operative observation:
- references the primary diagnosis (MII_PR_Onko_Diagnose_Primaertumor) via `Observation.focus`
- references the patient (Patient resource) via `Observation.subject`
- can be linked to a specific encounter via `Observation.encounter`
- relates to the operation performed (Procedure resource)

### oBDS context

The anastomotic leak corresponds to the oBDS data field KR8 "Anastomoseninsuffizienz" and documents the occurrence of this post-operative complication after colorectal interventions with anastomosis.

### Terminology binding

The ValueSet for the anastomotic leak is bound as **required** and contains the codes for the occurrence as well as for the grading of the leak.

- ValueSet: MII VS Onko KRK Anastomoseninsuffizienz

### Search parameters

The following search parameters are relevant for the KRK-Anastomoseninsuffizienz profile, including in combination:

- The search parameter `_id` MUST be supported: `GET [base]/Observation?_id=12345`
- The search parameter `_profile` MUST be supported: `GET [base]/Observation?_profile=https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-krk-anastomoseninsuffizienz`
- The search parameter `code` MUST be supported: `GET [base]/Observation?code=http://snomed.info/sct|235919008`
- The search parameter `subject` MUST be supported: `GET [base]/Observation?subject=Patient/test`
- The search parameter `focus` MUST be supported: `GET [base]/Observation?focus=Condition/primaertumor`
- The search parameter `value-concept` MUST be supported: `GET [base]/Observation?value-concept=https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/CodeSystem/mii-cs-onko-krk-anastomoseninsuffizienz|ja`
