# Home - MII IG Kerndatensatz-Modul Onkologie v2026.0.3

* [**Table of Contents**](toc.md)
* **Home**

## Home

| | |
| :--- | :--- |
| *Official URL*:https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/ImplementationGuide/mii-ig-onko-de-v2026 | *Version*:2026.0.3 |
| Active as of 2026-03-29 | *Computable Name*:MII_IG_Onko_DE |

> **Written during migration - review before release.** This guide is an **unofficial try-run migration** of the MII Core Dataset module **Onkologie** v2026.0.3 onto the FGDH MII KDS module template. It is not an MII artefact, it is not endorsed by the Medizininformatik-Initiative, and nothing here is published. The normative specification remains the official MII guide.

### Introduction

This specification describes the FHIR representation of the Core Dataset (CDS) module **Onkologie** of the Medical Informatics Initiative (MII). It covers the module's use cases and the associated FHIR profiles, extensions and terminology resources in their normative form. The MII Core Dataset enables the standardized secondary use of routine clinical data for medical research.

The Onkologie module serves the recording of data points. In its first version the module follows the ADT/GEKID basic data set, which forms the basis for the national cancer registries. This covers diagnostic and histological parameters as well as information on treatment, tumour staging at the outset and over the course of the disease, and the recording of adverse events and the detection of metastases.

### Content and purpose of the modelling

The KDS module Onkologie has the goal of correctly representing the oncological data that arises in primary care and in cancer registry reporting, and of relating it to other data sources.

The focus of the first implementation version is the transfer of the registry data arising in the oBDS for secondary use with the FDPG and other projects in the context of PM4Onko. This first version therefore contains only those data points that are clinical-diagnostic or therapeutic in character. Administrative (e.g. report, reporting party) or person-identifying (person, tumour assignment) data points are outside the scope under consideration.

Besides the basic data set, the oBDS provides for the collection of organ-specific data fields. In the first implementation step the organ-specific modules (Mamma, Darm, Prostata, Melanom) were not implemented.

### Mapping to open data standards

The oncological basic data set contains ValueSets that were primarily defined by ADT/GEKID and have no direct relation to open data standards and terminologies such as SNOMED CT or LOINC. The coding of the answer options was adopted in the same way as it is also present in the primary systems. At the same time, this implementation guide provides a preliminary mapping of the fields and answer options onto SNOMED CT (and, where applicable, other terminologies) as a FHIR ConceptMap. Together with the BfArM, the federal state cancer registries are aiming to produce an official national mapping of the oBDS cancer registry data onto SNOMED CT by the end of 2024. As soon as that is officially published, the mapping contained here will be updated accordingly.

| | |
| :--- | :--- |
| Date | 2026-03-29 |
| Version | 2026.0.3 (CalVer`YYYY.n.n`) |
| Status | active |
| Realm | DE |

### Target audience

##### Implementers

Data Integration Centers (DIC), software developers and system architects building FHIR-based solutions.
 → see [Profiles](profiles.md) and [Logical Models](logical-models.md).

##### Researchers

Scientists using KDS data for medical research.
 → see [Guidance for Researchers](researcher-guidance.md).

### Contents

* **[Guidance](guidance.md)** — getting started and domain notes.
* **Conformance** — the KDS-wide conformance rules (requirements language, Must Support, handling missing data) are maintained centrally by the [Meta module](https://github.com/medizininformatik-initiative/kerndatensatz-meta/wiki/Conformance); the module-specific [Security and Privacy](security-and-privacy.md) considerations are part of this guide.
* **[Profiles](profiles.md)** and the further **[artifact pages](artifacts.md)** — the technical artifacts.
* **[Examples](examples.md)** — example instances.
* **[Dependencies](ImplementationGuide-mii-ig-onko-de-v2026.md)** — the ImplementationGuide resource with the dependency table, cross-version analysis and copyright statements.

### Related guides

This module is part of the MII Core Dataset; the other KDS modules and their dependencies are described at [medizininformatik-initiative.de](https://www.medizininformatik-initiative.de/).

> [TODO: Name your module's formal dependencies (see `dependencies` in `sushi-config.yaml`) and any related guides.]

More FHIR implementation guides can be found in the official **[FHIR IG Registry](https://fhir.org/guides/registry/)** (source: [`FHIR/ig-registry`](https://github.com/FHIR/ig-registry)).

### Imprint

This guide was created within the Medical Informatics Initiative and is subject, by its governance process, to the coordination procedure of the Interoperability Forum and the technical committees of HL7 Germany.

### Contact

Questions about this publication can be asked on the HL7 FHIR Zulip [chat.fhir.org](https://chat.fhir.org) in the `german/mi-initiative` stream, or on the MII Zulip [mii.zulipchat.com](https://mii.zulipchat.com/) in the `MII-Kerndatensatz` stream. Comments and issues are welcome as **Issues** on [GitHub](https://github.com/forschungsgruppe-digital-health/mii-kds-onko-ig-inoffiziell/issues).

* Thomas Debertshäuser, Berlin Institute of Health (Charité)
* Martin Boeker (DIFUTURE)
* Sylvia Thun, Berlin Institute of Health (Charité)
* Karoline Buckow, TMF – Technologie- und Methodenplattform für die vernetzte medizinische Forschung e.V.
* Franziska Klepka, TMF – Technologie- und Methodenplattform für die vernetzte medizinische Forschung e.V.

### Authors (in alphabetical order)

* Christian Gulden (BZKF / Erlangen)
* Jori Kern (DKFZ Heidelberg)
* Julian Saß, Berlin Institute of Health (Charité)
* Margaux Gatrio, Berlin Institute of Health (Charité)
* Lotte Schwiening, Berlin Institute of Health (Charité)
* Paul Müller, Berlin Institute of Health (Charité)
* Nina Haffer, Berlin Institute of Health (Charité)
* Sophie Klopfenstein, Berlin Institute of Health (Charité)
* Thomas Debertshäuser, Berlin Institute of Health (Charité)
* Yuan Peng, Institut für Medizinische Informatik und Biometrie (TU Dresden)

### Copyright and License

© 2021+ TMF e. V., Charlottenstraße 42, 10117 Berlin

This work is licensed under the [Creative Commons Attribution 4.0 International License (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0/).

For the usage rights of the underlying FHIR technology, see the FHIR base specification.

Some of the code systems used are published and maintained by other organizations; the copyright of the respective publishers applies.

### Disclaimer

The content of this document is public. Please note that parts of this document are based on FHIR version R4, which is copyrighted by HL7 International.

Although this publication was prepared with the greatest care, the authors cannot accept any liability for direct or indirect damage that may arise from the content of this specification.

