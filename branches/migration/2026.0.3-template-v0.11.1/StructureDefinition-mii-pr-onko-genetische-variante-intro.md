<!-- markdownlint-disable MD041 -->
<!-- Migrated from Genetische-Variante-Observation.page.md (MII IG Modul Onkologie, Simplifier).
     Simplifier/FQL directives (page title, tree/XML/JSON/link tabs, FQL query blocks for
     profile metadata, dataset mapping and oBDS mapping) were removed - the IG Publisher
     renders all of that on this artifact page.
     Markup-only repair: in the source, search parameters 3 ("status") and 10 ("method") had a
     misplaced closing code fence that swallowed the usage-note sentence. The fences were moved
     to the end of the example line; no wording was changed.
     German mirror: input/translations/de/intro-notes/StructureDefinition-mii-pr-onko-genetische-variante-intro.md -->

### Context

Information on genetic variants has been recorded as part of the oBDS since the 2021 version. A
variant is recorded via two data fields:

* 'Genetische Variante Name' as free text
* 'Genetische Variante Ausprägung' as oBDS-specific codes for the interpretation.

With the Molekulargenetischer Befundbericht (MolGenBB), the MII already offers a structure for the
exchange of genetic findings. The MolGenBB is based on the GenomicReport (version STU2) of the
international HL7 Clinical Genomics Working Group and uses international terminologies and
nomenclatures such as:

* **HGNC** for the unambiguous description of gene names
* **HGVS** for the description of variants in the coding and non-coding DNA region as well as for
  proteins
* **ISCN** for the description of cytogenomic position and structural variants
* **Sequence Ontology** for the semantic annotation of the variants

It can be assumed that the genetic laboratories and bioinformatic pipelines work on the basis of
these classifications or are able to map to them.

The coarse-grained recording of the variant data in the oBDS, however, makes a direct mapping to the
terminologies and nomenclatures named above impossible.

### Conformance statements

Where possible, a more precise variant description **SHOULD** be done via the MII Variante.

An integration of these variants **SHOULD** be done by embedding them in the MII Molekulargenetischer
Befundbericht `DiagnosticReport` and the MII Molekulargenetische Anforderung `ServiceRequest`.

In the event that these modules cannot be implemented at the DIZ sites at all, not yet, or only
partially, a direct mapping of the oBDS fields onto the following fields **SHALL** be done:

* `Observation.note` for the variant name
* `Observation.interpretation` for the expression of the variant.

### Overview of the MII Variante

The variant profile of the Molekularer Befundbericht can be found here:
https://simplifier.net/medizininformatikinitiative-modulomics/sdmiimolgenvariante

When using the MII Variante, the following data fields are mandatory for conformance:

* `subject`: reference to a Patient
* `code`: fixed LOINC code (69548-6) identifying it as an examination of a genetic variant
* `status`: HL7 status
* `category`: fixed HL7 code classifying it as a laboratory value

In addition, the following details can optionally be provided:

* `specimen`: reference to the biospecimen
* `method`: methodology of the examination
* `valueCodeableConcept`: variant assessment (present, not present, not called, indeterminate)
* `component`: all further details on the methodological execution and evaluation as well as variant
  information

### Search parameters

The following search parameters are relevant for the Onkologie module, also in combination:

1. The search parameter ```_id``` SHALL be supported:

    Examples:

    ```GET [base]/Observation?_id=1234```

    Usage notes: further information on searching by "_id" can be found in the [FHIR base specification, section "Parameters for all resources"](http://hl7.org/fhir/R4/search.html#all).

2. The search parameter ```_profile``` SHALL be supported:

    Examples:

    ```GET [base]/Observation?_profile=https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-genetische-variante```

    Usage notes: further information on searching by "_profile" can be found in the [FHIR base specification, section "token"](http://hl7.org/fhir/R4/search.html#all).

3. The search parameter "status" SHALL be supported:

    Examples:

    ```GET [base]/Observation?status=final```

    Usage notes: further information on searching by "status" can be found in the FHIR base specification, section "token".

4. The search parameter "category" SHALL be supported:

    Examples:

    ```GET [base]/Observation?category=http://terminology.hl7.org/CodeSystem/observation-category|laboratory```

    Usage notes: further information on searching by "category" can be found in the FHIR base specification, section "token".

5. The search parameter "code" SHALL be supported:

    Examples:

    ```GET [base]/Observation?code=http://fhir.de/CodeSystem/sct|184305005```

    Usage notes: further information on searching by "code" can be found in the FHIR base specification, section "token".

6. The search parameter "subject" SHALL be supported:

    Examples:

    ```GET [base]/Observation?subject=Patient/example```

    Usage notes: further information on searching by "subject" can be found in the FHIR base specification, section "reference".

7. The search parameter "focus" SHALL be supported:

    Examples:

    ```GET [base]/Observation?focus=Condition/example```

    Usage notes: further information on searching by "focus" can be found in the FHIR base specification, section "reference".

8. The search parameter "encounter" SHALL be supported:

    Examples:

    ```GET [base]/Observation?encounter=Encounter/example```

    Usage notes: further information on searching by "encounter" can be found in the FHIR base specification, section "reference".

9. The search parameter "interpretation" SHALL be supported:

    Examples:

    ```GET [base]/Observation?interpretation=http://snomed.info/sct|55446002```

    Usage notes: further information on searching by "interpretation" can be found in the FHIR base specification, section "token".

10. The search parameter "method" SHALL be supported:

    Examples:

    ```GET [base]/Observation?method=http://loinc.org|LA26398-0```

    Usage notes: further information on searching by "method" can be found in the FHIR base specification, section "token".

11. The search parameter "specimen" SHALL be supported:

    Examples:

    ```GET [base]/Observation?specimen=Specimen/example```

    Usage notes: further information on searching by "specimen" can be found in the FHIR base specification, section "reference".

12. The search parameter "device" SHALL be supported:

    Examples:

    ```GET [base]/Observation?device-from=Device/example```

    Usage notes: further information on searching by "device" can be found in the FHIR base specification, section "reference".

13. The search parameter "derived-from" SHALL be supported:

    Examples:

    ```GET [base]/Observation?derived-from=Observation/example```

    Usage notes: further information on searching by "derived-from" can be found in the FHIR base specification, section "reference".

### Examples

<!-- DERIVED:bridge source=Genetische-Variante-Observation.page.md gate=B -->
> **Written during migration - review before release.** The instance
> `mii-exa-onko-genetische-variante-braf` in this guide illustrates the profile.
{: .ig-highlight .ig-highlight-blue}
