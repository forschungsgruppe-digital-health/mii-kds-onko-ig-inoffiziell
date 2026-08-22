<!-- markdownlint-disable MD041 -->
<!-- Source: kerndatensatz-basis input/pagecontent/guidance.md (MII module page set).
     "Guidance" overview page. The sub-page structure follows kerndatensatz-basis.
     German mirror: input/translations/de/pagecontent/guidance.md — keep both in
     step. The domain sections below carry the narrative of the source guide's
     top-level pages and of its "Anwendungsfälle / Informationsmodell" chapter. -->

This section collects the domain guidance for implementing and using the
**Onkologie** module.

### General Implementation Guidance

* **[Datasets and Descriptions](logical-models.html)** — the module's data
  elements, described as logical models. (This entry shares its target with
  *Artifacts → Logical Models*; neither Artifacts-Summary anchor is usable as
  a link target — see
  [`docs/page-structure.md`](https://github.com/forschungsgruppe-digital-health/mii-kds-onko-ig-inoffiziell/blob/main/docs/page-structure.md) in this repository.)
* **[UML Diagrams](uml-diagrams.html)** — visual representation of the data
  models and their relationships.

### Audience-Specific Guidance

* **[Guidance for Researchers](researcher-guidance.html)** — for researchers
  using the module's data.
* **[Guidance for Implementers](implementer-guidance.html)** — technical
  guidance for DIC implementers.

<!-- source: KontextimGesamtprojektBezgezuanderenModulen.page.md -->
### Context within the overall project and relations to other modules

The KDS module Onkologie makes comprehensive use of the base modules of the MII.

* The oncological primary diagnosis is based on the MII module
  **[Diagnose](https://simplifier.net/mii-basismodul-diagnose-2024)**
* The therapy documentation of operations, radiotherapy and general information
  on systemic therapies is based on the MII module
  **[Prozedur](https://simplifier.net/mii-basismodul-prozedur-2024)**
* The specific coding of active substances as part of the systemic therapy is
  based on the MII module
  **[Medikation](https://simplifier.net/mii-basismodul-medikation-2024)**.

Because the data collection for the oBDS is based on the cancer registry
reports, a representation via the modules named above is only partly possible.

For a more far-reaching linking of the oncological registry data the following
KDS modules are particularly relevant.

* [Pathologiebefundbericht](https://simplifier.net/medizininformatikinitiative-modulpathologie)
* [Biobank](https://simplifier.net/medizininformatikinitiative-modulbiobank)
* [Molekulargenetischer Befundbericht](https://simplifier.net/medizininformatikinitiative-modulomics)
* [Bildgebung](https://simplifier.net/Medizininformatik-Initiative-Modul-Bildgebung)
  (not yet implemented, integration planned for version 2027)

In the long term a close interlocking with the modules named above is planned.
In the first versions 2025 and 2026 it is, however, completely optional. There
is one main reason for this: the generation of FHIR resources from other modules
partly requires the existence of data that is not part of the oBDS in that form.
(Example: on creation, the Bioprobe module mandatorily requires the availability
to be stated.) Because FHIR resources can at present (as of July 2025) not yet
be delivered from primary systems across the board, and because not every DIZ
site is necessarily able to generate all KDS modules, in whole or in part, in
ETL pipelines, the use of other MII modules is intended but optional.

Beyond that, the KDS module Onkologie forms the basis for the
[KDS-Modul Molekulares Tumorboard](https://simplifier.net/mii-erweiterungsmodul-molekulares-tumorboard),
in which deeper oncologically relevant questions such as guideline treatment,
next-generation sequencing and personalized therapies can be represented in
detail. Required adjustments (e.g. a more precise adaptation of the therapy
recommendations) were specified for the MTB module and adopted into version
v2026.

### Use cases and information model

<!-- DERIVED:bridge source=AnwendungsflleInformationsmodell/Index.page.md gate=B -->
> **Written during migration - review before release.** The source guide opened
> this chapter with a page that was deliberately left blank. The two
> sub-sections below carry the chapter's content: the example scenario that
> shows how the module is applied, and the UML overviews of the information
> model. The data elements of the dataset itself are described on
> [Logical Models](logical-models.html).
{: .ig-highlight .ig-highlight-blue}

<!-- source: AnwendungsflleInformationsmodell/BeschreibungvonSzenarienfrdieAnwendungderModule.page.md -->
#### Description of scenarios for applying the modules

The oBDS serves as the basis for the cancer registry reports to the federal
state cancer registries.

The present profiling of the oBDS has the ambition of making the data that
arises in cancer registration usable for other fields of research.

The FHIR representation of the example below makes clear that information on
imaging procedures, on detailed treatment and irradiation schemes and on genetic
variants exists in more detailed form outside the cancer registry data. The
present FHIR profiling thereby makes an important contribution to incorporating
as much information as possible for oncological research.

##### Application scenario of a guideline-conform treatment

Disclaimer: The course of therapy corresponds to one possible guideline-conform
therapy; the data and the course are constructed for test purposes, similarities
with actual courses of disease are coincidental.

###### Textual representation of the example course of therapy

* Kim Musterperson, born 14.03.1956

* 10.06.2021 CT abdomen with contrast medium: suspected peritoneal
  carcinomatosis, ascites throughout the abdominal cavity, mass in the right
  ovary. Mesenteric retroperitoneal lymph node metastases, suspected liver
  metastasis

* 15.06.2021 Ascites puncture: with malignant tumour cells. Cytologically
  possible ovarian carcinoma.
* 22.06.2021 CT thorax: no indication of metastases.

* Tumour board 25.06.2021: Unambiguous CT correlate and cytological initial
  diagnosis of ovarian carcinoma.
    * Neoadjuvant chemotherapy with 3 cycles of Carboplatin/Paclitaxel, interval
      debulking in the further course.
        * 05.07.21-25.07.21 C1 Carboplatin AUC5 d1, Paclitaxel 175 mg/m2, d1,
          repeat d21
        * 26.07.21-15.08.21 C2 Carboplatin AUC5 d1, Paclitaxel 175 mg/m2, d1,
          repeat d21
        * 16.08.21-05.09.21 C3 Carboplatin AUC5 d1, Paclitaxel 175 mg/m2, d1,
          repeat d21
* 15.09.21 CT thorax/abdomen: assessment
increasing peritoneal carcinomatosis, retroperitoneal lymph nodes suspicious for
metastases. Suspected constant liver metastasis

* 16.09.21 Tumour board:
Clear tumour progression. Operation for histological confirmation already
planned, aim for optimal debulking.

* 30.09.2021 Operation
Interval debulking by longitudinal laparotomy, tumour resection by
hysterectomy, bilateral adnexectomy, and atypical liver segment resection
(segments II and V). Postoperatively: R0.

* Pathology report
    * Histology: resection specimen of 30.09.2021
    * Neoplasm of the ovary (status post neoadjuvant therapy) (ICD-10-C56) ovary
      NOS (ICD-O-C56.9) examined material: resection specimen WHO type: serous
      adenocarcinoma (ICD-O M-8441/3)
    * Local tumour extent: ovarian tumour on the left with a maximum size of
      2.2 cm and a tumour-infiltrated capsule with evidence of tumour cells on
      the ovarian surface, proportion of vital tumour cells approximately 80 %.
    * UICC classification (8th edition): ypT3c. pM1b (HEP) L1. V0. Pn0 FIGO: IVB
    * Immunohistochemistry: (example for a few markers, a real report contains
      many more) Occasional strong nuclear expression of the progesterone
      receptor. Positivity for P16 in the tumour. The proliferation index by
      MIB-1 is at most 38 %. Microscopy: partial evidence of mucin.
    * Comment: The immunohistochemical marker profile fits a high-grade serous
      adenocarcinoma of the ovary (status post neoadjuvant chemotherapy)

* Tumour board 25.10.2021:
    * Macroscopic complete resection achieved through the operation.
    * However, progression under neoadjuvant therapy.
    * Therefore switch to Carboplatin/Gemcitabine
    * Presentation to human genetics recommended

* Systemic therapy
    * 08.11.21-28.11.21 C1 Carboplatin AUC 4 d1, Gemcitabine 1000mg/m2 d1+d8
      repeat d22
    * 29.11.21-19.12.21 C2 Carboplatin AUC 4 d1, Gemcitabine 1000mg/m2 d1+d8
      repeat d22
    * 20.12.21-09.01.22 C3 Carboplatin AUC 4 d1, Gemcitabine 1000mg/m2 d1+d8
      repeat d22
* 15.01.22 CT: abdomen:
    * Regression of the known peritoneal carcinomatosis
    * Liver without clear indication of metastasis; status post atypical liver
      segment resection, most likely scarring changes
    * Assessment: regressive findings, status post interim operative debulking

* 20.01.22 Tumour board:
    * Maintenance therapy with Niraparib in BRCA wild type
    * Restaging in 3 months with CT thorax/abdomen and tumour markers
* 25.01.22 Start of Niraparib 300mg d1-28 repeat d28

###### Graphical representation of the example course of therapy

<img src="https://raw.githubusercontent.com/medizininformatik-initiative/kerndatensatzmodul-onkologie/refs/heads/dev/implementation-guides/ImplementationGuide-2026.x-DE/Images/MII_Onko_Example_Patient.svg" width="100%">

The image file can be viewed and downloaded separately
[here (Github)](https://raw.githubusercontent.com/medizininformatik-initiative/kerndatensatzmodul-onkologie/refs/heads/dev/implementation-guides/ImplementationGuide-2026.x-DE/Images/MII_Onko_Example_Timeline.svg)
for better display (provided as `.svg`).

<!-- source: AnwendungsflleInformationsmodell/UML.page.md -->
#### UML

The following UML diagram shows the implemented contents and cardinalities of
the oBDS that were implemented by the KDS module Onkologie in accordance with
its specifications.

<div style="width: 100%; overflow-x: auto;">
<img src="https://raw.githubusercontent.com/medizininformatik-initiative/kerndatensatzmodul-onkologie/dev/implementation-guides/ImplementationGuide-2026.x-DE/Images/onco_merged.svg" style="width: 100%; height: auto;" />
</div>

The image file can be viewed and downloaded separately
[here (Github)](https://raw.githubusercontent.com/medizininformatik-initiative/kerndatensatzmodul-onkologie/dev/implementation-guides/ImplementationGuide-2026.x-DE/Images/onco_merged.svg)
for better display (provided as `.svg`).

##### Organ-specific modules — UML diagrams

In addition to the overarching UML diagram, every organ-specific module has its
own detailed architecture diagrams:

- **Mamma module** — breast-carcinoma-specific profiles and their relationships
- **Prostata module** — prostate-carcinoma-specific profiles and their
  relationships
- **KRK module** — colorectal-carcinoma-specific profiles and their
  relationships
- **Malignes Melanom module** — malignant-melanoma-specific profiles and their
  relationships

<!-- source: Abweichungen-zum-oBDS.page.md -->
### Deviations from the oBDS

The present implementation guide describes an implementation of the oBDS in
FHIR. A pure 1:1 representation of the complete dataset is sensible neither in
content nor technically. Here are the most important deviations:

#### Contents

The KDS module Onkologie contains those groups of the oBDS that mainly comprise
clinical-diagnostic and therapeutic data points.

Several groups were therefore **not** implemented in FHIR. This comprises:

- The person-related groups
    - Group 3: patient master data
    - Group 4: reporting-party master data
    - Group 7: submitter
    - Group 22: surgeon
    - Group 25: additional contacts

- the administrative and report-related groups
    - Group 1: report
    - Group 2: centre
    - Group 21: remarks

The organ-specific modules were not part of the first profiling, but have been
part of the Onkologie module since version 2026.
- These are:
    - Modul Prostata
    - Modul Mamma
    - Modul Melanom
    - Modul Kolon

#### Cardinalities

The oBDS has mainly been optimized for data reporting to the cancer registries.

In the first versions the cardinalities were largely adopted from the oBDS, but
are in part set "more softly" in order to gain access to a broader data basis,
especially as a first step.

#### Integration of terminologies and code systems

In order to guarantee the evaluability by the Forschungsdatenportal Gesundheit
(FDPG), the statement of the medication in systemic therapy requires a coding by
means of ATC. Free text remains possible as an additional statement.

#### Validation

The oBDS XML schema 3.0.2 provides for a number of validations that check data
quality and completeness. These are technically **not** implemented in the first
version. It can be assumed that the oBDS data in the primary systems of tumour
documentation are validated at least to the extent that an export into the XML
format is possible. Further validations (e.g. mutually exclusive data fields)
could be carried out in the future if required. This would be necessary if the
present KDS module were to serve, beyond its current purpose, as a basis for
data collection for primary systems.

#### Contents of the modules and profiles

In the oBDS the data fields are bound to the reporting structure. Groups that
have different cardinalities are frequently held in different groups. For
example, Tumorkonferenz and Therapieempfehlungen are in two different groups,
because one tumour conference can refer to several therapy recommendations.
Both groups can, however, be represented without difficulty in the FHIR resource
CarePlan, so that these were merged into one FHIR profile. Important changes in
excerpt below:

- the diagnosis contains parts of the histology group (ICD-O topology, ICD-O
  morphology)
- the Tumorkonferenz group was merged into the group
  Tumorkonferenz/Therapieempfehlung
- the Allgemeiner Leistungszustand can be coded both as ECOG and as Karnofsky
  (an original merging of the data points was discarded after the commenting
  phase).

<!-- source: BezugZuNationalenStandards.page.md -->
### Relation to national standards

The described Basisdatensatz Onkologie is a dataset that follows the oBDS and
thereby the German cancer registry data models.

---

##### Informationssysteme im Krankenhaus (ISiK)

ISiK describes a standard that is to be used by hospital systems for the
exchange among each other. ISiK itself contains few content-related requirements
and bindings that are relevant for the collection of oncological data. Because
of its growing importance in the hospital sector, conformity was attended to
during the profiling.

- The Diagnose and Prozedur profiles are part of the ISiK base modules
  <https://simplifier.net/guide/isik-basis-v4?version=current>
- Medikation is part of the ISiK medication module
  <https://simplifier.net/guide/isik-medikation-v4?version=current>

##### Medizinische Informationsobjekte (MIOs)

MIOs are relevant as structured data elements in the context of the electronic
patient record (ePA). The first large building block is to be a provision of
structured medication data. At the time the profiling was created (Jan–Apr 2024)
the profiles for Medikation / Medikationsplan were still being profiled and could
therefore not be taken into account in the present specification. It should be
noted, however, that the medication list and the tumour documentation are
currently still separate ecosystems. A long-term harmonization of comparable
profiles is being coordinated and driven forward from 2025 by the KIG of the
gematik. The implementation guide for the "ePA Medication Service" is here:
<https://simplifier.net/guide/medication-service?version=1.1.0>
Link to the concrete profile EPA MedicationStatement
<https://simplifier.net/epa-medication/epamedicationstatement>

---

#### National preliminary work

##### German OncoLogical Data Standard (GOLD)

The GOLD project was initiated by Vision-Zero e.V. and aims at representing a
complete oncological patient journey. The data model and the associated profiles
were derived from existing data models from care, research and industry in
Germany and abroad. Proposals for the harmonization of various specifications
were developed and agreed with German experts. The first FHIR profiles, with a
focus on diagnosis and classifications such as the TNM classification, as well
as imaging and course of disease, have been incorporated into several further
projects, e.g. the Basisprofile Onkologie of HL7 Deutschland and the MII module
Befunde bildgebender Verfahren. The current version can be found here:
<https://vision-zero-oncology.github.io/GOLD/>

##### Basisprofile Onkologie of HL7 Deutschland

In the Basisprofile Deutschland, profiling work was delivered in particular in
2022 as a basis for the uniform use of FHIR resources in the oncological sector.
<https://simplifier.net/BasisprofileOnkologie>
Work on the Basisprofile has been dormant since the commenting phase in 2022.
The Basisprofile Onkologie of HL7 now refer to the present KDS module Onkologie
of the MII.

##### Deutsches Konsortium für Translationale Krebsforschung

The internal data model of the DKTK uses oBDS data prepared from the tumour
documentation systems in FHIR format as an exchange medium (available at
<https://simplifier.net/oncology>). The original information model of the KDS
module Onkologie was strongly oriented towards the DKTK model. The profiling
differs, however, in that the DKTK profiles are self-contained, whereas an MII
module is intended to work as well as possible with the MII base modules
(above all Diagnose, Prozedur, Medikation) and with already existing KDS modules.
One of the main modelling decisions was therefore the use of the MII Diagnose
and MII Medikation, as well as the representation of operations, radiotherapies
and systemic / watchful-waiting therapies as MII Prozeduren.

##### Modellvorhaben Genomsequenzierung

The Modellvorhaben Genomsequenzierung under §64e SGB V provides for the
collection of a data set around a next-generation sequencing (NGS) of
oncological patients. The data set contains information on the diagnostic and
therapeutic history, the molecular-genetic description of the tumour, the
recommendations on study participation and systemic therapies, as well as
follow-up information on therapies actually carried out and on therapy response
/ vital status.

There is a similar data set for rare diseases, which will in future be
represented in the module Seltene Erkrankungen.

A mapping of the data elements onto the MII KDS is currently being worked on.

<!-- DERIVED:summary source=BezugZuNationalenStandards.page.md gate=B -->
> **Written during migration - review before release.** The source page rendered
> the Modellvorhaben data set as a generated element tree and the mapping as a
> generated table excerpt. Neither carries over to this guide: the data set is
> published as the logical model
> [MVGenomSeq Onkologie](StructureDefinition-mii-lm-mvgenomseq-onkologie.html)
> and the mapping as the ConceptMap
> [mii-cm-onkologie-to-mvgenomseq](ConceptMap-mii-cm-onkologie-to-mvgenomseq.html),
> each of which renders its full content on its own artifact page.
{: .ig-highlight .ig-highlight-blue}

<!-- source: BezugZuInternationalenStandards.page.md -->
### Relation to international standards

The described Basisdatensatz Onkologie is a dataset that rests on the oBDS and
thereby on the German cancer registry data models.

In the FHIR modelling, the FHIR profiling of other national oncological data
models from abroad was considered.

---

#### mCODE, USA

<https://hl7.org/fhir/us/mcode/>
The model is currently in its fourth iteration. The data elements it contains
can be divided into:

- patient information
- characterization of the disease
- state of health
- genomic data
- treatment information
- outcomes

##### Influences of mCODE on the data modelling

1. mCODE captures the individual components of the **TNM classification** via
   individual FHIR Observations, which are then grouped by means of a Stage
   Group resource. Besides TNM there is a number of important tumour staging
   classifications / scores that were explicitly created as FHIR profiles. We
   likewise recommend this approach in the ongoing profiling of the
   organ-specific modules of the oBDS (e.g. Gleason score)
2. mCODE codes the details of individual **irradiation units** via extensions.
   With CodeX Radiation Therapy there is a module derived from mCODE that deals
   explicitly with the modelling of irradiation schemes
   (<https://hl7.org/fhir/us/codex-radiation-therapy/>) — this is, however,
   considerably more detailed than the oBDS.
3. mCODE captures the genomic data with the HL7 FHIR Genomics Report, which was
   developed by the HL7 FHIR Clinical Genomics Working Group. In its current
   version the oBDS contains only sparse information on **genetic variants**. If
   detailed information on the molecular-genetic investigations, variants and
   therapeutic consequences is available at the site, the Molekulargenetischer
   Befundbericht of the MII, which is likewise based on the HL7 Genomics Report,
   can be used.
4. Representation of further classifications (above all for further grading and
   staging systems)

##### Decisive differences mCODE - oBDS

1. mCODE and the data elements referenced by mCODE (comorbidities, vital
   parameters, ethnicity etc.) are based to a large extent on the US-American
   FHIR base modules from us-core and are therefore not directly applicable in
   Germany.
2. In the data modelling, clinical decision-making such as the recommendations
   of an interdisciplinary tumour board is not represented.
3. The intention is to work with actual treatment data, which is why many FHIR
   resources are more detailed than the data situation in the oBDS allows. Exact
   times of drug administration and dose statements, for example, are not part of
   the oBDS, but are part of mCODE.
4. Overall, mCODE is optimized for a prospective data collection, and can be
   continuously updated during treatment. In this the basic structure differs
   considerably from the retrospectively documented German cancer registry data,
   whose contents can vary by report type (diagnosis, operation, course of
   disease etc.).

---

#### OSIRIS, France

The French common data model "Interoperability and data sharing of clinical and
biological data in oncology" (OSIRIS) comprises two independent core datasets: a
clinical and a genomic part. A third part with a dataset on imaging and
radiotherapy is currently being worked on. Because the focus of the oBDS is on
the clinical data, commonalities and differences with the clinical dataset are
to be summarized briefly here.

The OSIRIS dataset models the temporal representation above all around so-called
"Tumor Events". Tumor Events are either initial diagnoses or follow-up
observations.

Further information can be read at:
<https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8140800/>

English version of the dataset available at:
<https://github.com/InstitutNationalduCancer/OSIRIS/blob/v1.1.05/documentation/ModeleCliniqueOSIRIS-english_version.pdf>

<https://github.com/InstitutNationalduCancer/OSIRIS/blob/master/documentation/MPD_OSIRIS_model_v1.1.05.png>

<!-- source: Referenzen.page.md -->
### References

The KDS module Onkologie is based on the onkologischer Basisdatensatz (oBDS) in
the version published in the Bundesanzeiger in 2021. The contents are publicly
available.

* Website of the oBDS with all relevant data fields, descriptions and answer
  options: <https://basisdatensatz.de/basisdatensatz>
* The oBDS: XML schema in version 3.03; here in particular the statements on the
  hierarchy, the field IDs and data validation
    * current version: <https://basisdatensatz.de/xml/oBDS_v3.0.3.xsd>
    * older versions available at <https://basisdatensatz.de/xml/>

* Confluence-based implementation guide of the Krebsregister-Plattform §65c
  <https://plattform65c.atlassian.net/wiki/spaces/UMK/overview>, in particular:
    * <https://plattform65c.atlassian.net/wiki/spaces/UMK/pages/15532576/Datenmodell>
      for the general data model
    * <https://plattform65c.atlassian.net/wiki/spaces/UMK/pages/15532143/Meldungsinhalte>
      and all sub-pages for detailed views and data model diagrams of the
      individual report contents

Older preliminary work on representing the oBDS as an information model exists
on the ART-DECOR platform, which currently does not fully reflect the present
state. It can be reached
[here](https://art-decor.org/art-decor/decor-datasets--mide-?id=2.16.840.1.113883.3.1937.777.24.1.1&effectiveDate=2018-06-05T12%3A44%3A12&conceptId=2.16.840.1.113883.3.1937.777.24.2.62&conceptEffectiveDate=2018-06-06T06%3A13%3A32).

---
For the KDS-wide conformance requirements see the
[Conformance rules of the Meta module](https://github.com/medizininformatik-initiative/kerndatensatz-meta/wiki/Conformance);
for the technical artifacts see [Profiles](profiles.html).
