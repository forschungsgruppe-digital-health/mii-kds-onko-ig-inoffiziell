<!-- markdownlint-disable MD041 -->
<!-- Migrated from Fruehere-Tumorerkrankung-Condition.page.md (MII IG Modul Onkologie, Simplifier guide tree).
     German mirror (source language): input/translations/de/intro-notes/StructureDefinition-mii-pr-onko-fruehere-tumorerkrankung-intro.md -->

This profile describes previous tumour diseases that were diagnosed or treated at an earlier point in the patient history. It is based on the FHIR Condition resource, because historical anamnestic data are frequently available as free text only.

### Distinction from the primary tumour diagnosis

In contrast to the profile "Diagnose Primärtumor" (MII_PR_Onko_Diagnose_Primaertumor), which describes the current oncological disease, this profile serves to record **previous** tumour diseases from the patient history.

**Key differences:**

* **Data source**: previous tumour diseases often originate from free-text entries in the patient history, whereas the primary tumour diagnosis is based on current diagnostic findings
* **Coding requirements**: code.text is mandatory, ICD-10-GM coding is optional (mandatory for the primary tumour)
* **Base profile**: based on FHIR Condition (not on MII Diagnose), in order to allow flexible free-text recording
* **Level of detail**: reduced requirements regarding diagnostic confirmation, topography and further details

### Usage notes

#### Mandatory data

* **code.text**: textual description of the previous tumour disease (e.g. "Hautkrebs am Rücken, ca. 2010")
* **category**: categorisation as an oncological diagnosis (SNOMED CT: 394593009 "Medical oncology")
* **subject**: reference to the patient

#### Optional data

* **code.coding[icd10-gm]**: ICD-10-GM coding, if it can be determined retrospectively
* **bodySite.coding[icd-o-3]**: ICD-O-3 topography, if known
* **extension[assertedDate]**: date of diagnosis of the previous tumour disease
* **clinicalStatus**: current clinical status (e.g. resolved, remission)
* **verificationStatus**: verification status (e.g. confirmed, unconfirmed)
* **note**: additional information on the previous tumour disease

### Mapping to oBDS 5.9

The profile represents the oBDS requirement for "Frühere Tumorerkrankungen" (section 5.9):

| oBDS element | FHIR path | Note |
|--------------|-----------|------|
| Frühere Tumorerkrankung Beschreibung | code.text | Mandatory field |
| Frühere Tumorerkrankung ICD-10-GM Code | code.coding[icd10-gm].code | Optional |
| Frühere Tumorerkrankung ICD-10-GM Version | code.coding[icd10-gm].version | Optional |
| Frühere Tumorerkrankung Diagnosedatum | extension[assertedDate].valueDateTime | Optional |
| Frühere Tumorerkrankung ICD-O-3 Topographie | bodySite.coding[icd-o-3].code | Optional |

### Examples

**Example 1: with ICD-10-GM coding**

```
Code.text: "Mamma-Ca, links"
Code.coding[icd10-gm]: C50.9 (ICD-10-GM 2013)
BodySite.coding[icd-o-3]: C50.9 "Breast, NOS"
Extension[assertedDate]: 2013
ClinicalStatus: resolved
```

**Example 2: free text only (typical anamnestic entry)**

```
Code.text: "Hautkrebs am Rücken, ca. 2010"
Extension[assertedDate]: 2010
ClinicalStatus: resolved
Note: "Patient berichtet von operativ entferntem Hautkrebs vor ca. 14 Jahren"
```

Complete examples are available in the instances:

* `mii-exa-onko-fruehere-tumorerkrankung-cervix` - Cervix-Ca in situ
* `mii-exa-onko-fruehere-tumorerkrankung-mamma` - Mammakarzinom
* `mii-exa-onko-fruehere-tumorerkrankung-prostata` - Prostatakarzinom
* `mii-exa-onko-fruehere-tumorerkrankung-freetext` - free text only, without ICD coding

### Conformance

The profile is compatible with the FHIR Condition resource R4.

**Search parameters**

The following search parameters are relevant for the profile Frühere Tumorerkrankung, also in combination:

1. The search parameter "_id" SHALL be supported:

    Examples:

    ```GET [base]/Condition?_id=12345```

    Usage notes: Further information on searching by "_id" is available in the [FHIR base specification — section "Parameters for all resources"](http://hl7.org/fhir/R4/search.html#all).

1. The search parameter "_profile" SHALL be supported:

    Examples:

    ```GET [base]/Condition?_profile=https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-fruehere-tumorerkrankung```

    Usage notes: Further information on searching by "_profile" is available in the [FHIR base specification — section "Parameters for all resources"](http://hl7.org/fhir/R4/search.html#all).

1. The search parameter "code" SHALL be supported:

    Examples:

    ```GET [base]/Condition?code=http://fhir.de/CodeSystem/bfarm/icd-10-gm|C50.9```

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

    ```GET [base]/Condition?body-site=http://terminology.hl7.org/CodeSystem/icd-o-3|C50.9```

    Usage notes: Further information on searching by "Condition.bodySite" is available in the [FHIR base specification — section "token"](http://hl7.org/fhir/R4/search.html#token).

1. The search parameter "clinical-status" SHALL be supported:

    Examples:

    ```GET [base]/Condition?clinical-status=resolved```

    Usage notes: Further information on searching by "Condition.clinicalStatus" is available in the [FHIR base specification — section "token"](http://hl7.org/fhir/R4/search.html#token).
