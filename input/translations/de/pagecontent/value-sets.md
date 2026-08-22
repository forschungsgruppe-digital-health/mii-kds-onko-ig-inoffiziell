<!-- markdownlint-disable MD041 -->
<!-- Deutsche Übersetzung von input/pagecontent/value-sets.md (aufgeteilt aus
     der früheren Seite terminology.md gemäß der TF-KDS-abgestimmten Menüstruktur).
     Der IG-Publisher listet die ValueSets auf den Artefakt-Seiten automatisch;
     hier stehen die MII-Hinweise dazu. -->
<!-- OPTIONAL-PAGE (0..1) — Marker entfernen, wenn die Seite BLEIBT; andernfalls
     die Seite gemäß docs/optional-pages.md entfernen. Der Konventions-Check
     (M9) lässt ein Release mit diesem Marker fehlschlagen. -->

> **Optionale Seite (0..1).** Das KDS-Modulmenü führt diese Seite als
> *optional*. Entscheiden Sie für Ihr Modul: Seite **behalten** — Inhalte
> ausfüllen und dieses Banner samt `OPTIONAL-PAGE`-Marker-Kommentar löschen (in
> dieser Datei UND in der englischen Quellseite) — oder Seite **entfernen**,
> nach der Schritt-für-Schritt-Anleitung in [`docs/optional-pages.md`](https://github.com/forschungsgruppe-digital-health/mii-kds-onko-ig-inoffiziell/blob/main/docs/optional-pages.md) dieses
> Repositories. Ein Release darf dieses Banner nicht enthalten
> (Konventions-Check M9).
{: .ig-highlight .ig-highlight-grey}

### ValueSets

Diese Seite beschreibt die ValueSets des Moduls **Onkologie**
(Namenskonvention `MII_VS_<Modul>_<Name>`). Allgemeine Hinweise zur Verwendung
von Codes: siehe
[FHIR Terminology](http://hl7.org/fhir/R4/terminologies.html); die
zugrunde liegenden CodeSystems beschreibt die Seite
[CodeSystems](code-systems.html).

{:.bg-info}
**Expansionen:** ValueSet-Expansionen dieses Leitfadens werden über einen
FHIR-Terminologieserver erzeugt — über SU-TermServ, sofern das
Client-Zertifikat konfiguriert ist, sonst über den öffentlichen HL7-Server
`tx.fhir.org` (dann expandieren einige KDS-spezifische ValueSets ggf. nicht
vollständig).

> [TODO: Falls Ihr Modul SNOMED CT nutzt, geben Sie die verwendete
> Edition/Version an. Listen Sie die modul-eigenen ValueSets auf oder verweisen
> Sie auf die automatisch erzeugte Artefakt-Liste — oder entfernen Sie diese
> Seite, wenn Ihr Modul keine definiert.]
{: .ig-highlight .ig-highlight-grey}

<!-- source: Systemische-Therapie-Terminologien.page.md (Simplifier-Guide,
     TechnischeImplementierung/FHIR-Profile/Systemische-Therapie/) — eine
     Gruppenseite zur CodeSystem-/ValueSet-Familie der Systemischen Therapie und
     daher hier als Abschnitt statt als Artefakt-Intro-Note. FQL-Blöcke, die
     Name/Status/Version/Code-Anzahl abfragten, wurden entfernt - der
     IG-Publisher stellt diese Angaben auf den Artefaktseiten dar. -->
### Terminologien der Systemischen Therapie

#### Übersicht

Die MII stellt **kuratierte, onkologierelevante Terminologien** für systemische Therapien bereit:

- **Therapieprotokolle**: 96 oBDS-basierte Standardprotokolle ([CodeSystem](https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/CodeSystem/mii-cs-onko-systemische-therapie-protokolle))
- **ATC-Substanzen**: Haupt-ValueSet + 8 jahresspezifische ValueSets (2018-2025)
- **UNII-Substanzen**: Für Wirkstoffe ohne ATC-Code ([ValueSet](https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/ValueSet/mii-vs-onko-systemische-therapie-substanzen-unii))

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

| Jahr | ValueSet | Canonical URL |
|------|----------|---------------|
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

- **Bis 31.12.2020**: `L01XE52`
- **Ab 01.01.2021**: `L01EX11`

**Kodierungsempfehlung**: Verwenden Sie den ATC-Code, der zum Therapiezeitpunkt gültig war. Bei Unsicherheit kann alternativ der UNII-Code verwendet werden.

Weitere Beispiele: Abemaciclib (L01XE50 → L01EF03), Acalabrutinib (L01XE51 → L01EL02).

##### Post-hoc Annotation von Freitext

DIZ **dürfen** historische Freitext-Medikationsdaten nachträglich auf ATC-Codes mappen, wenn:

1. **Provenance dokumentiert** wird (nachträgliche Kodierung kennzeichnen)
2. **Aktuelle ATC-Codes** verwendet werden (nicht historische)
3. **Originaltext erhalten** bleibt in `medicationCodeableConcept.text`

<details>
<summary>Beispiel: Post-Annotation</summary>

```fsh
Instance: mii-exa-onko-medikation-quizartinib-postannotated
InstanceOf: MII_PR_Onko_Systemische_Therapie_Medikation

* status = #completed
* subject = Reference(Patient/example)
* medicationCodeableConcept.coding[atcClassDe] = $atc-de#L01EX11 "Quizartinib"
* medicationCodeableConcept.text = "Quizartinib (Original: Freitext aus oBDS)"
* effectivePeriod.start = "2020-09-15"  // Therapie vor Code-Änderung
* effectivePeriod.end = "2020-12-15"
```

</details>

#### UNII-Substanzen

Die UNII-Codes stehen im ValueSet `mii-vs-onko-systemische-therapie-substanzen-unii`.

##### Substanzen ohne verfügbare Codes

Die folgenden oBDS-Einträge haben weder ATC- noch UNII-Codes:

- **EmboCept, Embozene, Hepasphere**: Embolisations-Mikrosphären
- **GcMAF**: Gc protein-derived macrophage activating factor
- **G-CSF**: Granulocyte colony-stimulating factor (generische Bezeichnung)
- **Studienmedikament**: Generische Platzhalter-Bezeichnung

→ Verwenden Sie `Coding.text` mit Freitext.

**Neu verfügbar:** **Dinatriumfolinat** ist nun als **LEUCOVORIN SODIUM** (UNII: 4MXU9LJS4Q) im UNII ValueSet und als **Natriumfolinat** (ATC: V03AF06) in den ATC ValueSets verfügbar.

<details>
<summary>Besondere Hinweise zu UNII-Substanzen (Klicken zum Aufklappen)</summary>

- **OLAPTESED PEGOL** (UNII: MTM792B442): Oft nur als "Olaptesed" dokumentiert
- **GEBASAXTUREV** (UNII: 4B57CWT710): Auch bekannt als "Coxsackievirus A21"
- **Daromun**: Entspricht **DARLEUKIN** (UNII: 2OQ3OPV2F8) oder **ONFEKAFUSP ALFA** (UNII: 6HXC0O6JMV)
- **Fibromun**: Entspricht **ONFEKAFUSP ALFA** (UNII: 6HXC0O6JMV)
- **LONCASTUXIMAB TESIRINE** (UNII: 7K5O7P6QIU): oBDS-Tippfehler "Ioncastuzimab tesiren"
- **NIDANILIMAB** (UNII: ND296JF21I): In oBDS als "Nadunolimab" gelistet
- **HUMAN PARVOVIRUS B19** (UNII: 94N635564T): Möglicherweise nicht identisch mit "Parvovirus H1"
- **PACLITAXEL** (UNII: P88XT4IS4D): oBDS meint wahrscheinlich "nab-Paclitaxel" (separate UNII möglich)
- **CYTARABINE** (UNII: 04079A1RDZ): oBDS meint wahrscheinlich liposomale Formulierung
- **DEPATUXIZUMAB** (UNII: W984C353CG): Ohne "mafodotin"-Teil (Toxin)

</details>

#### Terminologie-Binding in Profilen

**Procedure (Protokoll)**:

```fsh
* usedCode from MII_VS_Onko_Systemische_Therapie_Protokolle (extensible)
```

**MedicationStatement (Substanz)**:

```fsh
* medicationCodeableConcept from MII_VS_Onko_Systemische_Therapie_Substanzen (extensible)
```

<!-- source: Weitere-Klassifikationen-Terminologien.page.md (Simplifier-Guide,
     TechnischeImplementierung/FHIR-Profile/Weitere-Klassifikationen/) — eine
     Gruppenseite, die die CodeSystem- und ValueSet-Familie hinter dem Profil
     Weitere Klassifikationen beschreibt; sie landet daher hier als Abschnitt und
     nicht als Intro-Note eines Artefakts (der Quelltext spricht weiterhin von
     "dieser Seite"). FQL-Blöcke, die Konzepte, ValueSets und Profilelemente
     aufgelistet haben, wurden entfernt; der IG Publisher stellt diese auf den
     Artefaktseiten dar. -->
### Terminologien der Weiteren Klassifikationen

Diese Seite dokumentiert die Terminologien für weitere Klassifikationen in der Onkologie, einschließlich hämatologischer und organspezifischer Staging-Systeme.

<!-- DERIVED:bridge source=Weitere-Klassifikationen-Terminologien.page.md gate=B -->
> **Written during migration - review before release.** Dieser Abschnitt behandelt
> nur die Terminologie-Artefakte. Das Profil, das sie bindet, ist auf einer eigenen
> Seite dokumentiert: [Weitere Klassifikationen](StructureDefinition-mii-pr-onko-weitere-klassifikationen.html);
> dessen Intro beschreibt die Klassifikationssysteme klinisch und stellt das
> code+method+value-Pattern vollständig dar.
{: .ig-highlight .ig-highlight-blue}

#### Hintergrund

<!-- Quelldefekt, unverändert übernommen: dieser Absatz bricht zweimal mitten im
     Satz ab ("... oder Ann Arbor bei" und "Die Plattform 65c stellt"), schreibt
     "Nottingham" als "Nottigham", und der erste Satz ist in der Quelle
     grammatikalisch defekt ("definiert ... aus"). Bei der Migration nicht
     korrigiert - bitte prüfen. -->
Der oBDS definiert hauptsächlich TNM als Stagingsystem aus, viele weitere krankheits- ode rorganspezifischen Staging- und Gradingsysteme werden im oBDS über das Freitextfeld Weitere Klassifikationen abgebildet. Dazu gehören z.B. das Nottigham Grading beim Brustkrebs oder Ann Arbor bei
Die Plattform 65c stellt
Einige der Staging-Systeme sind international gebräuchlich und bereits in CodeSystems wie SNOMED-CT und NCIt/UMLS enthalten, während andere primär im deutschen/deutschsprachigen Kontext verwendet werden.

Auch wenn für einige Staging-Systeme ein SNOMED-Code vorhanden ist und dieser für die Interoperabilität besser ist als ein eigenen CodeSystem, haben wir uns für die Abbildung gemäß des oBDS entschieden, da ggfs. die Daten an den Standorten direkt in diesem Format vorliegen. Eine SNOMED-Annotierung kann hier in zukünftigen Versionen via ConceptMaps angestrebt werden.

#### Hierarchisches CodeSystem für Klassifikationssysteme

Das **Weitere Klassifikationen CodeSystem** nutzt eine hierarchische Struktur zur Organisation verschiedener Staging- und Klassifikationssysteme. Es wird als `mii-cs-onko-weitere-klassifikationen-obds` veröffentlicht.

<!-- Quelldefekt: die Quellseite führt die Überschriften "Struktur des
     hierarchischen Ansatzes" und "Alle Klassifikationssysteme (Elternkonzepte)"
     ohne jeden Inhalt - die Konzeptliste wurde nie geschrieben. Die leeren
     Überschriften wurden weggelassen; die DERIVED-Zusammenfassung unten nennt den
     Inhalt der veröffentlichten Artefakte. -->

#### ValueSets mit descendant-of Filter

Die ValueSets nutzen **descendant-of Filter** für wartbare Terminologie-Verwaltung.

<!-- Quelldefekt: die Quellseite nennt mii-vs-onko-weitere-klassifikationen das
     "Haupt-ValueSet für alle Klassifikationswerte" und bezeichnet den Filter-
     Operator als "descendant-of". In den veröffentlichten Artefakten liegen die
     Klassifikationswerte in mii-vs-onko-weitere-klassifikationen-auspraegungen,
     der Filter-Operator ist "is-a", und mii-vs-onko-weitere-klassifikationen
     enthält die Klassifikationssysteme. Bei der Migration nicht korrigiert -
     bitte prüfen. -->

<!-- DERIVED:summary source=Weitere-Klassifikationen-Terminologien.page.md gate=B -->
> **Written during migration - review before release.** Die Quellseite hat die
> Konzepte und die ValueSets über generierte Abfragen aufgelistet, die nicht in
> diesen Guide übernommen werden. Die veröffentlichte Familie besteht aus: dem
> CodeSystem
> [Weitere Klassifikationen oBDS](CodeSystem-mii-cs-onko-weitere-klassifikationen-obds.html),
> das 20 Klassifikationssysteme als oberste Konzepte und deren 161
> Klassifikationswerte als Unterkonzepte enthält; dem ValueSet
> [Weitere Klassifikationen](ValueSet-mii-vs-onko-weitere-klassifikationen.html),
> das die Klassifikationssysteme selbst aus SNOMED CT und dem NCI Thesaurus
> aufzählt; und dem ValueSet
> [Weitere Klassifikationen - Auspraegungen](ValueSet-mii-vs-onko-weitere-klassifikationen-auspraegungen.html),
> das die Werte je Klassifikationssystem über einen Filter auf das oBDS-CodeSystem
> auswählt. Überschrift und Einleitungssatz oben geben die Quellseite wieder, die
> die Werte dem ersten der beiden ValueSets zuordnet und den Filter-Operator
> `descendant-of` nennt - bitte vor dem Release abgleichen.
{: .ig-highlight .ig-highlight-blue}

#### mCODE STU4 Pattern Integration

Die Implementierung folgt dem **mCODE STU4 code+method+value Pattern**.

**Beispiel-Implementierung:**

<!-- Quelldefekt, unverändert übernommen: der Block unten nennt die Instanz
     mii-exa-onko-weitere-klassifikationen-binet und den Alias
     $mii-cs-onko-weitere-klassifikationen; die veröffentlichten Artefakte sind
     mii-exa-onko-weitere-klassifikationen-4 und das CodeSystem
     mii-cs-onko-weitere-klassifikationen-obds. Bei der Migration nicht korrigiert -
     bitte prüfen. -->

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

- BINET → SNOMED CT: 1149214008 (Binet chronic lymphocytic leukemia staging)
- Ann Arbor → SNOMED CT: 254373007 (Ann Arbor lymphoma staging)
- WHO Grade → SNOMED CT: 277612008 (WHO tumor grade)

#### Beispiele

- FIGO Stadium IVB (Ovariale Tumore): [mii-exa-onko-weitere-klassifikationen-1](Observation-mii-exa-onko-weitere-klassifikationen-1.html)
- Ann Arbor Stadium IIIX: [mii-exa-onko-weitere-klassifikationen-2](Observation-mii-exa-onko-weitere-klassifikationen-2.html)
- FIGO Grad 2: [mii-exa-onko-weitere-klassifikationen-3](Observation-mii-exa-onko-weitere-klassifikationen-3.html)

<!-- source: Terminologien.page.md (Simplifier-Guide,
     TechnischeImplementierung/Terminologien.page.md) — ValueSet-relevanter Teil;
     die Terminologien selbst beschreibt code-systems.md. -->
### Terminologie-Bindungen nach Datenbereich

<!-- DERIVED:summary source=Terminologien.page.md gate=B -->
> **Written during migration - review before release.** Verdichtet aus der
> Seite *Terminologien* des Quell-Guides, die jede Terminologie ausführlich auf
> der Seite [CodeSystems](code-systems.html) beschreibt. An welche Terminologie
> die ValueSets je Datenbereich binden:
>
> - Primärdiagnose, Vorerkrankungen und Todesursache — ICD-10-GM; das Modul
>   folgt hier bewusst den Vorgaben des oBDS und nicht der ICD-10-WHO, die das
>   BfArM für Todesursachen empfiehlt
> - Lokalisierung des Primärtumors — ICD-O-3 Topographie; die morphologische
>   Beschaffenheit — ICD-O-3 Morphologie
> - operative Prozeduren — OPS
> - Medikation der systemischen Therapie — ATC, mit UNII als zweitem System für
>   Substanzen ohne etablierten ATC-Code; deshalb erlaubt das
>   SystemischeTherapie-MedicationStatement-Profil eine duale Kodierung (die
>   ValueSets listet der Abschnitt oben)
> - Nebenwirkungen — CTCAE im Nebenwirkungsprofil; MedDRA deckt den weiteren
>   Umfang aus Pharmazeutika, Biologika, Vakzinen und
>   Arzneimittel/Geräte-Kombinationen ab
> - Tumorstadium — die TNM-Klassifikation in ihrer 8. Auflage, herausgegeben
>   zusammen mit der Union for International Cancer Control (UICC)
> - Codes und Maßeinheiten von Observations — LOINC, SNOMED-CT und UCUM
{: .ig-highlight .ig-highlight-blue}
