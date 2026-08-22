<!-- markdownlint-disable MD041 -->
<!-- Migrated from Tumorkonferenz-CarePlan.page.md (MII IG Modul Onkologie, Simplifier).
     Simplifier/FQL directives (page title, tree/XML/JSON/link tabs, FQL query blocks for
     profile metadata, dataset mapping and oBDS mapping) were removed - the IG Publisher
     renders all of that on this artifact page.
     German mirror: input/translations/de/intro-notes/StructureDefinition-mii-pr-onko-tumorkonferenz-intro.md -->

This profile describes the tumor board (Tumorkonferenz) and the therapy recommendations for both
traditional and molecular tumor board workflows. The data fields have been part of the oBDS since the
2021 version and are recorded in two different modules. Because all of the fields involved map very
well onto the FHIR CarePlan resource, all tumor board and therapy recommendation fields were
consolidated into the Tumorkonferenz profile.

### Unified Activity Slicing Architecture

The profile supports **two different implementation approaches** via activity slicing:

#### **obds slice**: standard oBDS therapy categorization

For traditional tumor boards using the oBDS 19.1 categorization:

- **Usage**: `activity[obds].detail.code` for the therapy type (CH, HO, IM, ZS, etc.)
- **Status tracking**: `activity[obds].detail.status` and `activity[obds].detail.statusReason` for
  therapy deviations
- **oBDS conformance**: complete representation of the oBDS fields 19.1 and 19.2

#### **extended slice**: molecular tumor board protocols

For detailed molecular tumor boards with structured therapy protocols:

- **Usage**: `activity[extended].reference` → RequestGroup/MedicationRequest/ServiceRequest
- **Use cases**: multi-agent protocols, pharmaceutical classes, specific drug selection
- **Extended functionality**: a level of detail beyond the oBDS categorization

### Common profile structure

Both slices share the common CarePlan elements:

* **Patient reference**: `subject`
* **Primary diagnosis reference**: `addresses`
* **Tumor board category**: `category` per oBDS 18.2
* **Date**: `created` per oBDS 18.1
* **Additional information**: `supportingInfo` for relevant follow-up stagings

### Status management

#### For the obds slice (traditional tumor boards)

The CarePlan resource requires the `status` element of an `activity` to be present. The therapies
actually carried out are recorded in the cancer registry data and SHOULD reference the Tumorkonferenz
resource via `Procedure.basedOn(Reference(CarePlan))`.

**Recommended status codes** per FHIR CarePlanActivityStatus:

- `completed`: completed therapy
- `on-hold`: therapy interruption for a therapy that has not yet started
- `stopped`: therapy interruption for a therapy that has already started
- `unknown`: unknown, no status information available

**Therapy deviations**: for `on-hold` and `stopped`, `statusReason` SHOULD be filled with the oBDS
field 'Therapieabweichung auf Wunsch des Patienten'.

#### For the extended slice (molecular tumor boards)

Status tracking happens in the referenced resources (RequestGroup, MedicationRequest,
ServiceRequest). `activity.progress` can be used for narrative progress notes.

Every tumor board with a therapy recommendation SHOULD be stored as an individual resource and
reference the primary diagnosis via `CarePlan.addresses(Reference(Condition))`.

### FHIR invariant management

**Problem**: the FHIR R4 invariant cpl-3 prevents the simultaneous use of `activity.detail.code` and
`activity.reference`

**Solution**: slice-specific element deactivation:

- **obds slice**: `activity.detail` enabled, `activity.reference` disabled (0..0)
- **extended slice**: `activity.reference` enabled, `activity.detail` disabled (0..0)

### Implementation flexibility

- **Backward compatibility**: existing oBDS implementations keep working unchanged
- **Hybrid approaches**: a single CarePlan can use both slice types
- **Incremental adoption**: start with the obds slice, extend to the extended slice when needed

### Usage examples

#### Traditional tumor board (obds slice):

```
* activity[obds].detail.code.coding = #OP "Operation"
* activity[obds].detail.status = #completed
```

#### Molecular tumor board (extended slice):

```
* activity[extended].reference = Reference(RequestGroup/molecular-protocol)
* activity[extended].progress.text = "HR+/HER2- mit PI3K-Aktivierung - CDK4/6 Inhibitor empfohlen"
```

#### Mixed approach:

```
* activity[obds].detail.code.coding = #OP "Operation"
* activity[extended].reference = Reference(RequestGroup/precision-medicine-protocol)
```

### Search parameters

The following search parameters are relevant for the Onkologie module, also in combination:

1. The search parameter ```_id``` SHALL be supported:

    Examples:

    ```GET [base]/CarePlan?_id=1234```

    Usage notes: further information on searching by "_id" can be found in the [FHIR base specification, section "Parameters for all resources"](http://hl7.org/fhir/R4/search.html#all).

2. The search parameter ```_profile``` SHALL be supported:

    Examples:

    ```GET [base]/CarePlan?_profile=https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-tumorkonferenz```

    Usage notes: further information on searching by "_profile" can be found in the [FHIR base specification, section "token"](http://hl7.org/fhir/R4/search.html#token).

3. The search parameter ```identifier``` SHALL be supported:

    Examples:

    ```GET [base]/CarePlan?identifier=Tumorkonferenz_1```

    Usage notes: further information on searching by "identifier" can be found in the [FHIR base specification, section "token"](http://hl7.org/fhir/R4/search.html#token).

4. The search parameter ```category``` SHALL be supported:

    Examples:

    ```GET [base]/CarePlan?category=http://snomed.info/sct|734163000```

    Usage notes: further information on searching by "category" can be found in the [FHIR base specification, section "token"](http://hl7.org/fhir/R4/search.html#token).

5. The search parameter ```subject``` SHALL be supported:

    Examples:

    ```GET [base]/CarePlan?subject=Patient/example```

    Usage notes: further information on searching by "subject" can be found in the [FHIR base specification, section "reference"](http://hl7.org/fhir/R4/search.html#reference).

6. The search parameter ```period``` SHALL be supported:

    Examples:

    ```GET [base]/CarePlan?date=eq2022-01-01```

    Usage notes: further information on searching by "period" can be found in the [FHIR base specification, section "date"](http://hl7.org/fhir/R4/search.html#date).

7. The search parameter ```contributor``` SHALL be supported:

    Examples:

    ```GET [base]/CarePlan?contributor=Practitioner/example```

    Usage notes: further information on searching by "contributor" can be found in the [FHIR base specification, section "reference"](http://hl7.org/fhir/R4/search.html#reference).

8. The search parameter ```addresses``` SHALL be supported:

    Examples:

    ```GET [base]/CarePlan?addresses=Condition/example```

    Usage notes: further information on searching by "addresses" can be found in the [FHIR base specification, section "reference"](http://hl7.org/fhir/R4/search.html#reference).

9. The search parameter ```activity-code``` SHALL be supported:

    Examples:

    ```GET [base]/CarePlan?activity-code=https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/CodeSystem/mii-cs-therapieempfehlung-typ|OP```

    Usage notes: further information on searching by "activity-code" can be found in the [FHIR base specification, section "token"](http://hl7.org/fhir/R4/search.html#token).

### Examples

<!-- DERIVED:bridge source=Tumorkonferenz-CarePlan.page.md gate=B -->
> **Written during migration - review before release.** Three examples in this guide illustrate the
> profile: `mii-exa-onko-tumorkonferenz-01` for a traditional oBDS tumor board (obds slice),
> `mii-exa-onko-tumorkonferenz-pure-molecular` for a molecular tumor board (extended slice), and
> `mii-exa-onko-tumorkonferenz-mixed-approach` for the mixed approach that uses both slices.
{: .ig-highlight .ig-highlight-blue}
