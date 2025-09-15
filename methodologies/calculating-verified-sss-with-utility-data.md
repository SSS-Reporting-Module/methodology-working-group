# Calculating Verified SSS with Utility Data

As a renewable energy technical expert advising Clean Incentive, Inc., which owns and operates the Granular Registry and Marketplace, this methodology outlines a standardized, transparent process for calculating (i) the volume of Renewable Energy Certificates (RECs) and other zero-carbon attributes retired on behalf of SSS customers and (ii) a supplier-specific emission factor (SSEF) for market-based Scope 2 reporting. This approach applies when a Load-Serving Entity (LSE) or utility submits structured data directly to the Granular Registry, superseding public-source estimates. It ensures accuracy by verifying retirement dates to address "vintage banking," where RPS regulations often permit utilities to bank RECs from prior years (e.g., up to 3 years in many states) or retire them after the calendar year (e.g., by July 1 of the following year in California for multi-year compliance periods). The process is conducted annually per energy-market region, aligned with the draft GHG Protocol SSS guidance.

This methodology focuses on annual baselines; hourly extensions are addressed in Section 8 for regions with time-stamped data.

## **1. Scope and Definitions**

* **Standard Supply Service (SSS)**: Default electricity service with costs recovered via regulated tariffs or universal service obligations, including mandated clean energy (e.g., from RPS).
* **Utility-Collected Data**: Structured submissions from the LSE/utility, including REC retirement logs, generation mixes, and emission data, verified against certificate-tracking systems (e.g., WREGIS, PJM-GATS).
* **Vintage Banking**: Practice under many RPS rules allowing utilities to carry forward RECs from prior generation years (vintages) for future compliance, or retire them post-calendar year (e.g., deadlines range from March to July of the following year across states like California, Texas, and New York).
* **REC**: Renewable Energy Certificate (1 MWh of renewable generation); extended to zero-carbon attributes (e.g., nuclear ZECs).
* **SSEF**: Supplier-specific emission factor (kg CO₂e/MWh), reflecting retired attributes.

Calculations adhere to GHG Protocol Scope 2 Quality Criteria, preventing double-counting and ensuring temporal alignment.

## **2. Data Requirements from Utility**

Utilities must submit:

* REC retirement logs: Including certificate IDs, generation vintages, retirement dates, and volumes (MWh) allocated to SSS.
* Retail sales volumes: Calendar-year MWh by customer class.
* Generation mix: Owned, contracted, and purchased MWh, with fuel types and zero-carbon allocations.
* Compliance filings: RPS/CES reports confirming obligations and retirements.
* Emission data: Plant-level CO₂e intensities, adjusted for retired attributes.

Data must be attested and verifiable via tracking systems. The Registry cross-checks against public sources for discrepancies.

## **3. Workflow (Per Market-Utility Pair)**

Follow these steps, documenting in a Jupyter notebook attached to the Registry entry.

### **Step 1: Validate Submitted Data**

* Confirm completeness and format alignment with Registry templates.
* Verify against tracking systems (e.g., WREGIS reports) for authenticity.

### **Step 2: Extract Retail-Sales Volumes**

* Use utility-submitted calendar-year MWh. Cross-verify with regulatory filings (e.g., EIA Form 861).

### **Step 3: Quantify Compliance REC Retirements**

* Sum retired REC MWh from logs, filtering for SSS allocation.
* Address vintage banking:\
  a. Check generation vintage (year of production) against retirement date.\
  b. Exclude banked RECs from prior vintages unless explicitly applied to the current year's compliance (per state rules, e.g., unlimited banking in New York for voluntary retirements, or 3-year limits in states like Texas).\
  c. Confirm retirement occurred within allowable deadlines (e.g., by July 1 post-year in California; verify state-specific rules).
* Calculate Obligation Gap = RPS/CES Obligation – Retired MWh; flag non-compliance.

### **Step 4: Identify Non-RPS Zero-Carbon SSS Resources**

* From utility data, sum MWh from regulated/public assets (e.g., legacy hydro, nuclear ZECs) not in RPS, with retirement verification as in Step 3.

### **Step 5: Assemble SSS-Retired REC Volume**

* SSS\_REC\_MWh = RPS\_Retired (post-vintage check) + Non-RPS\_Zero-Carbon – Externally\_Sold\_RECs.
* Subtract sales to voluntary markets, verified via tracking logs.

### **Step 6: Construct Supplier-Specific Emission Factor (SSEF)**

* Use utility-submitted SSEF if attested and integrated with verified retirements.
* Fallback: Bottom-up calculation:\
  a. Start with generation mix MWh.\
  b. Subtract retired zero-carbon MWh (post-vintage verification).\
  c. Apply fuel-specific CO₂e intensities to residual fossil MWh.\
  d. SSEF = Total tCO₂e / Retail Sales MWh.
* Include CH₄/N₂O per local protocols.

### **Step 7: Allocate Pro-Rata Entitlement to Reporting Customer**

* For load L\_customer (MWh): Claimable\_REC\_MWh = (SSS\_REC\_MWh / Retail\_Sales\_MWh) × L\_customer.
* SSEF applies to SSS-supplied load.

### **Step 8: Optional Hourly Allocation**

* If utility provides time-stamped data: Allocate RECs/SSEF hour-by-hour, nullifying emissions in matching hours.
* Verify hourly vintages/retirements to prevent cross-period banking misuse.

### **Step 9: QA/QC & Documentation**

* Re-verify retirement dates/vintages against state RPS rules (e.g., California's July 1 deadline, New York's indefinite voluntary banking).
* Ensure no double-counting; flag banking impacts.
* Version-stamp data; attach notebook.

## **4. Data-Quality Hierarchy**

1. Utility-attested, tracking-system-verified data (preferred).
2. Regulatory compliance filings.
3. Bottom-up reconstruction if gaps exist.
4. Flag high-uncertainty if vintage banking unresolvable.

## **5. Region-Specific Adaptations**

| Region       | Key Quirks on Banking/Retirement                                       | Verification Pointers                             |
| ------------ | ---------------------------------------------------------------------- | ------------------------------------------------- |
| California   | Banking flexible (consistent with IOUs); retire by July 1 post-period. | WREGIS logs; CPUC filings (e.g., multi-year CPs). |
| Texas        | 3-year banking common; deadlines via PUC notifications.                | ERCOT REC program; Admin Code §25.173.            |
| New York     | Indefinite banking for voluntary; Tier 1 restrictions.                 | NYGATS; NYSERDA reports.                          |
| General U.S. | Varies (e.g., 3-year limits in many); post-year retirements common.    | State regulator sites; DSIRE database.            |

## **6. Limitations & Future Work**

* Vintage banking may complicate annual attribution; however, it can enhance tracking for multi-year carryovers.
* Assumes utility data transparency; automates cross-checks.
* Transition to mandatory time-stamped submissions.
* Update annually per policy changes.

## **Example Calculation: PG\&E (California, 2024 Data)**

Assume the utility submits data for a customer with a 10,000 MWh SSS load.

**Step 1-2**: Validated retail sales = 80,000 GWh.

**Step 3**: RPS Retired = 35,200,000 MWh; vintages 2024 (90%) and 2023 banked (10%, verified as allowable); all retired by July 1, 2025.

**Step 4**: Non-RPS Zero-Carbon = 40,000,000 MWh (nuclear/hydro, current vintage).

**Step 5**: SSS\_REC\_MWh = 35,200,000 + 40,000,000 – 500,000 (sold) = 74,700,000 MWh.

**Step 6**: Submitted SSEF = 85 kg CO₂/MWh (verified post-retirements).

**Step 7**: Claimable\_REC\_MWh = (74,700,000 / 80,000,000) × 10,000 ≈ 9,338 MWh.\
Scope 2 = 10,000 × 85 = 850 tCO₂e.

**QA/QC**: Banking <3 years; no double-counting.
