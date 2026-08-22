This profile describes the concrete medications that are documented for the oBDS within a systemic therapy.

Because the oBDS groups systemic and watchful-waiting therapy in one field, the data for systemic and watchful-waiting therapy is covered both by a FHIR procedure (systemic and watchful-waiting) and as a FHIR medication.

The statements on systemic oncological medication in the oBDS are with the following data points
In the medication profile of the Systemische Therapie this is specifically:

* start and end of the medication
* name of the treatment regimen
* active substances (ATC-coded)

<!-- DERIVED:bridge source=Systemische-Therapie-MedicationStatement.page.md gate=B -->
> **Written during migration - review before release.** The sentence "Die Angaben zur systemischen onkologischen Medikation im oBDS wird amit folgenden Datenpunkten" breaks off incomplete in the source page and contains a typo ("amit"). The wording was carried over unchanged; the passage needs to be corrected before release.
{: .ig-highlight .ig-highlight-blue}

### Conformance

This profiling is compatible with the procedure profile of the ISiK Basismodule Stufe 4. https://simplifier.net/isik-medikation-v4/isikmedikationsinformation

This profiling is currently *not* compatible with the EPA MedicationStatement, because there MedicationStatement.medication explicitly requires a reference to a Medication resource, whereas the Onkologie MedicationStatement at hand prefers coding via ATC. https://simplifier.net/epa-medication/epamedicationstatement

<!-- DERIVED:summary source=Systemische-Therapie-MedicationStatement.page.md gate=B -->
> **Written during migration - review before release.** The source page listed every search parameter individually with an example query and a link into the FHIR base specification. Condensed here to the parameter names the source page declares as mandatory (MUSS): `_id`, `_profile`, `medicationCodeableConcept`, `partOf` and `effective`.
{: .ig-highlight .ig-highlight-blue}
