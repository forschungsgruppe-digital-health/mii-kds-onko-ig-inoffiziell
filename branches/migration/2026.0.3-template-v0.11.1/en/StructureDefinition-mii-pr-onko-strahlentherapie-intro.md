This profile describes a radiotherapy (Strahlentherapie) in oncology. The oncology radiotherapy profile is based on the MII Prozedur module. It therefore adopts the mandatory use of OPS as the coding for the kind of procedure. Because the details of the procedure are held in the individual irradiation (Bestrahlung) elements, the OPS code for radiotherapy is what is to be coded here.

The MII Prozedur module already has a [Durchführungsabsicht](https://www.medizininformatik-initiative.de/fhir/core/modul-prozedur/StructureDefinition/Durchfuehrungsabsicht) extension bound to SNOMED CT codes. Since the intention of the radiotherapy is, however, captured in the oBDS through an oBDS-specific answer set, the procedure was extended by an additional element "Intention". In the same way, the relation to any surgery (e.g. adjuvant/neoadjuvant) is captured through the extension element "Stellung".

The specific details of the radiotherapy are subdivided into individual irradiations (Bestrahlungen) and reported there. Each irradiation is captured as an extension.

Complications of the radiotherapy are not coded as `Procedure.complication` or `Procedure.complicationReference`; as with systemic therapy they are captured in a separate AdverseEvent resource that references the radiotherapy resource. Note that a reference to the radiotherapy resource points unspecifically to the complete radiotherapy and not to individual irradiations.

The reason the therapy ended (whether successfully or not) is coded via `Procedure.outcome`.

### Structure

There are several reasons for the decision to implement the irradiation data as extensions.

1. The oBDS data structure provides for one overall radiotherapy period with start and end plus one overall intention and one relation-to-surgery data point. All further structured treatment information on the irradiation (type of radiation, location, dose, boost, etc.) is to be coded individually in a "Bestrahlung" element.
2. The MII Prozedur requires that every procedure carries exactly one code, either OPS or SNOMED CT.
3. The US FHIR data model mCODE maps the relevant data points into extensions. It should be noted, however, that mCODE makes no distinction between an overarching radiotherapy and a subordinate irradiation. In return, mCODE does provide detailed information on the size of the target volume.

An alternative implementation was also discussed: leaving the overarching radiotherapy as a profile conformant to the MII Prozedur and profiling the subordinate irradiations from the regular `Procedure`. That profiling was rejected because of the larger number of resources it requires and the anticipated difficulty of populating the OPS/SNOMED code correctly.

### Category and codes

#### Category

- The MII Prozedur used here recommends representing the **category** by means of the OPS main categories transferred into SNOMED (https://www.medizininformatik-initiative.de/fhir/core/modul-prozedur/ValueSet/procedures-category-sct)
- The category used here, SNOMED `277132007 | Therapeutic procedure`, which corresponds to OPS category 8 ("Nicht-operative therapeutische Maßnahmen"), covers radiotherapy as well as nuclear medicine therapy and certain systemic therapies (e.g. chemotherapy and immunotherapy), while other systemic drug therapies (e.g. hormone therapy, targeted therapy) may also be coded under category 6 "Medikamente". It is therefore unspecific and not suitable for, say, filtering specifically for nuclear medicine therapies within a research question.

#### Code

- As the **code**, the MII Prozedur requires an OPS code or a SNOMED code.
- OPS contains codings for radiotherapy (`8-52`) and nuclear medicine treatment (`8-53`) with detailed sub-codings. In the oBDS itself, however, radiotherapy and nuclear medicine are not coded with OPS; the oBDS follows a cancer-registry-specific coding of location, mode of application and type of radiation plus further data points.
- In the MII Prozedur, exactly one coding (OPS or SNOMED CT) SHOULD be used for exactly one therapy. Additional procedures are represented as individual Procedure resources.

#### Implementation recommendation

The points above result in the following coding recommendation for oBDS radiotherapy:

- Category as a SNOMED code
    - Category for radiotherapy `1287742003 | Radiotherapy (procedure)`
    - Category for nuclear medicine `399315003 | Radionuclide therapy (procedure)`
- Coding via OPS
    - Radiotherapy as OPS `8-52 Strahlentherapie` (or more precise where available)
    - Nuclear medicine therapy as OPS `8-53 Nuklearmedizinische Therapie` (or more precise where available)

### Migration of the target area (Zielgebiet) from oBDS 2014 to 2021

The radiotherapy target-area coding changed fundamentally between oBDS 2014 and 2021:

<img src="https://raw.githubusercontent.com/medizininformatik-initiative/kerndatensatzmodul-onkologie/dev/implementation-guides/ImplementationGuide-2026.x-DE/Images/MII_Onko_Strahlentherapie_Zielgebiet_Migration/MII_Onko_Strahlentherapie_Zielgebiet_Migration.png" alt="oBDS 2014 → 2021 Strahlentherapie Zielgebiet Migration" style="max-width: 100%; height: auto;">

#### Migration strategy

- **oBDS 2014**: used combined codes with suffixes (`+` with lymph nodes, `-` without lymph nodes, `.` without further specification)
- **oBDS 2021**: separates organs (sections 1-8) and lymphatic drainage regions (section 9) into separate irradiations
- **Example**: the oBDS 2014 code `"3.1.+"` (breast with lymph nodes) becomes two separate codes: `#3.1` (breast) and `#9.3` (axillary lymph nodes)
- **ValueSet**: supports both CodeSystems for backward compatibility

### Conformance

This profiling is compatible with the procedure profile of the ISiK Basismodule Stufe 4. https://simplifier.net/isik-basis-v4/isikprozedur

<!-- DERIVED:summary source=Strahlentherapie-Procedure.page.md gate=B -->
> **Written during migration - review before release.** The source page listed every search parameter individually with an example query and a link into the FHIR base specification. Condensed here to the parameter names the source page declares as mandatory (MUSS): `_id`, `_profile`, `status`, `category`, `code`, `date`, `subject`, `patient`, `bodySite`, `dokumentationsdatum`, `durchfuehrungsabsicht`, `outcome`, `extension-intention`, `extension-stellung`, `extension-bestrahlung-applikationsart`, `extension-bestrahlung-strahlenart`, `extension-bestrahlung-zielgebiet`, `extension-bestrahlung-zielgebiet-Lateralitaet`, `extension-bestrahlung-boost`, `extension-bestrahlung-einzeldosis`, `extension-bestrahlung-gesamtdosis`.
{: .ig-highlight .ig-highlight-blue}
