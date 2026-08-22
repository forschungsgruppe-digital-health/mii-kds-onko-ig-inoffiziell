# CapabilityStatements - MII IG Kerndatensatz-Modul Onkologie v2026.0.3

* [**Inhaltsverzeichnis**](toc.md)
* **CapabilityStatements**

## CapabilityStatements

### CapabilityStatements

Die CapabilityStatements des Moduls **Onkologie** beschreiben die erwarteten Server-/Client-Fähigkeiten (unterstützte Ressourcen und Interaktionen).

> [TODO: Verweisen Sie auf das/die CapabilityStatement(s) Ihres Moduls, oder entfernen Sie diese Seite.]

### CapabilityStatement

Um eine dezentrale Datenauswertung mittel des Deutsche Forschungsdatenportal für Gesundheit der Medizininformatik-Initiative zu ermöglichen MUSS die [capabilities-Interaktion](https://www.hl7.org/fhir/R4/http.html#capabilities) untersützt werden, sodass durch durch den FHIR-Server unter `[BASE_URL]/metadata` ein CapabilityStatement exponiert wird. Innerhalb dieses CapabilityStatement MUSS angegeben werden welche Profile inkl. Version, sowie welche Suchparameter unterstüzt werden.

Nachfolgend wird aufgelistet weleche Inhalte verpflichtend im CapabilityStatement angegeben werden MÜSSEN. Darüber hinaus MUSS eine Konformität zu dem nachfolgenden CapabilityStatement in der jeweiligen CapabilityStatement Instanz unter [`CapabilityStatement.instantiates`](https://www.hl7.org/fhir/R4/capabilitystatement-definitions.html#CapabilityStatement.instantiates) angegeben werden.

Canonical: `https://www.medizininformatik-initiative.de/fhir/modul-onko/CapabilityStatement/metadata`

