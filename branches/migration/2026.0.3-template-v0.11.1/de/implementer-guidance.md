# Anleitung für Implementierende - MII IG Kerndatensatz-Modul Onkologie v2026.0.3

* [**Inhaltsverzeichnis**](toc.md)
* [**Anleitung**](guidance.md)
* **Anleitung für Implementierende**

## Anleitung für Implementierende

Technische Hinweise für DIZ-Implementierende zur Umsetzung der Profile des Moduls **Onkologie** (ETL aus Primärsystemen, FHIR-API, Validierung).

> [TODO: Beschreiben Sie die technischen Umsetzungsschritte für Ihr Modul.]

### Technische Implementierung

> **Written during migration - review before release.** Der Quell-Guide eröffnete sein Kapitel zur technischen Implementierung mit einer absichtlich leer gelassenen Seite. Die vier folgenden Abschnitte tragen den Inhalt dieses Kapitels: wie die Profile erben und welche oBDS-Datenfelder sie abbilden, wie die Ressourcen einander referenzieren, warum das Modul Extensions verwendet und welche Alternativen abgewogen wurden, sowie den aktuellen Stand der FHIR-Validierung. Die Terminologien beschreiben die Seiten [CodeSystems](code-systems.md) und [ValueSets](value-sets.md), die geforderten Server-Fähigkeiten die Seite [CapabilityStatements](capability-statements.md).

### Profile - Inhalt und Vererbung

Im Folgenden werden die Profile einmal in vereinfachter Version dargestellt. Diese Darstellung legt insbesondere Wert auf die übersichtliche Darstellung:

* Vererbung von anderen Profilen
* das Mapping der oBDS-Datenfelder auf die entsprechenden FHIR-Elemente.

Die Bildateien können [hier (Github)](https://github.com/medizininformatik-initiative/kerndatensatzmodul-onkologie/tree/refs/heads/dev/implementation-guides/ImplementationGuide-2026.x-DE/Images) zur besseren Darstellung einzeln betrachtet und heruntergeladen werden (Bereitstellung als `.png` und `.svg`).

#### Diagnose

Die Diagnose enthält sowohl Informationen zur Primärdiagnose selbst, als auch zur Histologie und Lokalisation des Primärtumors.

#### Histologie

#### TNM-Klassifikation

#### Weitere Klassifikationen, Residualstatus, Allgemeiner Gesundheitszustand, Fernmetastasen

#### Prozeduren, Medikation und Nebenwirkungen

#### Verlauf, Tumorkonferenz, Tod und Genetische Variante

### Profile - Beziehungen und Referenzen

Die folgende Übersicht soll die Referenzen der Ressourcen untereinander darstellen.

Die Bildateien können [hier (Github)](https://github.com/medizininformatik-initiative/kerndatensatzmodul-onkologie/tree/refs/heads/dev/implementation-guides/ImplementationGuide-2026.x-DE/Images) zur besseren Darstellung einzeln betrachtet und heruntergeladen werden (Bereitstellung als `.png` und `.svg`).

#### Zukünftig angedachte Einbindung der Module Biobank, MolGen-Befundbericht und Pathologiebefund

### Verwendung von Extensions

Die Umsetzung des oBDS erfolgt unter Verwendung von Extensions. Dies hat insbesondere mit der oBDS-Datenstruktur und den oBDS-spezifischen Codesystemen und dem Versuch zu tun, diese mit Modulen aus dem MII-Kerndatensatz abzubilden.

Die vorliegenden Extensions wurden mit dem Fokus auf die Integration in den MII-Kerndatensatz und die Verwendung als Sekundärdatennutzung der Krebsregisterdaten über das FDPG gestaltet.

Da die Verwendung von Extensions im FHIR-Kontext nach Möglichkeit zu vermeiden ist, zumindest solange es sinnvolle alternative Möglichkeiten innerhalb es bestehenden FHIR-Datenmodell gibt, sollen im Folgenden Umsetzungsalternativen aufgezeigt und diskutiert werden.

#### Prozeduren-Extension (Intention, Stellung)

**Intention**

* Notwendigkeit der Extension: 
* die FHIR R4 Prozedur enthält kein Element, das die Behandlungsintention adäquat darstellen kann.
* die MII-Prozedur enthält daher eine Extension [Durchführungsabsicht](https://www.medizininformatik-initiative.de/fhir/core/modul-prozedur/StructureDefinition/Durchfuehrungsabsicht)
* CarePlan enthält das Element Intention; dieses beschreibt jedoch die Stärke der Intention der Ressource (wie bindend die Ressource ist, also Plan, Option, Anforderung etc.) und kann damit nicht für die Kodierung der Behandlungsabsicht im Sinne des oBDS genutzt werden
 
* Alternativer Vorschlag 
* Eventuell kann über ein konsentiertes SNOMED-Mapping eine Übereinstimmung erreicht werden, so dass die Behandlungintention direkt in SNOMED-CT erfasst wird und so mittels der Extension [Durchführungsabsicht](https://www.medizininformatik-initiative.de/fhir/core/modul-prozedur/StructureDefinition/Durchfuehrungsabsicht) durchgeführt werden kann.
 

**Stellung**

* Die Stellung einer Strahlen- oder Systemischen Therapie kann über die bisherigen FHIR-Prozeduren nicht abgebildet werden. Eine Abbildung über eine andere Ressource (z.B. in CarePlan als Teil der Tumorkonferenz) wurde diskutiert, aber als nicht vorteilhafter eingeschätzt.

#### Strahlentherapie-Bestrahlungs-Extension

* Notwendigkeit der Extension: Abbildung des komplexen oBDS-Bestrahlungs-Typ über traditionelle FHIR-Ressourcen derzeitig nur bedingt möglich.
* Darstellung der Einzelbestrahlungen MII nicht möglich, da jeweils verpflichtende OPS-Codes oder SNOMED-CT-Codes angegeben werden müssen, die nicht für alle oBDS-Datenfelder vorliegen
* Alternativer Vorschlag 
* Strahlentherapie weiter as MII_Prozedur
* Bestrahlung als R4 Prozedur definieren 
* bodySite für Zielgebiet, mit Lateralitätsextension
* code als Applikationsart
* method als Slice für und Strahlenart
* Abbildung von Dosis und Boost weiterhin über Extensions
 
 

#### TNM (c/p, itc,sn) -Extensions

Alternative Umsetzungen:

* als Einzelobservations mit bestehender TNM-Grouperlogik 
* Vorteil: verhält sich genauso wie andere Kategorien und Symbole
* Nachteil: kommt nicht eigenständig vor, enge Kopplung an T/N/M_Klassifikationsprofile notwendig
 
* als Teil der T/N/M Kategorien (z.B. component)

### QA und Validierung

> **Written during migration - review before release.** Die Zahlen, Filterstatistiken und Fehlerlisten dieses Abschnitts sind der Stand, den der Quell-Guide am 2025-12-16 für die Packageversion 2026.0.0 festgehalten hat; alle Repository-Links darin verweisen auf das Upstream-Repository `kerndatensatzmodul-onkologie`, dem sie entnommen sind. Vor einem Release neu gegen den Build dieses Guides messen und die Links umhängen.

Diese Seite dokumentiert den aktuellen Stand der FHIR-Validierung für das MII Modul Onkologie.

#### Validierungsübersicht

Das Modul wird kontinuierlich gegen den FHIR R4 Standard und die definierten Profile validiert. Da Simplifier keinen öffentlichen QA-Report bereitstellt wie bei klassischen FHIR IG Publisher Builds, dokumentieren wir hier transparent den Validierungsstatus.

**Aktuelle Statistik** (Stand: 2025-12-16, Version 2026.0.0):

* **Actionable Fehler**: 9
* **Gefilterte Meldungen**: ~700+ (via advisor.json)

Die meisten ursprünglichen Meldungen werden durch Filter in `advisor.json` unterdrückt, da sie false-positives oder externe Abhängigkeiten betreffen.

#### Terminologie-Server und Validierungskonfiguration

Die betreffende Validierung betrifft die aktuelle Packageversion **2026.0.0**.

**MII Terminology Server**: [https://termserv.mii.medizininformatik-initiative.de/fhir](https://termserv.mii.medizininformatik-initiative.de/fhir)

**Validierungskonfiguration**: [`advisor.json`](https://github.com/medizininformatik-initiative/kerndatensatzmodul-onkologie/blob/dev/advisor.json)

#### Gefilterte Validierungsmeldungen

Diese Meldungen werden durch `advisor.json` unterdrückt. Die Tabelle zeigt die geschätzte Anzahl der Vorkommnisse und den Grund für die Filterung:

| | | | |
| :--- | :--- | :--- | :--- |
| `Terminology_TX_NoValid_16` | ~310 | Zeile 3, 10-12 | Betrifft ImplementationGuide Parameter und alle StructureDefinitions/ValueSets/CodeSystems. Externe Terminologie-Server-Limitation. |
| `MSG_DRAFT` | ~14 | Zeile 4 | Erwartete Warnung während Entwicklungsphase. Löst sich bei finalem Release. |
| `dom-6` | ? | Zeile 5 | FHIR Basisregel für DomainResource. Bekanntes Validator-Artefakt. |
| `eld-20` | ~294 | Zeile 6 | ElementDefinition Constraint. Strukturelle Validator-Limitation. |
| `UNABLE_TO_INFER_CODESYSTEM` | ~100 | Zeilen 7-9 | System URI kann bei bestimmten Codes nicht inferiert werden (betrifft StructureDefinition, ValueSet, CodeSystem). |

**Gesamte Suppressionen**: ~700+ Meldungen werden gefiltert

#### Verbleibende aktive Validierungsprobleme

Diese Fehler werden **nicht** gefiltert und sollten behoben werden:

##### Aktuelle Fehler (Stand: 2025-12-16)

| | | | |
| :--- | :--- | :--- | :--- |
| **Unknown_Code** | 3 | HER2-Status, Rezeptorstatus Estrogen/Progesteron | 🟡 TODO: Code-Bindings prüfen |
| **Reference_Not_Found** | 1 | AdverseEvent (MedDRA) | 🔵 EXTERNAL: MedDRA proprietär |
| **Profile-Match** | 1 | KRK-Bundle (Operation) | 🟡 TODO: Bundle-Struktur korrigieren |
| **TX-Server** | 2 | Mamma-Bundle, MRT-Faszie | 🔵 EXTERNAL: Terminology-Server-Limitation |
| **Sonstige** | 2 | KRK-Observation, Mamma-HER2 | 🟡 TODO: Review |

##### Betroffene Dateien

* `Bundle-mii-exa-onko-mamma-example-bundle-1.json` (2 Fehler)
* `AdverseEvent-mii-pr-onko-nebenwirkung-0.json` (1 Fehler)
* `Bundle-mii-exa-onko-krk-bundle.json` (1 Fehler)
* `Observation-mii-exa-onko-krk-abstand-mesorektale-fascie.json` (1 Fehler)
* `Observation-mii-exa-onko-mamma-her2neu-status.json` (1 Fehler)
* `Observation-mii-exa-onko-mamma-rezeptorstatus-estrogen-1.json` (1 Fehler)
* `Observation-mii-exa-onko-mamma-rezeptorstatus-progesteron-1.json` (1 Fehler)
* `StructureDefinition-mii-pr-onko-krk-mrt-mesorektale-faszie.json` (1 Fehler)

##### Externe Abhängigkeiten (EXTERNAL)

| | | |
| :--- | :--- | :--- |
| **MedDRA** | Proprietäre Terminologie, nicht öffentlich validierbar | Adverse Events können nicht vollständig validiert werden |
| **ICD-O-3** | Morphologie-Codes limitiert verfügbar in FHIR TX-Servern | Histologie-Codierung teilweise nicht validierbar |
| **OPS Versionen** | Multiple OPS-Versionen führen zu Warnungen | Procedure-Validierung zeigt Warnungen bei Versionsmix |

#### Status-Legende

| | | |
| :--- | :--- | :--- |
| 🔴 | **TODO** | Aktiv zu behebende Fehler |
| 🟡 | **MONITOR** | Beobachten, ggf. Aktion erforderlich |
| 🔵 | **EXTERNAL** | Externes Problem, löst sich durch Updates von Abhängigkeiten |
| ⚪ | **FILTERED** | Durch advisor.json gefiltert |

#### Continuous Integration

Die FHIR-Validierung läuft automatisch bei jedem Push über GitHub Actions:

* **JAVA_FHIR_VALIDATION**: HL7 FHIR Validator (offiziell)
* **DOTNET_FHIR_VALIDATION**: Firely .NET Validator (alternativ)

🔗 [Aktuelle CI-Runs anzeigen](https://github.com/medizininformatik-initiative/kerndatensatzmodul-onkologie/actions)

Die Validierungsergebnisse sind direkt im Repository verfügbar:

* [`validation.html`](https://github.com/medizininformatik-initiative/kerndatensatzmodul-onkologie/blob/dev/validation.html) - HTML-Report
* [`validation.json`](https://github.com/medizininformatik-initiative/kerndatensatzmodul-onkologie/blob/dev/validation.json) - Maschinenlesbare Ergebnisse

#### Wie kann ich helfen?

Wenn Sie zur Verbesserung der Validierung beitragen möchten:

1. **Prüfen Sie**die TODO-markierten Fehler oben
1. **Laden Sie**die Validierungs-Artefakte aus den[CI-Runs](https://github.com/medizininformatik-initiative/kerndatensatzmodul-onkologie/actions)herunter
1. **Erstellen Sie**einen Issue oder Pull Request im[GitHub Repository](https://github.com/medizininformatik-initiative/kerndatensatzmodul-onkologie)

**Hinweis**: Diese Seite wird manuell gepflegt. Für den aktuellsten technischen Stand siehe die CI-Runs im Repository.

