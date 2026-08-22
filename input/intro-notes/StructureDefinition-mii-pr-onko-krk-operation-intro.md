<!-- source: TechnischeImplementierung/FHIR-Profile/Organspezifische-Module/KolorektalesKarzinom/KRK-Operation-Procedure.page.md -->
This profile describes surgical interventions in colorectal cancer according to various oBDS criteria. It covers the type of the surgical intervention as well as specific colorectal operation types and their quality characteristics, such as the TME quality (total mesorectal excision).

The profile is based on a FHIR Procedure resource and uses several specialised ValueSets to code the different surgical aspects in colorectal cancer.

### Links to other resources

The KRK operation is a central therapeutic intervention:
- references the patient (Patient resource) via `Procedure.subject`
- can be linked to a specific encounter via `Procedure.encounter`
- relates to the primary diagnosis via `Procedure.reasonReference`
- can be linked to Specimen resources for the pathological work-up

### oBDS context

The KRK operation covers several oBDS data fields:
- operation type according to different classification systems
- TME quality in rectal cancer (KR4)
- further operation-specific parameters depending on the intervention

### Terminology binding

The profile uses several ValueSets for the different aspects of the KRK operation:

- ValueSet: MII VS Onko KRK Operationstyp
- ValueSet: MII VS Onko KRK TME Qualität

### Search parameters

The following search parameters are relevant for the KRK-Operation profile, including in combination:

- The search parameter `_id` MUST be supported: `GET [base]/Procedure?_id=12345`
- The search parameter `_profile` MUST be supported: `GET [base]/Procedure?_profile=https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-krk-operation`
- The search parameter `code` MUST be supported: `GET [base]/Procedure?code=http://snomed.info/sct|387713003`
- The search parameter `subject` MUST be supported: `GET [base]/Procedure?subject=Patient/test`
- The search parameter `status` MUST be supported: `GET [base]/Procedure?status=completed`
