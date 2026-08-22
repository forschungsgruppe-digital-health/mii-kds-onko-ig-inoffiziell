<!-- source: TechnischeImplementierung/FHIR-Profile/Organspezifische-Module/KolorektalesKarzinom/KRK-Anastomoseninsuffizienz-Observation.page.md -->
Dieses Profil beschreibt das Auftreten einer Anastomoseninsuffizienz beim Kolorektalen Karzinom gemäß oBDS KR8. Die Anastomoseninsuffizienz ist eine wichtige postoperative Komplikation nach kolorektalen Resektionen und hat Einfluss auf die Prognose und weitere Therapieplanung.

Das Profil basiert auf einer FHIR Observation-Ressource und verwendet ein dediziertes ValueSet zur Kodierung des Auftretens und Schweregrads der Anastomoseninsuffizienz.

### Verknüpfungen zu anderen Ressourcen

Die Anastomoseninsuffizienz-Beurteilung ist eine wichtige postoperative Beobachtung:
- verweist über `Observation.focus` auf die Primärdiagnose (MII_PR_Onko_Diagnose_Primaertumor)
- verweist über `Observation.subject` auf den Patienten (Patient-Ressource)
- kann über `Observation.encounter` mit einem spezifischen Behandlungsfall verknüpft werden
- steht in Bezug zur durchgeführten Operation (Procedure-Ressource)

### oBDS-Kontext

Die Anastomoseninsuffizienz entspricht dem oBDS-Datenfeld KR8 "Anastomoseninsuffizienz" und dokumentiert das Auftreten dieser postoperativen Komplikation nach kolorektalen Eingriffen mit Anastomosenanlegung.

### Terminologie-Binding

Das ValueSet für die Anastomoseninsuffizienz ist **required** gebunden und beinhaltet die Codes für das Auftreten sowie die Graduierung der Insuffizienz.

- ValueSet: MII VS Onko KRK Anastomoseninsuffizienz

### Suchparameter

Folgende Suchparameter sind für das KRK-Anastomoseninsuffizienz Profil relevant, auch in Kombination:

- Der Suchparameter `_id` MUSS unterstützt werden: `GET [base]/Observation?_id=12345`
- Der Suchparameter `_profile` MUSS unterstützt werden: `GET [base]/Observation?_profile=https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-krk-anastomoseninsuffizienz`
- Der Suchparameter `code` MUSS unterstützt werden: `GET [base]/Observation?code=http://snomed.info/sct|235919008`
- Der Suchparameter `subject` MUSS unterstützt werden: `GET [base]/Observation?subject=Patient/test`
- Der Suchparameter `focus` MUSS unterstützt werden: `GET [base]/Observation?focus=Condition/primaertumor`
- Der Suchparameter `value-concept` MUSS unterstützt werden: `GET [base]/Observation?value-concept=https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/CodeSystem/mii-cs-onko-krk-anastomoseninsuffizienz|ja`
