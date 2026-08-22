<!-- source: TechnischeImplementierung/FHIR-Profile/Organspezifische-Module/KolorektalesKarzinom/KRK-Abstand-Tumor-Anokutanlinie-Observation.page.md -->
Dieses Profil beschreibt den Abstand des Tumorunterrandes zur Anokutanlinie beim Kolorektalen Karzinom gemäß oBDS KR1. Diese Messung ist von besonderer Bedeutung für die Therapieplanung bei Rektumkarzinomen, da sie Einfluss auf die chirurgische Strategie und das sphinktererhaltende Operationsverfahren hat.

Das Profil basiert auf einer FHIR Observation-Ressource und verwendet LOINC zur standardisierten Kodierung der Abstandsmessung. Der Abstand wird als Quantity-Wert in Zentimetern angegeben.

### Verknüpfungen zu anderen Ressourcen

Die Abstandsmessung zur Anokutanlinie ist eine wichtige diagnostische Beobachtung:
- verweist über `Observation.focus` auf die Primärdiagnose (MII_PR_Onko_Diagnose_Primaertumor)
- verweist über `Observation.subject` auf den Patienten (Patient-Ressource)
- kann über `Observation.encounter` mit einem spezifischen Behandlungsfall verknüpft werden

### oBDS-Kontext

Die Abstandsmessung entspricht dem oBDS-Datenfeld KR1 "Abstand des Tumorunterrandes zur Anokutanlinie" und wird in Zentimetern dokumentiert. Diese Messung ist spezifisch für Rektumkarzinome und dient der präoperativen Planung.

### Terminologie-Binding

Das Profil verwendet LOINC Code 33748-5 "Distance from anal verge" zur standardisierten Kodierung der Abstandsmessung. Der Wert wird als UCUM-konforme Quantity in Zentimetern angegeben.

### Suchparameter

Folgende Suchparameter sind für das KRK-Abstand-Anokutanlinie Profil relevant, auch in Kombination:

- Der Suchparameter `_id` MUSS unterstützt werden: `GET [base]/Observation?_id=12345`
- Der Suchparameter `_profile` MUSS unterstützt werden: `GET [base]/Observation?_profile=https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-krk-abstand-anokutan`
- Der Suchparameter `code` MUSS unterstützt werden: `GET [base]/Observation?code=http://loinc.org|33748-5`
- Der Suchparameter `subject` MUSS unterstützt werden: `GET [base]/Observation?subject=Patient/test`
- Der Suchparameter `focus` MUSS unterstützt werden: `GET [base]/Observation?focus=Condition/primaertumor`
- Der Suchparameter `value-quantity` MUSS unterstützt werden: `GET [base]/Observation?value-quantity=5|http://unitsofmeasure.org|cm`
