<!-- markdownlint-disable MD041 -->
<!-- Migrated from Lymphknotenuntersuchung-Observation.page.md (MII IG Modul Onkologie, Simplifier guide tree).
     That source page covered all four lymph node profiles together; in this guide each profile has its own page.
     German mirror (source language): input/translations/de/intro-notes/StructureDefinition-mii-pr-onko-anzahl-untersuchte-lymphknoten-intro.md -->

This profile describes the lymph node examinations carried out as part of oncological staging.
The oBDS register provides for four different data points:

* Number of examined lymph nodes
* Number of involved lymph nodes

In addition, depending on the anatomy affected, sentinel lymph nodes can be recorded as well, hence additionally

* Number of examined **sentinel** lymph nodes
* Number of involved **sentinel** lymph nodes

The ratio between involved and examined lymph nodes is determined in some clinical settings, but is not represented as a data point in the oBDS and is therefore not part of this FHIR profiling either.

<!-- DERIVED:bridge source=Lymphknotenuntersuchung-Observation.page.md gate=B -->
> **Written during migration - review before release.** This profile covers the data point *Untersuchte Lymphknoten* (examined lymph nodes). The other three data points are separate profiles: [Anzahl befallene Lymphknoten](StructureDefinition-mii-pr-onko-anzahl-befallene-lymphknoten.html), [Anzahl befallene Sentinel-Lymphknoten](StructureDefinition-mii-pr-onko-anzahl-befallene-sentinel-lymphknoten.html) and [Anzahl untersuchte Sentinel-Lymphknoten](StructureDefinition-mii-pr-onko-anzahl-untersuchte-sentinel-lymphknoten.html). In the source guide all four were profiled and mapped on one shared page because their content is very similar.
{: .ig-highlight .ig-highlight-blue}

**Search parameters**

The following search parameters are relevant for the Onkologie module, also in combination:

1. The search parameter ```_id``` SHALL be supported:

    Examples:

    ```GET [base]/Condition?_id=1234```

    Usage notes: Further information on searching by "_id" is available in the [FHIR base specification — section "Parameters for all resources"](http://hl7.org/fhir/R4/search.html#all).

2. The search parameter "_profile" SHALL be supported:

    Examples:

    ```GET [base]/Condition?_profile=https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-diagnose```

    Usage notes: Further information on searching by "_profile" is available in the [FHIR base specification — section "token"](http://hl7.org/fhir/R4/search.html#all).

3. The search parameter "category" SHALL be supported:

    Examples:

    ```GET [base]/Observation?category=http://terminology.hl7.org/CodeSystem/observation-category|laboratory```

    Usage notes: Further information on searching by "category" is available in the FHIR base specification — section "token".

4. The search parameter "code" SHALL be supported:

    Examples:

    ```GET [base]/Observation?code=http://fhir.de/CodeSystem/sct|184305005```

    Usage notes: Further information on searching by "code" is available in the FHIR base specification — section "token".

5. The search parameter "subject" SHALL be supported:

    Examples:

    ```GET [base]/Observation?subject=Patient/example```

    Usage notes: Further information on searching by "subject" is available in the FHIR base specification — section "reference".

6. The search parameter "focus" SHALL be supported:

    Examples:

    ```GET [base]/Observation?focus=Condition/example```

    Usage notes: Further information on searching by "focus" is available in the FHIR base specification — section "reference".

7. The search parameter "encounter" SHALL be supported:

    Examples:

    ```GET [base]/Observation?encounter=Encounter/example```

    Usage notes: Further information on searching by "encounter" is available in the FHIR base specification — section "reference".

8. The search parameter "date" SHALL be supported:

    Examples:

    ```GET [base]/Observation?date=2024-02-08```

    Usage notes: Further information on searching by "date" is available in the FHIR base specification — section "date".

9. The search parameter "derived-from" SHALL be supported:

    Examples:

    ```GET [base]/Observation?derived-from=Observation/example```

    Usage notes: Further information on searching by "derived-from" is available in the FHIR base specification — section "reference".
