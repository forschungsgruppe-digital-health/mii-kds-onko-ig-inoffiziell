<!-- markdownlint-disable MD041 -->
<!-- Migrated from Histologiebefund-DiagnosticReport.page.md (MII IG Modul Onkologie, Simplifier guide tree).
     German mirror (source language): input/translations/de/intro-notes/StructureDefinition-mii-pr-onko-befund-intro.md -->

This profile describes a pathology report in oncology.

Because the data originate from the local tumour documentation systems, the majority of the reports will be available as plain text.

Within the MII, pathology reporting **MAY** likewise be carried out via the Pathologie-Befundbericht. In that case individual observations can be coded in a structured way as Patho Findings via LOINC or SNOMED.
<https://www.medizininformatik-initiative.de/Kerndatensatz/Modul_Pathologie_Befund/MII-IG-KDS-Modul-Pathologie-Befund-TechnischeImplementierung-FHIRProfile-MII-PR-Patho-Report.html>

**Search parameters**

The following search parameters are relevant for the Onkologie module, also in combination:

1. The search parameter ```_id``` SHALL be supported:

    Examples:

    ```GET [base]/Condition?_id=1234```

    Usage notes: Further information on searching by "_id" is available in the [FHIR base specification — section "Parameters for all resources"](http://hl7.org/fhir/R4/search.html#all).

2. The search parameter "_profile" SHALL be supported:

    Examples:

    ```GET [base]/DiagnosticReport?_profile=https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-befund```

    Usage notes: Further information on searching by "_profile" is available in the [FHIR base specification — section "token"](http://hl7.org/fhir/R4/search.html#all).
