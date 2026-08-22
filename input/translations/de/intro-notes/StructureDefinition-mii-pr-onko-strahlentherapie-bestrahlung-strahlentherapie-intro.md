Dieses Profil beschreibt Einzelbestrahlungen im Rahmen einer Strahlentherapie in der Onkologie. Dieses Profil beschriebt Strahlentherapie im engeren Sinne; Brachytherapien und systemische nuklearmedizinische Prozeduren werden über das Profil Nuklearmedizinische Therapien abgebildet.
Das Strahlentherapieprofil für die Onkologie basiert auf dem Prozedurenmodul der MII.

### Implementierungsempfehlung

Aus den oben genannten Punkten ergibt sich folgende Kodierempfehlung für die oBDS-Strahlentherapie:

- Kategorie als SNOMED - Code
    - Kategorie für Strahlentherapie `1287742003 | Radiotherapy (procedure)`
- Kodierung über OPS
    - Strahlentherapie als OPS `8-52 Strahlentherapie` oder genauer wenn vorhanden

### Konformität

Die vorliegenden Profilierungen sind kompatibel mit dem Prozedurenprofil der ISiK-Basismodule Stufe 4. https://simplifier.net/isik-basis-v4/isikprozedur

<!-- DERIVED:summary source=Bestrahlungstherapie-Procedure.page.md gate=B -->
> **Written during migration - review before release.** Die Quellseite führte jeden Suchparameter einzeln mit Beispielabfrage und Verweis auf die FHIR-Basisspezifikation auf. Hier verdichtet auf die Parameternamen, die die Quellseite als verpflichtend (MUSS) benennt: `_id`, `_profile`, `status`, `category`, `code`, `date`, `subject`, `patient`, `bodySite`, `dokumentationsdatum`, `durchfuehrungsabsicht`, `outcome`, `extension-intention`, `extension-stellung`, `bestrahlung-applikationsart`, `bestrahlung-strahlenart`, `bestrahlung-zielgebiet-lateralitaet`, `bestrahlung-boost`, `bestrahlung-einzeldosis`, `bestrahlung-gesamtdosis`.
{: .ig-highlight .ig-highlight-blue}
