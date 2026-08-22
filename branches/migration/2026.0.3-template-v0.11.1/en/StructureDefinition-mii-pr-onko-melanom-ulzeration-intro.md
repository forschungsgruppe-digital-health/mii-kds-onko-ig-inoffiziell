<!-- source: TechnischeImplementierung/FHIR-Profile/Organspezifische-Module/MalignesMelanom/Melanom-Ulzeration-Observation.page.md -->
This profile describes the ulceration in malignant melanoma of the skin according to oBDS MM4. Ulceration is an important histopathological criterion in melanoma and describes the presence of an ulceration of the epidermis over the melanoma. The presence of an ulceration is an independent prognostic factor and is required for the TNM classification (in particular pT1b).

The profile is based on a FHIR Observation resource and uses LOINC for the standardised coding of the ulceration. The assessment uses a dedicated ValueSet with the oBDS-conformant options J (Ja/yes), N (Nein/no) and U (Unbekannt/unknown).

### Links to other resources

The ulceration assessment is an important histopathological observation in melanoma:
- references the primary diagnosis (MII_PR_Onko_Diagnose_Primaertumor) via `Observation.focus`
- references the patient (Patient resource) via `Observation.subject`
- can be linked to a specific encounter via `Observation.encounter`

### oBDS context

The ulceration corresponds to the oBDS data field MM4 "Ulzeration" and documents the presence of an ulceration of the epidermis over the melanoma. This information is therapy-relevant and an important characteristic of the biological behaviour and the prognosis of the tumour.

### Terminology binding

The ValueSet for melanoma ulceration is bound as **required** and covers the oBDS-conformant assessment options J (Ja), N (Nein) and U (Unbekannt). This corresponds to the strict terminology requirement for oBDS data fields.

- ValueSet: MII VS Onko Melanom Ulzeration

### Search parameters

The following search parameters are relevant for the Melanom-Ulzeration profile, including in combination:

- The search parameter `_id` MUST be supported: `GET [base]/Observation?_id=12345`
- The search parameter `_profile` MUST be supported: `GET [base]/Observation?_profile=https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-melanom-ulzeration`
- The search parameter `code` MUST be supported: `GET [base]/Observation?code=http://loinc.org|97816-3`
- The search parameter `subject` MUST be supported: `GET [base]/Observation?subject=Patient/test`
- The search parameter `focus` MUST be supported: `GET [base]/Observation?focus=Condition/primaertumor`
- The search parameter `value-concept` MUST be supported: `GET [base]/Observation?value-concept=https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/CodeSystem/mii-cs-onko-melanom-ulzeration|J`
