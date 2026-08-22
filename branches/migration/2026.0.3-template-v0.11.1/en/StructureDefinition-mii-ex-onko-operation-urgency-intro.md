This extension captures the **modality under which the intervention was performed** (Art des Eingriffs) and distinguishes between elective and emergency interventions.

### Origin and scope

This data point originally comes from the organ-specific module **Kolorektales Karzinom (KRK 6)** as per oBDS 2021. Since the distinction between elective and emergency interventions is, however, clinically relevant for all surgical procedures, the extension was integrated into the general Operation profile and can be **applied universally to all oncological surgeries**.

### Clinical relevance

Recording the intervention modality is important for several reasons:

- **Quality assurance**: emergency interventions often show different complication rates than planned interventions
- **Risk stratification**: urgency influences perioperative morbidity and mortality
- **Statistical analyses**: fair comparisons between centres require the share of emergencies to be taken into account
- **Resource planning**: distinction between plannable and unplanned interventions

### Value range

The values come from the CodeSystem `mii-cs-onko-operation-urgency`:

- **E**: Elektiveingriff (planned intervention)
- **N**: Notfalleingriff (emergency intervention)
- **U**: Unbekannt (unknown)

### Mapping

Mapping [Einheitlicher onkologischer Basisdatensatz (oBDS)](https://basisdatensatz.de/basisdatensatz) to FHIR

This extension maps to the **KRK module** field:

- **KR6**: Art des Eingriffs (modality under which the intervention was performed)

### Related profiles

- Operation: `mii-pr-onko-operation`
- Extension Intention: `mii-ex-onko-operation-intention`
