<!-- source: TechnischeImplementierung/FHIR-Profile/Organspezifische-Module/Mamma/Mamma-Estrogen-Rezeptorstatus-Observation.page.md -->
Das **Estrogen-Rezeptorstatus Profil** dokumentiert den diagnostischen Estrogen-Rezeptorstatus einer pathologisch untersuchten Probe beim Mammakarzinom. Dieses Profil ermöglicht die detaillierte Erfassung sowohl der quantitativen Messwerte (Anteil positiver Zellen, Färbeintensität) als auch der interpretierten Ergebnisse nach verschiedenen Definitionen.

Der Estrogen-Rezeptorstatus ist ein zentraler prognostischer und prädiktiver Biomarker beim Mammakarzinom und entscheidet wesentlich über die Therapieplanung, insbesondere bezüglich einer antihormonellen Therapie.

### Verknüpfungen zu anderen Ressourcen

Das Profil ist eng mit anderen onkologischen Ressourcen verknüpft:
- verweist über `Observation.focus` auf die Primärdiagnose (MII_PR_Onko_Diagnose_Primaertumor)
- verweist über `Observation.subject` auf die Patientin (Patient-Ressource)
- kann über `Observation.encounter` mit einem spezifischen Behandlungsfall verknüpft werden

### oBDS-Kontext

Das Profil implementiert die **oBDS-Datenfelder für den Estrogen-Rezeptorstatus** beim Mammakarzinom. Dabei ist zu beachten, dass der [oBDS Mamma ursprünglich 2015 veröffentlicht wurde](https://www.basisdatensatz.de/download/Brust.pdf) und die Methodologie seither erheblichen Veränderungen unterworfen war.

**Historische vs. aktuelle Praxis:**
- **IRS (Immunreactive Score)**: Wurde 2015 noch verwendet, ist aber heute nicht mehr in breiter klinischer Anwendung, obwohl weiterhin relevant für Registerdaten
- **Schwellenwerte**: Moderne pathologische Praxis beginnt die Positivität bereits bei >1% positiven Zellen (statt der historischen 10%-Schwelle)
- **Bewertungsansätze**: Aktuelle S3-Leitlinien verwenden andere Definitionen als der ursprüngliche oBDS

**Modellierungskompromiß**: Das hier vorgeschlagene Profil stellt einen Kompromiß dar zwischen älteren Registerdaten, die durch das aktuelle Register-Framework erforderlich sind, und den Veränderungen in der klinischen und pathologischen Praxis.

**Kommentierungshinweis**: Zu diskutieren ist, ob ein separates Profil für den IRS (Immunreactive Score) ergänzt werden sollte, um historische Daten vollständig abzubilden.

### Terminologie-Binding

Das Profil verwendet eine **duale Kodierungsstrategie** mit **extensible** Binding. Dies bedeutet, dass die Codes aus den definierten ValueSets bevorzugt verwendet werden SOLLEN, jedoch bei Bedarf auch andere geeignete Codes verwendet werden KÖNNEN.

- ValueSet: MII VS Onko Mamma Rezeptorstatus oBDS
- ValueSet: MII VS Onko Mamma Rezeptorstatus Leitlinie

### Suchparameter

Folgende Suchparameter sind für das Mamma-Estrogen-Rezeptorstatus Profil relevant, auch in Kombination:

- Der Suchparameter `_id` MUSS unterstützt werden: `GET [base]/Observation?_id=12345`
- Der Suchparameter `_profile` MUSS unterstützt werden: `GET [base]/Observation?_profile=https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-mamma-rezeptorstatus-estrogen`
- Der Suchparameter `code` MUSS unterstützt werden: `GET [base]/Observation?code=http://loinc.org|40556-3`
- Der Suchparameter `subject` MUSS unterstützt werden: `GET [base]/Observation?subject=Patient/test`
- Der Suchparameter `patient` MUSS unterstützt werden: `GET [base]/Observation?patient=Patient/test`
- Der Suchparameter `focus` MUSS unterstützt werden: `GET [base]/Observation?focus=Condition/primaertumor`
- Der Suchparameter `value-concept` MUSS unterstützt werden: `GET [base]/Observation?value-concept=http://snomed.info/sct|416053008`
- Der Suchparameter `component-code` MUSS unterstützt werden: `GET [base]/Observation?component-code=http://snomed.info/sct|1234804006`
- Der Suchparameter `component-value-quantity` MUSS unterstützt werden: `GET [base]/Observation?component-value-quantity=gt50`
