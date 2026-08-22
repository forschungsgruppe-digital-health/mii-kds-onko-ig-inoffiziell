<!-- source: TechnischeImplementierung/FHIR-Profile/Organspezifische-Module/KolorektalesKarzinom/KRK-Specimen.page.md -->
This profile describes tissue specimens in colorectal cancer that are taken during surgical interventions. It covers the characterisation of the tissue as well as specific pathological aspects such as the TME quality (total mesorectal excision) in rectal cancer.

The profile is based on a FHIR Specimen resource and establishes the link between the surgical removal and the pathological work-up.

### Links to other resources

The KRK specimen is an important link in the diagnostic chain:
- references the patient (Patient resource) via `Specimen.subject`
- relates to the collection procedure via `Specimen.collection.procedure`
- can be linked to pathological observations (e.g. histology, grading)
- serves as the basis for determining the resection margins and the TNM classification

### oBDS context

The KRK specimen is the basis for various oBDS assessments:
- pathological assessment of the resection specimen
- TME quality in rectal cancer (KR4)
- histopathological characteristics of the tumour
- assessment of the resection margins

### Terminology binding

The profile uses specialised ValueSets for colorectal specimens, in particular for assessing the TME quality and other pathological parameters.

- ValueSet: MII VS Onko KRK TME Qualität

### Search parameters

The following search parameters are relevant for the KRK-Specimen profile, including in combination:

- The search parameter `_id` MUST be supported: `GET [base]/Specimen?_id=12345`
- The search parameter `_profile` MUST be supported: `GET [base]/Specimen?_profile=https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-krk-specimen`
- The search parameter `subject` MUST be supported: `GET [base]/Specimen?subject=Patient/test`
- The search parameter `type` MUST be supported: `GET [base]/Specimen?type=http://snomed.info/sct|119376003`
- The search parameter `status` MUST be supported: `GET [base]/Specimen?status=available`
