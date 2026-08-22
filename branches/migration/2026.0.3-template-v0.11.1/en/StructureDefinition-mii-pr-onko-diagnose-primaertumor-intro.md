<!-- markdownlint-disable MD041 -->
<!-- Migrated from Diagnose-Condition.page.md (MII IG Modul Onkologie, Simplifier guide tree).
     German mirror (source language): input/translations/de/intro-notes/StructureDefinition-mii-pr-onko-diagnose-primaertumor-intro.md -->

This profile describes a diagnosis in oncology. It is based on the MII KDS Modul Diagnose.

The oBDS expects the diagnosis to be coded via ICD-10 and the topography of the primary tumour and the histological morphology to be coded via ICD-O-3. In FHIR this combination can already be represented completely by the MII-Diagnose:

* ICD-10-GM via `Condition.code[icd10-gm]`, (derived from MII-Diagnose)
* ICD-O-3 morphology via `Condition.extension[morphology-behavior-icdo3]` (comparable to the mCODE extension)
* ICD-O-3 topography via `Condition.bodySite`.

Further histological examinations with differing morphologies over the course of treatment SHOULD be recorded via the Histologie profile.

### Links to other resources

The oncological diagnosis is the central core element of the Basisdatensatz. All case-related observations are linked to it directly or indirectly:

- all observations reference the primary diagnosis via `Observation.focus`
- the Tumorkonferenz resource references the primary diagnosis via `CarePlan.addresses`
- all procedures (surgery, radiotherapy, systemic therapy) reference the primary diagnosis via `reasonReference`

### Temporal assignment over the course of the disease

In the oBDS, observations are assigned as relevant for establishing the initial diagnosis by being part of the Diagnosemeldung. Later reports can then be made, for example, as Verlaufs-, Pathologie- oder Todesmeldung.

Observations made after the initial diagnosis has been established reference, in the present profiling, a "Verlauf" Observation resource with a date of its own.
The observations that are known at the time the initial diagnosis is established are of particular interest for prognostic research questions. To make these data points easier to identify, all observations from the oBDS Diagnosemeldung **SHOULD** be referenced via `evidence.detail` in a FHIR list with the profile "Evidenz Erstdiagnose".

### Conformance

The present profiling is compatible with the diagnosis profile of the ISiK Basismodule Stufe 4. <https://simplifier.net/isik-basis-v4/isikdiagnose>

**Search parameters**

The following search parameters are relevant for the Onkologie module, also in combination:

1. The search parameter "_id" SHALL be supported:

    Examples:

    ```GET [base]/Condition?_id=12345```

    Usage notes: Further information on searching by "_id" is available in the [FHIR base specification — section "Parameters for all resources"](http://hl7.org/fhir/R4/search.html#all).

1. The search parameter "_profile" SHALL be supported:

    Examples:

    ```GET [base]/Condition?_profile=https://www.medizininformatik-initiative.de/fhir/core/modul-diagnose/StructureDefinition/Diagnose```

    Usage notes: Further information on searching by "_profile" is available in the [FHIR base specification — section "Parameters for all resources"](http://hl7.org/fhir/R4/search.html#all).

1. The search parameter "code" SHALL be supported:

    Examples:

    ```GET [base]/Condition?code=http://fhir.de/CodeSystem/bfarm/icd-10-gm|A15.0```

    Usage notes: Further information on searching by "Condition.code" is available in the [FHIR base specification — section "Token Search"](http://hl7.org/fhir/R4/search.html#token).

1. The search parameter "subject" SHALL be supported:

    Examples:

    ```GET [base]/Condition?subject=Patient/test```

    Usage notes: Further information on searching by "Condition.subject" is available in the [FHIR base specification — section "reference"](http://hl7.org/fhir/R4/search.html#reference).

1. The search parameter "patient" SHALL be supported:

    Examples:

    ```GET [base]/Condition?patient=Patient/test```

    Usage notes: Further information on searching by "Condition.subject" is available in the [FHIR base specification — section "reference"](http://hl7.org/fhir/R4/search.html#reference).

1. The search parameter "body-site" SHALL be supported:

    Examples:

    ```GET [base]/Condition?body-site=http://terminology.hl7.org/CodeSystem/icd-o-3|C44.2```

    Usage notes: Further information on searching by "Condition.body-site" is available in the [FHIR base specification — section "reference"](http://hl7.org/fhir/R4/search.html#reference).

1. The search parameter "morphology-behaviour-icd03" SHALL be supported:

    Examples:

    ```GET [base]/Condition?morphology-behaviour-icdo3=http://terminology.hl7.org/CodeSystem/icd-o-3|8503/2```

    Usage notes: Further information on searching by "Condition.extension[morphology-behaviour-icdo3]" is available in the [FHIR base specification — section "reference"](http://hl7.org/fhir/R4/search.html#reference).

1. The search parameter "icd10gm-diagnosesicherheit" SHALL be supported:

    Examples:

    ```GET [base]/Condition?icd10gm-diagnosesicherheit=https://fhir.kbv.de/CodeSystem/KBV_CS_SFHIR_ICD_DIAGNOSESICHERHEIT|G```

    Usage notes: Further information on searching by "Condition.code.coding.extension.where(url='http://fhir.de/StructureDefinition/icd-10-gm-diagnosesicherheit').value" is available in the [FHIR base specification — section "token"](http://hl7.org/fhir/R4/search.html#token).

1. The search parameter "icd10gm-mehrfachcodierung" SHALL be supported:

    Examples:

    ```GET [base]/Condition?icd10gm-mehrfachcodierung=http://fhir.de/CodeSystem/icd-10-gm-mehrfachcodierungs-kennzeichen|†```

    Usage notes: Further information on searching by "Condition.code.coding.extension.where(url='http://fhir.de/StructureDefinition/icd-10-gm-mehrfachcodierungs-kennzeichen').value" is available in the [FHIR base specification — section "token"](http://hl7.org/fhir/R4/search.html#token).

1. The search parameter "icd10gm-seitenlokalisation" SHALL be supported:

    Examples:

    ```GET [base]/Condition?icd10gm-seitenlokalisation=https://fhir.kbv.de/CodeSystem/KBV_CS_SFHIR_ICD_SEITENLOKALISATION|B```

    Usage notes: Further information on searching by "Condition.code.coding.extension.where(url = 'http://fhir.de/StructureDefinition/seitenlokalisation').value" is available in the [FHIR base specification — section "token"](http://hl7.org/fhir/R4/search.html#token).
