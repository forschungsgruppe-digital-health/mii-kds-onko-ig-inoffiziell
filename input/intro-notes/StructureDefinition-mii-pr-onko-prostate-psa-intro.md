<!-- source: TechnischeImplementierung/FHIR-Profile/Organspezifische-Module/Prostata/Prostata-PSA-Observation.page.md -->
This profile describes the PSA value (prostate-specific antigen) in patients with prostate cancer in oncology. The PSA value is a central tumour marker for diagnosis, follow-up and therapy monitoring in prostate cancer.

The profile is based on a FHIR Observation resource and uses LOINC to code the observed parameter. PSA values can be documented both as total PSA and as free PSA.

### Links to other resources

The PSA value is an important tumour-specific observation:
- references the primary diagnosis (MII_PR_Onko_Diagnose_Primaertumor) via `Observation.focus`
- references the patient (Patient resource) via `Observation.subject`
- can be linked to a specific encounter via `Observation.encounter`

### oBDS context

According to oBDS P1, the PSA value is documented as a tumour marker for diagnosis and follow-up. Both diagnostic and follow-up PSA values can be recorded.

### Terminology binding

The ValueSet for PSA codes is bound as **required**, because LOINC codes for PSA determinations are standardised and unambiguously defined.

#### PSA codes

- **Free PSA**: LOINC 10886-0 "Prostate specific antigen Free [Mass/volume] in Serum or Plasma"

### Search parameters

The following search parameters are relevant for the Prostata-PSA profile, including in combination:

- The search parameter `_id` MUST be supported: `GET [base]/Observation?_id=12345`
- The search parameter `_profile` MUST be supported: `GET [base]/Observation?_profile=https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-prostate-psa`
- The search parameter `code` MUST be supported: `GET [base]/Observation?code=http://loinc.org|2857-1`
- The search parameter `subject` MUST be supported: `GET [base]/Observation?subject=Patient/test`
- The search parameter `focus` MUST be supported: `GET [base]/Observation?focus=Condition/primaertumor`
- The search parameter `value-quantity` MUST be supported: `GET [base]/Observation?value-quantity=gt5.0`
