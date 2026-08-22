# Extensions - MII IG Kerndatensatz-Modul Onkologie v2026.0.3

* [**Inhaltsverzeichnis**](toc.md)
* **Extensions**

## Extensions

> **Optionale Seite (0..1).** Das KDS-Modulmenü führt diese Seite als **optional**. Entscheiden Sie für Ihr Modul: Seite **behalten** — Inhalte ausfüllen und dieses Banner samt `OPTIONAL-PAGE`-Marker-Kommentar löschen (in dieser Datei UND in der englischen Quellseite) — oder Seite **entfernen**, nach der Schritt-für-Schritt-Anleitung in [`docs/optional-pages.md`](https://github.com/forschungsgruppe-digital-health/mii-kds-onko-ig-inoffiziell/blob/main/docs/optional-pages.md) dieses Repositories. Ein Release darf dieses Banner nicht enthalten (Konventions-Check M9).

### Extensions

Diese Seite listet die FHIR-Extensions, die das Modul **Onkologie** definiert (Namenskonvention `MII_EX_<Modul>_<Name>`). Extensions transportieren Informationen, die die Basis-Ressourcen und Profile nicht ausdrücken können; die Profile, die sie verwenden, stehen auf der Seite [Profile](profiles.md).

> [TODO: Listen und beschreiben Sie die Extensions Ihres Moduls — oder entfernen Sie diese Seite, wenn Ihr Modul keine definiert.]

### Bestrahlungs-Extensions der Strahlentherapie-Profile

Die Bestrahlungsextensions erfassen alle Informationen, die für einzelne Bestrahlungseinheiten relevant sind und die nicht bereits durch das übergeordnete Prozedurprofil Strahlentherapie abgedeckt wurden.

* Gesamtdosis (`mii-ex-onko-strahlentherapie-bestrahlung-gesamtdosis`)
* Einzeldosis (`mii-ex-onko-strahlentherapie-bestrahlung-einzeldosis`)
* Boost (`mii-ex-onko-strahlentherapie-bestrahlung-boost`)
* Seitenlokalisation (`mii-ex-onko-strahlentherapie-bestrahlung-seitenlokalisation`)

