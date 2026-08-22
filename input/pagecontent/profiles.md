<!-- markdownlint-disable MD041 -->
<!-- Split from the former combined profiles-and-extensions.md per the TF-KDS-agreed
     menu structure (one page per artifact type); naming convention from the
     meta wiki page "Namenskonventionen für FHIR-Ressourcen in der MII".
     German mirror: input/translations/de/pagecontent/profiles.md. -->
This page lists the FHIR profiles of the **Onkologie** module. As a
starting point the template ships one minimal example profile,
[Example Patient](StructureDefinition-example-patient.html) — replace it with
your module's profiles (naming convention `MII_PR_<Module>_<Name>`, see the
[`docs/recipes/add-a-profile.md`](https://github.com/forschungsgruppe-digital-health/mii-kds-onko-ig-inoffiziell/blob/main/docs/recipes/add-a-profile.md) in this repository, and the MII naming
conventions). The module's extensions are listed on the
[Extensions](extensions.html) page.

> [TODO: Describe your module's profiles and how they relate to each other. The
> IG Publisher generates the technical detail pages automatically.]
{: .ig-highlight .ig-highlight-grey}

<!-- source: Index.page.md (Simplifier guide,
     TechnischeImplementierung/oBDS-SNOMED-CT-Mapping/Index.page.md) -->
### oBDS to SNOMED CT mapping

<!-- DERIVED:bridge source=Index.page.md gate=B -->
> **Written during migration - review before release.** The oBDS-to-SNOMED-CT
> mappings of this module are published as ConceptMap artifacts, each with its
> own intro note; the notes in this section apply to all of them.
{: .ig-highlight .ig-highlight-blue}

The following pages contain the results of an oBDS-SNOMED mapping onto SNOMED,
carried out with the international SNOMED-CT version of March 2024, supplemented
by the UICC TNM and residual tumour concepts from March 2025.

1. The focus was placed on the answer lists held in the oBDS. For the mapping of
   other national and international classifications and terminologies (ICD-10,
   ICD-O, OPS, ATC, ...) the BfArM is the responsible contact.
1. Besides the answer lists, the data fields themselves are frequently coded in
   SNOMED and or LOINC as well. (to be found as the `code` element on most
   resources)
1. Equivalence assessment: every code is marked with one of four possible
   codings, which describes the relationship in content between source and
   target concept
    - `equivalent`: (almost) identical in content and to be treated as
      equivalent
    - `wider`: the target concept is more general than the source concept and
      can, for example, cover further concepts
    - `narrower`: the target concept is more specific than the source concept
      and covers, for example, only concrete manifestations
    - `unmatched`: no adequately comparable target concept was found.

<!-- source: Index.page.md (Simplifier guide,
     TechnischeImplementierung/FHIR-Profile/TNM-Klassifikation/Index.page.md) -->
### TNM classification

<!-- DERIVED:summary source=Index.page.md gate=B -->
> **Written during migration - review before release.** The TNM artefacts form
> one family. The grouping profile
> [TNM Klassifikation](StructureDefinition-mii-pr-onko-tnm-klassifikation.html)
> carries the reference date and the UICC staging derived from its members and
> references the individual observations in `hasMember`. The categories T, N, M,
> L, V, Pn and S and the symbols a, m, r and y are separate Observation
> profiles, each with its own intro. The c/p/u prefix that records the method of
> classification is a single shared
> [extension](StructureDefinition-mii-ex-onko-tnm-cp-praefix.html) used by the
> T, N and M profiles. The source page listed these artefacts through a
> generated index, which does not carry over to this guide.
{: .ig-highlight .ig-highlight-blue}

<!-- source: TechnischeImplementierung/FHIR-Profile/Organspezifische-Module/Index.page.md -->
## Organ-specific modules

The organ-specific modules extend the MII KDS Onkologie base module with **entity-specific data elements** in line with the requirements of the ADT/GEKID basic documentation. These modules address the particular diagnostic and therapeutic aspects of individual tumour entities that go beyond the general oncological data elements.

<!-- DERIVED:summary source=Index.page.md gate=B -->
> **Written during migration - review before release.** The KDS module Onkologie currently comprises four organ-specific modules - Mamma, Prostata, Kolorektales Karzinom (KRK) and Malignes Melanom - each documented in its own sub-section below. This paragraph replaces the source page's short teaser list, whose per-module bullet points are covered in full by those sub-sections.
{: .ig-highlight .ig-highlight-blue}

**Architecture and integration**

- **Logical model** - the structure of all organ-specific modules is formally defined in the central [Logical Model for organ-specific additional modules](StructureDefinition-mii-lm-onko-organspezifische-zusatzmodule.html).
- **FHIR mappings** - every organ-specific data element has precise FHIR mappings that allow it to be assigned unambiguously to the corresponding FHIR resources. The mappings use semantic annotations with SNOMED CT and LOINC for unambiguous identification.

**Implementation notes**

- **Modularity** - the organ-specific modules are designed as **optional extensions**:
  - can be implemented independently of one another
  - build on the base oncology profiles
  - use shared terminologies and extensions
- **Versioning** - all organ-specific modules follow the versioning of the overall module and are developed in step with the base module.
- **oBDS conformance** - the modules implement the organ-specific additional modules of the oBDS:
  - **Mamma**: oBDS module M (M1-M7)
  - **Prostata**: oBDS module P (P1-P8)
  - **Kolorektales Karzinom**: oBDS module KR (KR1-KR9)
  - **Malignes Melanom**: oBDS module MM (MM1-MM4)

**Technical detail**

- **Profile structure** - every organ-specific module consists of:
  - **Observation profiles** for clinical observations and laboratory values
  - **Procedure profiles** for organ-specific interventions
  - **Specimen profiles** for special specimen types
  - **Bundle examples** for complete use cases
- **Terminology bindings** - the modules use specific ValueSets for:
  - organ-specific surgical procedures (OPS + SNOMED CT)
  - specialised laboratory parameters (LOINC)
  - entity-specific classifications (oBDS codes)
- **Search parameters** - search parameters are defined for the Must Support elements of the organ-specific modules, so that the specialised data elements can be queried in a targeted way.

**Quality assurance**

- **Validation**
  - all profiles pass the automated FHIR validation
  - example data are validated against the profiles
  - terminology bindings are checked against reference terminology servers
- **Consistency** - the organ-specific modules are maintained in step with the base module in order to ensure consistency in naming conventions, cardinalities, terminology usage and mapping structures.

<!-- source: TechnischeImplementierung/FHIR-Profile/Organspezifische-Module/Mamma/Index.page.md -->
### Mamma

The **Mamma module** implements the organ-specific FHIR profiles for documenting breast-cancer-relevant data in accordance with the [oncological basic data set (oBDS) - Mammakarzinom](https://www.basisdatensatz.de/module/5/mammakarzinom).

The module comprises specialised profiles for the characteristic aspects of breast cancer treatment:

- **Receptor status determinations**: estrogen and progesterone receptor status with detailed documentation of staining intensity and proportion of positive cells
- **Her2Neu status**: as a multimodal biomarker with IHC and ISH detection methods, this is currently represented in the Molecular Tumorboard profile
- **Tumour size**: has been moved to the histology module, because it applies to multiple entities
- **Menopausal status**: pre-therapeutic determination of the menopausal status as an important prognostic factor
- **Study participation**: already covered by the current oBDS 2021 and implemented in the corresponding Studienteilnahme profile
- **Surgical procedures**: breast-specific surgical interventions and their documentation
- **Imaging procedures**: pre-operative marking modalities and intraoperative imaging

**Architecture overview.** The following figure shows the structure of the Mamma module and the relationships between the various FHIR resources:

<img src="https://raw.githubusercontent.com/medizininformatik-initiative/kerndatensatzmodul-onkologie/dev/implementation-guides/ImplementationGuide-2026.x-DE/Images/MII_Onko_Mamma_Module/MII_Onko_Mamma_Module.png" alt="MII Onkologie - breast cancer module architecture">

**Links to other resources.** The Mamma profiles are closely linked to the superordinate oncology resources:

- **Primary tumour diagnosis**: all breast-specific observations reference the primary tumour diagnosis as `focus`
- **Patient**: direct link via the `subject` reference
- **Encounter**: optional link to the treating encounter
- **Procedure**: integration of the breast-specific surgical procedures

**oBDS context.** The Mamma profiles implement the following oBDS data fields:

- **M1 Menopausenstatus**: pre-therapeutic determination (premenopausal, perimenopausal, postmenopausal)
- **M2 Rezeptorstatus**: estrogen and progesterone receptor status according to the oBDS definition and the S3 guidelines
- **Breast-specific operations**: extended documentation of the organ-specific interventions
- **Imaging procedures**: special marking and imaging modalities

**Terminology binding.** The Mamma profiles use a combination of different terminologies:

- **SNOMED CT**: primary coding for medical concepts (menopausal status, receptor status)
- **LOINC**: laboratory values and observations (e.g. estrogen receptor antigen)
- **oBDS-specific ValueSets**: for receptor status definitions according to the oBDS
- **S3 guideline ValueSets**: alternative definitions according to the current guidelines

**Contained profiles.** The Mamma module comprises the following FHIR profiles:

- Observations
  - **Estrogen-Rezeptorstatus**: detailed documentation with the proportion of positive cells and the staining intensity
  - **Progesteron-Rezeptorstatus**: corresponding documentation for progesterone receptors
  - **Menopausenstatus**: pre-therapeutic hormone status determination
  - **Tumorgröße**: reference to the histology module (MII_PR_Onko_Tumorgroesse)
  - **Studienteilnahme**: reference to the general study participation profile (MII_PR_Onko_Studienteilnahme)
- Procedures
  - **Mamma-Operationen**: organ-specific surgical interventions
  - **Präoperative Markierung**: modalities of pre-operative marking
- Terminologies
  - **ValueSets**: organ-specific value lists for breast-relevant concepts
  - **CodeSystems**: extended coding systems for special use cases

**Implementation notes.**

- Data capture
  - **Dual coding**: receptor status can be recorded both according to the oBDS and according to the S3 guidelines
  - **Component structure**: detailed breakdown of the receptor status components
  - **Referential integrity**: a consistent link to the primary tumour diagnosis is required
- Quality assurance
  - **Completeness check**: critical data fields are flagged as Must Support
  - **Value range validation**: restriction to medically meaningful value ranges
  - **Terminology consistency**: use of standardised coding systems

**Development note**: a further, more detailed specification of the Mamma profiles is currently being developed in cooperation between the BIH and the Deutsche Gesellschaft für Senologie.

The Mamma profiles enable complete and structured documentation of breast-cancer-specific data in accordance with the current medical standards and the oBDS.

<!-- source: TechnischeImplementierung/FHIR-Profile/Organspezifische-Module/Prostata/Index.page.md -->
### Prostata

The **Prostata module** implements the organ-specific FHIR profiles for documenting prostate-cancer-relevant data in accordance with the oncological basic data set (oBDS) for prostate cancer.

The module comprises specialised profiles for the characteristic aspects of prostate cancer treatment:

- **PSA values**: prostate-specific antigen as the central tumour marker for diagnosis and follow-up
- **Gleason scoring**: histopathological grading with primary, secondary and tertiary patterns
- **Grade Groups**: international standard classification by Grade Groups (1-5)
- **Biopsy results**: detailed documentation of the prostate biopsy findings
- **Post-operative complications**: Clavien-Dindo grading of surgical complications

**Architecture overview.** The following figure shows the structure of the Prostata module and the relationships between the various FHIR resources:

<img src="https://raw.githubusercontent.com/medizininformatik-initiative/kerndatensatzmodul-onkologie/dev/implementation-guides/ImplementationGuide-2026.x-DE/Images/MII_Onko_Prostata_Module/MII_Onko_Prostata_Module.png" alt="MII Onkologie - prostate cancer module architecture">

**Links to other resources.** The Prostata profiles are closely linked to the superordinate oncology resources:

- **Primary tumour diagnosis**: all prostate-specific observations reference the primary tumour diagnosis as `focus`
- **Patient**: direct link via the `subject` reference
- **Encounter**: optional link to the treating encounter
- **Procedure**: integration of the prostate-specific biopsy and surgical procedures

**oBDS context.** The Prostata profiles implement the following oBDS data fields:

- **P1 PSA-Wert**: tumour marker for diagnosis and follow-up
- **P2 Gleason Pattern**: primary, secondary and tertiary Gleason pattern (1-5)
- **P3 Gleason Score**: sum of the primary and secondary pattern with Grade Group
- **P4 Biopsie-Ergebnisse**: number of cores, positive cores and carcinoma involvement
- **P5 Chirurgische Komplikationen**: post-operative complications according to Clavien-Dindo

**Terminology binding.** The Prostata profiles use a combination of different terminologies:

- **LOINC**: primary coding for PSA values and Gleason scores
- **SNOMED CT**: medical concepts and methods (e.g. biopsy procedures)
- **oBDS-specific ValueSets**: for Gleason patterns and the complication classification
- **Clavien-Dindo ValueSets**: standardised grading of post-operative complications

**Contained profiles.** The Prostata module comprises the following FHIR profiles:

- Observations
  - **PSA-Wert**: prostate-specific antigen determination (free/total)
  - **Gleason Patterns**: individual histopathological patterns (primary, secondary, tertiary)
  - **Gleason Score und Grade Group**: combined scoring assessment
  - **Anzahl Stanzen**: total number of biopsy cores
  - **Anzahl positive Stanzen**: number of tumour-positive cores
  - **Karzinom-Befall Stanze**: percentage extent of the carcinoma per core
  - **Clavien-Dindo Komplikationen**: grading of post-operative complications
- Terminologies
  - **ValueSets**: organ-specific value lists for prostate-relevant concepts
  - **CodeSystems**: extended coding systems for the complication classification

**Implementation notes.**

- Data capture
  - **LOINC coding**: standardised laboratory values for PSA and Gleason scores
  - **Component structure**: Grade Group as a component of the Gleason score profile
  - **Referential integrity**: a consistent link to the primary tumour diagnosis is required
- Quality assurance
  - **Completeness check**: critical data fields are flagged as Must Support
  - **Value range validation**: medically meaningful value ranges (e.g. Gleason 1-5)
  - **Terminology consistency**: use of standardised coding systems

**Development note**: the Clavien-Dindo grading could possibly be moved into the general surgery module, because it is a universal surgical classification system (see the comment phase).

The Prostata profiles enable complete and structured documentation of prostate-cancer-specific data in accordance with the current medical standards and the oBDS.

<!-- source: TechnischeImplementierung/FHIR-Profile/Organspezifische-Module/KolorektalesKarzinom/Index.page.md -->
### Kolorektales Karzinom (KRK)

The **Kolorektales Karzinom (KRK) module** implements the organ-specific FHIR profiles for documenting colorectal cancer in accordance with the oncological basic data set (oBDS).

The module comprises specialised profiles for the characteristic aspects of KRK treatment:

- **Pre-operative assessment**: distance to the anocutaneous line, MRI-based measurement of the mesorectal fascia, ASA classification
- **Surgical interventions**: KRK-specific surgical procedures and stoma marking
- **Resection margins**: distance to the aboral margin and to the circumferential resection plane (CRM)
- **Post-operative complications**: grading of the anastomotic leak
- **Pathology specimens**: specific Specimen profiles for KRK resection specimens

**Architecture overview.** The following figure shows the structure of the KRK module and the relationships between the various FHIR resources:

<img src="https://raw.githubusercontent.com/medizininformatik-initiative/kerndatensatzmodul-onkologie/dev/implementation-guides/ImplementationGuide-2026.x-DE/Images/MII_Onko_KRK_Module/MII_Onko_KRK_Module.png" alt="MII Onkologie - colorectal cancer module architecture">

**Links to other resources.** The KRK profiles are closely linked to the superordinate oncology resources:

- **Primary tumour diagnosis**: all KRK-specific observations reference the primary tumour diagnosis as `focus`
- **Patient**: direct link via the `subject` reference
- **Encounter**: optional link to the treating encounter
- **Procedure**: integration of the KRK-specific surgical procedures
- **Specimen**: pathology specimens with specific KRK resection details

**oBDS context.** The KRK profiles implement the following oBDS data fields:

- **KR1 Abstand Anokutanlinie**: pre-operative localisation of the tumour
- **KR2 Abstand aboral**: minimum distance to the aboral resection margin
- **KR3 Abstand CRM**: distance to the circumferential resection plane
- **KR4 ASA-Klassifikation**: assessment of the anaesthesia risk
- **KR5 MRT Mesorektale Faszie**: distance to the mesorectal fascia on MRI
- **KR6 Anastomoseninsuffizienz**: post-operative complication (grade A/B/C)

**Terminology binding.** The KRK profiles use a combination of different terminologies:

- **LOINC**: ASA classification (97816-3)
- **SNOMED CT**: medical concepts and procedures
- **OPS**: German surgical procedure codes
- **oBDS-specific ValueSets**: for the grading of the anastomotic leak

**Contained profiles.** The KRK module comprises the following FHIR profiles:

- Observations
  - **ASA-Klassifikation**: pre-operative assessment of the anaesthesia risk
  - **Abstand Anokutanlinie**: tumour location relative to the anocutaneous line
  - **Abstand Circumferentielle Resektionsebene**: CRM measurement
  - **Abstand Resektionsrand Aboral**: aboral safety margin
  - **MRT Mesorektale Faszie**: pre-operative MRI assessment
  - **Anastomoseninsuffizienz**: post-operative complication
- Procedures
  - **KRK-Operation**: organ-specific surgical interventions
  - **Stoma-Markierung**: pre-operative marking for stoma creation
- Specimen
  - **KRK-Specimen**: pathology specimen with KRK-specific details

**Implementation notes.**

- Data capture
  - **Temporal assignment**: pre-operative vs. post-operative observations
  - **Referential integrity**: a consistent link to the primary tumour diagnosis and to the operation is required
  - **Resection status**: R0/R1/R2 classification based on the resection margins
- Quality assurance
  - **Completeness check**: critical data fields are flagged as Must Support
  - **Value range validation**: restriction to medically meaningful value ranges
  - **Terminology consistency**: use of standardised coding systems

The KRK profiles enable complete and structured documentation of colorectal-cancer-specific data in accordance with the current medical standards and the oBDS.

<!-- source: TechnischeImplementierung/FHIR-Profile/Organspezifische-Module/MalignesMelanom/Index.page.md -->
### Malignes Melanom

The melanoma-specific profiles extend the MII KDS Onkologie module with special data elements for malignant melanoma in line with the requirements of the organ-specific modules of the ADT/GEKID basic documentation.

**Overview of the melanoma-specific profiles.**

<img src="https://raw.githubusercontent.com/medizininformatik-initiative/kerndatensatzmodul-onkologie/dev/implementation-guides/ImplementationGuide-2026.x-DE/Images/MII_Onko_Melanom_Module/MII_Onko_Melanom_Module.png" alt="MII Onkologie - melanoma module architecture and relationships">

**Melanoma-specific data elements.** The melanoma modules comprise the following specific clinical parameters:

- **Breslow-Tiefe**
  - vertical tumour thickness in millimetres
  - most important prognostic factor in melanoma
  - LOINC: 39092-1 "Breslow depth"
- **Ulzeration**
  - presence of an ulceration of the primary tumour
  - influences the TNM classification
  - SNOMED CT: 385324008 "Tumor ulceration present"
- **Sicherheitsabstand**
  - surgical horizontal safety margin at excision
  - documented in millimetres
  - quality indicator for the surgical therapy
- **LDH (Laktatdehydrogenase)**
  - serum marker for tumour burden
  - important for staging (M1c/M1d)
  - LOINC: 2532-0 "Lactate dehydrogenase[Enyzmatic activity/volume] in Serum or Plasma"

**Clinical use.** These profiles are typically used in the following scenarios:

1. **Primary diagnosis**: documentation of the initial tumour characteristics
2. **Staging**: Breslow depth and ulceration are essential for the TNM classification
3. **Treatment planning**: the safety margin is based on the Breslow depth
4. **Follow-up**: LDH as a follow-up parameter in metastatic melanoma

**Integration with the base profiles.** All melanoma-specific profiles:

- are based on the FHIR Observation resource
- reference the primary diagnosis via `focus`
- can be integrated into transaction bundles
- support the oBDS documentation requirements

**Example bundle.** A complete example bundle for melanoma patients is available as
[Melanom Bundle Example](Bundle-mii-exa-onko-melanom-bundle.html). The bundle demonstrates the use of all melanoma-specific profiles in a realistic clinical context.
