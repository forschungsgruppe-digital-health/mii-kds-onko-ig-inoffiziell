<!-- markdownlint-disable MD041 -->
<!-- source: TechnischeImplementierung/FHIR-Profile/Allgemeiner-Leistungszustand/ASA-Klassifikation-Observation.page.md
     German mirror (source language): input/translations/de/intro-notes/StructureDefinition-mii-pr-onko-asa-klassifikation-intro.md -->

### Content

This profile describes the ASA classification (American Society of Anesthesiologists Physical Status Classification) in oncology. The ASA classification serves primarily for pre-operative risk assessment and is used to assess the general physical condition of patients before surgical interventions. It can, however, also be drawn on as a comorbidity index for systemic therapy decisions.

Originally from oBDS KR9 (Kolorektales Karzinom module), this profile was generalised for all oncological indications, because the ASA classification is a universal pre-operative assessment tool.

The profile is based on a FHIR Observation resource and uses LOINC for the standardised coding of the ASA classification. The specific ASA classes (ASA I to VI) are defined via a dedicated oBDS ValueSet.

### Links to other resources

The ASA classification is an important pre-operative assessment:
- references the primary diagnosis (MII_PR_Onko_Diagnose_Primaertumor) via `Observation.focus`
- references the patient (Patient resource) via `Observation.subject`
- can be linked to a specific encounter via `Observation.encounter`

### oBDS context

The ASA classification corresponds to the oBDS data field KR9 "ASA-Klassifikation" and covers the assessment levels ASA I to VI as well as "Unbekannt" (U). The classification also takes account of brain-dead patients for organ donation (ASA VI).

### Terminology binding

The ValueSet for the ASA classification is bound as **required**. This means that exclusively the codes from the defined oBDS ValueSet MUST be used.

- ValueSet: MII VS Onko ASA oBDS (`https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/ValueSet/mii-vs-onko-asa-obds`)

### Search parameters

The following search parameters are relevant for the ASA-Klassifikation profile, including in combination:

- The search parameter `_id` MUST be supported: `GET [base]/Observation?_id=12345`
- The search parameter `_profile` MUST be supported: `GET [base]/Observation?_profile=https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-asa-klassifikation`
- The search parameter `code` MUST be supported: `GET [base]/Observation?code=http://loinc.org|97816-3`
- The search parameter `subject` MUST be supported: `GET [base]/Observation?subject=Patient/test`
- The search parameter `focus` MUST be supported: `GET [base]/Observation?focus=Condition/primaertumor`
- The search parameter `value-concept` MUST be supported: `GET [base]/Observation?value-concept=https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/CodeSystem/mii-cs-onko-asa-obds|2`
