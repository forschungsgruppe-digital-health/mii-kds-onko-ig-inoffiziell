<!-- markdownlint-disable MD041 -->
<!-- Migrated from the Simplifier guide page TNM-Klassifikation-Observation.page.md
     (MII IG Modul Onkologie 2026.x). German mirror:
     input/translations/de/intro-notes/StructureDefinition-mii-pr-onko-tnm-klassifikation-intro.md -->
This profile is the grouping profile for a TNM classification in oncology.

The profile carries the reference date and serves as the anchor point for all
further individual TNM observations at that point in time. The element
`hasMember` contains references to all associated individual TNM observations.

In addition, the element `value` codes the UICC staging that is derived from the
subordinate TNM observations.

<!-- DERIVED:summary source=TNM-Klassifikation-Observation.page.md gate=B -->
> **Written during migration - review before release.** Condensed from the source
> page's search-parameter list (one numbered entry with an example query per
> parameter): for this profile the search parameters `_id`, `_profile`, `status`,
> `code`, `subject`, `focus`, `encounter`, `date`, `method`, `has-member` and
> `derived-from` MUST be supported, also in combination. The source page also
> rendered this profile's mappings to the oncology logical model and to the
> [Einheitlicher onkologischer Basisdatensatz (oBDS)](https://basisdatensatz.de/basisdatensatz);
> those mappings are part of the profile itself.
{: .ig-highlight .ig-highlight-blue}
