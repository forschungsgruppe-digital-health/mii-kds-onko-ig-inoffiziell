Dieses Profil beschreibt eine Strahlentherapie in der Onkologie. Das Strahlentherapieprofil für die Onkologie basiert auf dem Prozedurenmodul der MII. Es übernimmt damit die zwingende Angabe von OPS als Kodierung für die Art der Prozedur. Da die Details der Prozedur in den einzelnen Bestrahlungselementen hinterlegt sind, soll hier die OPS für Strahlentherapie kodiert werden.

Das MII-Modul Prozedur besitzt bereits eine Extension [Durchführungsabsicht](https://www.medizininformatik-initiative.de/fhir/core/modul-prozedur/StructureDefinition/Durchfuehrungsabsicht) mit Binding auf SNOMED-CT Codes. Da die Intention der Strahlentherapie im oBDS jedoch durch ein oBDS-spezifisches Antwortspektrum erfasst wird, wurde die Prozedur um eine zusätzliches Element "Intention" erweitert. Ebenso wird der Zusammenhang zu eventuellen Operationen (z.B. adjuvant/neoadjuvant) über das Erweiterungselement "Stellung" erfasst.

Die spezifischen Details der Strahlentherapie werden in einzelnen Bestrahlungen unterteilt und berichtet. Dabei wird jede Bestrahlung als Extension erfasst.

Komplikationen der Strahlentherapie werden nicht als `Procedure.complication` oder `Procedure.complicationReference` kodiert, sondern wie bei der Systemischen Therapie in einer gesonderten AdverseEvent-Ressource mit Verweis auf die Strahlentherapie-Ressource erfasst. Es ist dabei zu beachten, dass ein Verweis auf die Strahlentherapie-Ressource unspezifisch auf die komplette Strahlentherapie und nicht auf einzelne Bestrahlungen zeigt.

Der Grund der Beendigung (unabhängig ob erfolgreich oder nicht erfolgreich) wird über `Procedure.outcome` kodiert.

### Struktur

Die Entscheidung, die Bestrahlungsdaten als Extension umzusetzen, hat mehrere Gründe.

1. Die Datenstruktur des oBDS sieht die Angabe einer Strahlentherapie-Gesamtperiode mit Start und Ende sowie einem Gesamt-Intentions und Stellung-zur-OP-Datenpunkt vor. Alle weiteren strukturierten Behandlungsinformationen zur Bestrahlung (Strahlenart, Lokalisation, Dosis, Boost etc.) sollen einzeln in einem Element "Bestrahlung" kodiert werden.
2. Die MII-Prozedur verlangt, dass jede Prozedur genau einen Code vorliegen hat, entweder OPS oder SNOMED-CT.
3. Die US-amerikanische FHIR-Datenmodell mCODE bildet die relevanten Datenpunkte in Extensions ab. Zu erwähnen ist allerdings, dass es bei mCODE hier keine Unterscheidung in übergeordnete Strahlentherapie und untergeordnete Bestrahlung gibt. mCODE sieht jedoch dafür auch detaillierte Angaben zur Größe des Zielvolumens vor.

Alternativ wurde auch eine Umsetzung diskutiert, die übergreifende Strahlentherapie als Profil konform zur MII-Prozedur zu belassen, und die untergeordneten Bestrahlungen aus der regulären `Procedure` zu profilieren. Diese Profilierung wurde wegen der größeren Anzahl von notwenidgen Ressourcen und der vorrausichtlichen Schwierigkeit der korrekten Belegung des OPS/SNOMED Codes verworfen.

### Kategorie und Codes

#### Kategorie

- Die verwendete MII-Prozedur empfiehlt die Abbildung der **Kategorie** mittels der in SNOMED übertragenen OPS-Hauptkategorien (https://www.medizininformatik-initiative.de/fhir/core/modul-prozedur/ValueSet/procedures-category-sct)
- Die vorliegende Kategorie SNOMED `277132007 | Therapeutic procedure` , die der OPS Kategorie 8 ("Nicht-operative therapeutische Maßnahmen") entspricht, beinhaltet sowohl Strahlen - als auch Nuklearmedizinische Therapie als auch bestimmte systemische Therapien (z.B. Chemo- und Immuntherapie), wobei andere systemische medikamtöse Therapien (z.B. Hormontherapie, Targeted Therapy) auch unter Kategorie 6 "Medikamente" kodiert werden können. Er ist daher unspezifisch und nicht geeignet, um z.B. innerhalb einer Forschungsfrage gezielt nach Nuklearmedizinischen Therapien zu filtern.

#### Code

- Als **Code** wird von der MII-Prozedur ein OPS-Code oder ein SNOMED-Code verlangt.
- OPS beinhaltet Kodierungen für Strahlentherapie (`8-52`) und Nuklearmedizinische Behandlung (`8-53`) mit ausführlichen Unterkodierungen. Im oBDS selbst wird bei Strahlentherapie und Nuklearmedizin jedoch nicht nach OPS kodiert, sondern folgt einer krebsregisterspezifischen Kodierung von Lokalisation, Applikationsart und Strahlungsart sowie weiteren Datenpunkten.
- In der MII-Prozedur SOLL genau eine Kodierung (OPS oder SNOMED CT) für genau eine Therapie verwendet werden. Zusätzliche Prozeduren werden als einzelne Procedure-Ressourcen abgebildet.

#### Implementierungsempfehlung

Aus den oben genannten Punkten ergibt sich folgende Kodierempfehlung für die oBDS-Strahlentherapie:

- Kategorie als SNOMED - Code
    - Kategorie für Strahlentherapie `1287742003 | Radiotherapy (procedure)`
    - Kategorie für Nuklearmedizin `399315003 | Radionuclide therapy (procedure)`
- Kodierung über OPS
    - Strahlentherapie als OPS `8-52 Strahlentherapie` (oder genauer wenn vorhanden)
    - Nuklearmedizinische Therapie als OPS `8-53 Nuklearmedizinische Therapie` (oder genauer wenn vorhanden)

### oBDS 2014 zu 2021 Zielgebiet Migration

Die Strahlentherapie Zielgebiet-Kodierung hat sich zwischen oBDS 2014 und 2021 grundlegend geändert:

<img src="https://raw.githubusercontent.com/medizininformatik-initiative/kerndatensatzmodul-onkologie/dev/implementation-guides/ImplementationGuide-2026.x-DE/Images/MII_Onko_Strahlentherapie_Zielgebiet_Migration/MII_Onko_Strahlentherapie_Zielgebiet_Migration.png" alt="oBDS 2014 → 2021 Strahlentherapie Zielgebiet Migration" style="max-width: 100%; height: auto;">

#### Migrationsstrategie

- **oBDS 2014**: Verwendete kombinierte Codes mit Suffixen (`+` mit Lymphknoten, `-` ohne Lymphknoten, `.` ohne nähere Angabe)
- **oBDS 2021**: Trennt Organe (Sektionen 1-8) und Lymphabflussregionen (Sektion 9) in separate Bestrahlungen
- **Beispiel**: oBDS 2014 Code `"3.1.+"` (Mamma mit Lymphknoten) wird zu zwei separaten Codes: `#3.1` (Mamma) und `#9.3` (Axilläre Lymphknoten)
- **ValueSet**: Unterstützt beide CodeSystems für Abwärtskompatibilität

### Konformität

Die vorliegende Profilierung ist kompatibel mit dem Prozedurenprofil der ISiK-Basismodule Stufe 4. https://simplifier.net/isik-basis-v4/isikprozedur

<!-- DERIVED:summary source=Strahlentherapie-Procedure.page.md gate=B -->
> **Written during migration - review before release.** Die Quellseite führte jeden Suchparameter einzeln mit Beispielabfrage und Verweis auf die FHIR-Basisspezifikation auf. Hier verdichtet auf die Parameternamen, die die Quellseite als verpflichtend (MUSS) benennt: `_id`, `_profile`, `status`, `category`, `code`, `date`, `subject`, `patient`, `bodySite`, `dokumentationsdatum`, `durchfuehrungsabsicht`, `outcome`, `extension-intention`, `extension-stellung`, `extension-bestrahlung-applikationsart`, `extension-bestrahlung-strahlenart`, `extension-bestrahlung-zielgebiet`, `extension-bestrahlung-zielgebiet-Lateralitaet`, `extension-bestrahlung-boost`, `extension-bestrahlung-einzeldosis`, `extension-bestrahlung-gesamtdosis`.
{: .ig-highlight .ig-highlight-blue}
