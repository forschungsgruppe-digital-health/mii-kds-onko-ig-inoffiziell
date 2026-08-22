<!-- source: TechnischeImplementierung/FHIR-Profile/Organspezifische-Module/Prostata/Prostata-Clavien-Dindo-Observation.page.md -->
Dieses Profil beschreibt den Clavien-Dindo-Score für die Prostatektomie in der Onkologie. Die Clavien-Dindo-Klassifikation ist ein standardisiertes System zur Bewertung postoperativer Komplikationen basierend auf deren Schweregrad und der erforderlichen Therapie.

Das Profil basiert auf einer FHIR Observation-Ressource und verwendet SNOMED CT zur Kodierung des Assessment-Verfahrens. Es unterstützt sowohl die SNOMED CT Clavien-Dindo Grade als auch die oBDS-spezifischen Kodierungen für postoperative Komplikationen.

### Verknüpfungen zu anderen Ressourcen

Der Clavien-Dindo-Score ist eine wichtige postoperative Beobachtung:
- verweist über `Observation.focus[Diagnose]` auf die Primärdiagnose (MII_PR_Onko_Diagnose_Primaertumor)
- verweist über `Observation.focus[Operation]` auf die durchgeführte Operation (MII_PR_Onko_Operation)
- verweist über `Observation.subject` auf den Patienten (Patient-Ressource)
- kann über `Observation.encounter` mit einem spezifischen Behandlungsfall verknüpft werden
- kann über `Observation.specimen` mit entsprechenden Gewebeproben verknüpft werden

### oBDS-Kontext

Gemäß oBDS werden postoperative Komplikationen nach Prostatektomie systematisch erfasst. Die Clavien-Dindo-Klassifikation ergänzt die oBDS-Kodierung durch eine international standardisierte Bewertung der Komplikationsschwere.

### Terminologie-Binding

Das Profil verwendet **required** Bindings für beide Kodierungssysteme:

#### Assessment-Methode
- **SNOMED CT**: 789278003 "Clavien-Dindo classification (assessment scale)"

#### Beobachtungscode
- **SNOMED CT**: 789279006 "Clavien-Dindo classification grade (observable entity)"

#### Clavien-Dindo ValueSet
Das ValueSet umfasst die SNOMED CT Codes für alle Clavien-Dindo Grade: MII VS Onko Prostata Clavien-Dindo.

#### oBDS Postoperative Komplikationen ValueSet
Zusätzlich werden oBDS-spezifische Codes für postoperative Komplikationen unterstützt: MII VS Onko Prostata Postsurgical Complications.

### Suchparameter

Folgende Suchparameter sind für das Prostata-Clavien-Dindo Profil relevant, auch in Kombination:

- Der Suchparameter `_id` MUSS unterstützt werden: `GET [base]/Observation?_id=12345`
- Der Suchparameter `_profile` MUSS unterstützt werden: `GET [base]/Observation?_profile=https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-prostate-clavien-dindo`
- Der Suchparameter `code` MUSS unterstützt werden: `GET [base]/Observation?code=http://snomed.info/sct|789279006`
- Der Suchparameter `subject` MUSS unterstützt werden: `GET [base]/Observation?subject=Patient/test`
- Der Suchparameter `focus` MUSS unterstützt werden: `GET [base]/Observation?focus=Condition/primaertumor`, `GET [base]/Observation?focus=Procedure/prostatektomie`
- Der Suchparameter `method` MUSS unterstützt werden: `GET [base]/Observation?method=http://snomed.info/sct|789278003`
- Der Suchparameter `value-concept` MUSS unterstützt werden: `GET [base]/Observation?value-concept=http://snomed.info/sct|1367521005`
