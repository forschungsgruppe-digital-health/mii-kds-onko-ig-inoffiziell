<!-- markdownlint-disable MD041 -->
<!-- Deutsche Fassung (Quellsprache) von
     input/intro-notes/StructureDefinition-mii-pr-onko-tnm-klassifikation-intro.md;
     Wortlaut übernommen aus TNM-Klassifikation-Observation.page.md
     (MII IG Modul Onkologie 2026.x). -->
Dieses Profil ist das Gruppierungsprofil für eine TNM-Klassifikation in der Onkologie.

Das Profil enthält das Referenzdatum und dient als Ankerpunkt für alle weiteren
TNM-Einzelbeobachtungen zu diesem Zeitpunkt. Das Element `hasMember` enthält
Referenzen zu allen verbundenen TNM-Einzelbeobachtungen.

Außerdem wird im Element `value` das UICC-Staging kodiert, dass von den
untergeordneten TNM-Beobachtungen abgeleitet ist.

<!-- DERIVED:summary source=TNM-Klassifikation-Observation.page.md gate=B -->
> **Written during migration - review before release.** Verdichtet aus der
> Suchparameter-Liste der Quellseite (je Parameter ein nummerierter Eintrag mit
> Beispielabfrage): Für dieses Profil MÜSSEN die Suchparameter `_id`, `_profile`,
> `status`, `code`, `subject`, `focus`, `encounter`, `date`, `method`,
> `has-member` und `derived-from` unterstützt werden, auch in Kombination. Die
> Quellseite rendert außerdem die Mappings dieses Profils auf das Logische Modell
> Onkologie und auf den
> [Einheitlichen onkologischen Basisdatensatz (oBDS)](https://basisdatensatz.de/basisdatensatz);
> diese Mappings sind Bestandteil des Profils.
{: .ig-highlight .ig-highlight-blue}
