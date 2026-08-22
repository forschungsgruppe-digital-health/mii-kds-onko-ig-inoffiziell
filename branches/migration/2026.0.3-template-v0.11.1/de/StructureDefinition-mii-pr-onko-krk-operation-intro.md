<!-- source: TechnischeImplementierung/FHIR-Profile/Organspezifische-Module/KolorektalesKarzinom/KRK-Operation-Procedure.page.md -->
Dieses Profil beschreibt operative Eingriffe beim Kolorektalen Karzinom gemäß verschiedenen oBDS-Kriterien. Es umfasst sowohl die Art des operativen Eingriffs als auch spezifische kolorektale Operationstypen und deren Qualitätsmerkmale wie die TME-Qualität (Totale mesorektale Exzision).

Das Profil basiert auf einer FHIR Procedure-Ressource und verwendet mehrere spezialisierte ValueSets zur Kodierung der verschiedenen operativen Aspekte beim kolorektalen Karzinom.

### Verknüpfungen zu anderen Ressourcen

Die KRK-Operation ist ein zentraler therapeutischer Eingriff:
- verweist über `Procedure.subject` auf den Patienten (Patient-Ressource)
- kann über `Procedure.encounter` mit einem spezifischen Behandlungsfall verknüpft werden
- steht in Bezug zur Primärdiagnose über `Procedure.reasonReference`
- kann mit Specimen-Ressourcen für die pathologische Aufarbeitung verknüpft werden

### oBDS-Kontext

Die KRK-Operation umfasst mehrere oBDS-Datenfelder:
- Operationstyp nach verschiedenen Klassifikationssystemen
- TME-Qualität bei Rektumkarzinomen (KR4)
- Weitere operationsspezifische Parameter je nach Eingriff

### Terminologie-Binding

Das Profil verwendet mehrere ValueSets für die verschiedenen Aspekte der KRK-Operation:

- ValueSet: MII VS Onko KRK Operationstyp
- ValueSet: MII VS Onko KRK TME Qualität

### Suchparameter

Folgende Suchparameter sind für das KRK-Operation Profil relevant, auch in Kombination:

- Der Suchparameter `_id` MUSS unterstützt werden: `GET [base]/Procedure?_id=12345`
- Der Suchparameter `_profile` MUSS unterstützt werden: `GET [base]/Procedure?_profile=https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-krk-operation`
- Der Suchparameter `code` MUSS unterstützt werden: `GET [base]/Procedure?code=http://snomed.info/sct|387713003`
- Der Suchparameter `subject` MUSS unterstützt werden: `GET [base]/Procedure?subject=Patient/test`
- Der Suchparameter `status` MUSS unterstützt werden: `GET [base]/Procedure?status=completed`
