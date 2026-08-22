# Logical Models - MII IG Kerndatensatz-Modul Onkologie v2026.0.3

* [**Table of Contents**](toc.md)
* **Logical Models**

## Logical Models

### Logical Models

The logical data models of the **Onkologie** module describe the domain dataset independently of its concrete FHIR representation.

The dataset is based on the onkologischer Basisdatensatz (oBDS, see [References](guidance.md)).

In the implementation the focus was placed on the conversion of the data points arising in the registry report data into FHIR resources for the FDPG for secondary use.

Report-related and person-related data of the oBDS are therefore not contained.

> **Written during migration - review before release.** The source page rendered each of the three logical models below as a generated element tree followed by a generated table of paths and definitions. Those renderings do not carry over to this guide: every logical model publishes its elements, data types and definitions in full on its own artifact page, linked from each sub-section.

#### Basis-Onkologie Logical Model

The base model is published as [Onkologie](StructureDefinition-mii-lm-onko.md).

Note that the logical model aims purely at representing the data elements and their description. The data types and cardinalities used are not to be regarded as binding. This is finally determined by the FHIR profiles. For every element within the logical model there is a 1:1 mapping onto an element of a concrete FHIR resource.

#### Organ-specific additional modules

The organ-specific modules (Mamma, Prostata, Kolorektales Karzinom, Malignes Melanom) extend the base Onkologie module by entity-specific data elements in line with the ADT/GEKID requirements: [OrganspezifischeZusatzmodule](StructureDefinition-mii-lm-onko-organspezifische-zusatzmodule.md).

The structure of all organ-specific modules is additionally formally defined in the logical model, which provides the FHIR mappings for all entity-specific data elements.

#### Modellvorhaben Genomsequenzierung

The Modellvorhaben Genomsequenzierung under §64e SGB V defines additional data elements for next-generation sequencing (NGS) in oncological patients: [MVGenomSeq Onkologie](StructureDefinition-mii-lm-mvgenomseq-onkologie.md).

