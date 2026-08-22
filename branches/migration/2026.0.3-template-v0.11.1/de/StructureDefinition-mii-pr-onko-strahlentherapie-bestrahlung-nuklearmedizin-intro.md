Dieses Profil beschreibt "Einzelbestrahlungen" von Nuklearmedizinischen Therapie in der Onkologie. Mit diesem Profil sollen sowohl Brachytherapien als auch die systemische Gabe von radioaktiven Metaboliten oder vgl. abgedeckt werden. Das Profil für die Onkologie basiert auf dem Prozeduren-Profil des MII-Basismoduls Prozedur. Jede brachytherapeutischer Eingriff bzw. systemische nuklearmedizinische Therapie verweist auf eine übergeordnete Strahlentherapie-Prozedur, die übergreifende Angaben wie Intention und Outcome.

<!-- DERIVED:bridge source=NuklearmedizinischeTherapie-Procedure.page.md gate=B -->
> **Written during migration - review before release.** Der letzte Satz des Absatzes bricht in der Quellseite unvollständig ab ("... die übergreifende Angaben wie Intention und Outcome."). Der Wortlaut wurde unverändert übernommen; die Aussage ist vor der Veröffentlichung zu vervollständigen.
{: .ig-highlight .ig-highlight-blue}

### Implementierungsempfehlung

Aus den oben genannten Punkten ergibt sich folgende Kodierempfehlung für die oBDS-Nuklearmedizinische Behandlung:

- Kategorie als SNOMED - Code
    - Kategorie für Nuklearmedizin `399315003 | Radionuclide therapy (procedure)`
- Kodierung über OPS
    - Nuklearmedizinische Therapie als OPS `8-53 Nuklearmedizinische Therapie` (oder genauer wenn vorhanden)

### Konformität

Die vorliegenden Profilierungen sind kompatibel mit dem Prozedurenprofil der ISiK-Basismodule Stufe 4. https://simplifier.net/isik-basis-v4/isikprozedur

<!-- DERIVED:summary source=NuklearmedizinischeTherapie-Procedure.page.md gate=B -->
> **Written during migration - review before release.** Die Quellseite führte jeden Suchparameter einzeln mit Beispielabfrage und Verweis auf die FHIR-Basisspezifikation auf. Hier verdichtet auf die Parameternamen, die die Quellseite als verpflichtend (MUSS) benennt: `_id`, `_profile`, `status`, `category`, `code`, `date`, `subject`, `patient`, `bodySite`, `dokumentationsdatum`, `durchfuehrungsabsicht`, `outcome`, `extension-intention`, `extension-stellung`, `extension-bestrahlung-applikationsart`, `extension-bestrahlung-strahlenart`, `extension-bestrahlung-zielgebiet`, `extension-bestrahlung-zielgebiet-Lateralitaet`, `extension-bestrahlung-boost`, `extension-bestrahlung-einzeldosis`, `extension-bestrahlung-gesamtdosis`.
{: .ig-highlight .ig-highlight-blue}
