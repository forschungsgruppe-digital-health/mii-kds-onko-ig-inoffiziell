<!-- source: TechnischeImplementierung/FHIR-Profile/Organspezifische-Module/Prostata/Prostata-Gleason-Score-Grade-Group-Observation.page.md -->
Dieses Profil beschreibt den Gleason Score und die entsprechende Grade Group bei der histopathologischen Graduierung des Prostatakarzinoms. Der Gleason Score ergibt sich aus der Summe des primären und sekundären Gleason Patterns, während die Grade Group (1-5) eine internationale Standardklassifikation darstellt.

Das Profil basiert auf einer FHIR Observation-Ressource und verwendet LOINC zur Kodierung. Die Grade Group wird als Komponente der Observation dokumentiert.

### Verknüpfungen zu anderen Ressourcen

Der Gleason Score ist eine zentrale histopathologische Bewertung:
- verweist über `Observation.focus` auf die Primärdiagnose (MII_PR_Onko_Diagnose_Primaertumor)
- verweist über `Observation.subject` auf den Patienten (Patient-Ressource)
- kann über `Observation.encounter` mit einem spezifischen Behandlungsfall verknüpft werden
- kann über `Observation.partOf` mit der entsprechenden Biopsie-Procedure verknüpft werden
- kann über `Observation.hasMember` die einzelnen Gleason Pattern-Observations referenzieren

### oBDS-Kontext

Gemäß oBDS P3 wird der Gleason Score als Summe aus primärem und sekundärem Pattern dokumentiert. Die Grade Group stellt eine moderne internationale Klassifikation dar, die in der aktuellen onkologischen Praxis Standard ist.

### Terminologie-Binding

Das ValueSet für Gleason Score-Codes ist **required** gebunden. Die Grade Group-Codes sind ebenfalls **required** gebunden, da sie international standardisiert sind.

- ValueSet: MII VS Onko Prostata Gleason Score

### Suchparameter

Folgende Suchparameter sind für das Prostata-Gleason-Score-Grade-Group Profil relevant, auch in Kombination:

- Der Suchparameter `_id` MUSS unterstützt werden: `GET [base]/Observation?_id=12345`
- Der Suchparameter `_profile` MUSS unterstützt werden: `GET [base]/Observation?_profile=https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-prostate-gleason-grade-group`
- Der Suchparameter `code` MUSS unterstützt werden: `GET [base]/Observation?code=http://loinc.org|44642-7`
- Der Suchparameter `subject` MUSS unterstützt werden: `GET [base]/Observation?subject=Patient/test`
- Der Suchparameter `focus` MUSS unterstützt werden: `GET [base]/Observation?focus=Condition/primaertumor`
- Der Suchparameter `value-concept` MUSS unterstützt werden: `GET [base]/Observation?value-concept=http://snomed.info/sct|369771007`
- Der Suchparameter `component-code` MUSS unterstützt werden: `GET [base]/Observation?component-code=http://loinc.org|79892-6` - Zur Suche nach der Grade Group Komponente.
