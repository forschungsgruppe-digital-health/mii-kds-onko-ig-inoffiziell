# Code Systems - MII IG Kerndatensatz-Modul Onkologie v2026.0.3

* [**Table of Contents**](toc.md)
* **Code Systems**

## Code Systems

> **Optional page (0..1).** The KDS module menu lists this page as **optional**. Decide for your module: **keep** it — fill it in and delete this banner and the `OPTIONAL-PAGE` marker comment (in this file AND the German mirror) — or **remove** it, following the per-entry procedure in [`docs/optional-pages.md`](https://github.com/forschungsgruppe-digital-health/mii-kds-onko-ig-inoffiziell/blob/main/docs/optional-pages.md) of this repository. A release must not ship with this banner (convention check M9).

### Code Systems

This page describes the CodeSystems of the **Onkologie** module (naming convention `MII_CS_<Module>_<Name>`). The ValueSets built on them are described on the [Value Sets](value-sets.md) page.

**Important:** CodeSystem resources of external terminologies (e.g. ICD-10-GM, OPS, SNOMED CT) are **not** published in this module; they are obtained from the central KDS terminology service (SU-TermServ): [https://mii-termserv.de/](https://mii-termserv.de/).

> [TODO: List the module's own CodeSystems, or refer to the automatically generated artifact list — or remove this page if your module defines none.]

### Terminologies

#### ICD-10 GM

The International Statistical Classification of Diseases and Related Health Problems Version 10 German Modification (ICD-10-GM) is used to describe the primary diagnosis, for pre-existing conditions and to code the cause of death. The BfArM issues the ICD-10-GM annually on behalf of the Federal Ministry of Health. The current version is available here: [https://www.bfarm.de/DE/Kodiersysteme/Klassifikationen/ICD/ICD-10-GM/_node.html](https://www.bfarm.de/DE/Kodiersysteme/Klassifikationen/ICD/ICD-10-GM/_node.html)

Note: the oBDS provides for a cause-of-death report using ICD-10-GM. According to the BfArM, a cause of death should be coded with ICD-10-WHO (see here). The KDS module Onkologie follows the oBDS specification here and codes with ICD-10-GM.

#### ICD-O-3

The description of the site of the primary tumour is coded through ICD-O-3 Topographie. The morphological character is coded through ICD-O-3 Morphologie. The BfArM issues the ICD-O-3 on behalf of the Federal Ministry of Health. The current version is available here: [https://www.bfarm.de/DE/Kodiersysteme/Klassifikationen/ICD/ICD-O-3/_node.html](https://www.bfarm.de/DE/Kodiersysteme/Klassifikationen/ICD/ICD-O-3/_node.html)

#### OPS

The Operationen- und Prozedurenschlüssel (OPS) is used to code operative procedures carried out in the course of oncological diagnostics and therapy. The current version is available here: [https://www.bfarm.de/DE/Kodiersysteme/Klassifikationen/OPS-ICHI/OPS/_node.html](https://www.bfarm.de/DE/Kodiersysteme/Klassifikationen/OPS-ICHI/OPS/_node.html)

#### ATC

In the oBDS, medication is originally recorded as free text, whereby recording via ATC can be offered by the primary systems. In the FHIR profiles presented here we assume that the medication is primarily available coded in ATC. These are mainly medicinal products administered as antineoplastic therapies in the course of systemic therapy (chemotherapeutic, hormonal and immunotherapeutic agents). [https://www.bfarm.de/DE/Kodiersysteme/Klassifikationen/ATC/_node.html](https://www.bfarm.de/DE/Kodiersysteme/Klassifikationen/ATC/_node.html)

#### UNII (Unique Ingredient Identifier)

To support experimental and novel substances that do not yet have established ATC codes, the UNII system of the FDA (U.S. Food and Drug Administration) has been integrated. UNII codes allow the unambiguous identification of active substances at the molecular level and are particularly relevant for:

* Experimental substances in clinical trials (e.g. Iberdomide with UNII: 8V66F27X44)
* Novel immunomodulators and targeted therapies
* Substances in the early development phase, before ATC classification

The SystemischeTherapie MedicationStatement profile therefore supports dual coding with both ATC and UNII codes, in order to ensure complete coverage of all oncological therapy substances.

UNII database: [https://precision.fda.gov/uniisearch](https://precision.fda.gov/uniisearch) UNII CodeSystem in FHIR: [http://fdasis.nlm.nih.gov](http://fdasis.nlm.nih.gov)

#### TNM-Klassifikation

The TNM classification of malignant tumours is the system used worldwide for the clinical description of a tumour disease. The current 8th edition documents the current standards without gaps and is issued in collaboration with the Union for International Cancer Control (UICC).

#### CTCAE

The Common Terminology Criteria of Adverse Events is used in the Nebenwirkung profile to record adverse events of radiotherapy and systemic therapy.

[https://ctep.cancer.gov/protocoldevelopment/electronic_applications/ctc.htm](https://ctep.cancer.gov/protocoldevelopment/electronic_applications/ctc.htm)

#### SNOMED-CT

[https://www.bfarm.de/DE/Kodiersysteme/Terminologien/SNOMED-CT/_node.html](https://www.bfarm.de/DE/Kodiersysteme/Terminologien/SNOMED-CT/_node.html)

#### LOINC

LOINC (Logical Observation Identifiers Names and Codes) is an international system issued by the Regenstrief Institute for the unambiguous identification and coding of medical observations, in particular of laboratory examinations. Under § 355 (7) of the German Social Code Book V (SGB V), the BfArM is responsible for the further development of LOINC for German requirements and for providing translations for the electronic patient record. [https://www.bfarm.de/DE/Kodiersysteme/Terminologien/LOINC-UCUM/LOINC-und-RELMA/_node.html](https://www.bfarm.de/DE/Kodiersysteme/Terminologien/LOINC-UCUM/LOINC-und-RELMA/_node.html)

The current international LOINC version as well as the complete package with the individual translations is available at [http://loinc.org](http://loinc.org). A browser-based search is provided at search.loinc.org (registration required).

#### UCUM

Unified Code for Units of Measure (UCUM) is a system for coding units of measure. The coding system was developed with the aim of representing all units of measure used internationally in science, including in the laboratory-medical and pharmaceutical fields. The codes themselves represent units according to a defined notation, through which quantitative data and other numerical values can be exchanged unambiguously. UCUM has been maintained and issued in English by the Regenstrief Institute since 1999. The BfArM provides a value list with UCUM codes and descriptions of the codes for use in health applications in Germany. [https://www.bfarm.de/DE/Kodiersysteme/Terminologien/LOINC-UCUM/UCUM/_node.html](https://www.bfarm.de/DE/Kodiersysteme/Terminologien/LOINC-UCUM/UCUM/_node.html)

#### MedDRA

The scope of the Medical Dictionary for Regulatory Activities (MedDRA) covers pharmaceuticals, biologicals, vaccines and drug/device combinations.

[https://www.meddra.org/how-to-use/support-documentation/german/welcome](https://www.meddra.org/how-to-use/support-documentation/german/welcome)

