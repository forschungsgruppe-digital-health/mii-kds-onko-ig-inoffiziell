<!-- source: TechnischeImplementierung/FHIR-Profile/Organspezifische-Module/KolorektalesKarzinom/KRK-Specimen.page.md -->
Dieses Profil beschreibt Gewebeproben (Specimens) beim Kolorektalen Karzinom, die im Rahmen operativer Eingriffe entnommen werden. Es umfasst sowohl die Charakterisierung des Gewebes als auch spezifische pathologische Aspekte wie die TME-Qualität (Totale mesorektale Exzision) bei Rektumkarzinomen.

Das Profil basiert auf einer FHIR Specimen-Ressource und stellt die Verbindung zwischen der chirurgischen Entnahme und der pathologischen Aufarbeitung her.

### Verknüpfungen zu anderen Ressourcen

Das KRK-Specimen ist ein wichtiges Bindeglied in der Diagnostikkette:
- verweist über `Specimen.subject` auf den Patienten (Patient-Ressource)
- steht in Bezug zur Entnahme-Procedure über `Specimen.collection.procedure`
- kann mit pathologischen Observations verknüpft werden (z.B. Histologie, Grading)
- dient als Basis für die Bestimmung von Resektionsrändern und TNM-Klassifikation

### oBDS-Kontext

Das KRK-Specimen bildet die Grundlage für verschiedene oBDS-Bewertungen:
- Pathologische Beurteilung des Resektats
- TME-Qualität bei Rektumkarzinomen (KR4)
- Histopathologische Charakteristika des Tumors
- Resektionsrandbeurteilung

### Terminologie-Binding

Das Profil verwendet spezialisierte ValueSets für kolorektale Specimens, insbesondere für die Bewertung der TME-Qualität und anderer pathologischer Parameter.

- ValueSet: MII VS Onko KRK TME Qualität

### Suchparameter

Folgende Suchparameter sind für das KRK-Specimen Profil relevant, auch in Kombination:

- Der Suchparameter `_id` MUSS unterstützt werden: `GET [base]/Specimen?_id=12345`
- Der Suchparameter `_profile` MUSS unterstützt werden: `GET [base]/Specimen?_profile=https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-krk-specimen`
- Der Suchparameter `subject` MUSS unterstützt werden: `GET [base]/Specimen?subject=Patient/test`
- Der Suchparameter `type` MUSS unterstützt werden: `GET [base]/Specimen?type=http://snomed.info/sct|119376003`
- Der Suchparameter `status` MUSS unterstützt werden: `GET [base]/Specimen?status=available`
