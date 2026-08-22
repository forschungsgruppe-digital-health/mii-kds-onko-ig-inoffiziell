<!-- source: TechnischeImplementierung/FHIR-Profile/Organspezifische-Module/KolorektalesKarzinom/KRK-Bundle-Example.page.md -->
The **KRK bundle example** demonstrates how all colorectal-cancer-specific FHIR resources are assembled into a single transaction bundle. The bundle shows the KRK profiles in practical use and how they reference one another in a realistic clinical scenario of a rectal carcinoma.

The bundle implements the **transaction pattern** and is server-consumable, so that all contained resources can be transmitted as one atomic operation.

### Bundle structure

The KRK bundle contains the following resources:

#### Primary resources
- **Patient**: KRK patient (Klaus KolorektalCa)
- **Condition**: primary tumour diagnosis (C18 - malignant neoplasm of colon)
- **Encounter**: inpatient encounter

#### KRK-specific observations
- **Distance to the anocutaneous line**: tumour site 6cm from the anocutaneous line (KR1)
- **Circumferential resection plane**: minimum distance 2mm (KR3)
- **Aboral resection margin**: minimum distance 15mm (KR2)
- **MRI mesorectal fascia**: imaging assessment of the distance (KR2)
- **Anastomotic leak**: post-operative complication assessment (KR8)
- **ASA classification**: pre-operative risk assessment ASA II (KR9)

#### Therapeutic resources
- **Stoma marking**: pre-operative marking of the stoma position (KR7)
- **KRK operation**: surgical resection with TME quality assessment (KR4)
- **KRK specimen**: surgical specimen with pathological work-up

### Clinical scenario

The bundle represents a **patient with rectal carcinoma** with complete pre-operative diagnostics and surgical therapy:

**Patient characteristics:**
- **Diagnosis**: C18 colon carcinoma
- **ASA status**: ASA II (moderate surgical risk)
- **Tumour location**: 6cm from the anocutaneous line (low rectum)

**Pre-operative diagnostics:**
- **MRI staging**: assessment of the mesorectal fascia
- **Pre-operative preparation**: stoma marking performed

**Surgical therapy:**
- **Rectal resection**: with TME technique (total mesorectal excision)
- **Resection margins**: R0 resection with sufficient safety margins
- **Post-operative complications**: no anastomotic leak

### Technical implementation

#### Bundle type and structure
```
* type = #transaction
```
- **Transaction bundle**: atomic transmission of all resources
- **Server-consumable**: all entries with complete request information

#### Entry pattern
Every bundle entry contains:
- **fullUrl**: unique reference URL
- **resource**: the FHIR resource itself
- **request.method**: HTTP POST for creation
- **request.url**: target resource type

#### Reference integrity
- **Condition**: references Patient via `subject`
- **Observations**: reference both Patient (`subject`) and Condition (`focus`)
- **Procedures**: reference Patient (`subject`) and Condition (`reasonReference`)
- **Specimen**: references Patient (`subject`) and the collection procedure

### Reference pattern

The bundle demonstrates the **consistent reference structure** between KRK-specific resources:

```
Patient <- subject <- Condition (primary tumour)
                        ^ focus
                 Observations (distances, ASA, anastomotic leak)
                        ^ reasonReference
                   Procedures (stoma marking, operation)
                        ^ collection.procedure
                    Specimen (surgical specimen)
```

### oBDS assignment

The bundle demonstrates the complete representation of the oBDS data fields for colorectal cancer:

#### Tumour location
- **KR1**: distance anocutaneous line -> `Observation/mii-exa-onko-krk-abstand-tumor-anokutanlinie`

#### Pathological assessment
- **KR2**: distance aboral resection margin -> `Observation/mii-exa-onko-krk-abstand-resektionsrand-aboral`
- **KR3**: distance circumferential resection plane -> `Observation/mii-exa-onko-krk-abstand-circumferelle-resektionsebene`
- **KR4**: TME quality -> `Specimen/mii-exa-onko-krk-specimen`

#### Imaging procedures
- **KR5**: MRI/CT mesorectal fascia -> `Observation/mii-exa-onko-krk-abstand-mesorektale-fascie`

#### Surgical data
- **KR7**: stoma marking -> `Procedure/mii-exa-onko-krk-stoma-markierung`
- **KR8**: anastomotic leak -> `Observation/mii-exa-onko-krk-anastomoseninsuffizienz`
- **KR9**: ASA classification -> `Observation/mii-exa-onko-krk-asa-klassifikation`

### ValueSet usage

The bundle shows the various terminologies in practical use:

#### LOINC
- **Distance anocutaneous line**: `33748-5` "Distance from anal verge"
- **ASA classification**: `97816-3` "American Society of Anesthesiologists physical status score"

#### SNOMED CT
- **Anastomotic leak**: `235919008` "Anastomotic leak"
- **Surgical interventions**: various SNOMED CT codes for colorectal operations

#### ICD-10-GM
- **Diagnosis**: `C18` "Bösartige Neubildung des Kolons"

#### oBDS CodeSystems
- **ASA classification**: `mii-cs-onko-krk-asa-obds#2` "ASA II"
- **Stoma marking**: `mii-cs-onko-krk-stoma-anzeichnung#durchgefuehrt` "Durchgeführt"
- **TME quality**: `mii-cs-onko-krk-tme-qualitaet#komplett` "Komplett"
