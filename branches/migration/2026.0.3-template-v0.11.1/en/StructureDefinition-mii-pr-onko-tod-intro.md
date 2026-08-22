<!-- markdownlint-disable MD041 -->
<!-- Migrated from Tod-Observation.page.md (MII IG Modul Onkologie, Simplifier).
     Simplifier/FQL directives (page title, tree/XML/JSON/link tabs, FQL query blocks for
     profile metadata, dataset mapping and oBDS mapping) were removed - the IG Publisher
     renders all of that on this artifact page.
     German mirror: input/translations/de/intro-notes/StructureDefinition-mii-pr-onko-tod-intro.md -->

This profile describes whether and when a patient died as a result of the tumor. It is part of the
oBDS cancer registry dataset.

The date of death can also be represented in the MII core dataset via the Patient resource, but was
additionally added here as an Observation for reasons of data structure and data cohesion.

Since the version MII-Patient(2024), a cause of death is also present directly in the Patient
resource. Unlike the oBDS cause of death, which is recorded using ICD-10-GM, the MII-Patient cause of
death refers to ICD-10-WHO.

It contains:

* a reference to Patient
* the Observation code "184305005 | Cause of death (observable entity)" (SNOMED-CT)
* the exact date of death
* a coding of the cause of death per ICD-10 GM
* an interpretation of the relationship between the tumor disease and the cause of death

In the oBDS, the death report is transmitted as an independent entity. Because there should be only
one death report per patient, the FHIR profiling therefore does not hold a direct link to the primary
diagnosis or to the individual follow-up stagings, but exclusively to the patient.

### Search parameters

The following search parameters are relevant for the Onkologie module, also in combination:

1. The search parameter ```_id``` SHALL be supported:

    Examples:

    ```GET [base]/Observation?_id=1234```

    Usage notes: further information on searching by "_id" can be found in the [FHIR base specification, section "Parameters for all resources"](http://hl7.org/fhir/R4/search.html#all).

2. The search parameter "_profile" SHALL be supported:

    Examples:

    ```GET [base]/Observation?_profile=https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-tod```

    Usage notes: further information on searching by "_profile" can be found in the [FHIR base specification, section "token"](http://hl7.org/fhir/R4/search.html#all).

3. The search parameter "code" SHALL be supported:

    Examples:

    ```GET [base]/Observation?code=http://fhir.de/CodeSystem/sct|184305005```

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

8. The search parameter "interpretation" SHALL be supported:

    Examples:

    ```GET [base]/Observation?interpretation=http://fhir.de/CodeSystem/icd10gm|C44.3```

    Usage notes: further information on searching by "interpretation" can be found in the FHIR base specification, section "token".

9. The search parameter "derived-from" SHALL be supported:

    Examples:

    ```GET [base]/Observation?derived-from=Observation/example```

    Usage notes: further information on searching by "derived-from" can be found in the FHIR base specification, section "reference".

### Examples

<!-- DERIVED:bridge source=Tod-Observation.page.md gate=B -->
> **Written during migration - review before release.** Three instances in this guide illustrate the
> profile: `mii-exa-onko-tod-j`, `mii-exa-onko-tod-n` and `mii-exa-onko-tod-u` - one per code (J, N,
> U) of `mii-cs-onko-tod`, i.e. per interpretation of the relationship between the tumor disease and
> the cause of death.
{: .ig-highlight .ig-highlight-blue}
