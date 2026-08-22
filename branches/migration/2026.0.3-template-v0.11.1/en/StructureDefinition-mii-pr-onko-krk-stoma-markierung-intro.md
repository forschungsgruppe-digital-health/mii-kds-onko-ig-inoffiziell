<!-- source: TechnischeImplementierung/FHIR-Profile/Organspezifische-Module/KolorektalesKarzinom/KRK-Stoma-Markierung-Procedure.page.md -->
This profile describes the pre-operative stoma marking in colorectal cancer according to oBDS KR7. Pre-operative stoma marking is an important step in preparing for surgical interventions in which a stoma may become necessary, and it contributes significantly to the patient's quality of life.

The profile is based on a FHIR Procedure resource and documents both the performance and the status of the pre-operative stoma marking.

### Links to other resources

Stoma marking is a pre-operative measure:
- references the patient (Patient resource) via `Procedure.subject`
- can be linked to a specific encounter via `Procedure.encounter`
- relates to the planned operation via `Procedure.reasonReference`
- can be linked to the actual stoma creation during the operation

### oBDS context

Stoma marking corresponds to the oBDS data field KR7 "Präoperative Stomamarkierung" and documents whether the stoma position was marked pre-operatively. This is particularly relevant in rectal cancer, where a stoma is more frequently required.

### Terminology binding

The ValueSet for stoma marking is bound as **required** and contains the codes for the performance as well as the status of the pre-operative marking.

- ValueSet: MII VS Onko KRK Stoma Anzeichnung

### Search parameters

The following search parameters are relevant for the KRK-Stoma-Markierung profile, including in combination:

- The search parameter `_id` MUST be supported: `GET [base]/Procedure?_id=12345`
- The search parameter `_profile` MUST be supported: `GET [base]/Procedure?_profile=https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-krk-stoma-markierung`
- The search parameter `code` MUST be supported: `GET [base]/Procedure?code=https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/CodeSystem/mii-cs-onko-krk-stoma-anzeichnung|durchgefuehrt`
- The search parameter `subject` MUST be supported: `GET [base]/Procedure?subject=Patient/test`
- The search parameter `status` MUST be supported: `GET [base]/Procedure?status=completed`
