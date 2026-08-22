# Anleitung - MII IG Kerndatensatz-Modul Onkologie v2026.0.3

* [**Inhaltsverzeichnis**](toc.md)
* **Anleitung**

## Anleitung

Dieser Abschnitt bündelt die fachlichen Hinweise zur Umsetzung und Nutzung des Moduls **Onkologie**.

### Allgemeine Umsetzungshinweise

* **[Datensätze und Beschreibungen](logical-models.md)** — die Datenelemente des Moduls, beschrieben als logische Modelle. (Dieser Eintrag teilt sein Ziel mit **Artefakte → Logische Modelle**; keiner der Anker der Artefakt-Übersicht ist als Linkziel nutzbar — siehe [`docs/page-structure.md`](https://github.com/forschungsgruppe-digital-health/mii-kds-onko-ig-inoffiziell/blob/main/docs/page-structure.md) in diesem Repository.)
* **[UML-Diagramme](uml-diagrams.md)** — visuelle Darstellung der Datenmodelle und ihrer Beziehungen.

### Zielgruppenspezifische Hinweise

* **[Anleitung für Forschende](researcher-guidance.md)** — für Forschende, die Moduldaten nutzen.
* **[Anleitung für Implementierende](implementer-guidance.md)** — technische Hinweise für DIZ-Implementierende.

### Kontext im Gesamtprojekt / Bezüge zu anderen Modulen

Das KDS-Modul Onkologie bedient sich umfassend der Basismodule des MII.

* Die onkologische Primärdiagnose basiert auf dem MII-Modul **[Diagnose](https://simplifier.net/mii-basismodul-diagnose-2024)**
* Die Therapiedokumentation von Operationen, Strahlen- und allgemeine Angaben zu Systemischen Therapien basieren auf dem MII-Modul **[Prozedur](https://simplifier.net/mii-basismodul-prozedur-2024)**
* Die spezifische Kodierung von Wirkstoffen als Teil der Systemischen Therapie basiert auf dem MII-Modul **[Medikation](https://simplifier.net/mii-basismodul-medikation-2024)**.

Da die Datenerfassung für den oBDS auf den Krebsregistermeldungen basiert, ist eine Abbildung über die oben genannten Module jedoch nur teilweise möglich.

Für eine weitergehende Verknüpfung der onkologischen Registerdaten sind besonders folgende KDS-Module relevant.

* [Pathologiebefundbericht](https://simplifier.net/medizininformatikinitiative-modulpathologie)
* [Biobank](https://simplifier.net/medizininformatikinitiative-modulbiobank)
* [Molekulargenetischer Befundbericht](https://simplifier.net/medizininformatikinitiative-modulomics)
* [Bildgebung](https://simplifier.net/Medizininformatik-Initiative-Modul-Bildgebung) (noch nicht umgesetzt, Integration geplant für Version 2027)

Langfristig ist eine enge Verzahnung mit den oben genannten Modulen geplant. In den ersten Versionen 2025 und 2026 ist diese jedoch komplett optional. Das hat vor allem einen Grund: Die Erzeugung von FHIR-Ressourcen aus anderen Modulen erfordert teilweise die Existenz von Daten, die in dieser Form nicht Teil des oBDS sind. (Beispiel: Das Modul Bioprobe erfordert bei der Erstellung zwingend die Angabe der Verfügbarkeit). Da FHIR-Ressourcen derzeit (Stand Juli 2025) noch nicht flächendeckend aus Primärsystemen ausgespielt werden können, und nicht jeder DIZ-Standorte zwingenderweise alle KDS-Module ganz oder teilweise in ETL-Strecken erzeugen können, ist die Verwendung von anderen MII-Modulen angedacht, aber optional.

Das KDS-Modul Onkologie bildet darüber hinaus die Grundlage für das [KDS-Modul Molekulares Tumorboard](https://simplifier.net/mii-erweiterungsmodul-molekulares-tumorboard), in dem tiefergehende onkologisch relevante Fragestellungen wie Leitlinien-Behandlung, Next-Generation-Sequencing und personalisierte Therapien detailliert abgebildet werden können. Benötigte Anpassungen (z.B. genauere Anpassung der Therapieempfehlungen) wurden für das MTB-Modul ausspezifiziert und in die Version v2026 übernommen.

### Anwendungsfälle / Informationsmodell

> **Written during migration - review before release.** Der Quell-Guide eröffnete dieses Kapitel mit einer absichtlich leer gelassenen Seite. Die beiden folgenden Unterabschnitte tragen den Inhalt des Kapitels: das Anwendungsszenario, das die Nutzung des Moduls zeigt, und die UML-Übersichten des Informationsmodells. Die Datenelemente des Datensatzes selbst beschreibt die Seite [Logische Modelle](logical-models.md).

#### Beschreibung von Szenarien für die Anwendung der Module

Der oBDS dient als Grundlage für die Krebsregistermeldungen an die Landeskrebsregister.

Die vorliegende Profilierung des oBDS hat den Anspruch, die Daten, die bei der Krebsregistrierung anfallen, für andere Forschungsfelder nutzbar zu machen.

So wird bei der FHIR-Abbildung des untenstehenden Beispiels klar, dass Informationen zu bildgebenden Verfahren, zu detaillierten Behandlungs- und Bestrahlungsschemata und zu genetischen Varianten außerhalb der Krebsregisterdaten in detaillierter Form vorliegen. Die vorliegende FHIR-Profilierung liefert damit einen wichtigen Beitrag zur Einbindung möglichst vieler Informationen für die onkologische Forschung.

##### Anwendungsszenario einer leitliniengerechten Behandlung

Disclaimer: Der Therapieverlauf entspricht einer möglichen leitliniengerechten Therapie, Daten und Verlauf sind für Testzwecke konstruiert, Ähnlichkeiten mit tatsächlichen Krankheitsverläufen sind zufällig.

###### Textuelle Darstellung des beispielhaften Therapieverlaufs

* Kim Musterperson, geb. 14.03.1956
* 10.06.2021 CT Abdomen mit KM: V.a. Peritonealkarzinose, Aszites im gesamten Bauchraum, Raumforderung Ovar rechts. Mesenteriale retroperitoneale LK-Metastasen, V.a. Lebermetastasierung
* 15.06.2021 Aszitespunktion: mit malignen Tumorzellen. Zytologisch mögliches Ovarial-CA.
* 22.06.2021 CT Thorax: kein Hinweis auf Metastasen.
* Tumorboard 25.06.2021: Eindeutiges CT-Korrelat und zytologisch ED Ovarial-CA. 
* Neoadjuvante Chemotherapie mit 3 Zyklen Carboplatin/Paxlitaxel, Intervall-Debulking im Verlauf. 
* 05.07.21-25.07.21 Z1 Carboplatin AUC5 d1, Paclitaxel 175 mg/m2, d1, Wdh. d21
* 26.07.21-15.08.21 Z2 Carboplatin AUC5 d1, Paclitaxel 175 mg/m2, d1, Wdh. d21
* 16.08.21-05.09.21 Z3 Carboplatin AUC5 d1, Paclitaxel 175 mg/m2, d1, Wdh. d21
 
 
* 15.09.21 CT Thorax/Abdomen: Beurteilung Peritonelakarzinose zunehmend, metastasensuspekte Lymphknoten retroperitoneal. V.a. konstante Lebermetastasierung
* 16.09.21 Tumorboard: Deutlicher Tumorprogress. OP zur histologischen Sicherung bereits geplant, optimales Debulking anstreben.
* 30.09.2021 OP Intervalldebulking mittels Längsschnittlaparotomie, Tumorresektion mittels Hysterektomie, bilateraler Adnexektomie, und atpyischer Lebersegmentresektion (Seg. II und V). Postoperativ: R0.
* Pathologischer Bericht 
* Histologie: Resektat vom 30.09.2021
* Neoplasie des Ovars (Z.n. neoadjuvanter Therapie) (ICD-10-C56) Ovar o.n.A. (ICD-O-C56.9) Untersuchungsmaterial: Resektat WHO-Typ: Seröses Adenokarzinom (ICD-O M-8441/3)
* Lokale Tumorausbreitung: Ovartumor links mit einer max. Größe von 2,2 cm und tumorinfiltrierter Kapsel mit Nachweis von Tumorzellen auf der Ovaroberfläche, Anteil vitaler Tumorzellen von ca. 80 %.
* UICC-Klassifikation (8. Auflage): ypT3c. pM1b (HEP) L1. V0. Pn0 FIGO: IVB
* Immunhistochemie: (Beispiel für einige Marker, in echtem Befund stehen viel mehr) Vereinzelt kräftige nukleäre Expression des Progesteronrezeptors. Positivität für P16 im Tumor. Der Proliferationsindex mittels MIB-1 liegt bei max. 38%. Mikroskopie: Partieller Nachweis von Muzin.
* Kommentar: Das immunhistochemische Markerprofil passt zu einem high-grade serösen Adenokarzinom des Ovars (Z.n. neoadjuvanter CTX)
 
* Tumorboard 25.10.2021 : 
* Durch OP makroskopische Komplett-Resektion erreicht.
* Jedoch Progress unter Neoadjuvanz.
* Daher Umstellung auf Carboplatin/Gemcitabine
* Humangenetische Vorstellung empfohlen
 
* Systemische Therapie 
* 08.11.21-28.11.21 Z1 Carboplatin AUC 4 d1, Gemcitabin 1000mg/m2 d1+d8 Wdh d22
* 29.11.21- 19.12.21 Z2 Carboplatin AUC 4 d1, Gemcitabin 1000mg/m2 d1+d8 Wdh d22
* 20.12.21-09.01.22 Z3 Carboplatin AUC 4 d1, Gemcitabin 1000mg/m2 d1+d8 Wdh d22
 
* 15.01.22 CT: Abdomen: 
* Regredienz der bekannten Peritonealkarzinose
* Leber ohne eindeutigen Hinweis auf Metastasierung, bei Z.n. atpyischer Lebersegmentresektion a.e. narbige Veränderungen
* Beurteilung: Regredienter Befund, bei Z.n. zwischenzeitig operativem Debulking
 
* 20.01.22 Tumorboard: 
* Erhaltungstherapie mit Niraparib bei BRCAwt
* Restaging in 3 Monaten mit CT Thorax/Abdomen und TM
 
* 25.01.22 Beginn Niraparib 300mg d1-28 wdh d28

###### Grafische Darstellung des beispielhaften Therapieverlaufs

![](https://raw.githubusercontent.com/medizininformatik-initiative/kerndatensatzmodul-onkologie/refs/heads/dev/implementation-guides/ImplementationGuide-2026.x-DE/Images/MII_Onko_Example_Patient.svg)

Die Bildatei kann [hier (Github)](https://raw.githubusercontent.com/medizininformatik-initiative/kerndatensatzmodul-onkologie/refs/heads/dev/implementation-guides/ImplementationGuide-2026.x-DE/Images/MII_Onko_Example_Timeline.svg) zur besseren Darstellung einzeln betrachtet und heruntergeladen werden (Bereitstellung als `.svg`).

#### UML

Das folgende UML-Diagramm zeigt die umgesetzten Inhalte und Kardinalitäten des oBDS, die gemäß dessen Vorgaben durch das KDS-Modul Onkologie umgesetzt wurden.

Die Bildatei kann [hier (Github)](https://raw.githubusercontent.com/medizininformatik-initiative/kerndatensatzmodul-onkologie/dev/implementation-guides/ImplementationGuide-2026.x-DE/Images/onco_merged.svg) zur besseren Darstellung einzeln betrachtet und heruntergeladen werden (Bereitstellung als `.svg`).

##### Organspezifische Module — UML Diagramme

Zusätzlich zu dem übergreifenden UML-Diagramm verfügt jedes organspezifische Modul über eigene detaillierte Architekturdiagramme:

* **Mamma-Modul** — Mammakarzinom-spezifische Profile und deren Beziehungen
* **Prostata-Modul** — Prostatakarzinom-spezifische Profile und deren Beziehungen
* **KRK-Modul** — Kolorektales Karzinom-spezifische Profile und deren Beziehungen
* **Malignes-Melanom-Modul** — Malignes Melanom-spezifische Profile und deren Beziehungen

### Abweichungen zum oBDS

Der vorliegende Implementation Guide beschreibt eine Umsetzung des oBDS in FHIR. Eine reine 1:1 Abbildung des kompletten Datensatzes ist weder inhaltlich noch technisch sinnvoll. Hier die wichtigsten Abweichungen:

#### Inhalte

Das KDS-Modul Onkologie beinhaltet diejenigen Gruppen des oBDS, die v.a. klinisch-diagnostische und therapeutische Datenpunkte umfassen.

Daher wurden mehrere Gruppen **nicht** in FHIR implementiert. Das umfasst:

* Die personenbezogenen Gruppen 
* Gruppe 3: Patienten Stammdaten
* Gruppe 4: Melder Stammdaten
* Gruppe 7: Einsender
* Gruppe 22: Operateur
* Gruppe 25: Zusätzliche Kontakte
 
* die administrativen und meldungsbezogenen Gruppen 
* Gruppe 1: Meldung
* Gruppe 2: Zentrum
* Gruppe 21: Anmerkungen
 

Die organspezifischen Module waren nicht Teil der ersten Profilierung, sind aber seit der Version 2026 Teil des Moduls Onkologie.

* Dazu gehören: 
* Modul Prostata
* Modul Mamma
* Modul Melanom
* Modul Kolon
 

#### Kardinalitäten

Der oBDS ist hauptsächlich für die Datenmeldung an die Krebsregister optimiert worden.

In den ersten Versionen wurden die Kardinalitäten größtenteils aus dem oBDS übernommen, sind teilweise aber "weicher" eingestellt, um gerade in einem ersten Schritt Zugang zu einer breiteren Datenbasis zu bekommen.

#### Einbindung von Terminologien und Codesystemen

Um eine Auswertbarkeit durch das Forschungsdatenportal Gesundheit (FDPG) zu gewährleisten, verlangt die Angabe der Medikation bei Systemischer Therapie eine Kodierung mittels ATC. Freitext ist weiterhin als zusätzliche Angabe möglich.

#### Validierung

Im oBDS-XML-Schema 3.0.2 ist eine Reihe von Validierungen vorgesehen, die die Datenqualität und -vollständigkeit überprüfen. Diese sind technisch in der ersten Version **nicht** mit implementiert. Es ist davon auszugehen, dass die oBDS-Daten in den Primärsystemen der Tumordokumentation zumindest soweit validiert werden, dass ein Export ins XML-Format möglich ist. Weitere Validierungen (z.B. sich gegenseitig ausschließende Datenfelder) könnten bei Bedarf in Zukunft vorgenommen werden. Dies wäre erforderlich, wenn das vorliegende KDS-Modul über seinen derzeitigen Zweck hinaus als Datenerhebungsgrundlage für Primärsysteme dienen soll.

#### Inhalte der Module und Profile

Im oBDS sind die Datenfelder an die Meldestruktur gebunden. Gruppen, die unterschiedliche Kardinalitäten haben, sind häufig in verschiedenen Gruppen gelagert. So sind bspw. Tumorkonferenz und Therapieempfehlungen in zwei verschiedenen Gruppen, da eine Tumorkonferenz auf mehrere Therapieempfehlungen verweisen kann. Beide Gruppen sind aber problemlos in der FHIR-Ressource CarePlan abbildbar, so dass dieses in ein FHIR-Profil zusammengelegt wurde. Wichtige Änderungen im Folgenden auszughaft:

* die Diagnose enthält Teile des Histologie-Gruppe (ICD-O Topologie, ICD-O Morphologie)
* die Tumorkonferenz-Gruppe wurden in der Gruppe Tumorkonferenz/Therapieempfehlung zusammengelegt
* der Allgemeine Leistungszustand kann sowohl als ECOG als auch als Karnofsky kodiert werden (eine ursprüngliche Zusammenlegung der Datenpunkte wurde nach der Kommentierungsphase verworfen).

### Bezug zu nationalen Standards

Beim beschriebenen Basisdatensatz Onkologie handelt es sich um einen Datensatz, der auf dem oBDS und damit den deutschen Krebsregister-Datenmodellen folgt.

-------

##### Informationssysteme im Krankenhaus (ISiK)

ISiK beschreibt einen Standard, der für Krankenhaussysteme zum Austausch untereinander genutzt werden soll. ISiK selbst enthält wenige inhaltliche Vorgaben und Binding, die für die Erfassung von onkologischen Daten relevant sind. Durch die steigende Bedeutung im Krankenhaussektor wurde bei der Profilierung auf eine Konformität geachtet.

* Die Diagnose- und Prozedur-Profile sind Teil der ISiK-Basismodule [https://simplifier.net/guide/isik-basis-v4?version=current](https://simplifier.net/guide/isik-basis-v4?version=current)
* Medikation ist Teil des ISiK-Medikationsmoduls [https://simplifier.net/guide/isik-medikation-v4?version=current](https://simplifier.net/guide/isik-medikation-v4?version=current)

##### Medizinische Informationsobjekte (MIOs)

MIOs sind als strukturierte Datenelemente im Kontext der elektronischen Patientenakte (ePA) von Bedeutung. Der erste große Baustein soll dabei eine Bereistellung von strukturierten Medikationsdaten Zum Zeitpunkt der Erstellung der Profilierung (Jan-Apr 2024) befanden sich die Profile für Medikation / Medikationsplan noch in der Profilierung und konnten daher in der vorliegenden Spezifikation keine Berücksichtigung finden. Zu beachten ist dabei aber, dass die Medikationsliste und die Tumordokumentation momentan noch getrennte Ökosysteme sind. Eine langfriste Harmonisierung von vergleichbaren Profilen wird ab 2025 durch das KIG der gematik koordiniert und vorangetrieben. Der Implementierungsleitfaden für den "ePA Medication Service" befindet sich hier: [https://simplifier.net/guide/medication-service?version=1.1.0](https://simplifier.net/guide/medication-service?version=1.1.0) Link zum konkreten Profil EPA MedicationStatement [https://simplifier.net/epa-medication/epamedicationstatement](https://simplifier.net/epa-medication/epamedicationstatement)

-------

#### Nationale Vorarbeiten

##### German OncoLogical Data Standard (GOLD)

Das Projekt GOLD wurde vom Vision-Zero e.V. initiiert und zielt auf die Abbildung einer kompletten onkologischen Patient Journey ab. Das Datenmodell und die dazugehörigen Profile wurden von existierenden Datenmodellen aus Versorgung, Forschung und Industrie in Deutschland und Ausland abgeleitet. Es wurden Vorschläge für Harmonisierung verschiedener Spezifikationen erarbeitet und mit deutschen Experten abgestimmt. Die ersten FHIR-Profile mit Fokus auf Diagnose und Klassifikationen, wie die TNM-Klassifikation, sowie Bildgebung und Verlauf sind in mehrere weitere Projekte eingeflossen, z.B. Basisprofile Onkologie von HL7 Deutschland und das MII-Modul Befunde bildgebender Verfahren. Die aktuelle Version ist hier zu finden: [https://vision-zero-oncology.github.io/GOLD/](https://vision-zero-oncology.github.io/GOLD/)

##### Basisprofile Onkologie von HL7 Deutschland

In den Basisprofilen Deutschland wurden insb. 2022 Profilierungsarbeiten für eine Grundlage der einheitlichen Verwendung von FHIR-Ressourcen im onkologischen Sektor geliefert. [https://simplifier.net/BasisprofileOnkologie](https://simplifier.net/BasisprofileOnkologie) Die Arbeiten an den Basisprofilen ruhen seit der Kommentierung 2022. Mittlerweile verweisen die Basisprofile Onkologie der HL7 auf das hier vorliegende KDS-Modul Onkologie der MII.

##### Deutsches Konsortium für Translationale Krebsforschung

Das interne Datenmodell der DKTK nutzt aus den Tumordokumentationssystemen aufbereitete oBDS-Daten im FHIR-Format als Austauschmedium. (erreichbar unter [https://simplifier.net/oncology](https://simplifier.net/oncology)) Das ursprüngliche Informationsmodell des KDS-Moduls Onkologie war stark am DKTK-Modell orientiert. Die Profilierung unterscheidet sich jedoch insofern, als dass die DKTK-Profile in sich abgeschlossen sind, während ein MII-Modul möglichst gut mit den MII-Basismodulen (v.a. Diagnose, Prozedur, Medikation) und bereits bestehenden KDS-Modulen arbeiten soll. Daher war einer der Hauptmodellierungsentscheidungen die Verwendung der MII-Diagnose und MII-Medikation, sowie die Darstellung von OPs, Strahlentherapien und Systemischen / abwartenden Therapien als MII-Prozeduren.

##### Modellvorhaben Genomsequenzierung

Das Modellvorhaben Genomsequezierung nach §64e SGB V sieht die Erhebung eines Datenkranzes bei einer Next-Generation-Sequenzierung (NGS) von onkologischen Patienten vor. Der Datenkranz beinhaltet dabei Informationen zur diagnostischen und therapeutischen Vorgeschichte, der molekulargenetischen Beschreibung des Tumors, den Empfehlungen zu Studienteilnahmen und systemischen Therapien sowie Follow-up-Informationen zu tatsächlich durchgeführten Therapien und Therapieansprechen / Vitalstatus.

Es gibt einen ähnlichen Datenkranz für Seltene Erkrankungen, der zukünftig im Modul Seltene Erkrankungen abgebildet wird.

Ein Mapping der Datenelemente auf den MII KDS ist derzeit in Arbeit.

> **Written during migration - review before release.** Die Quellseite stellte den Datenkranz des Modellvorhabens als generierten Element-Baum und das Mapping als generierten Tabellen-Ausschnitt dar. Beides wird in diesem Leitfaden nicht wiederholt: Der Datenkranz ist als logisches Modell [MVGenomSeq Onkologie](StructureDefinition-mii-lm-mvgenomseq-onkologie.md) veröffentlicht, das Mapping als ConceptMap [mii-cm-onkologie-to-mvgenomseq](ConceptMap-mii-cm-onkologie-to-mvgenomseq.md); beide zeigen ihren vollständigen Inhalt auf ihrer eigenen Artefakt-Seite.

### Bezug zu internationalen Standards

Beim beschriebenen Basisdatensatz Onkologie handelt es sich um einen Datensatz, der auf dem oBDS und damit den deutschen Krebsregister-Datenmodellen beruht.

In der FHIR-Modellierung wurde die FHIR-Profilierung anderer nationaler onkologischer Datenmodelle aus dem Ausland betrachtet.

-------

#### mCODE, USA

[https://hl7.org/fhir/us/mcode/](https://hl7.org/fhir/us/mcode/) Das Modell befindet sich momentan in der vierten Iteration. Die enthaltenen Datenelemente lassen sich unterteilen in:

* Patienteninformationen
* Charakterisierung der Erkrankung
* Gesundheitszustand
* Genomische Daten
* Behandlungsinformationen
* Outcomes

##### Einflüsse von mCODE auf die Datenmodellierung

1. mCODE erfasst die individuellen Bestandteile der**TNM-Klassifikation**über einzelne FHIR-Observationen, die dann mittels einer Stage Group Ressource gruppiert werden. Neben TNM gibt es eine Reihe wichtiger Tumor Staging Klassifikation / Scores, die explizit als FHIR-PRofile angelegt wurden. Dieses Vorgehen empfehlen wir ebenfalls in der fortlaufenden Profilierung der organspezifischen Module des oBDS (z.B. Gleason-Score)
1. mCODE kodiert die Details zu einzelnen**Bestrahlungseinheiten**über Erweiterungen. Es gibt mit CodeX Radiation Therapy ein von mCODE abgeleitetes Modul, das sich explizit mit der Modellierung von Bestrahlungsschemata befasst ([https://hl7.org/fhir/us/codex-radiation-therapy/](https://hl7.org/fhir/us/codex-radiation-therapy/)) - dieses ist jedoch deutlich detaillierter als der oBDS.
1. mCODE erfasst die genomischen Daten mit dem HL7 FHIR Genomics Report, der von der HL7 FHIR Clinical Genomics Working Group erarbeitet wurde. In der aktuellen Version beinhaltet der oBDS nur spärliche Informationen zu**genetischen Varianten**. Falls am Standort detaillierte Informationen über die molekulargenetischen Untersuchungen, Varianten und therapeutischen Konsequenzen vorliegen, kann der Molekulargenetische Befundbericht der MII genutzt werden, der ebenfalls auf dem HL7 Genomics Report basiert.
1. Darstellung weiterer Klassifikationen (v.a. für weitere Grading- und Staging-Systeme)

##### Entscheidende Unterschiede mCODE - oBDS

1. mCODE und durch mCODE referenzierte Datenelemente (Komorbiditäten, Vitalparameter, Ethnizität etc.) basieren zu großen Teilen auf den US-amerikanischen FHIR-Basismodulen aus us-core und ist daher in Deutschland nicht direkt anwendbar.
1. In der Datenmodellierung ist die klinische Entscheidungsfindung wie z.B. Empfehlungen eines interdisziplinären Tumorboards nicht abgebildet.
1. Es soll mit tatsächlichen Behandlungsdaten gearbeitet werden, daher sind viele FHIR-Ressourcen detaillierter, als es die Datenlage im oBDS zulässt. So sind genaue Zeitpunkte der Medikamentengabe und Dosisangaben nicht Teil des oBDS, wohl aber von mCODE.
1. Insgesamt ist mCODE für eine prospektive Datenerfassung optimiert bzw. kann in der Behandlung kontinuierlich fortgeschrieben werden. Hierin unterscheidet sich der Grundaufbau deutlich von den retrospektiv dokumentierten deutschen Krebsregisterdaten, deren Inhalte meldungsspezifisch variieren können (Diagnose, Operation, Verlauf etc).

-------

#### OSIRIS, Frankreich

Das französische Common Data Model "Interoperability and data sharing of clinical and biological data in oncology" (OSIRIS) umfasst zwei unabhängige Kerndatensätze: einen klinischen und einen genomischen Teil. Ein dritter Teil mit einem Datensatz zu Imaging und Strahlentherapie ist gerade in Arbeit. Da der Fokus des oBDS auf den klinischen Daten liegt, sollen hier kurz Gemeinsamkeiten und Unterschiede zum klinischen Datensatz zusammengefasst werden.

Der OSIRIS-Datensatz modelliert die zeitliche Darstellung vor allem um sog. "Tumor Events". Tumor Events sind dabei entweder Erstdiagnosen oder Verlaufsbeobachtungen.

Weitere Informationen sind nachzulesen unter: [https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8140800/](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8140800/)

Englische Version des Datensatzes verfügbar unter: [https://github.com/InstitutNationalduCancer/OSIRIS/blob/v1.1.05/documentation/ModeleCliniqueOSIRIS-english_version.pdf](https://github.com/InstitutNationalduCancer/OSIRIS/blob/v1.1.05/documentation/ModeleCliniqueOSIRIS-english_version.pdf)

[https://github.com/InstitutNationalduCancer/OSIRIS/blob/master/documentation/MPD_OSIRIS_model_v1.1.05.png](https://github.com/InstitutNationalduCancer/OSIRIS/blob/master/documentation/MPD_OSIRIS_model_v1.1.05.png)

### Referenzen

Das KDS-Modul Onkologie basiert auf dem onkologischen Basisdatensatz (oBDS) in der im Bundesanzeiger 2021 veröffentlichten Version. Die Inhalte sind öffentlich verfügbar.

* Webseite des oBDS mit allen relevanten Datenfeldern, Beschreibungen und Antwortmöglichkeiten: [https://basisdatensatz.de/basisdatensatz](https://basisdatensatz.de/basisdatensatz)
* Das oBDS: XML-Schema in der Version 3.03; hier insbesondere die Angaben zur Hierarchie, den Feld-Ids und Datenvalidierung 
* aktuelle Version: [https://basisdatensatz.de/xml/oBDS_v3.0.3.xsd](https://basisdatensatz.de/xml/oBDS_v3.0.3.xsd)
* ältere Versionen verfügbar unter [https://basisdatensatz.de/xml/](https://basisdatensatz.de/xml/)
 
* Auf Confluence basierender Umsetzungsleitfaden der Krebsregister-Plattform §65c [https://plattform65c.atlassian.net/wiki/spaces/UMK/overview](https://plattform65c.atlassian.net/wiki/spaces/UMK/overview), insbesondere: 
* [https://plattform65c.atlassian.net/wiki/spaces/UMK/pages/15532576/Datenmodell](https://plattform65c.atlassian.net/wiki/spaces/UMK/pages/15532576/Datenmodell) für das allgemeine Datenmodell
* [https://plattform65c.atlassian.net/wiki/spaces/UMK/pages/15532143/Meldungsinhalte](https://plattform65c.atlassian.net/wiki/spaces/UMK/pages/15532143/Meldungsinhalte) und alle Unterpages für Detailansichten und Datenmodelldiagramme der einzelnen Meldeinhalten
 

Es existieren ältere Vorarbeiten zur Abbildung des oBDS als Informationsmodell auf der Plattform ART-DECOR, die momentan den aktuellen Stand nicht vollständig abbilden. Diese sind [hier](https://art-decor.org/art-decor/decor-datasets--mide-?id=2.16.840.1.113883.3.1937.777.24.1.1&effectiveDate=2018-06-05T12%3A44%3A12&conceptId=2.16.840.1.113883.3.1937.777.24.2.62&conceptEffectiveDate=2018-06-06T06%3A13%3A32) zu erreichen.

-------

Für die KDS-weiten Konformitätsanforderungen siehe die [Konformitätsregeln des Meta-Moduls](https://github.com/medizininformatik-initiative/kerndatensatz-meta/wiki/Conformance); für die technischen Artefakte siehe [Profile](profiles.md).

