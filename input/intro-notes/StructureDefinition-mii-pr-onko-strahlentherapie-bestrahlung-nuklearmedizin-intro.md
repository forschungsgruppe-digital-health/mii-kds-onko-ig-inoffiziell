This profile describes "individual irradiations" (Einzelbestrahlungen) of nuclear medicine therapy in oncology. It is intended to cover both brachytherapies and the systemic administration of radioactive metabolites or comparable agents. The oncology profile is based on the procedure profile of the MII Basismodul Prozedur. Every brachytherapeutic intervention or systemic nuclear medicine therapy references an overarching radiotherapy procedure, which overarching information such as intention and outcome.

<!-- DERIVED:bridge source=NuklearmedizinischeTherapie-Procedure.page.md gate=B -->
> **Written during migration - review before release.** The last sentence of the paragraph breaks off incomplete in the source page ("... die übergreifende Angaben wie Intention und Outcome."). The wording was carried over unchanged; the statement needs to be completed before release.
{: .ig-highlight .ig-highlight-blue}

### Implementation recommendation

The points above result in the following coding recommendation for oBDS nuclear medicine treatment:

- Category as a SNOMED code
    - Category for nuclear medicine `399315003 | Radionuclide therapy (procedure)`
- Coding via OPS
    - Nuclear medicine therapy as OPS `8-53 Nuklearmedizinische Therapie` (or more precise where available)

### Conformance

These profilings are compatible with the procedure profile of the ISiK Basismodule Stufe 4. https://simplifier.net/isik-basis-v4/isikprozedur

<!-- DERIVED:summary source=NuklearmedizinischeTherapie-Procedure.page.md gate=B -->
> **Written during migration - review before release.** The source page listed every search parameter individually with an example query and a link into the FHIR base specification. Condensed here to the parameter names the source page declares as mandatory (MUSS): `_id`, `_profile`, `status`, `category`, `code`, `date`, `subject`, `patient`, `bodySite`, `dokumentationsdatum`, `durchfuehrungsabsicht`, `outcome`, `extension-intention`, `extension-stellung`, `extension-bestrahlung-applikationsart`, `extension-bestrahlung-strahlenart`, `extension-bestrahlung-zielgebiet`, `extension-bestrahlung-zielgebiet-Lateralitaet`, `extension-bestrahlung-boost`, `extension-bestrahlung-einzeldosis`, `extension-bestrahlung-gesamtdosis`.
{: .ig-highlight .ig-highlight-blue}
