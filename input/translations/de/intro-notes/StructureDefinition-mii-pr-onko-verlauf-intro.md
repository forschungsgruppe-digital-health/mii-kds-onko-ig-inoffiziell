<!-- markdownlint-disable MD041 -->
<!-- Deutsche Quellfassung, wortgleich übernommen aus Verlauf-Observation.page.md
     (MII IG Modul Onkologie, Simplifier). Simplifier-/FQL-Direktiven (Seitentitel,
     Darstellung/XML/JSON/Link-Tabs, FQL-Abfragen für Profil-Metadaten, Datensatz- und
     oBDS-Mapping) wurden entfernt - der IG-Publisher stellt diese Informationen auf der
     Artefaktseite selbst dar.
     Englische Fassung: input/intro-notes/StructureDefinition-mii-pr-onko-verlauf-intro.md -->

### Kontext

Dieses Profil beschreibt eine Verlaufsbeobachtung im Rahmen der onkologischen Therapie.

Im oBDS ist die Verlaufsmeldung eine von mehreren Meldearten. Die Verlaufsmeldung kann dabei mehrere andere Meldeinhalte enthalten. In der vorliegenden FHIR-Profilierung sind Verlaufs-Beobachtungen neben Tumorkonferenzen eine der zwei entscheidenden Ressourcentypen, die der zeitlichen Modellierung des Behandlungsverlaufs dienen.

Die korrekte Kodierung und Interpretation der Krebsregister-Verlaufsdaten ist nicht trivial - Details sind dem Dokumentationsleitfaden der Plattform §65c zu entnehmen.

https://plattform65c.atlassian.net/wiki/spaces/Dokumentat/pages/75628552/Verlaufsmeldung

### Conformance Statements

- Eine Verlaufs-Beobachtung **SOLL** mittels `focus` einen Verweis auf die Primärdiagnose haben
- Eine Verlaufs-Beobachtung **SOLLTE** im `value` eine Einschätzung des Krankheitsprogresses (PD, PR, MR etc.) beinhalten, insofern diese vorgenommen wurde und in den Daten vorliegt
- Eine Verlaufs-Beobachtung **SOLLTE** weitherin im `component` Einschätzungen zum Staging des Tumors, der Lymphknoten und der Fernmetastasen enthalten, insofern diese vorgenommen wurden und diese für das Staging relevant sind
- Da die FHIR-Profilierung keine komplette Verlaufs-Meldung abbildet, **SOLLEN** andere Beobachtungen, die zusätzlich oder abweichend zu den oben genannenten TNM-Kriterien für das Staging relevant sind, von der Verlaufs-Beobachtung über `hasMember` referenziert werden. Beispielsweise sind das neu diagnostizierte Fernmetastasen, zusätzlich angefertigte Histologien oder später im Verlauf durchgeführte genetische Untersuchungen. Diese Beobachtungen **KÖNNEN** direkt aus den oBDS-Meldeinhalten der jeweiligen Verlaufs-Meldung übernommen werden.

### Suchparameter

Folgende Suchparameter sind für das Modul Onkologie relevant, auch in Kombination:

1. Der Suchparameter ```_id``` MUSS unterstützt werden:

    Beispiele:

    ```GET [base]/Observation?_id=1234```

    Anwendungshinweise: Weitere Informationen zur Suche nach "_id" finden sich in der [FHIR-Basisspezifikation - Abschnitt "Parameters for all resources"](http://hl7.org/fhir/R4/search.html#all).

2. Der Suchparameter "_profile" MUSS unterstützt werden:

    Beispiele:

    ```GET [base]/Observation?_profile=https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-allgemeiner-leistungszustand```

    Anwendungshinweise: Weitere Informationen zur Suche nach "_profile" finden sich in der [FHIR-Basisspezifikation - Abschnitt "token"](http://hl7.org/fhir/R4/search.html#all).

3. Der Suchparameter "identfier" MUSS unterstützt werden:

    Beispiele:

    ```GET [base]/Observation?identfier=http://charite.de/labor/labortests|1234```

    Anwendungshinweise: Weitere Informationen zur Suche nach "identfier" finden sich in der FHIR-Basisspezifikation - Abschnitt "token".

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

8. Der Suchparameter "component-code-value-concept" MUSS unterstützt werden:

    Beispiele:

    ```GET [base]/Observation?component-code-value-concept=http://loinc.org|12345-6$http://fhir.de/CodeSystem/sct|12345678```

    Anwendungshinweise: Weitere Informationen zur Suche nach "components" finden sich in der FHIR-Basisspezifikation - Abschnitt "compodsite".

<!-- DERIVED:bridge source=Verlauf-Observation.page.md gate=B -->
> **Written during migration - review before release.** Suchparameter 2 oben trägt die Canonical von
> `mii-pr-onko-allgemeiner-leistungszustand`, nicht die dieses Profils. Der Wortlaut wurde
> unverändert aus der Quellseite übernommen; vor der Veröffentlichung ist er auf
> `https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-verlauf`
> zu korrigieren. Derselbe Copy-and-paste-Fehler betraf die gelöschten Mapping-Abfragen der
> Quellseite.
{: .ig-highlight .ig-highlight-blue}

### Beispiele

<!-- DERIVED:bridge source=Verlauf-Observation.page.md gate=B -->
> **Written during migration - review before release.** Die Instanz `mii-exa-onko-verlauf-tumor`
> in diesem Leitfaden veranschaulicht das Profil.
{: .ig-highlight .ig-highlight-blue}
