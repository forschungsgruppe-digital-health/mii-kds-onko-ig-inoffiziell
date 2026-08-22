<!-- source: TechnischeImplementierung/FHIR-Profile/Organspezifische-Module/Prostata/Prostata-Anzahl-Stanzen-Observation.page.md -->
Dieses Profil beschreibt die Gesamtanzahl der entnommenen Biopsie-Stanzen bei der Prostatabiopsie. Diese Information ist wichtig für die Bewertung der Repräsentativität der Biopsie und die Interpretation der Befunde.

Das Profil basiert auf einer FHIR Observation-Ressource und verwendet LOINC zur Kodierung. Der Wert wird als Quantity mit der Einheit "Stück" angegeben.

### Verknüpfungen zu anderen Ressourcen

Die Anzahl der Stanzen ist eine wichtige Biopsie-Parameter:
- verweist über `Observation.focus` auf die Primärdiagnose (MII_PR_Onko_Diagnose_Primaertumor)
- verweist über `Observation.subject` auf den Patienten (Patient-Ressource)
- kann über `Observation.partOf` mit der entsprechenden Biopsie-Procedure verknüpft werden

### oBDS-Kontext

Gemäß oBDS P4.1 wird die Gesamtanzahl der entnommenen Biopsie-Stanzen dokumentiert. Diese Information ist essentiell für die Beurteilung der Adequatheit der Probeentnahme.

### Terminologie-Binding

Der LOINC-Code für die Anzahl der Stanzen ist **required** gebunden.

### Suchparameter

Folgende Suchparameter sind für das Prostata-Anzahl-Stanzen Profil relevant:

- Der Suchparameter `_id` MUSS unterstützt werden: `GET [base]/Observation?_id=12345`
- Der Suchparameter `_profile` MUSS unterstützt werden: `GET [base]/Observation?_profile=https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-prostate-anzahl-stanzen`
- Der Suchparameter `code` MUSS unterstützt werden: `GET [base]/Observation?code=http://loinc.org|33747-0`
- Der Suchparameter `value-quantity` MUSS unterstützt werden: `GET [base]/Observation?value-quantity=gt10`
