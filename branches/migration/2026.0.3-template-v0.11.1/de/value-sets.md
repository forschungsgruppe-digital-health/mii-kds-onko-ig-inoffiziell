# ValueSets - MII IG Kerndatensatz-Modul Onkologie v2026.0.3

* [**Inhaltsverzeichnis**](toc.md)
* **ValueSets**

## ValueSets

> **Optionale Seite (0..1).** Das KDS-Modulmenü führt diese Seite als **optional**. Entscheiden Sie für Ihr Modul: Seite **behalten** — Inhalte ausfüllen und dieses Banner samt `OPTIONAL-PAGE`-Marker-Kommentar löschen (in dieser Datei UND in der englischen Quellseite) — oder Seite **entfernen**, nach der Schritt-für-Schritt-Anleitung in [`docs/optional-pages.md`](https://github.com/forschungsgruppe-digital-health/mii-kds-onko-ig-inoffiziell/blob/main/docs/optional-pages.md) dieses Repositories. Ein Release darf dieses Banner nicht enthalten (Konventions-Check M9).

### ValueSets

Diese Seite beschreibt die ValueSets des Moduls **Onkologie** (Namenskonvention `MII_VS_<Modul>_<Name>`). Allgemeine Hinweise zur Verwendung von Codes: siehe [FHIR Terminology](http://hl7.org/fhir/R4/terminologies.html); die zugrunde liegenden CodeSystems beschreibt die Seite [CodeSystems](code-systems.md).

**Expansionen:** ValueSet-Expansionen dieses Leitfadens werden über einen FHIR-Terminologieserver erzeugt — über SU-TermServ, sofern das Client-Zertifikat konfiguriert ist, sonst über den öffentlichen HL7-Server `tx.fhir.org` (dann expandieren einige KDS-spezifische ValueSets ggf. nicht vollständig).

> [TODO: Falls Ihr Modul SNOMED CT nutzt, geben Sie die verwendete Edition/Version an. Listen Sie die modul-eigenen ValueSets auf oder verweisen Sie auf die automatisch erzeugte Artefakt-Liste — oder entfernen Sie diese Seite, wenn Ihr Modul keine definiert.]

### Terminologien der Systemischen Therapie

#### Übersicht

Die MII stellt **kuratierte, onkologierelevante Terminologien** für systemische Therapien bereit:

* **Therapieprotokolle**: 96 oBDS-basierte Standardprotokolle ([CodeSystem](https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/CodeSystem/mii-cs-onko-systemische-therapie-protokolle))
* **ATC-Substanzen**: Haupt-ValueSet + 8 jahresspezifische ValueSets (2018-2025)
* **UNII-Substanzen**: Für Wirkstoffe ohne ATC-Code ([ValueSet](https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/ValueSet/mii-vs-onko-systemische-therapie-substanzen-unii))

**Wichtig**: Die ValueSets enthalten nur onkologisch relevante Substanzen, nicht die vollständige ATC-Klassifikation.

#### Therapieprotokolle

Die Protokolle stehen im CodeSystem `mii-cs-onko-systemische-therapie-protokolle`.

**Beispiele häufiger Protokolle**: FOLFOX, R-CHOP, AC, BEACOPP, ICE

Neue Protokolle bitte unter [GitHub Issues](https://github.com/medizininformatik-initiative/kerndatensatzmodul-onkologie/issues) einreichen.

#### ATC-Substanzen

##### Haupt-ValueSet (Aktuelle Codes)

Die aktuellen Codes stehen im ValueSet `mii-vs-onko-systemische-therapie-substanzen`.

##### Jahresspezifische ValueSets

Für die Validierung historischer Daten stehen jahresspezifische ValueSets zur Verfügung:

| | | |
| :--- | :--- | :--- |
| 2025 | mii-vs-onko-systemische-therapie-substanzen-2025 | [Link](https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/ValueSet/mii-vs-onko-systemische-therapie-substanzen-2025) |
| 2024 | mii-vs-onko-systemische-therapie-substanzen-2024 | [Link](https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/ValueSet/mii-vs-onko-systemische-therapie-substanzen-2024) |
| 2023 | mii-vs-onko-systemische-therapie-substanzen-2023 | [Link](https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/ValueSet/mii-vs-onko-systemische-therapie-substanzen-2023) |
| 2022 | mii-vs-onko-systemische-therapie-substanzen-2022 | [Link](https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/ValueSet/mii-vs-onko-systemische-therapie-substanzen-2022) |
| 2021 | mii-vs-onko-systemische-therapie-substanzen-2021 | [Link](https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/ValueSet/mii-vs-onko-systemische-therapie-substanzen-2021) |
| 2020 | mii-vs-onko-systemische-therapie-substanzen-2020 | [Link](https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/ValueSet/mii-vs-onko-systemische-therapie-substanzen-2020) |
| 2019 | mii-vs-onko-systemische-therapie-substanzen-2019 | [Link](https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/ValueSet/mii-vs-onko-systemische-therapie-substanzen-2019) |
| 2018 | mii-vs-onko-systemische-therapie-substanzen-2018 | [Link](https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/ValueSet/mii-vs-onko-systemische-therapie-substanzen-2018) |

##### ATC-Code Transitionen

Die deutsche ATC-Klassifikation wird jährlich aktualisiert. **Beispiel Quizartinib** (FLT3-Inhibitor):

* **Bis 31.12.2020**: `L01XE52`
* **Ab 01.01.2021**: `L01EX11`

**Kodierungsempfehlung**: Verwenden Sie den ATC-Code, der zum Therapiezeitpunkt gültig war. Bei Unsicherheit kann alternativ der UNII-Code verwendet werden.

Weitere Beispiele: Abemaciclib (L01XE50 → L01EF03), Acalabrutinib (L01XE51 → L01EL02).

##### Post-hoc Annotation von Freitext

DIZ **dürfen** historische Freitext-Medikationsdaten nachträglich auf ATC-Codes mappen, wenn:

1. **Provenance dokumentiert**wird (nachträgliche Kodierung kennzeichnen)
1. **Aktuelle ATC-Codes**verwendet werden (nicht historische)
1. **Originaltext erhalten**bleibt in`medicationCodeableConcept.text`

#### UNII-Substanzen

Die UNII-Codes stehen im ValueSet `mii-vs-onko-systemische-therapie-substanzen-unii`.

##### Substanzen ohne verfügbare Codes

Die folgenden oBDS-Einträge haben weder ATC- noch UNII-Codes:

* **EmboCept, Embozene, Hepasphere**: Embolisations-Mikrosphären
* **GcMAF**: Gc protein-derived macrophage activating factor
* **G-CSF**: Granulocyte colony-stimulating factor (generische Bezeichnung)
* **Studienmedikament**: Generische Platzhalter-Bezeichnung

→ Verwenden Sie `Coding.text` mit Freitext.

**Neu verfügbar:** **Dinatriumfolinat** ist nun als **LEUCOVORIN SODIUM** (UNII: 4MXU9LJS4Q) im UNII ValueSet und als **Natriumfolinat** (ATC: V03AF06) in den ATC ValueSets verfügbar.

#### Terminologie-Binding in Profilen

**Procedure (Protokoll)**:

```
* usedCode from MII_VS_Onko_Systemische_Therapie_Protokolle (extensible)

```

**MedicationStatement (Substanz)**:

```
* medicationCodeableConcept from MII_VS_Onko_Systemische_Therapie_Substanzen (extensible)

```

### Terminologien der Weiteren Klassifikationen

Diese Seite dokumentiert die Terminologien für weitere Klassifikationen in der Onkologie, einschließlich hämatologischer und organspezifischer Staging-Systeme.

> **Written during migration - review before release.** Dieser Abschnitt behandelt nur die Terminologie-Artefakte. Das Profil, das sie bindet, ist auf einer eigenen Seite dokumentiert: [Weitere Klassifikationen](StructureDefinition-mii-pr-onko-weitere-klassifikationen.md); dessen Intro beschreibt die Klassifikationssysteme klinisch und stellt das code+method+value-Pattern vollständig dar.

#### Hintergrund

Der oBDS definiert hauptsächlich TNM als Stagingsystem aus, viele weitere krankheits- ode rorganspezifischen Staging- und Gradingsysteme werden im oBDS über das Freitextfeld Weitere Klassifikationen abgebildet. Dazu gehören z.B. das Nottigham Grading beim Brustkrebs oder Ann Arbor bei Die Plattform 65c stellt Einige der Staging-Systeme sind international gebräuchlich und bereits in CodeSystems wie SNOMED-CT und NCIt/UMLS enthalten, während andere primär im deutschen/deutschsprachigen Kontext verwendet werden.

Auch wenn für einige Staging-Systeme ein SNOMED-Code vorhanden ist und dieser für die Interoperabilität besser ist als ein eigenen CodeSystem, haben wir uns für die Abbildung gemäß des oBDS entschieden, da ggfs. die Daten an den Standorten direkt in diesem Format vorliegen. Eine SNOMED-Annotierung kann hier in zukünftigen Versionen via ConceptMaps angestrebt werden.

#### Hierarchisches CodeSystem für Klassifikationssysteme

Das **Weitere Klassifikationen CodeSystem** nutzt eine hierarchische Struktur zur Organisation verschiedener Staging- und Klassifikationssysteme. Es wird als `mii-cs-onko-weitere-klassifikationen-obds` veröffentlicht.

#### ValueSets mit descendant-of Filter

Die ValueSets nutzen **descendant-of Filter** für wartbare Terminologie-Verwaltung.

> **Written during migration - review before release.** Die Quellseite hat die Konzepte und die ValueSets über generierte Abfragen aufgelistet, die nicht in diesen Guide übernommen werden. Die veröffentlichte Familie besteht aus: dem CodeSystem [Weitere Klassifikationen oBDS](CodeSystem-mii-cs-onko-weitere-klassifikationen-obds.md), das 20 Klassifikationssysteme als oberste Konzepte und deren 161 Klassifikationswerte als Unterkonzepte enthält; dem ValueSet [Weitere Klassifikationen](ValueSet-mii-vs-onko-weitere-klassifikationen.md), das die Klassifikationssysteme selbst aus SNOMED CT und dem NCI Thesaurus aufzählt; und dem ValueSet [Weitere Klassifikationen - Auspraegungen](ValueSet-mii-vs-onko-weitere-klassifikationen-auspraegungen.md), das die Werte je Klassifikationssystem über einen Filter auf das oBDS-CodeSystem auswählt. Überschrift und Einleitungssatz oben geben die Quellseite wieder, die die Werte dem ersten der beiden ValueSets zuordnet und den Filter-Operator `descendant-of` nennt - bitte vor dem Release abgleichen.

#### mCODE STU4 Pattern Integration

Die Implementierung folgt dem **mCODE STU4 code+method+value Pattern**.

**Beispiel-Implementierung:**

```
Instance: mii-exa-onko-weitere-klassifikationen-binet
InstanceOf: MII_PR_Onko_Weitere_Klassifikationen

// Allgemeiner Code für Staging
* code = $sct#385388004 "Tumorstadium-Befund"

// Spezifische Methode
* method = $mii-cs-onko-weitere-klassifikationen#binet "BINET Staging System"

// Tatsächlicher Wert
* valueCodeableConcept = $mii-cs-onko-weitere-klassifikationen#binet-a "BINET A"

```

#### Mapping zu oBDS

Die Weitere Klassifikationen entsprechen dem **oBDS Feld 9 "Weitere Klassifikationen"**.

#### SNOMED CT Mappings

Für einige Klassifikationssysteme existieren SNOMED CT Äquivalente:

* BINET → SNOMED CT: 1149214008 (Binet chronic lymphocytic leukemia staging)
* Ann Arbor → SNOMED CT: 254373007 (Ann Arbor lymphoma staging)
* WHO Grade → SNOMED CT: 277612008 (WHO tumor grade)

#### Beispiele

* FIGO Stadium IVB (Ovariale Tumore): [mii-exa-onko-weitere-klassifikationen-1](Observation-mii-exa-onko-weitere-klassifikationen-1.md)
* Ann Arbor Stadium IIIX: [mii-exa-onko-weitere-klassifikationen-2](Observation-mii-exa-onko-weitere-klassifikationen-2.md)
* FIGO Grad 2: [mii-exa-onko-weitere-klassifikationen-3](Observation-mii-exa-onko-weitere-klassifikationen-3.md)

### Terminologie-Bindungen nach Datenbereich

> **Written during migration - review before release.** Verdichtet aus der Seite **Terminologien** des Quell-Guides, die jede Terminologie ausführlich auf der Seite [CodeSystems](code-systems.md) beschreibt. An welche Terminologie die ValueSets je Datenbereich binden:
* Primärdiagnose, Vorerkrankungen und Todesursache — ICD-10-GM; das Modul folgt hier bewusst den Vorgaben des oBDS und nicht der ICD-10-WHO, die das BfArM für Todesursachen empfiehlt
* Lokalisierung des Primärtumors — ICD-O-3 Topographie; die morphologische Beschaffenheit — ICD-O-3 Morphologie
* operative Prozeduren — OPS
* Medikation der systemischen Therapie — ATC, mit UNII als zweitem System für Substanzen ohne etablierten ATC-Code; deshalb erlaubt das SystemischeTherapie-MedicationStatement-Profil eine duale Kodierung (die ValueSets listet der Abschnitt oben)
* Nebenwirkungen — CTCAE im Nebenwirkungsprofil; MedDRA deckt den weiteren Umfang aus Pharmazeutika, Biologika, Vakzinen und Arzneimittel/Geräte-Kombinationen ab
* Tumorstadium — die TNM-Klassifikation in ihrer 8. Auflage, herausgegeben zusammen mit der Union for International Cancer Control (UICC)
* Codes und Maßeinheiten von Observations — LOINC, SNOMED-CT und UCUM

