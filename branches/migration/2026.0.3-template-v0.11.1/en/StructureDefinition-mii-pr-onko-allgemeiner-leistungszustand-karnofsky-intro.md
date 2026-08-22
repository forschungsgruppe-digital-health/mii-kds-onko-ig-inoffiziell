<!-- markdownlint-disable MD041 -->
<!-- source: TechnischeImplementierung/FHIR-Profile/Allgemeiner-Leistungszustand/Allgemeiner-Leistungszustand-Karnofsky-Observation.page.md
     German mirror (source language): input/translations/de/intro-notes/StructureDefinition-mii-pr-onko-allgemeiner-leistungszustand-karnofsky-intro.md -->

### Context

This profile describes the general performance status (Allgemeiner Leistungszustand) of a patient in oncology according to Karnofsky.

Recording the general performance status is prescribed in the oBDS.
The actual report is coded and transmitted as ECOG, whereby the answer options allow a mapping from the Karnofsky score.

In the previous oBDS and in the FHIR profiles at hand, documenting the ECOG with the answer options 0-4 as well as the Karnofsky score with 10%, 20% etc. is permitted.
The current Umsetzungsleitfaden does, however, contain a note that in future only the ECOG shall be reported. https://plattform65c.atlassian.net/wiki/spaces/UMK/pages/15532323/Allgemeiner+Leistungszustand+Typ

For the case that the findings only refer to the general condition without coding it in ECOG or Karnofsky, the documentation guide of the Plattform §65c recommends developing in-house guidelines for better reproducibility. https://plattform65c.atlassian.net/wiki/spaces/Dokumentat/pages/86310992/Allgemeiner+Leistungszustand

### Karnofsky-ECOG mapping: oBDS vs. clinical literature

**Important note**: different Karnofsky-ECOG conversion tables exist in the literature:

**oBDS 12.1 specification** (used in this profile):
- Karnofsky 90-100% = ECOG 0
- Karnofsky 70-80% = ECOG 1
- Karnofsky 50-60% = ECOG 2
- Karnofsky 30-40% = ECOG 3
- Karnofsky 10-20% = ECOG 4
- Karnofsky 0% = ECOG 5

**Clinical literature** (Buccheri et al., 1996; Ma et al., 2010):
- Karnofsky 100% = ECOG 0
- Karnofsky 80-90% = ECOG 1
- Karnofsky 70% = ECOG 2
- Karnofsky 50-60% = ECOG 3
- Karnofsky 10-40% = ECOG 4

Compared with the clinical literature, the oBDS mappings are shifted downwards by about 10-20%. Because these profiles implement the oBDS, all reference ranges and ObservationDefinitions use the oBDS specification.

Implementers should be aware of these differences, in particular when converting between Karnofsky and ECOG or when exchanging data with international systems that may use other conversion tables.

### LOINC support for international interoperability

The profile supports optional LOINC coding in addition to the mandatory oBDS coding:

- **`code.coding`**: besides the mandatory SNOMED CT code (761869008), the LOINC code 89243-0 may optionally be given
- **`valueCodeableConcept.coding`**: besides the mandatory oBDS coding, LOINC Answer List codes may optionally be given

The following ConceptMap is available for translating between oBDS and LOINC codes:
- `https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/ConceptMap/mii-cm-onko-allgemeiner-leistungszustand-karnofsky-loinc`

### Search parameters

The following search parameters are relevant for the Onkologie module, also in combination:

<!-- Source defect, kept verbatim: the "_profile" example below names the canonical
     .../mii-pr-onko-allgemeiner-leistungszustand, which is not the canonical of this
     profile (.../mii-pr-onko-allgemeiner-leistungszustand-karnofsky). Not corrected
     during migration - please review. -->
- The search parameter `_id` MUST be supported: `GET [base]/Observation?_id=1234`
- The search parameter `_profile` MUST be supported: `GET [base]/Observation?_profile=https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-allgemeiner-leistungszustand`
- The search parameter `code` MUST be supported: `GET [base]/Observation?code=http://fhir.de/CodeSystem/sct|184305005`
- The search parameter `subject` MUST be supported: `GET [base]/Observation?subject=Patient/example`
- The search parameter `encounter` MUST be supported: `GET [base]/Observation?encounter=Encounter/example`
