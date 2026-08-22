<!-- source: TechnischeImplementierung/FHIR-Profile/Organspezifische-Module/KolorektalesKarzinom/KRK-Abstand-Circumferelle-Resektionsebene-Observation.page.md -->
Dieses Profil beschreibt den minimalen Abstand des Tumorrandes zur circumferellen Resektionsebene beim Kolorektalen Karzinom gemäß oBDS KR3. Diese Messung ist ein wichtiger prognostischer Faktor und wird sowohl makroskopisch als auch mikroskopisch bestimmt. Ein geringer circumfereller Resektionsrand ist mit einem erhöhten Lokalrezidivrisiko assoziiert.

Das Profil basiert auf einer FHIR Observation-Ressource und verwendet ein dediziertes ValueSet zur Unterscheidung zwischen makroskopischer und mikroskopischer Bewertung. Der Abstand wird als Quantity-Wert in Millimetern angegeben.

### Verknüpfungen zu anderen Ressourcen

Die circumferelle Resektionsrandmessung ist eine wichtige pathologische Beobachtung:
- verweist über `Observation.focus` auf die Primärdiagnose (MII_PR_Onko_Diagnose_Primaertumor)
- verweist über `Observation.subject` auf den Patienten (Patient-Ressource)
- kann über `Observation.encounter` mit einem spezifischen Behandlungsfall verknüpft werden

### oBDS-Kontext

Die Abstandsmessung entspricht dem oBDS-Datenfeld KR3 "Minimaler Abstand des Tumorrandes zur circumferellen Resektionsebene" und wird in Millimetern dokumentiert. Die Unterscheidung zwischen makroskopischer und mikroskopischer Bewertung ist durch das entsprechende ValueSet abgebildet.

### Terminologie-Binding

Das ValueSet für die circumferelle Resektionsebene ist **extensible** gebunden und unterscheidet zwischen makroskopischer und mikroskopischer Bewertung der Resektionsränder.

- ValueSet: MII VS Onko KRK Abstand Circumferelle Resektionsrand

### Suchparameter

Folgende Suchparameter sind für das KRK-Circumferelle-Resektionsebene Profil relevant, auch in Kombination:

- Der Suchparameter `_id` MUSS unterstützt werden: `GET [base]/Observation?_id=12345`
- Der Suchparameter `_profile` MUSS unterstützt werden: `GET [base]/Observation?_profile=https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-krk-abstand-circumferelle-resektionsebene`
- Der Suchparameter `code` MUSS unterstützt werden: `GET [base]/Observation?code=https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/CodeSystem/mii-cs-onko-krk-abstand-circumferelle-resektionsebene|makroskopisch`
- Der Suchparameter `subject` MUSS unterstützt werden: `GET [base]/Observation?subject=Patient/test`
- Der Suchparameter `focus` MUSS unterstützt werden: `GET [base]/Observation?focus=Condition/primaertumor`
- Der Suchparameter `value-quantity` MUSS unterstützt werden: `GET [base]/Observation?value-quantity=2|http://unitsofmeasure.org|mm`
