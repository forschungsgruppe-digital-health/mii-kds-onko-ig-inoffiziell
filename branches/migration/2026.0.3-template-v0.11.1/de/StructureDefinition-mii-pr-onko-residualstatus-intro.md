<!-- markdownlint-disable MD041 -->
<!-- Deutsche Fassung (Quellsprache) von TechnischeImplementierung/FHIR-Profile/Residualstatus/Residualstatus-Observation.page.md
     Englisches Pendant: input/intro-notes/StructureDefinition-mii-pr-onko-residualstatus-intro.md -->

Dieses Profil beschreibt die Gesamtstatus des Tumorresiduums nach einer (operativen)Therapie in der Onkologie.

Der oBDS-Datensatz sieht abhängig von den durchgeführten Prozeduren entweder eine lokale oder globale Bestimmung des Residualstatus vor.
Der OPS-Katalog der Prozeduren, für die ein lokaler Residualstatus erwartet wird, wird von der Plattform §65c bereitgestellt.

Aufgrund des direkten Bezugs wurde die Beurteilung des lokalen Residualstatus nach Abschluss einer Operation als Procedure.outcome in dem Profil Operation abgebildet.

### Suchparameter

Folgende Suchparameter sind für das Modul Onkologie relevant, auch in Kombination:

<!-- Quelldefekt, unverändert übernommen: das "_profile"-Beispiel unten nennt die
     Canonical .../mii-pr-onko-tod, die nicht die Canonical dieses Profils ist
     (.../mii-pr-onko-residualstatus). Bei der Migration nicht korrigiert - bitte prüfen. -->
- Der Suchparameter `_id` MUSS unterstützt werden: `GET [base]/Observation?_id=1234`
- Der Suchparameter `_profile` MUSS unterstützt werden: `GET [base]/Observation?_profile=https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-tod`
- Der Suchparameter `code` MUSS unterstützt werden: `GET [base]/Observation?code=http://fhir.de/CodeSystem/sct|184305005`
- Der Suchparameter `subject` MUSS unterstützt werden: `GET [base]/Observation?subject=Patient/example`
- Der Suchparameter `focus` MUSS unterstützt werden: `GET [base]/Observation?focus=Condition/example`
- Der Suchparameter `encounter` MUSS unterstützt werden: `GET [base]/Observation?encounter=Encounter/example`
- Der Suchparameter `derived-from` MUSS unterstützt werden: `GET [base]/Observation?derived-from=Observation/example`
