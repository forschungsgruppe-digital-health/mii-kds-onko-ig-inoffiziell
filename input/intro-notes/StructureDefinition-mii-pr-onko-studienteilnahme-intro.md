<!-- markdownlint-disable MD041 -->
<!-- Migrated from Studienteilnahme-Observation.page.md (MII IG Modul Onkologie, Simplifier).
     Simplifier/FQL directives (page title, tree/XML/JSON/link tabs, FQL query blocks for
     profile metadata, dataset mapping and oBDS mapping) were removed - the IG Publisher
     renders all of that on this artifact page.
     German mirror: input/translations/de/intro-notes/StructureDefinition-mii-pr-onko-studienteilnahme-intro.md -->

This profile describes whether and when a patient took part in a study.

It contains:

* a reference to Patient
* a reference to the primary diagnosis
* the Observation code "709491003 | Enrollment in clinical trial (procedure)" (SNOMED-CT)
* the exact date of first enrolment into a study with an ethics vote
* the status of the study participation (yes, no, unknown)

In the case of a pharmacological study, there SHOULD ideally be a reference to a Procedure /
Systemische Therapie, either via Observation.partOf = Reference (SystemischeTherapie),
Observation.basedOn = Reference (MedicationRequest); or Procedure.basedOn.

### Referencing studies

Information about the specific study (organization, study ID, study phase, etc.) MAY be provided via
the element `Observation.focus[studie]` with a reference to a ResearchStudy resource from the
[MII Modul Studie](https://simplifier.net/medizininformatikinitiative-modul-studie).

The ResearchStudy resource enables the structured recording of:

* study identifiers (DRKS, ClinicalTrials.gov, EudraCT, Innovationsfonds project number)
* study type and phase
* primary study objectives
* study context and indication
* study status

A complete example can be found in the PRO-B study participation, which references a ResearchStudy
with a DRKS registration (DRKS00024015) and an Innovationsfonds project number (01NVF19013).

### Search parameters

The following search parameters are relevant for the Onkologie module, also in combination:

1. The search parameter ```_id``` SHALL be supported:

    Examples:

    ```GET [base]/Observation?_id=1234```

    Usage notes: further information on searching by "_id" can be found in the [FHIR base specification, section "Parameters for all resources"](http://hl7.org/fhir/R4/search.html#all).

2. The search parameter "_profile" SHALL be supported:

    Examples:

    ```GET [base]/Observation?_profile=https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-studienteilnahme```

    Usage notes: further information on searching by "_profile" can be found in the [FHIR base specification, section "token"](http://hl7.org/fhir/R4/search.html#all).

3. The search parameter "code" SHALL be supported:

    Examples:

    ```GET [base]/Observation?code=http://fhir.de/CodeSystem/sct|709491003```

    Usage notes: further information on searching by "code" can be found in the FHIR base specification, section "token".

4. The search parameter "subject" SHALL be supported:

    Examples:

    ```GET [base]/Observation?subject=Patient/example```

    Usage notes: further information on searching by "subject" can be found in the FHIR base specification, section "reference".

5. The search parameter "focus" SHALL be supported:

    Examples:

    ```GET [base]/Observation?focus=Condition/example```

    Usage notes: further information on searching by "focus" can be found in the FHIR base specification, section "reference".

6. The search parameter "encounter" SHALL be supported:

    Examples:

    ```GET [base]/Observation?encounter=Encounter/example```

    Usage notes: further information on searching by "encounter" can be found in the FHIR base specification, section "reference".

7. The search parameter "date" SHALL be supported:

    Examples:

    ```GET [base]/Observation?date=2024-02-08```

    Usage notes: further information on searching by "date" can be found in the FHIR base specification, section "date".

8. The search parameter "derived-from" SHALL be supported:

    Examples:

    ```GET [base]/Observation?derived-from=Observation/example```

    Usage notes: further information on searching by "derived-from" can be found in the FHIR base specification, section "reference".

### Examples

Example 1: simple study participation

Example 2: study participation with a ResearchStudy reference (PRO-B study)

This example shows the documentation of a study participation with a reference to a ResearchStudy
resource that contains detailed study information including the DRKS registration and the
Innovationsfonds project number.

<!-- DERIVED:bridge source=Studienteilnahme-Observation.page.md gate=B -->
> **Written during migration - review before release.** The instances behind the two examples are
> `mii-exa-onko-studienteilnahme` (example 1) and `mii-exa-onko-studienteilnahme-prob` (example 2);
> the ResearchStudy resource referenced by example 2 is `mii-exa-onko-studie-prob`.
{: .ig-highlight .ig-highlight-blue}
