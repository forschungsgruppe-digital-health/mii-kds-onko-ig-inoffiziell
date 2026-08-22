<!-- markdownlint-disable MD041 -->
<!-- source: TechnischeImplementierung/FHIR-Profile/Fernmetastasen-Observation/Fernmetastasen-Observation.page.md
     German mirror (source language): input/translations/de/intro-notes/StructureDefinition-mii-pr-onko-fernmetastasen-intro.md -->

This profile describes distant metastases (Fernmetastasen) as they are recorded within the oBDS in oncology for the report to the cancer registries. For each metastasis the following data fields are to be given individually:
* date of the determination
* location based on the oBDS's own coding

In the FHIR profiling, each distant metastasis **SHOULD** be created as an individual resource.
The oBDS does not provide for stating non-invasive diagnostic procedures. Nor does the oBDS require the degree of diagnostic certainty (clinical, radiological, histological) to be recorded. Where needed, a distant metastasis **MAY** reference the corresponding diagnostic procedures.

This profile is conformant to the [Patho-Finding profile of the MII pathology report](https://simplifier.net/guide/mii-ig-pathologie/Befund-TechnischeImplementierung-FHIRProfile-MII-PR-Patho-Finding?version=current) and can therefore be embedded as an Observation into a pathology report.

### Search parameters

The following search parameters are relevant for the Onkologie module, also in combination:

<!-- Source defect, kept verbatim: the "_profile" example below names the canonical
     .../mii-pr-onko-allgemeiner-leistungszustand, which is not the canonical of this
     profile (.../mii-pr-onko-fernmetastasen). Not corrected during migration -
     please review. -->
- The search parameter `_id` MUST be supported: `GET [base]/Observation?_id=1234`
- The search parameter `_profile` MUST be supported: `GET [base]/Observation?_profile=https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-allgemeiner-leistungszustand`
- The search parameter `code` MUST be supported: `GET [base]/Observation?code=http://fhir.de/CodeSystem/sct|184305005`
- The search parameter `subject` MUST be supported: `GET [base]/Observation?subject=Patient/example`
- The search parameter `focus` MUST be supported: `GET [base]/Observation?focus=Condition/example`
- The search parameter `encounter` MUST be supported: `GET [base]/Observation?encounter=Encounter/example`
- The search parameter `date` MUST be supported: `GET [base]/Observation?date=2024-02-08`
- The search parameter `body-site` MUST be supported: `GET [base]/Observation?body-site=http://snomed.info/sct|258332000`
- The search parameter `derived-from` MUST be supported: `GET [base]/Observation?derived-from=Observation/example`
