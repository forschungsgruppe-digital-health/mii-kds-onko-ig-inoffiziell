<!-- markdownlint-disable MD041 -->
<!-- Deutsche Fassung (Quellsprache) von Erstdiagnose-Evidenz-List.page.md (MII IG Modul Onkologie, Simplifier).
     Die Quellseite wiederholte dieselben zwei Suchparameter-Einträge dreimal; hier einmal übernommen.
     Englisches Pendant: input/intro-notes/StructureDefinition-mii-pr-onko-liste-evidenz-erstdiagnose-intro.md -->

Die List-Ressource ist eine flache Sammlung von Ressourcen und bietet Funktionen für die Verwaltung der Sammlung. In diesem Fall dient die Ressource als Sammlung der Observationen und Befundberichte, die zum Zeitpunkt der onkologischen Erstdiagnose bekannt sind. Dazu gehören beispielsweise eine TNM-Klassifikation sowie weitere diagnostisch relevante Klassifikationen, Fernmetastasen, Histologien etc.

Die Evidenz-Liste selbst ist nicht Teil des oBDS, sondern soll den Stand zum Zeitpunkt der Erstdiagnose dauerhaft festhalten.

* Die Liste **SOLLTE** auf Basis der Inhalte erstellt werden, die vor bzw. zum Zeitpunkt der Erstdiagnosestellung bekannt waren.
* Dazu **KÖNNEN** die Einträge direkt aus der Diagnosemeldung übernommen werden.

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
