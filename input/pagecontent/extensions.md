<!-- markdownlint-disable MD041 -->
<!-- Split from the former combined profiles-and-extensions.md per the TF-KDS-agreed
     menu structure (one page per artifact type).
     German mirror: input/translations/de/pagecontent/extensions.md. -->
<!-- OPTIONAL-PAGE (0..1) — remove this marker when you KEEP the page; remove
     the page per docs/optional-pages.md when you don't. The convention check
     (M9) fails a release while this marker is present. -->

> **Optional page (0..1).** The KDS module menu lists this page as *optional*.
> Decide for your module: **keep** it — fill it in and delete this banner and
> the `OPTIONAL-PAGE` marker comment (in this file AND the German mirror) — or
> **remove** it, following the per-entry procedure in [`docs/optional-pages.md`](https://github.com/forschungsgruppe-digital-health/mii-kds-onko-ig-inoffiziell/blob/main/docs/optional-pages.md)
> of this repository. A release must not ship with this banner (convention
> check M9).
{: .ig-highlight .ig-highlight-grey}

### Extensions

This page lists the FHIR extensions defined by the **Onkologie** module
(naming convention `MII_EX_<Module>_<Name>`). Extensions carry information the
base resources and profiles cannot express; the profiles that use them are on
the [Profiles](profiles.html) page.

> [TODO: List and describe your module's extensions — or remove this page if
> your module defines none.]
{: .ig-highlight .ig-highlight-grey}

### Irradiation extensions of the radiotherapy profiles

The irradiation (Bestrahlung) extensions capture all information that is
relevant for individual irradiation units and that is not already covered by the
overarching Strahlentherapie procedure profile.

- Gesamtdosis (`mii-ex-onko-strahlentherapie-bestrahlung-gesamtdosis`)
- Einzeldosis (`mii-ex-onko-strahlentherapie-bestrahlung-einzeldosis`)
- Boost (`mii-ex-onko-strahlentherapie-bestrahlung-boost`)
- Seitenlokalisation (`mii-ex-onko-strahlentherapie-bestrahlung-seitenlokalisation`)
