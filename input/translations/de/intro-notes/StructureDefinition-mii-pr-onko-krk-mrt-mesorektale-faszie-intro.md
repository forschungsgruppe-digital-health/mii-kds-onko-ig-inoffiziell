<!-- source: TechnischeImplementierung/FHIR-Profile/Organspezifische-Module/KolorektalesKarzinom/KRK-MRT-Mesorektale-Faszie-Observation.page.md -->
Dieses Profil beschreibt den Abstand zur mesorektalen Faszie bei bildgebenden Verfahren (MRT/CT) beim Kolorektalen Karzinom gemäß oBDS KR2. Diese präoperative Bildgebungsbeurteilung ist essentiell für die Therapieplanung bei Rektumkarzinomen und die Einschätzung der lokalen Tumorausbreitung.

Das Profil basiert auf einer FHIR Observation-Ressource und beinhaltet sowohl die Quantitätsmessung als auch die Begründung für fehlende Abstandsmessungen. Der Abstand wird als Quantity-Wert in Millimetern angegeben.

<!-- DERIVED:bridge source=KRK-MRT-Mesorektale-Faszie-Observation.page.md gate=B -->
> **Written during migration - review before release.** Die Quellseite gab als `subject` die Canonical `.../StructureDefinition/mii-pr-onko-krk-abstand-mesorektale-fascie` an, die in diesem Leitfaden nicht als Artefakt existiert; das Profil wird hier als [MII_PR_Onko_KRK_MRT_Mesorektale_Faszie](StructureDefinition-mii-pr-onko-krk-mrt-mesorektale-faszie.html) publiziert. Diese Notiz wurde diesem Artefakt zugeordnet und das `_profile`-Suchbeispiel unten entsprechend umgestellt. Zu beachten: die Beispielinstanz trägt weiterhin die ältere Schreibweise (`mii-exa-onko-krk-abstand-mesorektale-fascie`).
{: .ig-highlight .ig-highlight-blue}

### Verknüpfungen zu anderen Ressourcen

Die MRT-Bewertung der mesorektalen Faszie ist eine wichtige bildgebende Beobachtung:
- verweist über `Observation.focus` auf die Primärdiagnose (MII_PR_Onko_Diagnose_Primaertumor)
- verweist über `Observation.subject` auf den Patienten (Patient-Ressource)
- kann über `Observation.encounter` mit einem spezifischen Behandlungsfall verknüpft werden

### oBDS-Kontext

Die MRT-Bewertung entspricht dem oBDS-Datenfeld KR2 "MRT/CT: Abstand zur mesorektalen Faszie" und umfasst sowohl die Abstandsmessung in Millimetern als auch Codes für Situationen, in denen eine Messung nicht verfügbar ist (AbstandNichtVerfuegbarGrund).

### Terminologie-Binding

Das ValueSet für den MRT-Status der mesorektalen Faszie ist **extensible** gebunden und beinhaltet die verschiedenen Status-Codes für die bildgebende Bewertung sowie Gründe für fehlende Messungen.

- ValueSet: MII VS Onko KRK MRT Mesorektale Faszie Status

### Suchparameter

Folgende Suchparameter sind für das KRK-MRT-Mesorektale-Faszie Profil relevant, auch in Kombination:

- Der Suchparameter `_id` MUSS unterstützt werden: `GET [base]/Observation?_id=12345`
- Der Suchparameter `_profile` MUSS unterstützt werden: `GET [base]/Observation?_profile=https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-krk-mrt-mesorektale-faszie`
- Der Suchparameter `code` MUSS unterstützt werden: `GET [base]/Observation?code=https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/CodeSystem/mii-cs-onko-krk-mrt-mesorektale-faszie-status|befunden`
- Der Suchparameter `subject` MUSS unterstützt werden: `GET [base]/Observation?subject=Patient/test`
- Der Suchparameter `focus` MUSS unterstützt werden: `GET [base]/Observation?focus=Condition/primaertumor`
- Der Suchparameter `value-quantity` MUSS unterstützt werden: `GET [base]/Observation?value-quantity=1.5|http://unitsofmeasure.org|mm`
