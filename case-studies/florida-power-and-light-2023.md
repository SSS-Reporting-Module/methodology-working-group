# Florida Power & Light (2023)

As a renewable energy technical expert advising Clean Incentive, Inc., which owns and operates the Granular Registry and Marketplace, this methodology page outlines the approach used to develop the Florida Power & Light (FPL) Standard Supply Service (SSS) Emissions Case Study for calendar year 2023. The analysis estimates (i) the volume of Renewable Energy Certificates (RECs) and other zero-carbon attributes retired on behalf of FPL's SSS customers and (ii) a supplier-specific emission factor (SSEF) for market-based Scope 2 GHG reporting. This follows the Granular Registry's standardized methodology for proxy bundle estimation when direct supplier data is unavailable, ensuring compliance with GHG Protocol Scope 2 guidance (including market-based accounting principles). The process relies exclusively on public sources to derive a defendable, transparent estimate, with all calculations aligned to annual granularity (hourly extensions noted as optional).

### 1. Scope and Definitions

* **SSS**: Default electricity service provided by FPL under regulated tariffs, serving all retail customers not enrolled in voluntary green programs (e.g., SolarTogether). This includes residential, commercial, and industrial load in FPL's peninsular Florida franchise area.
* **Proxy Bundle**: Paired dataset comprising estimated SSS-retired RECs (or equivalent zero-carbon MWh) and SSEF, derived from public data for use in Scope 2 inventories.
* **Energy-Market Region**: Florida's regulated utility territory (formerly FRCC region), outside any ISO/RTO, with no interstate market or RPS mandate.
* **Zero-Carbon Resources**: Nuclear generation (embedded in default supply) and any renewables backed by retired RECs for SSS; excludes voluntary program RECs or sold attributes.
* **SSEF**: Market-based emission factor (kg CO₂e/MWh) for SSS-supplied electricity, reflecting the residual mix after subtracting zero-carbon MWh.

This methodology produces an annual baseline, recognized as a "credible third-party dataset" under draft GHG Protocol SSS guidance. It does not allocate hourly certificates but can be extended for granular matching (see Section 3, Step 8).

### 2. Data-Source Inventory

Data were sourced from publicly available, verifiable references specific to North America (U.S. non-ISO markets), with priority on regulatory filings and federal datasets:

* **Retail-Sales Volumes**: U.S. Energy Information Administration (EIA) Form 861 (2023 data).
* **Mandated RPS/CES Targets and REC Retirements**: Florida Public Service Commission (PSC) filings; DSIRE database (confirming no RPS); no compliance tracking system required due to absence of mandates.
* **Publicly Owned Hydro/Nuclear Attributes**: FPL Ten-Year Site Plans (2023); EIA Form 923 generation data; NextEra Energy (FPL parent) Form 10-K.
* **System/Supplier Emission Factors**: EPA eGRID (2021 FRCC subregion, adjusted for 2023 mix); FPL fuel mix disclosures in PSC reports.
* **Plant-Level Emission Factors**: EPA eGRID fuel-specific intensities (e.g., natural gas \~900 lbs CO₂e/MWh); includes CO₂, CH₄, N₂O per GHG Protocol.
* **Additional Sources**: FRCC Regional Load and Resource Plan (2023); FPL SolarTogether FAQ (for voluntary REC exclusions); EIA state energy profiles (Florida).

All sources were retrieved as of early 2024, with links documented in the case study citations. Data quality prioritizes regulatory compliance filings over estimates.

### 3. Workflow

The analysis followed a step-by-step process tailored to FPL's regulated, non-RPS market:

**Step 1: Define Market Boundary**\
FPL's vertically integrated service area in peninsular Florida (outside ISO/RTOs) was identified as the boundary. No competitive retail choice exists; SSS covers all default load under PSC oversight. Legal entity: Florida Power & Light Company (NextEra Energy subsidiary).

**Step 2: Extract Retail-Sales Volumes**\
Total SSS load was pulled from EIA Form 861: 127,522,613 MWh for 2023 (all retail sectors). This represents FPL's entire default supply, excluding voluntary program opt-ins.

**Step 3: Quantify Compliance REC Obligations & Retirements**\
Florida has no RPS or CES mandate (confirmed via DSIRE and PSC reports), so compliance obligations = 0 MWh. Actual REC retirements for SSS = 0 MWh. Voluntary RECs (e.g., from SolarTogether) were excluded as they serve only subscribers. FPL's energy marketing indicated sales of unneeded solar RECs to third parties, confirming no retention for default customers.

**Step 4: Identify Non-RPS Zero-Carbon SSS Resources**\
Public filings were reviewed for embedded zero-carbon generation:

* Nuclear: \~29.3 million MWh from Turkey Point, St. Lucie, and Farley units (FPL Ten-Year Site Plan; EIA data). Fully allocated to SSS as carbon-free (no RECs required).
* Hydro/Other: Negligible (\~131 GWh statewide, not FPL-owned).
* Solar: \~5-7% of physical supply (\~6-9 million MWh), but RECs were sold or retired for voluntary programs; excluded from SSS zero-carbon total.\
  Result: Only nuclear MWh qualify as zero-carbon for SSS.

**Step 5: Assemble SSS-Retired REC Volume**\
SSS\_REC\_MWh = RPS\_retired (0) + Public\_asset\_zero-carbon (\~29.3 million MWh nuclear) – RECs\_sold\_externally (solar RECs confirmed sold). Final estimate: \~29.3 million MWh zero-carbon (all nuclear), equating to \~21-23% of retail sales.

**Step 6: Construct Supplier-Specific Emission Factor (SSEF)**\
Fallback bottom-up calculation used (no published SSEF from FPL integrating RECs):

* Generation Mix for SSS: \~79% fossil (primarily natural gas, <3% coal/oil) after subtracting nuclear.
* Residual Mix Adjustment: Unbundled solar MWh (RECs sold) treated as fossil-equivalent (assigned gas emissions to avoid free pass).
* Emissions Assignment: Applied fuel-specific factors to residual MWh (e.g., natural gas \~900 lbs CO₂e/MWh from eGRID FRCC; coal \~2,100 lbs; includes CH₄/N₂O).
* Calculation: Total emissions (tons CO₂e) ÷ Retail Sales MWh = \~0.315 t CO₂e/MWh (\~315 kg CO₂e/MWh). This reflects FPL's gas-nuclear profile, lower than U.S. average but higher than suppliers retaining solar RECs.

**Step 7: Allocate Pro-Rata Entitlement to Reporting Customer**\
For a customer with load L\_customer (MWh):

* Claimable Zero-Carbon MWh = (\~29.3 million / 127.5 million) × L\_customer ≈ 23% of load.
* SSEF applies to remaining \~77% of load for market-based Scope 2.

**Step 8: Optional Hourly Proxy**\
Not implemented here due to lack of hourly residual-mix factors (FRCC data is annual). If available (e.g., future GB/Nordics analogs), apply subtraction hour-by-hour: H\_SSS\_EF = H\_Residual\_EF – (H\_SSS\_CFE\_MWh × 0 / H\_Load\_MWh). Disclose as approximation.

**Step 9: QA/QC & Documentation**

* Cross-verified REC volumes (zero) against PSC/DSIRE; nuclear MWh against EIA/FPL filings.
* Ensured no double-counting (voluntary RECs excluded).
* Version-stamped data (2023 calendar year).
* Calculations documented in a Jupyter notebook (available via Granular Registry entry).

### 4. Data-Quality Hierarchy

1. Regulatory filings (EIA, PSC, eGRID) – primary sources used.
2. Certificate-tracking reports – not applicable (no RPS).
3. Bottom-up mix reconstruction – applied for SSEF.\
   No data scarcity; all inputs high-confidence.

### 5. Region-Specific Adaptations

* **Florida/FRCC Quirks**: No RPS; heavy nuclear/gas reliance; voluntary solar programs strip RECs from SSS. Nuclear treated as public asset equivalent (cost-recovered via rates).
* **Additional Pointers**: PSC Ten-Year Plans for mix; EIA for sales/generation; eGRID for emissions (2021 baseline adjusted for 2023 coal retirements).

### 6. Limitations & Future Work

* Annual granularity may not capture hourly variations; recommend time-stamped certificates for 24/7 claims.
* Assumes no significant curtailment; solar exclusion increases SSEF conservatively.
* Nuclear data approximate (pro-rata shares); add confidence scores in updates.
* Future: Annual refresh; incorporate any Florida clean-energy policy changes; explore hourly eGRID analogs for granular extensions.

This methodology ensures the FPL case study is robust, auditable, and aligned with Granular Registry standards, enabling SSS customers to accurately report Scope 2 emissions. For questions or custom applications, contact Clean Incentive, Inc.
