# Extensions - MII IG Kerndatensatz-Modul Onkologie v2026.0.3

* [**Table of Contents**](toc.md)
* **Extensions**

## Extensions

> **Optional page (0..1).** The KDS module menu lists this page as **optional**. Decide for your module: **keep** it — fill it in and delete this banner and the `OPTIONAL-PAGE` marker comment (in this file AND the German mirror) — or **remove** it, following the per-entry procedure in [`docs/optional-pages.md`](https://github.com/forschungsgruppe-digital-health/mii-kds-onko-ig-inoffiziell/blob/main/docs/optional-pages.md) of this repository. A release must not ship with this banner (convention check M9).

### Extensions

This page lists the FHIR extensions defined by the **Onkologie** module (naming convention `MII_EX_<Module>_<Name>`). Extensions carry information the base resources and profiles cannot express; the profiles that use them are on the [Profiles](profiles.md) page.

> [TODO: List and describe your module's extensions — or remove this page if your module defines none.]

### Irradiation extensions of the radiotherapy profiles

The irradiation (Bestrahlung) extensions capture all information that is relevant for individual irradiation units and that is not already covered by the overarching Strahlentherapie procedure profile.

* Gesamtdosis (`mii-ex-onko-strahlentherapie-bestrahlung-gesamtdosis`)
* Einzeldosis (`mii-ex-onko-strahlentherapie-bestrahlung-einzeldosis`)
* Boost (`mii-ex-onko-strahlentherapie-bestrahlung-boost`)
* Seitenlokalisation (`mii-ex-onko-strahlentherapie-bestrahlung-seitenlokalisation`)

