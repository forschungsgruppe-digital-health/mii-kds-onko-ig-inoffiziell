This profile describes a systemic or watchful-waiting therapy in oncology.

### Description

The oBDS maps several clinical concepts within Systemische Therapie

* Systemic therapies
    * Chemotherapie
    * Immuntherapie
    * Targeted Therapy
    * combination therapies of the therapies listed above
    * Hormontherapie
    * stem cell and bone marrow transplantation
* Watchful-waiting therapies
    * Watchful Waiting
    * Active Surveillance
    * Wait and see

For these individual therapies the oBDS records further data elements, which are represented here, among them:

- start and end date of the therapy
- relation to surgery and intention of the therapy
- the reason the therapy ended (whether successful or not)
- the therapy protocol used, with its substance combinations (as per the oBDS Umsetzungsleitfaden).

#### Category

- The MII Prozedur used here recommends representing the **category** by means of the OPS main categories transferred into SNOMED (https://www.medizininformatik-initiative.de/fhir/core/modul-prozedur/ValueSet/procedures-category-sct)
- The category used here, SNOMED `277132007 | Therapeutic procedure`, which corresponds to OPS category 8 ("Nicht-operative therapeutische Maßnahmen"), covers radiotherapy as well as nuclear medicine therapy and certain systemic therapies (e.g. chemotherapy and immunotherapy), while other systemic drug therapies (e.g. hormone therapy, targeted therapy) may also be coded under category 6 "Medikamente". It is therefore unspecific and not suitable for, say, filtering specifically for nuclear medicine therapies within a research question.

#### Code

- As the **code**, the MII Prozedur requires an OPS code or a SNOMED code.
- The medication-based systemic therapies are coded through different OPS categories depending on the kind of therapy.
- For the watchful-waiting therapies there are no OPS codes in the current catalogue.
- In the MII Prozedur, exactly one coding (OPS or SNOMED CT) SHOULD be used for exactly one therapy. Additional procedures are represented as individual Procedure resources.

#### Therapy protocol

- The specific therapy protocols used in the systemic therapy are documented as **usedCode**.
- The protocols are based on the [oBDS Umsetzungsleitfaden](https://plattform65c.atlassian.net/wiki/spaces/UMK/pages/15532385/Systemische+Therapie+SYST+Protokolle) and contain standardised substance combinations.
- Each protocol is documented with its characteristic designation (e.g. "FOLFOX", "R-CHOP", "AC") and the active substances it contains.
- Coding is done via the **MII CodeSystem Systemische Therapie Protokolle**, which covers all common oncological therapy protocols.
- Protocols that are not included can still be documented - here, however, harmonisation across the sites is decisive. Please therefore submit new protocols via [GitHub Issues](https://github.com/medizininformatik-initiative/kerndatensatzmodul-onkologie/issues).

#### Implementation recommendation

The points above result in the following coding recommendation for the systemic / watchful-waiting therapy from the oBDS:

- Category as a SNOMED code
    - Category for systemic therapies `18629005 | Administration of drug or medicament (procedure)`
    - Category for watchful-waiting therapies: none (no suitable parent concept; searching directly via the coding is recommended)
- Coding
    - Systemic therapy via OPS as follows. Note that the exact active substance is coded via ATC as part of the MedicationStatement resource. An additional documentation of the medication via
        - chemotherapy via OPS `8-54` or more specific
        - immunotherapy via OPS `8-54` or more specific (additional statement of )
        - stem cell therapy via OPS `8-86` or more specific
        - hormone therapy via OPS `6-xxx.y` (e.g. `6-009.0` for olaparib, oral, in prostate carcinoma)
    - Watchful-waiting therapy via SNOMED CT as follows
        - Watchful Waiting: SNOMED CT `373818007 | No anti-cancer treatment - watchful waiting (finding)`
        - Active Surveillance: SNOMED CT `424313000 | Active surveillance (regime/therapy)`
        - Wait and see: SNOMED CT `310341009 | Follow-up (wait and see) (finding)`

<!-- DERIVED:bridge source=Systemische-Therapie-Procedure.page.md gate=B -->
> **Written during migration - review before release.** Two statements in the coding recommendation break off incomplete in the source page: "Eine zusätzliche Dokumentation der Medikation über" ends without a continuation, and the parenthesis for immunotherapy is empty ("Zusatzangabe von )"). The wording was carried over unchanged; both places need to be completed before release.
{: .ig-highlight .ig-highlight-blue}

### Conformance

This profiling is compatible with the procedure profile of the ISiK Basismodule Stufe 4. https://simplifier.net/isik-basis-v4/isikprozedur

<!-- DERIVED:summary source=Systemische-Therapie-Procedure.page.md gate=B -->
> **Written during migration - review before release.** The source page listed every search parameter individually with an example query and a link into the FHIR base specification. Condensed here: mandatory (MUSS) are `_id`, `_profile`, `status`, `category`, `code`, `date`, `subject`, `patient`, `bodySite`, `dokumentationsdatum`, `durchfuehrungsabsicht`, `outcome` and `extension-intention`; `used-code` SHOULD be supported.
{: .ig-highlight .ig-highlight-blue}
