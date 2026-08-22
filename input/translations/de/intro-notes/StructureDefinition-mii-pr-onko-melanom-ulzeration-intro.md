<!-- source: TechnischeImplementierung/FHIR-Profile/Organspezifische-Module/MalignesMelanom/Melanom-Ulzeration-Observation.page.md -->
Dieses Profil beschreibt die Ulzeration beim Malignen Melanom der Haut gemäß oBDS MM4. Die Ulzeration ist ein wichtiges histopathologisches Kriterium beim Melanom und beschreibt das Vorliegen einer Ulzeration der Epidermis über dem Melanom. Das Vorhandensein einer Ulzeration ist ein unabhängiger prognostischer Faktor und wird bei der TNM-Klassifikation (insbesondere pT1b) benötigt.

Das Profil basiert auf einer FHIR Observation-Ressource und verwendet LOINC zur standardisierten Kodierung der Ulzeration. Die Bewertung erfolgt durch ein dediziertes ValueSet mit den oBDS-konformen Optionen J (Ja), N (Nein) und U (Unbekannt).

### Verknüpfungen zu anderen Ressourcen

Die Ulzerations-Bewertung ist eine wichtige histopathologische Beobachtung beim Melanom:
- verweist über `Observation.focus` auf die Primärdiagnose (MII_PR_Onko_Diagnose_Primaertumor)
- verweist über `Observation.subject` auf den Patienten (Patient-Ressource)
- kann über `Observation.encounter` mit einem spezifischen Behandlungsfall verknüpft werden

### oBDS-Kontext

Die Ulzeration entspricht dem oBDS-Datenfeld MM4 "Ulzeration" und dokumentiert das Vorliegen einer Ulzeration der Epidermis über dem Melanom. Diese Information ist therapierelevant und ein wichtiges Merkmal für das biologische Verhalten sowie die Prognose des Tumors.

### Terminologie-Binding

Das ValueSet für die Melanom-Ulzeration ist **required** gebunden und umfasst die oBDS-konformen Bewertungsoptionen J (Ja), N (Nein) und U (Unbekannt). Dies entspricht der strengen Terminologie-Anforderung für oBDS-Datenfelder.

- ValueSet: MII VS Onko Melanom Ulzeration

### Suchparameter

Folgende Suchparameter sind für das Melanom-Ulzeration Profil relevant, auch in Kombination:

- Der Suchparameter `_id` MUSS unterstützt werden: `GET [base]/Observation?_id=12345`
- Der Suchparameter `_profile` MUSS unterstützt werden: `GET [base]/Observation?_profile=https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-melanom-ulzeration`
- Der Suchparameter `code` MUSS unterstützt werden: `GET [base]/Observation?code=http://loinc.org|97816-3`
- Der Suchparameter `subject` MUSS unterstützt werden: `GET [base]/Observation?subject=Patient/test`
- Der Suchparameter `focus` MUSS unterstützt werden: `GET [base]/Observation?focus=Condition/primaertumor`
- Der Suchparameter `value-concept` MUSS unterstützt werden: `GET [base]/Observation?value-concept=https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/CodeSystem/mii-cs-onko-melanom-ulzeration|J`
