<!-- markdownlint-disable MD041 -->
<!-- Migrated from Verlaufshistologie-Observation.page.md (MII IG Modul Onkologie, Simplifier guide tree).
     German mirror (source language): input/translations/de/intro-notes/StructureDefinition-mii-pr-onko-histologie-icdo3-intro.md -->

This profile describes a histological examination in oncology.

For histologies used to establish the primary diagnosis, the ICD-O-3 codings SHOULD be recorded directly in the primary diagnosis.
The present profile is reserved for the case that an ICD-O-3 is determined in a histology in the course of the disease. Possible scenarios for this are the histological confirmation of distant metastases or a histological follow-up of known tumour sites.
Examinations that lead to new cancer diagnoses SHOULD be coded directly as part of the new diagnosis.

**Search parameters**

The following search parameters are relevant for the Onkologie module, also in combination:

1. The search parameter ```_id``` SHALL be supported:

    Examples:

    ```GET [base]/Observation?_id=1234```

    Usage notes: Further information on searching by "_id" is available in the [FHIR base specification — section "Parameters for all resources"](http://hl7.org/fhir/R4/search.html#all).

2. The search parameter "_profile" SHALL be supported:

    Examples:

    ```GET [base]/Observation?_profile=https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-grading```

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

10. The search parameter "body-site" SHALL be supported:

    Examples:

    ```GET [base]/Observation?bodysite=http://fhir.de/CodeSystem/icd-o-3|C00.4```

    Usage notes: Further information on searching by "derived-from" is available in the FHIR base specification — section "reference".
