<!-- source: TechnischeImplementierung/FHIR-Profile/Organspezifische-Module/MalignesMelanom/Melanom-Bundle-Example.page.md -->
The **Melanom bundle example** demonstrates how all melanoma-specific FHIR resources are assembled into a single transaction bundle. The bundle shows the melanoma profiles in practical use and how they reference one another in a realistic clinical scenario of a malignant melanoma of the skin.

The bundle implements the **transaction pattern** and is server-consumable, so that all contained resources can be transmitted as one atomic operation.

### Bundle structure

The melanoma bundle contains the following resources:

#### Primary resources
- **Patient**: melanoma patient (Maria Melanom)
- **Condition**: primary tumour diagnosis (C43.9 - malignant neoplasm: skin, unspecified)
- **Encounter**: inpatient encounter

#### Melanoma-specific observations
- **Breslow depth**: tumour thickness 2.1mm from the granular layer to the deepest invasion (Breslow)
- **Safety margin**: minimum distance to the resection margin 5mm (MM1)
- **Ulceration**: evidence of an ulceration of the epidermis (MM4)
- **LDH**: lactate dehydrogenase value 280 U/L as a prognostic marker (LDH)

#### Bundle-specific characteristics
- **Transaction bundle**: server-consumable atomic operation
- **Reference consistency**: all individual resources reference the bundle's core resources
- **Complete coverage**: all 4 melanoma profiles are included

### Clinical scenario

The bundle represents a **patient with malignant melanoma** with complete histopathological diagnostics and surgical therapy:

**Patient characteristics:**
- **Diagnosis**: C43.9 malignant melanoma of the skin
- **Breslow depth**: 2.1mm (prognostically important)
- **Tumour location**: skin, unspecified

**Histopathological diagnostics:**
- **Ulceration**: evidence of an ulceration of the epidermis
- **LDH**: elevated value (280 U/L) as a prognostic marker

**Surgical therapy:**
- **Excision**: with a sufficient safety margin
- **Safety margin**: minimum distance 5mm to the resection margin
- **Resection status**: R0 resection achieved

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

### oBDS assignment

The bundle demonstrates the complete representation of the oBDS data fields for malignant melanoma:

#### Histopathological assessment
- **MM2**: Breslow depth -> `Observation/mii-exa-onko-melanom-breslow-tiefe`
- **MM4**: ulceration -> `Observation/mii-exa-onko-melanom-ulzeration`

#### Surgical assessment
- **MM1**: safety margin -> `Observation/mii-exa-onko-melanom-sicherheitsabstand`

#### Laboratory parameters
- **MM3**: lactate dehydrogenase -> `Observation/mii-exa-onko-melanom-ldh`

### ValueSet usage

The bundle shows the various terminologies in practical use:

#### LOINC
- **LDH**: `14805-6` "Lactate dehydrogenase activity in Serum or Plasma"

#### SNOMED CT
- **Breslow depth**: `106243009` "Breslow depth staging for melanoma of skin"
- **Safety margin**: `396511007` "Distance of in situ melanoma from closest lateral surgical margin"
- **Ulceration**: `97816-3` "Ulceration present in melanoma of skin"

#### ICD-10-GM
- **Diagnosis**: `C43.9` "Bösartige Neubildung: Haut, nicht näher bezeichnet"

#### oBDS CodeSystems
- **Ulceration**: `mii-cs-onko-melanom-ulzeration#J` "Ja"
- **LDH assessment**: `mii-cs-onko-melanom-ldh-bewertung#erhoeht` "Erhöht"
