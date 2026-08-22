<!-- source: TechnischeImplementierung/FHIR-Profile/Organspezifische-Module/MalignesMelanom/Melanom-LDH-Observation.page.md -->
Dieses Profil beschreibt die Laktatdehydrogenase (LDH) Laborwerte beim Malignen Melanom gemäß oBDS "LDH". Die LDH ist ein wichtiger prognostischer Marker beim metastasierten Melanom und wird zur Beurteilung des Krankheitsverlaufs und der Prognose herangezogen. Erhöhte LDH-Werte korrelieren mit schlechterer Prognose.

Das Profil basiert auf einer FHIR Observation-Ressource mit Kategorie "laboratory" und verwendet LOINC zur standardisierten Kodierung der LDH-Bestimmung. Der Wert wird als Quantity in Units per Liter (U/L) angegeben.

### Verknüpfungen zu anderen Ressourcen

Die LDH-Bestimmung ist eine wichtige laborchemische Beobachtung beim Melanom:
- verweist über `Observation.focus` auf die Primärdiagnose (MII_PR_Onko_Diagnose_Primaertumor)
- verweist über `Observation.subject` auf den Patienten (Patient-Ressource)
- kann über `Observation.encounter` mit einem spezifischen Behandlungsfall verknüpft werden
- dient als prognostischer Marker für die Therapieplanung

### oBDS-Kontext

Die LDH-Bestimmung entspricht dem oBDS-Datenfeld "LDH" für die Laktatdehydrogenase beim Malignen Melanom und wird als prognostischer Marker dokumentiert, insbesondere bei metastasierter Erkrankung. Eine Bewertung der LDH als normal oder erhöht erfolgt in Relation zu laborspezifischen Referenzwerten.

### Terminologie-Binding

Das Profil verwendet LOINC-Codes zur standardisierten Kodierung der LDH-Bestimmung. Das ValueSet umfasst drei verschiedene LDH-spezifische LOINC-Codes und ist **required** gebunden:

* 2532-0 "Lactate dehydrogenase [Enzymatic activity/volume] in Serum or Plasma"
* 14804-9 "Lactate dehydrogenase [Enzymatic activity/volume] in Serum or Plasma by Lactate to pyruvate reaction"
* 14805-6 "Lactate dehydrogenase [Enzymatic activity/volume] in Serum or Plasma by Pyruvate to lactate reaction"

- ValueSet: MII VS Onko Melanom LDH

### Suchparameter

Folgende Suchparameter sind für das Melanom-LDH Profil relevant, auch in Kombination:

- Der Suchparameter `_id` MUSS unterstützt werden: `GET [base]/Observation?_id=12345`
- Der Suchparameter `_profile` MUSS unterstützt werden: `GET [base]/Observation?_profile=https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-melanom-ldh`
- Der Suchparameter `code` MUSS unterstützt werden: `GET [base]/Observation?code=http://loinc.org|14805-6`
- Der Suchparameter `subject` MUSS unterstützt werden: `GET [base]/Observation?subject=Patient/test`
- Der Suchparameter `focus` MUSS unterstützt werden: `GET [base]/Observation?focus=Condition/primaertumor`
- Der Suchparameter `value-quantity` MUSS unterstützt werden: `GET [base]/Observation?value-quantity=280|http://unitsofmeasure.org|U/L`
