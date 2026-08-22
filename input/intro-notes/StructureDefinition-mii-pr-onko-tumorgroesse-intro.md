<!-- markdownlint-disable MD041 -->
<!-- Migrated from Tumorgroesse-Observation.page.md (MII IG Modul Onkologie, Simplifier guide tree).
     German mirror (source language): input/translations/de/intro-notes/StructureDefinition-mii-pr-onko-tumorgroesse-intro.md -->

This profile describes the tumour size in oncology, in particular in the context of breast cancer.
In the Mamma module of the oBDS the tumour size is given as the maximum diameter of the tumour in its largest dimension in millimetres. The profile covers the oBDS Mamma fields **M7** (Tumorgröße Invasives Karzinom) and **M8** (Tumorgröße DCIS). The distinction between invasive and DCIS follows from the linked Condition resource.

Although the tumour size is often described by the T staging, it is nevertheless recorded and documented in various tumour entities, which is why it was implemented as a generic tumour-size Observation.

This profile is designed primarily for the **Mamma module** and maps to:

- **M7**: Tumorgröße Invasives Karzinom (maximum diameter of the invasive carcinoma in mm)
- **M8**: Tumorgröße DCIS (maximum diameter of the DCIS in mm, when no invasive component is present)

**Search parameters**

The following search parameters are relevant for the Onkologie module, also in combination:

1. The search parameter ```_id``` SHALL be supported:

    Examples:

    ```GET [base]/Observation?_id=1234```

    Usage notes: Further information on searching by "_id" is available in the [FHIR base specification — section "Parameters for all resources"](http://hl7.org/fhir/R4/search.html#all).

2. The search parameter "_profile" SHALL be supported:

    Examples:

    ```GET [base]/Observation?_profile=https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-tumorgroesse```

    Usage notes: Further information on searching by "_profile" is available in the [FHIR base specification — section "token"](http://hl7.org/fhir/R4/search.html#all).

3. The search parameter "code" SHALL be supported:

    Examples:

    ```GET [base]/Observation?code=http://loinc.org|21889-1```

    Usage notes: Further information on searching by "code" is available in the FHIR base specification — section "token".

4. The search parameter "subject" SHALL be supported:

    Examples:

    ```GET [base]/Observation?subject=Patient/example```

    Usage notes: Further information on searching by "subject" is available in the FHIR base specification — section "reference".

5. The search parameter "focus" SHALL be supported:

    Examples:

    ```GET [base]/Observation?focus=Condition/example```

    Usage notes: Further information on searching by "focus" is available in the FHIR base specification — section "reference".

6. The search parameter "encounter" SHALL be supported:

    Examples:

    ```GET [base]/Observation?encounter=Encounter/example```

    Usage notes: Further information on searching by "encounter" is available in the FHIR base specification — section "reference".

7. The search parameter "effective" SHALL be supported:

    Examples:

    ```GET [base]/Observation?effective=2024-01-15```

    Usage notes: Further information on searching by "effective" is available in the FHIR base specification — section "date".
