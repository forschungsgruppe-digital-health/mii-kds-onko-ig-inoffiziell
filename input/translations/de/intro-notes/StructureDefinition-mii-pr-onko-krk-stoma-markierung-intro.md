<!-- source: TechnischeImplementierung/FHIR-Profile/Organspezifische-Module/KolorektalesKarzinom/KRK-Stoma-Markierung-Procedure.page.md -->
Dieses Profil beschreibt die präoperative Stomamarkierung beim Kolorektalen Karzinom gemäß oBDS KR7. Die präoperative Stomamarkierung ist ein wichtiger Schritt in der Vorbereitung auf operative Eingriffe, bei denen eine Stomaanlage erforderlich werden könnte, und trägt wesentlich zur Lebensqualität der Patienten bei.

Das Profil basiert auf einer FHIR Procedure-Ressource und dokumentiert sowohl die Durchführung als auch den Status der präoperativen Stomamarkierung.

### Verknüpfungen zu anderen Ressourcen

Die Stomamarkierung ist eine präoperative Maßnahme:
- verweist über `Procedure.subject` auf den Patienten (Patient-Ressource)
- kann über `Procedure.encounter` mit einem spezifischen Behandlungsfall verknüpft werden
- steht in Bezug zur geplanten Operation über `Procedure.reasonReference`
- kann mit der tatsächlichen Stomaanlage während der Operation verknüpft werden

### oBDS-Kontext

Die Stomamarkierung entspricht dem oBDS-Datenfeld KR7 "Präoperative Stomamarkierung" und dokumentiert, ob eine präoperative Markierung der Stomaposition durchgeführt wurde. Dies ist besonders relevant bei Rektumkarzinomen, wo eine Stomaanlage häufiger erforderlich ist.

### Terminologie-Binding

Das ValueSet für die Stomamarkierung ist **required** gebunden und beinhaltet die Codes für die Durchführung sowie den Status der präoperativen Markierung.

- ValueSet: MII VS Onko KRK Stoma Anzeichnung

### Suchparameter

Folgende Suchparameter sind für das KRK-Stoma-Markierung Profil relevant, auch in Kombination:

- Der Suchparameter `_id` MUSS unterstützt werden: `GET [base]/Procedure?_id=12345`
- Der Suchparameter `_profile` MUSS unterstützt werden: `GET [base]/Procedure?_profile=https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-krk-stoma-markierung`
- Der Suchparameter `code` MUSS unterstützt werden: `GET [base]/Procedure?code=https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/CodeSystem/mii-cs-onko-krk-stoma-anzeichnung|durchgefuehrt`
- Der Suchparameter `subject` MUSS unterstützt werden: `GET [base]/Procedure?subject=Patient/test`
- Der Suchparameter `status` MUSS unterstützt werden: `GET [base]/Procedure?status=completed`
