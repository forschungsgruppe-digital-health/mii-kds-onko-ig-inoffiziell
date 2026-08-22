<!-- source: TechnischeImplementierung/FHIR-Profile/Organspezifische-Module/Mamma/Mamma-Praeoperative-Markierung-Procedure.page.md -->
Das **Mamma-Präoperative Markierung Profil** dokumentiert radiologisch durchgeführte Markierungen von Tumorgewebe in der Brust vor operativen Eingriffen. Dieses Profil basiert auf der FHIR Procedure-Ressource und erfasst verschiedene Markierungsmodalitäten, die zur präzisen Lokalisation von Tumorgewebe eingesetzt werden.

Die präoperative Markierung ist ein wichtiger Bestandteil der brusterhaltenden Therapie und ermöglicht es Chirurgen, nicht-palpable Läsionen exakt zu lokalisieren und vollständig zu entfernen.

### Verknüpfungen zu anderen Ressourcen

Das Profil ist eng mit anderen onkologischen Ressourcen verknüpft:
- verweist über `Procedure.partOf` auf die übergeordnete Operation (MII_PR_Onko_Operation)
- verweist über `Procedure.subject` auf die Patientin (Patient-Ressource)
- kann über `Procedure.encounter` mit einem spezifischen Behandlungsfall verknüpft werden

### oBDS-Kontext

Das Profil implementiert **Mamma-spezifische Markierungsverfahren** als Erweiterung des allgemeinen oBDS-Operationsdatensatzes. Die präoperative Markierung ist besonders relevant für:

**Klinische Anwendungen:**
- **Brusterhaltende Therapie**: Präzise Lokalisation nicht-palpabler Tumoren
- **Multifokale Tumoren**: Markierung mehrerer Tumorherde
- **Nachexzision**: Markierung bei R1-Resektionen
- **Qualitätssicherung**: Dokumentation der Markierungsqualität

**Markierungsmodalitäten (aktuell im ValueSet):**
- **Drahtmarkierung mit Ultraschall-Führung**: SNOMED CT 433222002
- **Marker-Insertion mit Röntgen-Führung**: SNOMED CT 836381000000102
- **Drahtmarkierung mit MRT-Führung**: SNOMED CT 911831000000104

**Weitere klinisch relevante Modalitäten (noch nicht im ValueSet):**
- **Radioaktive Seed-Markierung**: Radioaktive Seeds zur Lokalisation
- **Magnetische Seed-Markierung**: Moderne drahtlose Verfahren (z.B. Magseed(R))
- **Clip-Markierung**: Metallclips zur Orientierung

*Hinweis: Das aktuelle ValueSet fokussiert auf bildgebungsgeführte Draht- und Markerverfahren. Moderne Seed-basierte Verfahren könnten in zukünftigen Versionen ergänzt werden.*

### Terminologie-Binding

Das Profil verwendet **extensible Binding** für Markierungsmodalitäten direkt auf `Procedure.code`:

- ValueSet: MII VS Onko Mamma Präoperative Markierung Modalität

### Suchparameter

Folgende Suchparameter sind für das Mamma-Präoperative Markierung Profil relevant, auch in Kombination:

- Der Suchparameter `_id` MUSS unterstützt werden: `GET [base]/Procedure?_id=12345`
- Der Suchparameter `_profile` MUSS unterstützt werden: `GET [base]/Procedure?_profile=https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-mamma-praeoperative-markierung`
- Der Suchparameter `code` MUSS unterstützt werden: `GET [base]/Procedure?code=http://snomed.info/sct|392021009`
- Der Suchparameter `subject` MUSS unterstützt werden: `GET [base]/Procedure?subject=Patient/test`
- Der Suchparameter `patient` MUSS unterstützt werden: `GET [base]/Procedure?patient=Patient/test`
- Der Suchparameter `part-of` MUSS unterstützt werden: `GET [base]/Procedure?part-of=Procedure/hauptoperation`
- Der Suchparameter `date` MUSS unterstützt werden: `GET [base]/Procedure?date=2024-01-15`
