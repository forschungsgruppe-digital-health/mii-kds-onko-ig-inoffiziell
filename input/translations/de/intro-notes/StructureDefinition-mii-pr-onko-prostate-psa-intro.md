<!-- source: TechnischeImplementierung/FHIR-Profile/Organspezifische-Module/Prostata/Prostata-PSA-Observation.page.md -->
Dieses Profil beschreibt den PSA-Wert (Prostataspezifisches Antigen) bei Patienten mit Prostatakarzinom in der Onkologie. Der PSA-Wert ist ein zentraler Tumormarker für die Diagnostik, Verlaufskontrolle und Therapieüberwachung bei Prostatakarzinom.

Das Profil basiert auf einer FHIR Observation-Ressource und verwendet LOINC zur Kodierung des beobachteten Parameters. PSA-Werte können sowohl als Gesamt-PSA als auch als freies PSA dokumentiert werden.

### Verknüpfungen zu anderen Ressourcen

Der PSA-Wert ist eine wichtige tumorspezifische Beobachtung:
- verweist über `Observation.focus` auf die Primärdiagnose (MII_PR_Onko_Diagnose_Primaertumor)
- verweist über `Observation.subject` auf den Patienten (Patient-Ressource)
- kann über `Observation.encounter` mit einem spezifischen Behandlungsfall verknüpft werden

### oBDS-Kontext

Gemäß oBDS P1 wird der PSA-Wert als Tumormarker für Diagnostik und Verlaufskontrolle dokumentiert. Es können sowohl Diagnose- als auch Verlaufs-PSA-Werte erfasst werden.

### Terminologie-Binding

Das ValueSet für PSA-Codes ist **required** gebunden, da LOINC-Codes für PSA-Bestimmungen standardisiert und eindeutig definiert sind.

#### PSA-Codes

- **Freies PSA**: LOINC 10886-0 "Prostate specific antigen Free [Mass/volume] in Serum or Plasma"

### Suchparameter

Folgende Suchparameter sind für das Prostata-PSA Profil relevant, auch in Kombination:

- Der Suchparameter `_id` MUSS unterstützt werden: `GET [base]/Observation?_id=12345`
- Der Suchparameter `_profile` MUSS unterstützt werden: `GET [base]/Observation?_profile=https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-prostate-psa`
- Der Suchparameter `code` MUSS unterstützt werden: `GET [base]/Observation?code=http://loinc.org|2857-1`
- Der Suchparameter `subject` MUSS unterstützt werden: `GET [base]/Observation?subject=Patient/test`
- Der Suchparameter `focus` MUSS unterstützt werden: `GET [base]/Observation?focus=Condition/primaertumor`
- Der Suchparameter `value-quantity` MUSS unterstützt werden: `GET [base]/Observation?value-quantity=gt5.0`
