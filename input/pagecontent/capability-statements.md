<!-- markdownlint-disable MD041 -->
<!-- Source: kerndatensatz-basis input/pagecontent/capability-statements.md.
     German mirror: input/translations/de/pagecontent/capability-statements.md. -->
### Capability Statements

The CapabilityStatements of the **Onkologie** module describe the expected server/client capabilities (supported resources and interactions).

> [TODO: Link to your module's CapabilityStatement(s), or delete this page.]
{: .ig-highlight .ig-highlight-grey}

<!-- source: CapabilityStatement.page.md (Simplifier guide,
     TechnischeImplementierung/CapabilityStatement.page.md). The source page
     rendered the artefact through a Simplifier render directive on the
     canonical; here it is rendered from this guide's own generated resource
     CapabilityStatement-mii-cps-onko-capabilitystatement. -->
### CapabilityStatement

To enable decentralised data analysis by means of the Deutsches
Forschungsdatenportal für Gesundheit of the Medizininformatik-Initiative, the
[capabilities interaction](https://www.hl7.org/fhir/R4/http.html#capabilities)
MUST be supported, so that the FHIR server exposes a CapabilityStatement at
```[BASE_URL]/metadata```. That CapabilityStatement MUST state which profiles,
including version, and which search parameters are supported.

The following lists the content that MUST be given in the CapabilityStatement.
In addition, conformance to the CapabilityStatement below MUST be declared in
the respective CapabilityStatement instance under
[```CapabilityStatement.instantiates```](https://www.hl7.org/fhir/R4/capabilitystatement-definitions.html#CapabilityStatement.instantiates).

Canonical: ```https://www.medizininformatik-initiative.de/fhir/modul-onko/CapabilityStatement/metadata```

{% lang-fragment CapabilityStatement-mii-cps-onko-capabilitystatement-html.xhtml %}
