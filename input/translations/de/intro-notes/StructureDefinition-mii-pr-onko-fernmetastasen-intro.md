<!-- markdownlint-disable MD041 -->
<!-- Deutsche Fassung (Quellsprache) von TechnischeImplementierung/FHIR-Profile/Fernmetastasen-Observation/Fernmetastasen-Observation.page.md
     Englisches Pendant: input/intro-notes/StructureDefinition-mii-pr-onko-fernmetastasen-intro.md -->

Dieses Profil beschreibt Fernmetastasen, wie sie im Rahmen des oBDS in der Onkologie für die Meldung an die Krebsregister erfasst werden. Für jede Metastase sind folgende Datenfelder einzeln anzugeben:
* Datum der Feststellung
* Lokalisation basierend auf oBDS-eigener Kodierung

In der FHIR-Profilierung **SOLL** jede Fernmetastase als einzelne Ressource angelegt werden.
Im oBDS ist die Angabe von nicht-invasiven diagnostischen Prozeduren nicht vorgesehen. Ebensowenig muss laut oBDS der Grad der diagnostischen Sicherung (klinisch, radiologisch, histologisch) erhoben werden. Bei Bedarf **KANN** eine Fernmetastase auf entsprechende diagnostische Prozeduren verweisen.

Dieses Profil ist konform zum [Patho-Finding-Profil des MII-Pathologiebefundes](https://simplifier.net/guide/mii-ig-pathologie/Befund-TechnischeImplementierung-FHIRProfile-MII-PR-Patho-Finding?version=current) und kann daher als Observation in einen pathologischen Befundbericht eingebunden werden.

### Suchparameter

Folgende Suchparameter sind für das Modul Onkologie relevant, auch in Kombination:

<!-- Quelldefekt, unverändert übernommen: das "_profile"-Beispiel unten nennt die
     Canonical .../mii-pr-onko-allgemeiner-leistungszustand, die nicht die Canonical
     dieses Profils ist (.../mii-pr-onko-fernmetastasen). Bei der Migration nicht
     korrigiert - bitte prüfen. -->
- Der Suchparameter `_id` MUSS unterstützt werden: `GET [base]/Observation?_id=1234`
- Der Suchparameter `_profile` MUSS unterstützt werden: `GET [base]/Observation?_profile=https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-allgemeiner-leistungszustand`
- Der Suchparameter `code` MUSS unterstützt werden: `GET [base]/Observation?code=http://fhir.de/CodeSystem/sct|184305005`
- Der Suchparameter `subject` MUSS unterstützt werden: `GET [base]/Observation?subject=Patient/example`
- Der Suchparameter `focus` MUSS unterstützt werden: `GET [base]/Observation?focus=Condition/example`
- Der Suchparameter `encounter` MUSS unterstützt werden: `GET [base]/Observation?encounter=Encounter/example`
- Der Suchparameter `date` MUSS unterstützt werden: `GET [base]/Observation?date=2024-02-08`
- Der Suchparameter `body-site` MUSS unterstützt werden: `GET [base]/Observation?body-site=http://snomed.info/sct|258332000`
- Der Suchparameter `derived-from` MUSS unterstützt werden: `GET [base]/Observation?derived-from=Observation/example`
