<!-- markdownlint-disable MD041 -->
<!-- Migrated from Verlauf-Observation.page.md (MII IG Modul Onkologie, Simplifier).
     Simplifier/FQL directives (page title, tree/XML/JSON/link tabs, FQL query blocks for
     profile metadata, dataset mapping and oBDS mapping) were removed - the IG Publisher
     renders all of that on this artifact page.
     German mirror: input/translations/de/intro-notes/StructureDefinition-mii-pr-onko-verlauf-intro.md -->

### Context

This profile describes a follow-up observation in the context of oncological therapy.

In the oBDS, the follow-up report (Verlaufsmeldung) is one of several report types. A follow-up
report can contain several other report contents. In the FHIR profiling at hand, follow-up
observations are - alongside tumor boards - one of the two decisive resource types that serve the
temporal modelling of the course of treatment.

The correct coding and interpretation of the cancer registry follow-up data is not trivial - details
can be found in the documentation guide of the Plattform §65c.

https://plattform65c.atlassian.net/wiki/spaces/Dokumentat/pages/75628552/Verlaufsmeldung

### Conformance statements

- A follow-up observation **SHOULD** have a reference to the primary diagnosis via `focus`
- A follow-up observation **SHOULD** contain an assessment of the disease progression (PD, PR, MR
  etc.) in `value`, insofar as this was carried out and is present in the data
- A follow-up observation **SHOULD** furthermore contain assessments of the staging of the tumor, the
  lymph nodes and the distant metastases in `component`, insofar as these were carried out and are
  relevant for the staging
- Because the FHIR profiling does not represent a complete follow-up report, other observations that
  are relevant for the staging in addition to, or deviating from, the TNM criteria named above
  **SHOULD** be referenced by the follow-up observation via `hasMember`. Examples are newly diagnosed
  distant metastases, additionally prepared histologies or genetic examinations carried out later in
  the course. These observations **MAY** be taken directly from the oBDS report contents of the
  respective follow-up report.

### Search parameters

The following search parameters are relevant for the Onkologie module, also in combination:

1. The search parameter ```_id``` SHALL be supported:

    Examples:

    ```GET [base]/Observation?_id=1234```

    Usage notes: further information on searching by "_id" can be found in the [FHIR base specification, section "Parameters for all resources"](http://hl7.org/fhir/R4/search.html#all).

2. The search parameter "_profile" SHALL be supported:

    Examples:

    ```GET [base]/Observation?_profile=https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-allgemeiner-leistungszustand```

    Usage notes: further information on searching by "_profile" can be found in the [FHIR base specification, section "token"](http://hl7.org/fhir/R4/search.html#all).

3. The search parameter "identfier" SHALL be supported:

    Examples:

    ```GET [base]/Observation?identfier=http://charite.de/labor/labortests|1234```

    Usage notes: further information on searching by "identfier" can be found in the FHIR base specification, section "token".

4. The search parameter "code" SHALL be supported:

    Examples:

    ```GET [base]/Observation?code=http://fhir.de/CodeSystem/sct|184305005```

    Usage notes: further information on searching by "code" can be found in the FHIR base specification, section "token".

5. The search parameter "subject" SHALL be supported:

    Examples:

    ```GET [base]/Observation?subject=Patient/example```

    Usage notes: further information on searching by "subject" can be found in the FHIR base specification, section "reference".

6. The search parameter "focus" SHALL be supported:

    Examples:

    ```GET [base]/Observation?focus=Condition/example```

    Usage notes: further information on searching by "focus" can be found in the FHIR base specification, section "reference".

7. The search parameter "encounter" SHALL be supported:

    Examples:

    ```GET [base]/Observation?encounter=Encounter/example```

    Usage notes: further information on searching by "encounter" can be found in the FHIR base specification, section "reference".

8. The search parameter "component-code-value-concept" SHALL be supported:

    Examples:

    ```GET [base]/Observation?component-code-value-concept=http://loinc.org|12345-6$http://fhir.de/CodeSystem/sct|12345678```

    Usage notes: further information on searching by "components" can be found in the FHIR base specification, section "compodsite".

<!-- DERIVED:bridge source=Verlauf-Observation.page.md gate=B -->
> **Written during migration - review before release.** Search parameter 2 above carries the
> canonical of `mii-pr-onko-allgemeiner-leistungszustand`, not of this profile. The wording was
> migrated unchanged from the source page; correct it to
> `https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-verlauf`
> before release. The same copy-and-paste defect affected the deleted mapping queries of the source
> page.
{: .ig-highlight .ig-highlight-blue}

### Examples

<!-- DERIVED:bridge source=Verlauf-Observation.page.md gate=B -->
> **Written during migration - review before release.** The instance
> `mii-exa-onko-verlauf-tumor` in this guide illustrates the profile.
{: .ig-highlight .ig-highlight-blue}
