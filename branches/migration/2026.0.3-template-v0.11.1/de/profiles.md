# Profile - MII IG Kerndatensatz-Modul Onkologie v2026.0.3

* [**Inhaltsverzeichnis**](toc.md)
* **Profile**

## Profile

Diese Seite listet die FHIR-Profile des Moduls **Onkologie**. Als Ausgangspunkt liefert die Vorlage ein minimales Beispielprofil, durch die Profile Ihres Moduls (Namenskonvention `MII_PR_<Modul>_<Name>`, siehe [`docs/recipes/add-a-profile.md`](https://github.com/forschungsgruppe-digital-health/mii-kds-onko-ig-inoffiziell/blob/main/docs/recipes/add-a-profile.md) in diesem Repository sowie die MII-Namenskonventionen). Die Extensions des Moduls stehen auf der Seite [Extensions](extensions.md).

> [TODO: Beschreiben Sie die Profile Ihres Moduls und ihre Beziehungen zueinander. Die technischen Detailseiten erzeugt der IG-Publisher automatisch.]

### oBDS-SNOMED-CT-Mapping

> **Written during migration - review before release.** Die oBDS-SNOMED-CT-Mappings dieses Moduls werden als ConceptMap-Artefakte veröffentlicht, jedes mit einer eigenen Einleitung; die Hinweise in diesem Abschnitt gelten für alle davon.

Die folgenden Seiten enthalten die Ergebnisse eines oBDS-SNOMED-Mappings auf SNOMED, durchgeführt mit der internationalen SNOMED-CT Version März 2024, ergänzt um die UICC-TNM- und Residualtumorkonzepte aus dem März 2025.

1. Es wurde Fokus auf die im oBDS hinterlegten Antwortlisten gelegt. Für das Mapping von anderen nationalen und internationalen Klassifikationen und Terminologien (ICD-10, ICD-O, OPS, ATC, …) ist das BfArM der zuständige Ansprechpartner.
1. Neben den Antwortlisten sind die Datenfelder selbst häufig ebenfalls in SNOMED und oder LOINC kodiert. (zu finden als`code`-Element an den meisten Ressourcen)
1. Äquivalenz-Bewertung: Jeder Code ist mit einem von vier möglichen Kodierungen gekennzeichnet, der die inhaltliche Beziehung von Quell- und Zielkonzept beschreibt
* `equivalent`: inhaltlich (nahezu) identisch und gleichwertig zu behandeln
* `wider`: das Zielkonzept ist allgemeiner als das Quellkonzept und kann z.B. noch andere Konzepte umfassen
* `narrower`: das Zielkonzept ist spezifischer als das Quellkonzept und umfasst z.B. nur konkrete Ausprägungen
* `unmatched`: Es wurde kein adäquat vergleichbares Zielkonzept gefunden.

### TNM-Klassifikation

> **Written during migration - review before release.** Die TNM-Artefakte bilden eine Familie. Das Gruppierungsprofil [TNM Klassifikation](StructureDefinition-mii-pr-onko-tnm-klassifikation.md) trägt das Referenzdatum und das aus seinen Mitgliedern abgeleitete UICC-Staging und referenziert die Einzelbeobachtungen in `hasMember`. Die Kategorien T, N, M, L, V, Pn und S sowie die Symbole a, m, r und y sind eigene Observation-Profile mit jeweils eigener Einleitung. Der c/p/u Präfix, der die Methode der Klassifikation festhält, ist eine einzige gemeinsam genutzte [Extension](StructureDefinition-mii-ex-onko-tnm-cp-praefix.md), die die Profile der T-, N- und M-Kategorie nutzen. Die Quellseite hat diese Artefakte über einen generierten Index aufgelistet, der nicht in diesen Guide übernommen wird.

## Organspezifische Module

Die organspezifischen Module erweitern das MII KDS Onkologie Basismodul um **entitätsspezifische Datenelemente** gemäß den Anforderungen der ADT/GEKID-Basisdokumentation. Diese Module adressieren die besonderen diagnostischen und therapeutischen Aspekte einzelner Tumorentitäten, die über die allgemeinen onkologischen Datenelemente hinausgehen.

> **Written during migration - review before release.** Das KDS-Modul Onkologie umfasst derzeit vier organspezifische Module - Mamma, Prostata, Kolorektales Karzinom (KRK) und Malignes Melanom -, die jeweils in einem eigenen Unterabschnitt weiter unten dokumentiert sind. Dieser Absatz ersetzt die Kurzübersicht der Quellseite, deren Stichpunkte je Modul vollständig in diesen Unterabschnitten enthalten sind.

**Architektur und Integration**

* **Logisches Modell** - Die Struktur aller organspezifischen Module ist im zentralen [Logischen Modell für Organspezifische Zusatzmodule](StructureDefinition-mii-lm-onko-organspezifische-zusatzmodule.md) formal definiert.
* **FHIR-Mappings** - Jedes organspezifische Datenelement verfügt über präzise FHIR-Mappings, die eine eindeutige Zuordnung zu den entsprechenden FHIR-Ressourcen ermöglichen. Die Mappings verwenden semantische Annotationen mit SNOMED CT und LOINC zur eindeutigen Identifikation.

**Implementierungshinweise**

* **Modularität** - Die organspezifischen Module sind als **optionale Erweiterungen** konzipiert: 
* Unabhängig voneinander implementierbar
* Bauen auf den Basis-Onkologie-Profilen auf
* Nutzen gemeinsame Terminologien und Extensions
 
* **Versionierung** - Alle organspezifischen Module folgen der Versionierung des Gesamtmoduls und werden synchron mit dem Basismodul weiterentwickelt.
* **oBDS-Konformität** - Die Module implementieren die organspezifischen Zusatzmodule des oBDS: 
* **Mamma**: oBDS Modul M (M1-M7)
* **Prostata**: oBDS Modul P (P1-P8)
* **Kolorektales Karzinom**: oBDS Modul KR (KR1-KR9)
* **Malignes Melanom**: oBDS Modul MM (MM1-MM4)
 

**Technische Details**

* **Profile-Struktur** - Jedes organspezifische Modul besteht aus: 
* **Observation-Profilen** für klinische Beobachtungen und Laborwerte
* **Procedure-Profilen** für organspezifische Eingriffe
* **Specimen-Profilen** für spezielle Probentypen
* **Bundle-Beispielen** für vollständige Anwendungsfälle
 
* **Terminologie-Bindings** - Die Module verwenden spezifische ValueSets für: 
* Organspezifische Operationsverfahren (OPS + SNOMED CT)
* Spezialisierte Laborparameter (LOINC)
* Entitätsspezifische Klassifikationen (oBDS-Codes)
 
* **Search-Parameter** - Für Must-Support-Elemente der organspezifischen Module sind entsprechende Suchparameter definiert, die eine gezielte Abfrage der spezialisierten Datenelemente ermöglichen.

**Qualitätssicherung**

* **Validierung** 
* Alle Profile durchlaufen die automatisierte FHIR-Validierung
* Beispieldaten werden gegen die Profile validiert
* Terminologie-Bindings werden gegen Referenz-Terminologieserver geprüft
 
* **Konsistenz** - Die organspezifischen Module werden synchron mit dem Basismodul gepflegt, um Konsistenz in Namenskonventionen, Kardinalitäten, Terminologie-Verwendung und Mapping-Strukturen zu gewährleisten.

### Mamma

Das **Mamma-Modul** implementiert die organspezifischen FHIR-Profile für die Dokumentation von Mammakarzinom-relevanten Daten gemäß dem [onkologischen Basisdatensatz (oBDS) - Mammakarzinom](https://www.basisdatensatz.de/module/5/mammakarzinom).

Das Modul umfasst spezialisierte Profile für die charakteristischen Aspekte der Mammakarzinom-Behandlung:

* **Rezeptorstatus-Bestimmungen**: Estrogen- und Progesteron-Rezeptorstatus mit detaillierter Dokumentation von Färbeintensität und Anteil positiver Zellen
* **Her2Neu-Status**: Als multimodaler Biomarker mit IHC- und ISH-Nachweismethoden ist dieser derzeit im Molecular Tumorboard-Profil abgebildet
* **Tumorgröße**: Wurde in das Histologie-Modul verschoben, da sie auf multiple Entitäten anwendbar ist
* **Menopausenstatus**: Prätherapeutische Bestimmung des Menopausenstatus als wichtiger prognostischer Faktor
* **Studienteilnahme**: Bereits durch den aktuellen oBDS 2021 abgedeckt und im entsprechenden Studienteilnahme-Profil implementiert
* **Operationsverfahren**: Mamma-spezifische chirurgische Eingriffe und deren Dokumentation
* **Bildgebungsverfahren**: Präoperative Markierungsmodalitäten und intraoperatives Imaging

**Architekturübersicht.** Die folgende Abbildung zeigt die Struktur des Mamma-Moduls und die Beziehungen zwischen den verschiedenen FHIR-Ressourcen:

![](https://raw.githubusercontent.com/medizininformatik-initiative/kerndatensatzmodul-onkologie/dev/implementation-guides/ImplementationGuide-2026.x-DE/Images/MII_Onko_Mamma_Module/MII_Onko_Mamma_Module.png)

**Verknüpfungen zu anderen Ressourcen.** Die Mamma-Profile sind eng mit den übergeordneten onkologischen Ressourcen verknüpft:

* **Primärtumor-Diagnose**: Alle Mamma-spezifischen Observations referenzieren die Primärtumordiagnose als `focus`
* **Patient**: Direkte Verknüpfung über `subject`-Referenz
* **Encounter**: Optionale Verknüpfung zum behandelnden Aufenthalt
* **Procedure**: Integration der Mamma-spezifischen Operationsverfahren

**oBDS-Kontext.** Die Mamma-Profile implementieren folgende oBDS-Datenfelder:

* **M1 Menopausenstatus**: Prätherapeutische Bestimmung (prämenopausal, perimenopausal, postmenopausal)
* **M2 Rezeptorstatus**: Estrogen- und Progesteron-Rezeptorstatus nach oBDS-Definition und S3-Leitlinien
* **Mamma-spezifische Operationen**: Erweiterte Dokumentation der organspezifischen Eingriffe
* **Bildgebungsverfahren**: Spezielle Markierungs- und Imaging-Modalitäten

**Terminologie-Binding.** Die Mamma-Profile verwenden eine Kombination verschiedener Terminologien:

* **SNOMED CT**: Primäre Kodierung für medizinische Konzepte (Menopausenstatus, Rezeptorstatus)
* **LOINC**: Laborwerte und Beobachtungen (z.B. Estrogen-Rezeptor-Antigen)
* **oBDS-spezifische ValueSets**: Für Rezeptorstatus-Definitionen nach oBDS
* **S3-Leitlinien ValueSets**: Alternative Definitionen nach aktuellen Leitlinien

**Enthaltene Profile.** Das Mamma-Modul umfasst folgende FHIR-Profile:

* Beobachtungen (Observations) 
* **Estrogen-Rezeptorstatus**: Detaillierte Dokumentation mit Anteil positiver Zellen und Färbeintensität
* **Progesteron-Rezeptorstatus**: Entsprechende Dokumentation für Progesteron-Rezeptoren
* **Menopausenstatus**: Prätherapeutische Hormonstatusbestimmung
* **Tumorgröße**: Referenz zum Histologie-Modul (MII_PR_Onko_Tumorgroesse)
* **Studienteilnahme**: Referenz zum allgemeinen Studienteilnahme-Profil (MII_PR_Onko_Studienteilnahme)
 
* Verfahren (Procedures) 
* **Mamma-Operationen**: Organspezifische chirurgische Eingriffe
* **Präoperative Markierung**: Modalitäten der präoperativen Markierung
 
* Terminologien 
* **ValueSets**: Organspezifische Wertelisten für Mamma-relevante Konzepte
* **CodeSystems**: Erweiterte Kodierungssysteme für spezielle Anwendungsfälle
 

**Implementierungshinweise.**

* Datenerfassung 
* **Duale Kodierung**: Rezeptorstatus sowohl nach oBDS als auch nach S3-Leitlinien erfassbar
* **Komponentenstruktur**: Detaillierte Aufschlüsselung der Rezeptorstatus-Komponenten
* **Referenzintegrität**: Konsistente Verknüpfung zu Primärtumordiagnose erforderlich
 
* Qualitätssicherung 
* **Vollständigkeitsprüfung**: Kritische Datenfelder als Must Support markiert
* **Wertebereichsvalidierung**: Einschränkung auf medizinisch sinnvolle Wertebereiche
* **Terminologie-Konsistenz**: Verwendung standardisierter Kodierungssysteme
 

**Entwicklungshinweis**: Eine weitere, detailliertere Spezifikation der Mamma-Profile ist derzeit in Zusammenarbeit zwischen dem BIH und der Deutschen Gesellschaft für Senologie in Entwicklung.

Die Mamma-Profile ermöglichen eine vollständige und strukturierte Dokumentation der mammakarzinom-spezifischen Daten entsprechend den aktuellen medizinischen Standards und dem oBDS.

### Prostata

Das **Prostata-Modul** implementiert die organspezifischen FHIR-Profile für die Dokumentation von Prostatakarzinom-relevanten Daten gemäß dem onkologischen Basisdatensatz (oBDS) für Prostatakarzinom.

Das Modul umfasst spezialisierte Profile für die charakteristischen Aspekte der Prostatakarzinom-Behandlung:

* **PSA-Werte**: Prostataspezifisches Antigen als zentraler Tumormarker für Diagnostik und Verlaufskontrolle
* **Gleason-Scoring**: Histopathologische Graduierung mit primären, sekundären und tertiären Patterns
* **Grade Groups**: Internationale Standard-Klassifikation nach Grade Groups (1-5)
* **Biopsie-Ergebnisse**: Detaillierte Dokumentation der Prostatabiopsie-Befunde
* **Postoperative Komplikationen**: Clavien-Dindo-Graduierung chirurgischer Komplikationen

**Architekturübersicht.** Die folgende Abbildung zeigt die Struktur des Prostata-Moduls und die Beziehungen zwischen den verschiedenen FHIR-Ressourcen:

![](https://raw.githubusercontent.com/medizininformatik-initiative/kerndatensatzmodul-onkologie/dev/implementation-guides/ImplementationGuide-2026.x-DE/Images/MII_Onko_Prostata_Module/MII_Onko_Prostata_Module.png)

**Verknüpfungen zu anderen Ressourcen.** Die Prostata-Profile sind eng mit den übergeordneten onkologischen Ressourcen verknüpft:

* **Primärtumor-Diagnose**: Alle Prostata-spezifischen Observations referenzieren die Primärtumordiagnose als `focus`
* **Patient**: Direkte Verknüpfung über `subject`-Referenz
* **Encounter**: Optionale Verknüpfung zum behandelnden Aufenthalt
* **Procedure**: Integration der Prostata-spezifischen Biopsie- und Operationsverfahren

**oBDS-Kontext.** Die Prostata-Profile implementieren folgende oBDS-Datenfelder:

* **P1 PSA-Wert**: Tumormarker für Diagnostik und Verlaufskontrolle
* **P2 Gleason Pattern**: Primäres, sekundäres und tertiäres Gleason Pattern (1-5)
* **P3 Gleason Score**: Summe aus primärem und sekundärem Pattern mit Grade Group
* **P4 Biopsie-Ergebnisse**: Anzahl Stanzen, positive Stanzen und Karzinom-Befall
* **P5 Chirurgische Komplikationen**: Postoperative Komplikationen nach Clavien-Dindo

**Terminologie-Binding.** Die Prostata-Profile verwenden eine Kombination verschiedener Terminologien:

* **LOINC**: Primäre Kodierung für PSA-Werte und Gleason-Scores
* **SNOMED CT**: Medizinische Konzepte und Methoden (z.B. Biopsie-Verfahren)
* **oBDS-spezifische ValueSets**: Für Gleason Pattern und Komplikations-Klassifikation
* **Clavien-Dindo ValueSets**: Standardisierte Graduierung postoperativer Komplikationen

**Enthaltene Profile.** Das Prostata-Modul umfasst folgende FHIR-Profile:

* Beobachtungen (Observations) 
* **PSA-Wert**: Prostataspezifisches Antigen-Bestimmung (frei/total)
* **Gleason Patterns**: Einzelne histopathologische Patterns (primär, sekundär, tertiär)
* **Gleason Score und Grade Group**: Kombinierte Scoring-Bewertung
* **Anzahl Stanzen**: Gesamtzahl der Biopsie-Stanzen
* **Anzahl positive Stanzen**: Anzahl tumorpositiver Stanzen
* **Karzinom-Befall Stanze**: Prozentuale Ausdehnung des Karzinoms pro Stanze
* **Clavien-Dindo Komplikationen**: Postoperative Komplikationsgraduierung
 
* Terminologien 
* **ValueSets**: Organspezifische Wertelisten für Prostata-relevante Konzepte
* **CodeSystems**: Erweiterte Kodierungssysteme für Komplikations-Klassifikation
 

**Implementierungshinweise.**

* Datenerfassung 
* **LOINC-Kodierung**: Standardisierte Laborwerte für PSA und Gleason-Scores
* **Komponentenstruktur**: Grade Group als Komponente des Gleason Score Profils
* **Referenzintegrität**: Konsistente Verknüpfung zu Primärtumordiagnose erforderlich
 
* Qualitätssicherung 
* **Vollständigkeitsprüfung**: Kritische Datenfelder als Must Support markiert
* **Wertebereichsvalidierung**: Medizinisch sinnvolle Wertebereiche (z.B. Gleason 1-5)
* **Terminologie-Konsistenz**: Verwendung standardisierter Kodierungssysteme
 

**Entwicklungshinweis**: Die Clavien-Dindo Graduierung könnte möglicherweise ins allgemeine Surgery-Modul verschoben werden, da es sich um ein universelles chirurgisches Klassifikationssystem handelt (siehe Kommentierungsphase).

Die Prostata-Profile ermöglichen eine vollständige und strukturierte Dokumentation der prostatakarzinom-spezifischen Daten entsprechend den aktuellen medizinischen Standards und dem oBDS.

### Kolorektales Karzinom (KRK)

Das **Kolorektales Karzinom (KRK) Modul** implementiert die organspezifischen FHIR-Profile für die Dokumentation von kolorektalem Karzinom gemäß dem onkologischen Basisdatensatz (oBDS).

Das Modul umfasst spezialisierte Profile für die charakteristischen Aspekte der KRK-Behandlung:

* **Präoperative Beurteilung**: Abstand zur Anokutanlinie, MRT-basierte Mesorektale Faszie-Messung, ASA-Klassifikation
* **Chirurgische Eingriffe**: KRK-spezifische Operationsverfahren und Stoma-Markierung
* **Resektionsränder**: Abstand zum aboralen Rand und zur zirkumferentiellen Resektionsebene (CRM)
* **Postoperative Komplikationen**: Anastomoseninsuffizienz-Graduierung
* **Pathologie-Specimens**: Spezifische Specimen-Profile für KRK-Resektate

**Architekturübersicht.** Die folgende Abbildung zeigt die Struktur des KRK-Moduls und die Beziehungen zwischen den verschiedenen FHIR-Ressourcen:

![](https://raw.githubusercontent.com/medizininformatik-initiative/kerndatensatzmodul-onkologie/dev/implementation-guides/ImplementationGuide-2026.x-DE/Images/MII_Onko_KRK_Module/MII_Onko_KRK_Module.png)

**Verknüpfungen zu anderen Ressourcen.** Die KRK-Profile sind eng mit den übergeordneten onkologischen Ressourcen verknüpft:

* **Primärtumor-Diagnose**: Alle KRK-spezifischen Observations referenzieren die Primärtumordiagnose als `focus`
* **Patient**: Direkte Verknüpfung über `subject`-Referenz
* **Encounter**: Optionale Verknüpfung zum behandelnden Aufenthalt
* **Procedure**: Integration der KRK-spezifischen Operationsverfahren
* **Specimen**: Pathologie-Specimens mit spezifischen KRK-Resektatdetails

**oBDS-Kontext.** Die KRK-Profile implementieren folgende oBDS-Datenfelder:

* **KR1 Abstand Anokutanlinie**: Präoperative Lokalisation des Tumors
* **KR2 Abstand aboral**: Minimaler Abstand zum aboralen Resektionsrand
* **KR3 Abstand CRM**: Abstand zur zirkumferentiellen Resektionsebene
* **KR4 ASA-Klassifikation**: Anästhesierisiko-Bewertung
* **KR5 MRT Mesorektale Faszie**: Abstand zur mesorektalen Faszie im MRT
* **KR6 Anastomoseninsuffizienz**: Postoperative Komplikation (Grade A/B/C)

**Terminologie-Binding.** Die KRK-Profile verwenden eine Kombination verschiedener Terminologien:

* **LOINC**: ASA-Klassifikation (97816-3)
* **SNOMED CT**: Medizinische Konzepte und Prozeduren
* **OPS**: Deutsche Operationscodes
* **oBDS-spezifische ValueSets**: Für Anastomoseninsuffizienz-Graduierung

**Enthaltene Profile.** Das KRK-Modul umfasst folgende FHIR-Profile:

* Beobachtungen (Observations) 
* **ASA-Klassifikation**: Präoperative Anästhesierisiko-Bewertung
* **Abstand Anokutanlinie**: Tumorlokalisation relativ zur Anokutanlinie
* **Abstand Circumferentielle Resektionsebene**: CRM-Messung
* **Abstand Resektionsrand Aboral**: Aboraler Sicherheitsabstand
* **MRT Mesorektale Faszie**: Präoperative MRT-Bewertung
* **Anastomoseninsuffizienz**: Postoperative Komplikation
 
* Verfahren (Procedures) 
* **KRK-Operation**: Organspezifische chirurgische Eingriffe
* **Stoma-Markierung**: Präoperative Markierung für Stomaanlage
 
* Specimen 
* **KRK-Specimen**: Pathologie-Specimen mit KRK-spezifischen Details
 

**Implementierungshinweise.**

* Datenerfassung 
* **Zeitliche Zuordnung**: Präoperative vs. postoperative Beobachtungen
* **Referenzintegrität**: Konsistente Verknüpfung zu Primärtumordiagnose und Operation
* **Resektionsstatus**: R0/R1/R2-Klassifikation basierend auf Resektionsrändern
 
* Qualitätssicherung 
* **Vollständigkeitsprüfung**: Kritische Datenfelder als Must Support markiert
* **Wertebereichsvalidierung**: Einschränkung auf medizinisch sinnvolle Wertebereiche
* **Terminologie-Konsistenz**: Verwendung standardisierter Kodierungssysteme
 

Die KRK-Profile ermöglichen eine vollständige und strukturierte Dokumentation der kolorektal-karzinom-spezifischen Daten entsprechend den aktuellen medizinischen Standards und dem oBDS.

### Malignes Melanom

Die Melanom-spezifischen Profile erweitern das MII KDS Onkologie Modul um spezielle Datenelemente für das maligne Melanom gemäß den Anforderungen der organspezifischen Module der ADT/GEKID-Basisdokumentation.

**Übersicht der Melanom-spezifischen Profile.**

![](https://raw.githubusercontent.com/medizininformatik-initiative/kerndatensatzmodul-onkologie/dev/implementation-guides/ImplementationGuide-2026.x-DE/Images/MII_Onko_Melanom_Module/MII_Onko_Melanom_Module.png)

**Melanom-spezifische Datenelemente.** Die Melanom-Module umfassen folgende spezifische klinische Parameter:

* **Breslow-Tiefe** 
* Vertikale Tumordicke in Millimetern
* Wichtigster prognostischer Faktor beim Melanom
* LOINC: 39092-1 "Breslow depth"
 
* **Ulzeration** 
* Vorhandensein einer Ulzeration des Primärtumors
* Beeinflusst die TNM-Klassifikation
* SNOMED CT: 385324008 "Tumor ulceration present"
 
* **Sicherheitsabstand** 
* Chirurgischer horizontaler Sicherheitsabstand bei der Exzision
* In Millimetern dokumentiert
* Qualitätsindikator für die operative Therapie
 
* **LDH (Laktatdehydrogenase)** 
* Serummarker für Tumorlast
* Wichtig für Stadiumseinteilung (M1c/M1d)
* LOINC: 2532-0 "Lactate dehydrogenase[Enyzmatic activity/volume] in Serum or Plasma"
 

**Klinische Verwendung.** Diese Profile werden typischerweise in folgenden Szenarien verwendet:

1. **Primärdiagnostik**: Dokumentation der initialen Tumorcharakteristika
1. **Staging**: Breslow-Tiefe und Ulzeration sind essentiell für die TNM-Klassifikation
1. **Therapieplanung**: Sicherheitsabstand basiert auf Breslow-Tiefe
1. **Verlaufskontrolle**: LDH als Verlaufsparameter bei metastasiertem Melanom

**Integration mit Basisprofilen.** Alle Melanom-spezifischen Profile:

* Basieren auf der FHIR Observation-Ressource
* Referenzieren die Primärdiagnose über `focus`
* Sind in Transaction-Bundles integrierbar
* Unterstützen die oBDS-Dokumentationsanforderungen

**Beispiel-Bundle.** Ein vollständiges Beispiel-Bundle für Melanom-Patienten ist verfügbar unter [Melanom Bundle Example](Bundle-mii-exa-onko-melanom-bundle.md). Das Bundle demonstriert die Verwendung aller Melanom-spezifischen Profile in einem realistischen klinischen Kontext.

