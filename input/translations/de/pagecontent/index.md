<!-- markdownlint-disable MD041 -->
<!--
  HOME PAGE — GERMAN TRANSLATION of the source page input/pagecontent/index.md
  (English is the IG's default language). The structure follows the standard MII
  module IG page set (MII IG template and kerndatensatz-basis). See
  docs/recipes/add-translation.md; keep this file in step with the English
  source.
-->

<!-- DERIVED:bridge source=Index.page.md gate=B -->
> **Written during migration - review before release.** Dieser Leitfaden ist
> eine **inoffizielle Probe-Migration** des MII-Kerndatensatz-Moduls
> *Onkologie* v2026.0.3 auf die FGDH-Vorlage für MII-KDS-Module. Er ist kein
> MII-Artefakt, er ist nicht von der Medizininformatik-Initiative autorisiert,
> und nichts davon ist veröffentlicht. Verbindlich bleibt die offizielle
> MII-Spezifikation.
{: .ig-highlight .ig-highlight-blue}

### Einleitung

Diese Spezifikation beschreibt die FHIR-Repräsentation des
Kerndatensatz-(KDS-)Moduls **Onkologie** der Medizininformatik-Initiative
(MII). Sie beschreibt die Anwendungsfälle des Moduls sowie die zugehörigen
FHIR-Profile, Extensions und Terminologie-Ressourcen in ihrer verbindlichen
Form. Der MII-Kerndatensatz dient der standardisierten Nutzung klinischer
Routinedaten für die medizinische Forschung.

<!-- source: BeschreibungModulOnko.page.md -->
Das Modul Onkologie dient der Erfassung von Datenpunkten. In seiner ersten
Version orientiert sich das Modul am ADT/GEKID Basisdatensatz, der die Basis
für die nationalen Krebsregister bildet. Das umfasst diagnostische und
histologische Parameter sowie Angaben zu Behandlung, Tumor-Staging zu Beginn
und im Verlauf, sowie die Erfassung von Nebenwirkungen und Erkennung von
Metastasen.

### Inhalt und Zweck der Modellierung

<!-- source: BeschreibungModulOnko.page.md -->
Das KDS-Modul Onkologie hat das Ziel, die onkologischen Daten, die in der
Primärversorgung und bei der Krebsregistermeldung anfallen, korrekt abzubilden
und mit anderen Datenquellen in Beziehung zu bringen.

Fokus der ersten Implementierungsversion ist die Überführung der im oBDS
anfallenden Registerdaten für die Sekundärdatennutzung mit dem FDPG und anderen
Projekten im Rahmen von PM4Onko. Daher sind in dieser ersten Version nur die
Datenpunkte enthalten, die klinisch-diagnostische oder therapeutischen
Charakter haben. Administrative (z.B. Meldung, Melder) oder
personenidentifizierende (Person, Tumorzuordnung) Datenpunkte sind nicht
innerhalb des Betrachtungsrahmens.

Der oBDS sieht neben dem Basisdatensatz eine Erhebung von organspezifischen
Datenfeldern vor. Im ersten Umsetzungsschritt wurde auf die Umsetzung der
organspezifischen Module (Mamma, Darm, Prostata, Melanom) verzichtet.

### Mapping auf offene Datenstandards

<!-- source: BeschreibungModulOnko.page.md -->
Der onkologischen Basisdatensatz enthält ValueSets, die primär durch ADT/GEKID
definiert wurden und keinen direkten Bezug zu offenen Datenstandards und
-terminologien wie SNOMED-CT oder LOINC haben. Die Kodierung der
Antwortmöglichkeiten wurden in der gleichen Art und Weise übernommen, wie Sie
auch in den Primärsystemen vorliegen. Gleichzeitig stellt dieser
Implementierungsleitfaden ein vorläufiges Mapping der Felder und
Antwortmöglichkeiten auf SNOMED-CT (sowie ggfs. anderer Terminologien) als FHIR
ConceptMap bereit. Die Landeskrebsregister streben mit dem BfArM für Ende 2024
die Erstellung eines offiziellen nationalen Mappings der oBDS-Krebsregisterdaten
auf SNOMED-CT an. Sobald dieses offiziell veröffentlicht ist, wird das hier
enthaltene Mapping entsprechend geupdated.

| Veröffentlichung |               |
|------------------|---------------|
| Datum            | 2026-03-29 |
| Version          | 2026.0.3 (CalVer `JJJJ.n.n`) |
| Status           | active        |
| Realm            | DE            |

### Zielgruppe

Dieser Implementierungsleitfaden richtet sich an:

<div class="ig-highlight ig-highlight-blue">
<h5>Implementierende</h5>
<p>Datenintegrationszentren (DIZ), Software-Entwickelnde und System-Architekt:innen, die FHIR-basierte Lösungen umsetzen.<br/>
→ siehe <a href="profiles.html">Profile</a> und <a href="logical-models.html">Logische Modelle</a>.</p>
</div>

<div class="ig-highlight ig-highlight-green">
<h5>Forschende</h5>
<p>Wissenschaftler:innen, die KDS-Daten für die medizinische Forschung nutzen.<br/>
→ siehe <a href="researcher-guidance.html">Anleitung für Forschende</a>.</p>
</div>

### Inhalt dieses Leitfadens

- **[Anleitung](guidance.html)** — Einstieg und fachliche Hinweise.
- **Konformität** — die KDS-weiten Konformitätsregeln (Anforderungssprache,
  Must-Support, Umgang mit fehlenden Daten) pflegt zentral das
  [Meta-Modul](https://github.com/medizininformatik-initiative/kerndatensatz-meta/wiki/Conformance);
  die modul-spezifischen Aspekte zu
  [Sicherheit und Datenschutz](security-and-privacy.html) sind Teil dieses
  Leitfadens.
- **[Profile](profiles.html)** und die weiteren
  **[Artefakt-Seiten](artifacts.html)** — die technischen Artefakte.
- **[Beispiele](examples.html)** — Beispielinstanzen.
- **[Abhängigkeiten](ImplementationGuide-mii-ig-onko-de-v2026.html)** — die
  ImplementationGuide-Ressource mit Abhängigkeitstabelle, versionsübergreifender
  Analyse und Urheberrechtshinweisen.

### Verwandte Leitfäden

Dieses Modul ist Teil des MII-Kerndatensatzes; die weiteren KDS-Module und ihre
Abhängigkeiten sind unter
[medizininformatik-initiative.de](https://www.medizininformatik-initiative.de/)
beschrieben.

> [TODO: Nennen Sie die formalen Abhängigkeiten (siehe `dependencies` in
> `sushi-config.yaml`) und verwandte Leitfäden Ihres Moduls.]
{: .ig-highlight .ig-highlight-grey}

Weitere FHIR-Implementierungsleitfäden finden Sie im offiziellen
**[FHIR IG Registry](https://fhir.org/guides/registry/)** (Quelle:
[`FHIR/ig-registry`](https://github.com/FHIR/ig-registry)).

### Impressum

Dieser Leitfaden ist im Rahmen der Medizininformatik-Initiative erstellt worden
und unterliegt per Governance-Prozess dem Abstimmungsverfahren des
Interoperabilitätsforums und der Technischen Komitees von HL7 Deutschland e. V.

### Ansprechpartner

Fragen zu dieser Publikation können im HL7-FHIR-Zulip
[chat.fhir.org](https://chat.fhir.org) im Stream `german/mi-initiative` oder im
MII-Zulip [mii.zulipchat.com](https://mii.zulipchat.com/) im Stream
`MII-Kerndatensatz` gestellt werden.
Anmerkungen und Kritik werden als *Issues* auf
[GitHub](https://github.com/forschungsgruppe-digital-health/mii-kds-onko-ig-inoffiziell/issues) entgegengenommen.

<!-- source: Index.page.md -->
* Thomas Debertshäuser, Berlin Institute of Health (Charité)
* Martin Boeker (DIFUTURE)
* Sylvia Thun, Berlin Institute of Health (Charité)
* Karoline Buckow, TMF – Technologie- und Methodenplattform für die vernetzte medizinische Forschung e.V.
* Franziska Klepka, TMF – Technologie- und Methodenplattform für die vernetzte medizinische Forschung e.V.

### Autor:innen (in alphabetischer Reihenfolge)

<!-- source: Index.page.md -->
* Christian Gulden (BZKF / Erlangen)
* Jori Kern (DKFZ Heidelberg)
* Julian Saß, Berlin Institute of Health (Charité)
* Margaux Gatrio, Berlin Institute of Health (Charité)
* Lotte Schwiening, Berlin Institute of Health (Charité)
* Paul Müller, Berlin Institute of Health (Charité)
* Nina Haffer, Berlin Institute of Health (Charité)
* Sophie Klopfenstein, Berlin Institute of Health (Charité)
* Thomas Debertshäuser, Berlin Institute of Health (Charité)
* Yuan Peng, Institut für Medizinische Informatik und Biometrie (TU Dresden)

### Urheberrecht und Lizenz

© 2021+ TMF e. V., Charlottenstraße 42, 10117 Berlin

Dieses Werk ist lizenziert unter der
[Creative Commons Namensnennung 4.0 International Lizenz (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0/deed.de).

Für die Nutzungsrechte der zugrunde liegenden FHIR-Technologie siehe die
FHIR-Basisspezifikation.

Einige der verwendeten Codesysteme werden von anderen Organisationen
veröffentlicht und gepflegt; es gilt das Urheberrecht der jeweiligen Herausgeber.

### Haftungsausschluss

Der Inhalt dieses Dokuments ist öffentlich. Bitte beachten Sie, dass Teile
dieses Dokuments auf FHIR Version R4 basieren, dessen Urheberrecht bei
HL7 International liegt.

Obwohl diese Publikation mit größter Sorgfalt erstellt wurde, können die
Autor:innen keine Haftung für direkte oder indirekte Schäden übernehmen, die
aus dem Inhalt dieser Spezifikation entstehen könnten.
