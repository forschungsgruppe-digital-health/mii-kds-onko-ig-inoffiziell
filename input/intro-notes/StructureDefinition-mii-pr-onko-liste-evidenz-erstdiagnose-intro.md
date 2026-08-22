<!-- markdownlint-disable MD041 -->
<!-- Migrated from Erstdiagnose-Evidenz-List.page.md (MII IG Modul Onkologie, Simplifier guide tree).
     The source page repeated the same two search parameter entries three times; kept once here.
     German mirror (source language): input/translations/de/intro-notes/StructureDefinition-mii-pr-onko-liste-evidenz-erstdiagnose-intro.md -->

The List resource is a flat collection of resources and offers functions for managing the collection. In this case the resource serves as the collection of the observations and diagnostic reports that are known at the time of the initial oncological diagnosis. These include, for example, a TNM classification as well as further diagnostically relevant classifications, distant metastases, histologies etc.

The evidence list itself is not part of the oBDS; it is intended to permanently record the state at the time of the initial diagnosis.

* The list **SHOULD** be created on the basis of the content that was known before or at the time the initial diagnosis was established.
* For this, the entries **MAY** be taken directly from the Diagnosemeldung.

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
