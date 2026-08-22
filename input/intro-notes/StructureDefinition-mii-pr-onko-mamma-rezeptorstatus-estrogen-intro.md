<!-- source: TechnischeImplementierung/FHIR-Profile/Organspezifische-Module/Mamma/Mamma-Estrogen-Rezeptorstatus-Observation.page.md -->
The **estrogen receptor status profile** documents the diagnostic estrogen receptor status of a pathologically examined specimen in breast cancer. The profile allows both the quantitative measurements (proportion of positive cells, staining intensity) and the interpreted results according to the different definitions to be recorded in detail.

The estrogen receptor status is a central prognostic and predictive biomarker in breast cancer and is decisive for treatment planning, in particular with regard to anti-hormonal therapy.

### Links to other resources

The profile is closely linked to the other oncology resources:
- references the primary diagnosis (MII_PR_Onko_Diagnose_Primaertumor) via `Observation.focus`
- references the patient (Patient resource) via `Observation.subject`
- can be linked to a specific encounter via `Observation.encounter`

### oBDS context

The profile implements the **oBDS data fields for the estrogen receptor status** in breast cancer. Note that the [oBDS Mamma was originally published in 2015](https://www.basisdatensatz.de/download/Brust.pdf) and that the methodology has undergone considerable change since then.

**Historical vs. current practice:**
- **IRS (Immunreactive Score)**: was still in use in 2015, but is no longer in broad clinical use today, although it remains relevant for registry data
- **Thresholds**: modern pathological practice already treats >1% positive cells as positive (instead of the historical 10% threshold)
- **Assessment approaches**: the current S3 guidelines use definitions other than the original oBDS

**Modelling compromise**: the profile proposed here is a compromise between older registry data, which the current registry framework requires, and the changes in clinical and pathological practice.

**Comment note**: it is open for discussion whether a separate profile for the IRS (Immunreactive Score) should be added in order to represent historical data completely.

### Terminology binding

The profile uses a **dual coding strategy** with an **extensible** binding. This means that the codes from the defined ValueSets SHOULD preferably be used, but that other suitable codes MAY be used where needed.

- ValueSet: MII VS Onko Mamma Rezeptorstatus oBDS
- ValueSet: MII VS Onko Mamma Rezeptorstatus Leitlinie

### Search parameters

The following search parameters are relevant for the Mamma-Estrogen-Rezeptorstatus profile, including in combination:

- The search parameter `_id` MUST be supported: `GET [base]/Observation?_id=12345`
- The search parameter `_profile` MUST be supported: `GET [base]/Observation?_profile=https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-mamma-rezeptorstatus-estrogen`
- The search parameter `code` MUST be supported: `GET [base]/Observation?code=http://loinc.org|40556-3`
- The search parameter `subject` MUST be supported: `GET [base]/Observation?subject=Patient/test`
- The search parameter `patient` MUST be supported: `GET [base]/Observation?patient=Patient/test`
- The search parameter `focus` MUST be supported: `GET [base]/Observation?focus=Condition/primaertumor`
- The search parameter `value-concept` MUST be supported: `GET [base]/Observation?value-concept=http://snomed.info/sct|416053008`
- The search parameter `component-code` MUST be supported: `GET [base]/Observation?component-code=http://snomed.info/sct|1234804006`
- The search parameter `component-value-quantity` MUST be supported: `GET [base]/Observation?component-value-quantity=gt50`
