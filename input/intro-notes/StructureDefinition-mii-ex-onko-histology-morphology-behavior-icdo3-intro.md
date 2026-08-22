<!-- markdownlint-disable MD041 -->
<!-- Migrated from Extension-ICD-O-3-Morphologie.page.md (MII IG Modul Onkologie, Simplifier guide tree).
     The source page's heading read "Extensions von Operation" — a leftover from another page; dropped, the publisher renders the title.
     German mirror (source language): input/translations/de/intro-notes/StructureDefinition-mii-ex-onko-histology-morphology-behavior-icdo3-intro.md -->

- This extension replaces the previous ICD-O-3 slice in the MII-Diagnose.
- The original profiling built on the ICD-O-3 slice of the `Condition.code` element. At the same time the `Condition.code` field also carries the ICD-10 coding of the oncological diagnosis. During the commenting phase it was noted, however, that an ICD-O-3 morphology describes a clinically different concept than an ICD-10-coded diagnosis. Representing both in the same CodeableConcept therefore contradicts common FHIR modelling conventions. For that reason a modelling as an extension, comparable to mCODE, was chosen. The representation of the ICD-O-3 topography via `Condition.bodySite` is not affected by this. Further histologies carried out as part of a follow-up shall continue to be represented via the Verlaufshistologie profile (Observation.bodySite and Observation.valueCodeableConcept); the present extension is not used there.
