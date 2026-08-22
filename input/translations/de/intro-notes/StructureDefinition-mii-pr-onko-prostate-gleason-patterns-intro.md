<!-- source: TechnischeImplementierung/FHIR-Profile/Organspezifische-Module/Prostata/Prostata-Gleason-Patterns-Observation.page.md -->
Dieses Profil beschreibt die einzelnen Gleason Patterns (primär, sekundär, tertiär) bei der histopathologischen Graduierung des Prostatakarzinoms. Die Gleason-Patterns bilden die Grundlage für die Gleason-Score-Berechnung und sind entscheidend für die Prognoseeinschätzung.

Das Profil basiert auf einer FHIR Observation-Ressource und verwendet LOINC zur Kodierung der verschiedenen Pattern-Typen. Jedes Pattern wird mit einem Wert von 1-5 bewertet, wobei Pattern >=3 als maligne gelten.

### Verknüpfungen zu anderen Ressourcen

Die Gleason Patterns sind wichtige histopathologische Beobachtungen:
- verweist über `Observation.focus` auf die Primärdiagnose (MII_PR_Onko_Diagnose_Primaertumor)
- verweist über `Observation.subject` auf den Patienten (Patient-Ressource)
- kann über `Observation.encounter` mit einem spezifischen Behandlungsfall verknüpft werden
- kann über `Observation.partOf` mit der entsprechenden Biopsie-Procedure verknüpft werden

### oBDS-Kontext

Gemäß oBDS P2 werden Gleason Patterns als primäres, sekundäres oder tertiäres Pattern dokumentiert. Die Pattern-Werte von 1-5 entsprechen der internationalen Gleason-Graduierung, wobei Pattern ab Grad 3 als maligne klassifiziert werden.

### Terminologie-Binding

Das ValueSet für Gleason Pattern-Codes ist **required** gebunden, da die LOINC-Codes für Gleason-Patterns standardisiert sind.

- ValueSet: MII VS Onko Prostata Gleason Patterns

### Suchparameter

Folgende Suchparameter sind für das Prostata-Gleason-Patterns Profil relevant, auch in Kombination:

- Der Suchparameter `_id` MUSS unterstützt werden: `GET [base]/Observation?_id=12345`
- Der Suchparameter `_profile` MUSS unterstützt werden: `GET [base]/Observation?_profile=https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-prostate-gleason-patterns`
- Der Suchparameter `code` MUSS unterstützt werden: `GET [base]/Observation?code=http://loinc.org|44641-9`
- Der Suchparameter `subject` MUSS unterstützt werden: `GET [base]/Observation?subject=Patient/test`
- Der Suchparameter `focus` MUSS unterstützt werden: `GET [base]/Observation?focus=Condition/primaertumor`
- Der Suchparameter `value-concept` MUSS unterstützt werden: `GET [base]/Observation?value-concept=http://snomed.info/sct|369771007`
