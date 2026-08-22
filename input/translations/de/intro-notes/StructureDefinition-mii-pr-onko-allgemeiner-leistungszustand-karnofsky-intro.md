<!-- markdownlint-disable MD041 -->
<!-- Deutsche Fassung (Quellsprache) von TechnischeImplementierung/FHIR-Profile/Allgemeiner-Leistungszustand/Allgemeiner-Leistungszustand-Karnofsky-Observation.page.md
     Englisches Pendant: input/intro-notes/StructureDefinition-mii-pr-onko-allgemeiner-leistungszustand-karnofsky-intro.md -->

### Kontext

Dieses Profil beschreibt den allgemeinen Leistungszustand eines Patienten in der Onkologie nach Karnofsky.

Die Erfassung des allgemeine Leistungszustand wird im oBDS vorgeschrieben.
Dabei wird die eigentliche Meldung als ECOG kodiert und übertragen, wobei die Antwortmöglichkeiten ein Mapping vom Karnofsky-Score ermöglichen.

Im bisherigen oBDS und in den vorliegenden FHIR-Profilen ist sowohl eine Dokumentation des ECOG mit den Antwortmöglichkeiten 0-4 als auch des Karnofsky-Scores mit 10%, 20% etc. gestattet.
Der aktuelle Umsetzungsleitfaden enthält jedoch einen Hinweis, dass in Zukunft ausschließlich der ECOG gemeldet werden soll. https://plattform65c.atlassian.net/wiki/spaces/UMK/pages/15532323/Allgemeiner+Leistungszustand+Typ

Für den Fall, dass in den Befunden nur Bezug auf den Allgemeinzustand genommen wird, ohne dabei in ECOG oder Karnofsky zu kodieren, empfiehlt der Dokumentationsleitfaden der Plattform §65c die Entwicklung hausinterner Richtlinien zur besseren Reproduzierbarkeit. https://plattform65c.atlassian.net/wiki/spaces/Dokumentat/pages/86310992/Allgemeiner+Leistungszustand

### Karnofsky-ECOG Mapping: oBDS vs. klinische Literatur

**Wichtiger Hinweis**: Es existieren unterschiedliche Karnofsky-ECOG-Konversionstabellen in der Literatur:

**oBDS 12.1 Spezifikation** (in diesem Profil verwendet):
- Karnofsky 90-100% = ECOG 0
- Karnofsky 70-80% = ECOG 1
- Karnofsky 50-60% = ECOG 2
- Karnofsky 30-40% = ECOG 3
- Karnofsky 10-20% = ECOG 4
- Karnofsky 0% = ECOG 5

**Klinische Literatur** (Buccheri et al., 1996; Ma et al., 2010):
- Karnofsky 100% = ECOG 0
- Karnofsky 80-90% = ECOG 1
- Karnofsky 70% = ECOG 2
- Karnofsky 50-60% = ECOG 3
- Karnofsky 10-40% = ECOG 4

Die oBDS-Mappings sind gegenüber der klinischen Literatur um ca. 10-20% nach unten verschoben. Da diese Profile den oBDS implementieren, verwenden alle Referenzbereiche und ObservationDefinitions die oBDS-Spezifikation.

Implementierer sollten sich dieser Unterschiede bewusst sein, insbesondere bei der Konversion zwischen Karnofsky und ECOG oder beim Austausch mit internationalen Systemen, die möglicherweise andere Konversionstabellen verwenden.

### LOINC-Unterstützung für internationale Interoperabilität

Das Profil unterstützt optionale LOINC-Kodierung zusätzlich zur verpflichtenden oBDS-Kodierung:

- **`code.coding`**: Neben dem verpflichtenden SNOMED CT Code (761869008) kann optional der LOINC Code 89243-0 angegeben werden
- **`valueCodeableConcept.coding`**: Neben der verpflichtenden oBDS-Kodierung können optional LOINC Answer List Codes angegeben werden

Zur Übersetzung zwischen oBDS- und LOINC-Codes steht folgende ConceptMap zur Verfügung:
- `https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/ConceptMap/mii-cm-onko-allgemeiner-leistungszustand-karnofsky-loinc`

### Suchparameter

Folgende Suchparameter sind für das Modul Onkologie relevant, auch in Kombination:

<!-- Quelldefekt, unverändert übernommen: das "_profile"-Beispiel unten nennt die
     Canonical .../mii-pr-onko-allgemeiner-leistungszustand, die nicht die Canonical
     dieses Profils ist (.../mii-pr-onko-allgemeiner-leistungszustand-karnofsky). Bei
     der Migration nicht korrigiert - bitte prüfen. -->
- Der Suchparameter `_id` MUSS unterstützt werden: `GET [base]/Observation?_id=1234`
- Der Suchparameter `_profile` MUSS unterstützt werden: `GET [base]/Observation?_profile=https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-allgemeiner-leistungszustand`
- Der Suchparameter `code` MUSS unterstützt werden: `GET [base]/Observation?code=http://fhir.de/CodeSystem/sct|184305005`
- Der Suchparameter `subject` MUSS unterstützt werden: `GET [base]/Observation?subject=Patient/example`
- Der Suchparameter `encounter` MUSS unterstützt werden: `GET [base]/Observation?encounter=Encounter/example`
