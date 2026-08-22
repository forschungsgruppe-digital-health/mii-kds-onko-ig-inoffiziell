<!-- source: TechnischeImplementierung/FHIR-Profile/Organspezifische-Module/Mamma/Mamma-Bundle-Example.page.md -->
The **Mamma bundle example** demonstrates how all breast-specific FHIR resources are assembled into a single transaction bundle. The bundle shows the Mamma profiles in practical use and how they reference one another in a realistic clinical scenario.

The bundle implements the **transaction pattern** and is server-consumable, so that all contained resources can be transmitted as one atomic operation.

### Bundle structure

The Mamma bundle contains the following resources:

#### Primary resources
- **Patient**: breast cancer patient (Martha MammaCa)
- **Condition**: primary tumour diagnosis (C50.3 - lower inner quadrant of breast)

#### Breast-specific observations
- **Menopause status**: premenopausal status of the patient
- **Estrogen receptor status**: positive finding with 5% positive cells, weak staining intensity
- **Progesterone receptor status**: positive finding with 25% positive cells, weak staining intensity

#### Additional elements
- **Tumour size determination**: largest dimension 25mm
- **Pre-operative marking**: example of a marking procedure

### Clinical scenario

The bundle represents a **premenopausal patient** with a **hormone-receptor-positive breast cancer** in the lower inner quadrant of the breast:

**Patient characteristics:**
- **Age/status**: premenopausal (important for treatment planning)
- **Tumour location**: C50.3 (lower inner quadrant)
- **Tumour size**: 25mm (T2 category)

**Receptor status:**
- **Estrogen receptor**: positive (5% positive cells, weak intensity)
- **Progesterone receptor**: positive (25% positive cells, weak intensity)
- **Therapeutic consequence**: candidate for anti-hormonal therapy

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

### Reference pattern

The bundle demonstrates the **consistent reference structure** between breast-specific resources:

```
Patient <- subject <- Condition (primary tumour)
                        ^ focus
                 Observations (menopause, receptor status)
                        ^ reasonReference
                   Procedures (marking)
```

### ValueSet usage

The bundle shows the various terminologies in practical use:

#### SNOMED CT
- **Menopause status**: `22636003` "Premenopausal state"
- **Anatomical location**: `110494001` "Structure of upper inner quadrant of right breast"

#### LOINC
- **Estrogen receptor**: `40556-3` "Estrogen receptor Ag [Presence] in Tissue by Immune stain"
- **Progesterone receptor**: `85339-0` "Progesterone receptor Ag [Presence] in Breast cancer specimen by Immune stain"
- **Tumour size**: `21889-1` "Size Tumor"
- **Receptor status**: `LA6576-8` "Positive"

#### ICD-10-GM
- **Diagnosis**: `C50.3` "Bösartige Neubildung: Unterer innerer Quadrant der Brustdrüse"
