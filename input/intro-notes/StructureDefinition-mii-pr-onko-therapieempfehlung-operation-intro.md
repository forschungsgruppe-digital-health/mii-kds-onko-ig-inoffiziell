<!-- markdownlint-disable MD041 -->
<!-- Migrated from Therapieempfehlung-Operation-ServiceRequest.page.md
     (MII IG Modul Onkologie, Simplifier). Simplifier/FQL directives (page title,
     tree/XML/JSON/link tabs, FQL query blocks for profile metadata and the oBDS mapping)
     were removed - the IG Publisher renders all of that on this artifact page. The two
     pagelink directives were resolved to their targets.
     German mirror: input/translations/de/intro-notes/StructureDefinition-mii-pr-onko-therapieempfehlung-operation-intro.md -->

This profile describes a **surgery therapy recommendation** in the context of the tumor board. It is
based on the FHIR ServiceRequest and enables the structured recording of surgical therapy
recommendations.

### Content

The ServiceRequest profile enables the recording of surgery recommendations of the tumor board with:

- **Categorization**: the kind of surgery recommended
- **Relation to the tumor disease**: reference to the primary tumor diagnosis
- **Supporting information**: relevant findings and staging results

### Use cases

#### **Primary tumor surgery**

Recommendation to surgically remove the primary tumor:

```
ServiceRequest
├── intent: #proposal
├── category: Surgical procedure
├── authoredOn: 2024-01-15
├── reasonReference: Reference(Primärtumor)
└── supportingInfo: Reference(TNM-Staging)
```

#### **Metastasis surgery**

Recommendation to resect metastases:

```
ServiceRequest
├── intent: #proposal
├── category: Surgical procedure
├── authoredOn: 2024-01-15
├── reasonReference: Reference(Primärtumor)
└── supportingInfo: Reference(Fernmetastasen-Observation)
```

### Technical implementation

#### **Intent**

The `intent` element is fixed to `#proposal`, because this is a therapy recommendation.

#### **Category**

The `category` allows the recommended surgery to be classified (e.g. curative vs. palliative
intent).

#### **reasonReference**

Reference to the underlying tumor disease:

```
reasonReference: Reference(MII_PR_Onko_Diagnose_Primaertumor)
```

#### **supportingInfo**

Optional references to supporting clinical information:

- **Staging results**: TNM classification
- **Imaging**: relevant diagnostic findings
- **Laboratory values**: tumor markers or other relevant parameters

### Use with the Extended CarePlan

This profile is primarily designed for use with the **Tumorkonferenz Detailed Recommendations
CarePlan**:

- **Standard oBDS**: cancer registries record only "surgery planned" (therapy recommendation type
  "OP") without details on the kind of surgery
- **Extended CarePlan**: enables specific surgery recommendations with SNOMED CT coding

<!-- DERIVED:bridge source=Therapieempfehlung-Operation-ServiceRequest.page.md gate=B -->
> **Written during migration - review before release.** The source page cross-linked a profile
> "Tumorkonferenz Detailed Recommendations CarePlan". This module does not contain that profile, so
> the reference above is plain text rather than a link. Decide before release whether the profile is
> added or the sentence is rewritten against
> [Tumorkonferenz](StructureDefinition-mii-pr-onko-tumorkonferenz.html) and its extended slice.
{: .ig-highlight .ig-highlight-blue}

**Integration**:

```
CarePlan (Detailed Recommendations)
└── activity.reference → ServiceRequest
    ├── code: SNOMED CT (spezifische OP)
    └── reasonReference: Reference(Primärtumor)
```

### oBDS context

This profile supports the recording of therapy recommendations per oBDS chapter 19:

- **19.1 Therapieempfehlung Typ**: "OP" (Operation)

**Note**: the standard oBDS recording happens via `CarePlan.activity.detail.code`. This
ServiceRequest profile offers extended structuring for molecular tumor boards and specialized use
cases.

The detailed planning and performance of the surgery is recorded in the separate
[Operation (Procedure)](StructureDefinition-mii-pr-onko-operation.html) profile.

### Delimitation

| Profile | Resource | Usage |
|--------|-----------|------------|
| **Therapieempfehlung Operation** | ServiceRequest | Recommendation of the tumor board |
| **Operation** | Procedure | Surgery performed |

### Search parameters

1. The search parameter ```_id``` SHALL be supported:
    ```GET [base]/ServiceRequest?_id=1234```

2. The search parameter "_profile" SHALL be supported:
    ```GET [base]/ServiceRequest?_profile=https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-therapieempfehlung-operation```

3. The search parameter "subject" SHALL be supported:
    ```GET [base]/ServiceRequest?subject=Patient/example```

4. The search parameter "intent" SHOULD be supported:
    ```GET [base]/ServiceRequest?intent=proposal```

5. The search parameter "category" SHOULD be supported:
    ```GET [base]/ServiceRequest?category=surgical-procedure```
