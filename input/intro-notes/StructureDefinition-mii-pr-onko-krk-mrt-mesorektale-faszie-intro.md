<!-- source: TechnischeImplementierung/FHIR-Profile/Organspezifische-Module/KolorektalesKarzinom/KRK-MRT-Mesorektale-Faszie-Observation.page.md -->
This profile describes the distance to the mesorectal fascia in imaging procedures (MRI/CT) in colorectal cancer according to oBDS KR2. This pre-operative imaging assessment is essential for treatment planning in rectal cancer and for estimating the local tumour spread.

The profile is based on a FHIR Observation resource and covers both the quantitative measurement and the reason for a missing distance measurement. The distance is given as a Quantity value in millimetres.

### Links to other resources

The MRI assessment of the mesorectal fascia is an important imaging observation:
- references the primary diagnosis (MII_PR_Onko_Diagnose_Primaertumor) via `Observation.focus`
- references the patient (Patient resource) via `Observation.subject`
- can be linked to a specific encounter via `Observation.encounter`

### oBDS context

The MRI assessment corresponds to the oBDS data field KR2 "MRT/CT: Abstand zur mesorektalen Faszie" and covers both the distance measurement in millimetres and codes for situations in which no measurement is available (AbstandNichtVerfuegbarGrund).

### Terminology binding

The ValueSet for the MRI status of the mesorectal fascia is bound as **extensible** and contains the various status codes for the imaging assessment as well as reasons for missing measurements.

- ValueSet: MII VS Onko KRK MRT Mesorektale Faszie Status

### Search parameters

The following search parameters are relevant for the KRK-MRT-Mesorektale-Faszie profile, including in combination:

- The search parameter `_id` MUST be supported: `GET [base]/Observation?_id=12345`
- The search parameter `_profile` MUST be supported: `GET [base]/Observation?_profile=https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/StructureDefinition/mii-pr-onko-krk-mrt-mesorektale-faszie`
- The search parameter `code` MUST be supported: `GET [base]/Observation?code=https://www.medizininformatik-initiative.de/fhir/ext/modul-onko/CodeSystem/mii-cs-onko-krk-mrt-mesorektale-faszie-status|befunden`
- The search parameter `subject` MUST be supported: `GET [base]/Observation?subject=Patient/test`
- The search parameter `focus` MUST be supported: `GET [base]/Observation?focus=Condition/primaertumor`
- The search parameter `value-quantity` MUST be supported: `GET [base]/Observation?value-quantity=1.5|http://unitsofmeasure.org|mm`
