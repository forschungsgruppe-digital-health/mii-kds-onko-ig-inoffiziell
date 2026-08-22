<!-- markdownlint-disable MD041 -->
<!-- source: TechnischeImplementierung/FHIR-Profile/Residualstatus/Residualstatus-Observation.page.md
     German mirror (source language): input/translations/de/intro-notes/StructureDefinition-mii-pr-onko-residualstatus-intro.md -->

This profile describes the overall status of the tumour residuum after a (surgical) therapy in oncology.

Depending on the procedures carried out, the oBDS dataset provides for either a local or a global determination of the residual status.
The OPS catalogue of the procedures for which a local residual status is expected is provided by the Plattform §65c.

Because of the direct relation, the assessment of the local residual status after the completion of a surgery is represented as `Procedure.outcome` in the Operation profile.

### Search parameters

The following search parameters are relevant for the Onkologie module, also in combination:

<!-- Source defect, kept verbatim: the "_profile" example below names the canonical
     .../mii-pr-onko-tod, which is not the canonical of this profile
     (.../mii-pr-onko-residualstatus). Not corrected during migration - please review. -->
- The search parameter `_id` MUST be supported: `GET [base]/Observation?_id=1234`
- The search parameter `_profile` MUST be supported: `GET [base]/Observation?_profile=https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-tod`
- The search parameter `code` MUST be supported: `GET [base]/Observation?code=http://fhir.de/CodeSystem/sct|184305005`
- The search parameter `subject` MUST be supported: `GET [base]/Observation?subject=Patient/example`
- The search parameter `focus` MUST be supported: `GET [base]/Observation?focus=Condition/example`
- The search parameter `encounter` MUST be supported: `GET [base]/Observation?encounter=Encounter/example`
- The search parameter `derived-from` MUST be supported: `GET [base]/Observation?derived-from=Observation/example`
