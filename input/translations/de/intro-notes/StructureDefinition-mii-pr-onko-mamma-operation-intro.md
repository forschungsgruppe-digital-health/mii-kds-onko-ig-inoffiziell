<!-- source: TechnischeImplementierung/FHIR-Profile/Organspezifische-Module/Mamma/Mamma-Operation-Procedure.page.md -->
Das **Mamma-Operation Profil** dokumentiert operative Eingriffe an der Brust im Rahmen der Mammakarzinom-Behandlung. Dieses Profil erweitert das allgemeine MII_PR_Onko_Operation Profil um Mamma-spezifische Aspekte und ermöglicht die detaillierte Erfassung von brustchirurgischen Verfahren.

Das Profil unterstützt sowohl brusterhaltende Therapien als auch Mastektomien sowie begleitende Verfahren wie Lymphknotenentfernungen und den Einsatz intraoperativer Hilfsmittel.

**Kommentierungshinweis**: Zu diskutieren ist, ob präoperative Markierung als separate Extraressource (wie derzeit implementiert) oder einfach als usedCode mit präoperativ- und intraoperativ-Slices modelliert werden sollte.

<!-- DERIVED:bridge source=Mamma-Operation-Procedure.page.md gate=B -->
> **Written during migration - review before release.** Die Quellseite gab als `subject` die Canonical `.../StructureDefinition/mii-pr-onko-mamma-intraoperatives-imaging-specimen` an, die in diesem Leitfaden nicht als Artefakt existiert. Inhaltlich beschreibt sie das Procedure-Profil zur Mamma-Operation; diese Notiz wurde daher [MII_PR_Onko_Mamma_Operation](StructureDefinition-mii-pr-onko-mamma-operation.html) zugeordnet und das `_profile`-Suchbeispiel unten auf diese Canonical umgestellt. Bitte das gemeinte Profil bestätigen.
{: .ig-highlight .ig-highlight-blue}

### Verknüpfungen zu anderen Ressourcen

Das Profil ist eng mit anderen onkologischen Ressourcen verknüpft:
- verweist über `Procedure.reasonReference` auf die Primärdiagnose (MII_PR_Onko_Diagnose_Primaertumor)
- verweist über `Procedure.subject` auf die Patientin (Patient-Ressource)
- kann über `Procedure.partOf` mit übergeordneten Operationen verknüpft werden
- kann über `Procedure.encounter` mit einem spezifischen Behandlungsfall verknüpft werden

### oBDS-Kontext

Das Profil implementiert **Mamma-spezifische Operationsdaten** als Erweiterung des allgemeinen oBDS-Operationsdatensatzes (Sektion 13). Die Mamma-Chirurgie umfasst verschiedene Verfahren:

**Operative Verfahren:**
- **Brusterhaltende Therapie (BET)**: Lumpektomie, Segmentresektion, Quadrantektomie
- **Mastektomie**: Einfache, modifiziert radikale, radikale Mastektomie
- **Lymphknotenchirugie**: Sentinel-Lymphknoten-Biopsie, Axilladissektion
- **Rekonstruktive Verfahren**: Sofortrekonstruktion, sekundäre Rekonstruktion

**Intraoperative Hilfsmittel:**
- **Drahtmarkierungen**: Präoperative Lokalisation nicht-palpabler Tumoren
- **Seed-Markierungen**: Radioaktive Markierung zur Tumorlokalisation
- **Markierungsclips**: Orientierungshilfen für die Nachsorge
- **Intraoperatives Imaging**: Specimen-Radiographie, Ultraschall

### Terminologie-Binding

Das Profil verwendet **duale Kodierungsstrategie** mit SNOMED CT und OPS:

- ValueSet: MII VS Onko Mamma Operation SNOMED CT
- ValueSet: MII VS Onko Mamma Operation OPS

### Suchparameter

Folgende Suchparameter sind für das Mamma-Operation Profil relevant, auch in Kombination:

- Der Suchparameter `_id` MUSS unterstützt werden: `GET [base]/Procedure?_id=12345`
- Der Suchparameter `_profile` MUSS unterstützt werden: `GET [base]/Procedure?_profile=https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-mamma-operation`
- Der Suchparameter `code` MUSS unterstützt werden: `GET [base]/Procedure?code=http://snomed.info/sct|392090004`
- Der Suchparameter `subject` MUSS unterstützt werden: `GET [base]/Procedure?subject=Patient/test`
- Der Suchparameter `patient` MUSS unterstützt werden: `GET [base]/Procedure?patient=Patient/test`
- Der Suchparameter `reason-reference` MUSS unterstützt werden: `GET [base]/Procedure?reason-reference=Condition/primaertumor`
- Der Suchparameter `part-of` MUSS unterstützt werden: `GET [base]/Procedure?part-of=Procedure/hauptoperation`
- Der Suchparameter `date` MUSS unterstützt werden: `GET [base]/Procedure?date=2024-01-15`
