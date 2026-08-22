This profile describes individual irradiations (Einzelbestrahlungen) within a radiotherapy in oncology. It describes radiotherapy in the narrower sense; brachytherapies and systemic nuclear medicine procedures are represented through the Nuklearmedizinische Therapien profile.
The oncology radiotherapy profile is based on the MII Prozedur module.

### Implementation recommendation

The points above result in the following coding recommendation for oBDS radiotherapy:

- Category as a SNOMED code
    - Category for radiotherapy `1287742003 | Radiotherapy (procedure)`
- Coding via OPS
    - Radiotherapy as OPS `8-52 Strahlentherapie`, or more precise where available

### Conformance

These profilings are compatible with the procedure profile of the ISiK Basismodule Stufe 4. https://simplifier.net/isik-basis-v4/isikprozedur

<!-- DERIVED:summary source=Bestrahlungstherapie-Procedure.page.md gate=B -->
> **Written during migration - review before release.** The source page listed every search parameter individually with an example query and a link into the FHIR base specification. Condensed here to the parameter names the source page declares as mandatory (MUSS): `_id`, `_profile`, `status`, `category`, `code`, `date`, `subject`, `patient`, `bodySite`, `dokumentationsdatum`, `durchfuehrungsabsicht`, `outcome`, `extension-intention`, `extension-stellung`, `bestrahlung-applikationsart`, `bestrahlung-strahlenart`, `bestrahlung-zielgebiet-lateralitaet`, `bestrahlung-boost`, `bestrahlung-einzeldosis`, `bestrahlung-gesamtdosis`.
{: .ig-highlight .ig-highlight-blue}
