<!-- source: TechnischeImplementierung/FHIR-Profile/Organspezifische-Module/KolorektalesKarzinom/KRK-Abstand-Resektionsrand-Aboral-Observation.page.md -->
Dieses Profil beschreibt den minimalen Abstand des aboralen Tumorrandes zum aboralen Resektionsrand beim Kolorektalen Karzinom gemäß oBDS KR2. Diese Messung ist entscheidend für die Beurteilung der R-Klassifikation und des Risikos für Lokalrezidive bei Rektumkarzinomen.

Das Profil basiert auf einer FHIR Observation-Ressource und verwendet ein dediziertes ValueSet zur Spezifikation der aboralen Resektionsebene. Der Abstand wird als Quantity-Wert in Millimetern angegeben.

### Verknüpfungen zu anderen Ressourcen

Die aborale Resektionsrandmessung ist eine wichtige pathologische Beobachtung:
- verweist über `Observation.focus` auf die Primärdiagnose (MII_PR_Onko_Diagnose_Primaertumor)
- verweist über `Observation.subject` auf den Patienten (Patient-Ressource)
- kann über `Observation.encounter` mit einem spezifischen Behandlungsfall verknüpft werden

### oBDS-Kontext

Die Abstandsmessung entspricht dem oBDS-Datenfeld KR2 "Minimaler Abstand des aboralen Tumorrandes zum aboralen Resektionsrand" und wird in Millimetern dokumentiert. Diese Messung ist besonders bei Rektumkarzinomen von prognostischer Bedeutung.

### Terminologie-Binding

Das ValueSet für die aborale Resektionslinie ist **extensible** gebunden und spezifiziert die verschiedenen Aspekte der aboralen Resektionsrandbestimmung.

- ValueSet: MII VS Onko KRK Abstand Resektionslinie Aboral

### Suchparameter

Folgende Suchparameter sind für das KRK-Abstand-Aboral Profil relevant, auch in Kombination:

- Der Suchparameter `_id` MUSS unterstützt werden: `GET [base]/Observation?_id=12345`
- Der Suchparameter `_profile` MUSS unterstützt werden: `GET [base]/Observation?_profile=https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-krk-abstand-aboral`
- Der Suchparameter `code` MUSS unterstützt werden: `GET [base]/Observation?code=https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/CodeSystem/mii-cs-onko-krk-abstand-resektionslinie-aboral|aboral`
- Der Suchparameter `subject` MUSS unterstützt werden: `GET [base]/Observation?subject=Patient/test`
- Der Suchparameter `focus` MUSS unterstützt werden: `GET [base]/Observation?focus=Condition/primaertumor`
- Der Suchparameter `value-quantity` MUSS unterstützt werden: `GET [base]/Observation?value-quantity=3|http://unitsofmeasure.org|mm`
