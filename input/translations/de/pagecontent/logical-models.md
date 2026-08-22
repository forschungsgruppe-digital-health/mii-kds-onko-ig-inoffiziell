<!-- markdownlint-disable MD041 -->
<!-- Die Datensatz-Beschreibung stammt aus dem Kapitel "Anwendungsfälle /
     Informationsmodell → Datensätze inkl. Beschreibungen" des Quell-Guides. -->
### Logische Modelle

Die logischen Datenmodelle des Moduls **Onkologie** beschreiben den fachlichen Datensatz unabhängig von der konkreten FHIR-Repräsentation.

<!-- source: AnwendungsflleInformationsmodell/Datenstzeinkl.Beschreibungen.page.md -->
Der Datensatz basiert auf dem onkologischen Basisdatensatz (oBDS, siehe
[Referenzen](guidance.html)).

In der Umsetzung wurde der Fokus auf die Umwandlung der bei der
Registermeldungdaten anfallenden Datenpunkte in FHIR-Ressourcen für das FDPG für
die Sekundärdatennutzung

Daher sind Meldungs- und personenrelevante Daten des oBDS nicht enthalten.

<!-- DERIVED:summary source=AnwendungsflleInformationsmodell/Datenstzeinkl.Beschreibungen.page.md gate=B -->
> **Written during migration - review before release.** Die Quellseite stellte
> jedes der drei folgenden logischen Modelle als generierten Element-Baum mit
> anschließender generierter Tabelle aus Pfaden und Definitionen dar. Diese
> Darstellungen werden in diesem Leitfaden nicht wiederholt: Jedes logische
> Modell zeigt seine Elemente, Datentypen und Definitionen vollständig auf seiner
> eigenen Artefakt-Seite, die aus dem jeweiligen Unterabschnitt verlinkt ist.
{: .ig-highlight .ig-highlight-blue}

#### Basis-Onkologie Logical Model

Das Basismodell ist als
[Onkologie](StructureDefinition-mii-lm-onko.html) veröffentlicht.

Es ist zu beachten, dass das Logical Model rein auf die Abbildung der
Datenelemente und deren Beschreibung abzielt. Verwendete Datentypen und
Kardinalitäten sind nicht als verpflichtend anzusehen. Dies wird abschließend
durch die FHIR-Profile festgelegt. Für jedes Element innerhalb des Logical
Models existiert ein 1:1 Mapping auf ein Element einer konkreten FHIR Ressource.

#### Organspezifische Zusatzmodule

Die organspezifischen Module (Mamma, Prostata, Kolorektales Karzinom, Malignes
Melanom) erweitern das Basis-Onkologie-Modul um entitätsspezifische
Datenelemente gemäß den ADT/GEKID-Anforderungen:
[OrganspezifischeZusatzmodule](StructureDefinition-mii-lm-onko-organspezifische-zusatzmodule.html).

<!-- source: AnwendungsflleInformationsmodell/UML.page.md -->
Die Struktur aller organspezifischen Module ist zusätzlich im Logical Model
formal definiert, welches die FHIR-Mappings für alle entitätsspezifischen
Datenelemente bereitstellt.

#### Modellvorhaben Genomsequenzierung

Das Modellvorhaben Genomsequenzierung nach §64e SGB V definiert zusätzliche
Datenelemente für die Next-Generation-Sequenzierung (NGS) bei onkologischen
Patienten:
[MVGenomSeq Onkologie](StructureDefinition-mii-lm-mvgenomseq-onkologie.html).
