<!-- markdownlint-disable MD041 -->
<!-- Deutsche Fassung (Quellsprache) von Lymphknotenuntersuchung-Observation.page.md (MII IG Modul Onkologie, Simplifier).
     Die Quellseite behandelte alle vier Lymphknoten-Profile gemeinsam; in diesem Leitfaden hat jedes Profil eine eigene Seite.
     Englisches Pendant: input/intro-notes/StructureDefinition-mii-pr-onko-anzahl-befallene-sentinel-lymphknoten-intro.md -->

Dieses Profil beschreibt die Lymphknotenuntersuchungen, die im Rahmen eines onkologischen Stagings durchgeführt werden.
Das oBDS-Register sieht vier unteschiedliche Datenpunkte vor:

* Anzahl der untersuchten Lymphknoten
* Anzahl der befallenen Lymphknoten

Zusätzlich können je nach betroffener Anatomie Sentinel-Lymphknoten miterfasst werden, daher zusätzlich

* Anzahl der untersuchten **Sentinel**-Lymphknoten
* Anzahl der befallenen **Sentinel**-Lymphknoten

Das Verhältnis zwischen befallenen und untersuchten wird teilweise im klinischen Alltag bestimmt, ist im oBDS aber nicht als Datenpunkt abgebildet und daher auch nicht Teil dieser FHIR-Profilierung.

<!-- DERIVED:bridge source=Lymphknotenuntersuchung-Observation.page.md gate=B -->
> **Written during migration - review before release.** Dieses Profil bildet den Datenpunkt *Befallene Sentinel-Lymphknoten* ab. Die drei übrigen Datenpunkte sind als eigene Profile abgebildet: [Anzahl befallene Lymphknoten](StructureDefinition-mii-pr-onko-anzahl-befallene-lymphknoten.html), [Anzahl untersuchte Lymphknoten](StructureDefinition-mii-pr-onko-anzahl-untersuchte-lymphknoten.html) und [Anzahl untersuchte Sentinel-Lymphknoten](StructureDefinition-mii-pr-onko-anzahl-untersuchte-sentinel-lymphknoten.html). Im Quell-Leitfaden waren alle vier wegen ihrer sehr ähnlichen inhaltlichen Profilierung auf einer gemeinsamen Seite dargestellt.
{: .ig-highlight .ig-highlight-blue}

**Suchparameter**

Folgende Suchparameter sind für das Modul Onkologie relevant, auch in Kombination:

1. Der Suchparameter ```_id``` MUSS unterstützt werden:

    Beispiele:

    ```GET [base]/Condition?_id=1234```

    Anwendungshinweise: Weitere Informationen zur Suche nach "_id" finden sich in der [FHIR-Basisspezifikation - Abschnitt "Parameters for all resources"](http://hl7.org/fhir/R4/search.html#all).

2. Der Suchparameter "_profile" MUSS unterstützt werden:

    Beispiele:

    ```GET [base]/Condition?_profile=https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-diagnose```

    Anwendungshinweise: Weitere Informationen zur Suche nach "_profile" finden sich in der [FHIR-Basisspezifikation - Abschnitt "token"](http://hl7.org/fhir/R4/search.html#all).

3. Der Suchparameter "category" MUSS unterstützt werden:

    Beispiele:

    ```GET [base]/Observation?category=http://terminology.hl7.org/CodeSystem/observation-category|laboratory```

    Anwendungshinweise: Weitere Informationen zur Suche nach "category" finden sich in der FHIR-Basisspezifikation - Abschnitt "token".

4. Der Suchparameter "code" MUSS unterstützt werden:

    Beispiele:

    ```GET [base]/Observation?code=http://fhir.de/CodeSystem/sct|184305005```

    Anwendungshinweise: Weitere Informationen zur Suche nach "code" finden sich in der FHIR-Basisspezifikation - Abschnitt "token".

5. Der Suchparameter "subject" MUSS unterstützt werden:

    Beispiele:

    ```GET [base]/Observation?subject=Patient/example```

    Anwendungshinweise: Weitere Informationen zur Suche nach "subject" finden sich in der FHIR-Basisspezifikation - Abschnitt "reference".

6. Der Suchparameter "focus" MUSS unterstützt werden:

    Beispiele:

    ```GET [base]/Observation?focus=Condition/example```

    Anwendungshinweise: Weitere Informationen zur Suche nach "focus" finden sich in der FHIR-Basisspezifikation - Abschnitt "reference".

7. Der Suchparameter "encounter" MUSS unterstützt werden:

    Beispiele:

    ```GET [base]/Observation?encounter=Encounter/example```

    Anwendungshinweise: Weitere Informationen zur Suche nach "encounter" finden sich in der FHIR-Basisspezifikation - Abschnitt "reference".

8. Der Suchparameter "date" MUSS unterstützt werden:

    Beispiele:

    ```GET [base]/Observation?date=2024-02-08```

    Anwendungshinweise: Weitere Informationen zur Suche nach "date" finden sich in der FHIR-Basisspezifikation - Abschnitt "date".

9. Der Suchparameter "derived-from" MUSS unterstützt werden:

    Beispiele:

    ```GET [base]/Observation?derived-from=Observation/example```

    Anwendungshinweise: Weitere Informationen zur Suche nach "derived-from" finden sich in der FHIR-Basisspezifikation - Abschnitt "reference".
