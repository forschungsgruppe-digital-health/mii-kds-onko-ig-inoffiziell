<!-- source: TechnischeImplementierung/FHIR-Profile/Organspezifische-Module/Prostata/Prostata-Karzinom-Befall-Stanze-Observation.page.md -->
Dieses Profil beschreibt den prozentualen Befall der am stärksten befallenen Stanze einer Prostata-Biopsie oder eines Prostata-Exzisionspräparates in der Onkologie. Diese Angabe ist ein wichtiger histopathologischer Parameter zur Beurteilung der Tumorausdehnung und Aggressivität bei Prostatakarzinom.

Das Profil basiert auf einer FHIR Observation-Ressource und verwendet LOINC zur Kodierung des beobachteten Parameters. Der Wert wird als Prozentsatz angegeben und bezieht sich auf die am stärksten befallene Stanze der Biopsie.

### Verknüpfungen zu anderen Ressourcen

Der Karzinom-Befall der Stanze ist eine wichtige histopathologische Beobachtung:
- verweist über `Observation.focus` auf die Primärdiagnose (MII_PR_Onko_Diagnose_Primaertumor)
- verweist über `Observation.subject` auf den Patienten (Patient-Ressource)
- kann über `Observation.encounter` mit einem spezifischen Behandlungsfall verknüpft werden
- kann über `Observation.specimen` mit der entsprechenden Gewebeprobe verknüpft werden

### oBDS-Kontext

Gemäß oBDS P4.3 wird der prozentuale Karzinombefall der am stärksten befallenen Stanze einer Prostata-Biopsie dokumentiert. Dies ist ein wichtiger Parameter für die histopathologische Beurteilung der Tumorausdehnung.

### Terminologie-Binding

Das Profil verwendet einen **required** LOINC-Code für die eindeutige Identifikation der Beobachtung:

#### Karzinom-Befall Code
- **LOINC**: 44654-2 "Tissue involved by tumor in Prostate tumor"

### Suchparameter

Folgende Suchparameter sind für das Prostata-Karzinom-Befall-Stanze Profil relevant, auch in Kombination:

- Der Suchparameter `_id` MUSS unterstützt werden: `GET [base]/Observation?_id=12345`
- Der Suchparameter `_profile` MUSS unterstützt werden: `GET [base]/Observation?_profile=https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-prostate-ca-befall-stanze`
- Der Suchparameter `code` MUSS unterstützt werden: `GET [base]/Observation?code=http://loinc.org|44654-2`
- Der Suchparameter `subject` MUSS unterstützt werden: `GET [base]/Observation?subject=Patient/test`
- Der Suchparameter `focus` MUSS unterstützt werden: `GET [base]/Observation?focus=Condition/primaertumor`
- Der Suchparameter `value-quantity` MUSS unterstützt werden: `GET [base]/Observation?value-quantity=gt50`
