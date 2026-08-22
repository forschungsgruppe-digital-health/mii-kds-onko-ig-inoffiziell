<!-- markdownlint-disable MD041 -->
<!-- Migrated from Specimen-Specimen.page.md (MII IG Modul Onkologie, Simplifier guide tree).
     German mirror (source language): input/translations/de/intro-notes/StructureDefinition-mii-pr-onko-specimen-intro.md -->

This profile describes a biosample in oncology.

The two data points of a single biosample that are relevant for the oBDS are:

* Tumor Histologiedatum -> `collection.collectedDateTime`
* Histologie-Einsendenummer -> `accsessionIdentifier.value`

Within the core data set of the Medizininformatik-Initiative, a biosample **MAY** likewise be created conforming to the biosample profile of the Biobank module. <https://www.medizininformatik-initiative.de/Kerndatensatz/Modul_Biobank/SpecimenBioprobe.html>

In that case the following elements have to be given in addition to the two data points above:

- `status` (availability of the sample)
- `type` kind of sample (SNOMED CT coded)

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
