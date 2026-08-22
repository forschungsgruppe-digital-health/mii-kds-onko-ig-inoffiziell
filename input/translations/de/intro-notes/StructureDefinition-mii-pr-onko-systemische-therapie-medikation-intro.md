Dieses Profil beschreibt die konkreten Medikationen, die im Rahmen der systemischen Therapie für den oBDS dokumentiert werden.

Da im oBDS systemische und abwartende Therapie in einem Feld gruppiert sind, werden die Daten für die systemische und abwartende Therapie sowohl über eine FHIR-Prozedur (systemisch und abwartend) als auch als FHIR-Medikation abgedeckt.

Die Angaben zur systemischen onkologischen Medikation im oBDS wird amit folgenden Datenpunkten
Im Medikationsprofil der Systemischen Therapie ist das spezifisch:

* Start und Ende der Medikation
* Name des Behandlungsschemas
* Wirkstoffe (ATC-kodiert)

<!-- DERIVED:bridge source=Systemische-Therapie-MedicationStatement.page.md gate=B -->
> **Written during migration - review before release.** Der Satz "Die Angaben zur systemischen onkologischen Medikation im oBDS wird amit folgenden Datenpunkten" bricht in der Quellseite unvollständig ab und enthält einen Tippfehler ("amit"). Der Wortlaut wurde unverändert übernommen; die Stelle ist vor der Veröffentlichung zu korrigieren.
{: .ig-highlight .ig-highlight-blue}

### Konformität

Die vorliegende Profilierung ist kompatibel mit dem Prozedurenprofil der ISiK-Basismodule Stufe 4. https://simplifier.net/isik-medikation-v4/isikmedikationsinformation

Die vorliegende Profilierung ist derzeit *nicht* kompatibel mit dem EPA MedicationStatement, da dort unter MedicationStatement.medication explizit eine Referenz zu einer Medication-Ressource verlangt, während im vorliegenden Onkologie-MedicationStatement eine Kodierung über ATC präferiert wird. https://simplifier.net/epa-medication/epamedicationstatement

<!-- DERIVED:summary source=Systemische-Therapie-MedicationStatement.page.md gate=B -->
> **Written during migration - review before release.** Die Quellseite führte jeden Suchparameter einzeln mit Beispielabfrage und Verweis auf die FHIR-Basisspezifikation auf. Hier verdichtet auf die Parameternamen, die die Quellseite als verpflichtend (MUSS) benennt: `_id`, `_profile`, `medicationCodeableConcept`, `partOf` und `effective`.
{: .ig-highlight .ig-highlight-blue}
