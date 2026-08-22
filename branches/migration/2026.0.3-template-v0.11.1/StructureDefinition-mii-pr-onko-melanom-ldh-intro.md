<!-- source: TechnischeImplementierung/FHIR-Profile/Organspezifische-Module/MalignesMelanom/Melanom-LDH-Observation.page.md -->
This profile describes the lactate dehydrogenase (LDH) laboratory values in malignant melanoma according to the oBDS field "LDH". LDH is an important prognostic marker in metastatic melanoma and is used to assess the course of the disease and the prognosis. Elevated LDH values correlate with a poorer prognosis.

The profile is based on a FHIR Observation resource with the category "laboratory" and uses LOINC for the standardised coding of the LDH determination. The value is given as a Quantity in units per litre (U/L).

### Links to other resources

The LDH determination is an important laboratory observation in melanoma:
- references the primary diagnosis (MII_PR_Onko_Diagnose_Primaertumor) via `Observation.focus`
- references the patient (Patient resource) via `Observation.subject`
- can be linked to a specific encounter via `Observation.encounter`
- serves as a prognostic marker for treatment planning

### oBDS context

The LDH determination corresponds to the oBDS data field "LDH" for lactate dehydrogenase in malignant melanoma and is documented as a prognostic marker, in particular in metastatic disease. Whether the LDH is assessed as normal or elevated is decided in relation to laboratory-specific reference values.

### Terminology binding

The profile uses LOINC codes for the standardised coding of the LDH determination. The ValueSet covers three different LDH-specific LOINC codes and is bound as **required**:

* 2532-0 "Lactate dehydrogenase [Enzymatic activity/volume] in Serum or Plasma"
* 14804-9 "Lactate dehydrogenase [Enzymatic activity/volume] in Serum or Plasma by Lactate to pyruvate reaction"
* 14805-6 "Lactate dehydrogenase [Enzymatic activity/volume] in Serum or Plasma by Pyruvate to lactate reaction"

- ValueSet: MII VS Onko Melanom LDH

### Search parameters

The following search parameters are relevant for the Melanom-LDH profile, including in combination:

- The search parameter `_id` MUST be supported: `GET [base]/Observation?_id=12345`
- The search parameter `_profile` MUST be supported: `GET [base]/Observation?_profile=https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-melanom-ldh`
- The search parameter `code` MUST be supported: `GET [base]/Observation?code=http://loinc.org|14805-6`
- The search parameter `subject` MUST be supported: `GET [base]/Observation?subject=Patient/test`
- The search parameter `focus` MUST be supported: `GET [base]/Observation?focus=Condition/primaertumor`
- The search parameter `value-quantity` MUST be supported: `GET [base]/Observation?value-quantity=280|http://unitsofmeasure.org|U/L`
