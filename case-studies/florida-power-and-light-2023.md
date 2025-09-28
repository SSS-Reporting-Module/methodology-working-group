---
title: 'Florida Power & Light Standard Supply Service (SSS) Case Study (2023)'
utility: 'Florida Power & Light Company (NextEra Energy subsidiary)'
year: '2023'
jurisdiction: 'Florida, USA'
iso_rto_or_balancing_area: 'Non-ISO Regulated (FRCC/Florida)'
service_type: Standard Supply Service (SSS)
data_vintage: '2023 EIA 861; 2023 EIA 923; 2021 EPA eGRID adjusted to 2023'
authors:
  - Clean Incentive, Inc.
version: v0.2-draft
last_updated: '2025-09-28'
related_methodologies:
  - ../methodologies/sss-methodology.md
  - ../methodologies/calculating-verified-sss-with-utility-data.md
  - ../methodologies/estimating-sss-from-public-sources.md
confidentiality: Public case study
contact: support@cleani.com
data_path: Public Fallback
---

# Florida Power & Light (SSS) — Case Study (2023)

### 0. At‑a‑Glance Metrics

* **SSS retail sales (MWh)**: 127,522,613
* **Zero‑carbon MWh allocated to SSS**: ~29,300,000 (nuclear)
* **SSS zero‑carbon share (%)**: ~23%
* **Supplier‑Specific Emission Factor (SSEF)**: ~315 kg CO₂e/MWh
* **Coverage**: Annual baseline; Hourly extension optional
* **Data confidence**: High (regulatory/public datasets; bottom‑up SSEF)
* **Data vintage**: 2023 EIA 861/923; 2021 eGRID adjusted to 2023
* **Data path**: Public Fallback

***

### 1. Scope and Definitions

* **SSS**: Default electricity service provided by FPL under regulated tariffs, serving all retail customers not enrolled in voluntary green programs (e.g., SolarTogether). Legal entity: Florida Power & Light Company.
* **SSS Bundle**: Paired dataset of (i) SSS‑retired zero‑carbon MWh and (ii) SSEF for market‑based Scope 2.
* **Zero‑Carbon Resources**: Nuclear generation embedded in default supply and any renewables backed by RECs retired for SSS; excludes voluntary program RECs and externally sold attributes. For 2023, only nuclear qualifies.
* **SSEF**: Utility‑specific market‑based emission factor (kg CO₂e/MWh) after subtracting zero‑carbon MWh.
* **Boundary**: FPL’s vertically integrated service territory in peninsular Florida (formerly FRCC region), outside ISO/RTOs; no retail choice; imports/exports immaterial for SSS claims.

***

### 2. Data‑Source Inventory

Priority follows `../methodologies/sss-methodology.md` (utility‑attested preferred; public fallback used here):

* **Retail sales**: U.S. EIA Form 861 (2023).
* **Compliance mandates & REC retirements**: Florida PSC dockets; DSIRE Florida (no RPS/CES); no compliance tracking system required.
* **Generation by plant/fuel**: EIA Form 923 (2023); FPL Ten‑Year Site Plan (2023); NextEra Energy Form 10‑K.
* **Emission factors**: EPA eGRID (2021 FRCC baseline) adjusted qualitatively to 2023 mix; FPL fuel‑mix disclosures.
* **Certificate treatment**: FPL SolarTogether program documentation (REC exclusion for non‑subscribers).
* **Regional planning/context**: FRCC Load & Resource Plan; EIA Florida state energy profile.

All sources reflect public data with retrieval primarily in early 2024; see Section 7 for citations.

***

### 3. Workflow (Replicable Steps)

**Step 1: Define Market Boundary**\
Identify FPL’s regulated, vertically integrated territory in peninsular Florida. SSS covers all default load under PSC oversight. Legal entity: Florida Power & Light Company.

**Step 2: Extract Retail‑Sales Volumes**\
Use EIA Form 861 total retail sales for 2023: 127,522,613 MWh (all sectors). Excludes voluntary green‑program opt‑ins from SSS attribution.

**Step 3: Quantify Compliance Obligations & REC Retirements**\
Florida has no RPS/CES mandate (DSIRE/PSC). Compliance obligations = 0 MWh; SSS REC retirements = 0 MWh. Voluntary program RECs (e.g., SolarTogether) excluded from SSS. Public disclosures indicate solar RECs sold externally when not retired for subscribers.

**Step 4: Identify Non‑RPS Zero‑Carbon SSS Resources**\
Eligible embedded zero‑carbon generation:

* Nuclear: ~29.3 million MWh from Turkey Point, St. Lucie, and Farley units (EIA/FPL filings). Treated as zero‑carbon within SSS (no RECs required).
* Hydro/Other: Negligible in 2023 for FPL.
* Solar: Physical MWh present but attributes sold or retired for voluntary programs; excluded from SSS zero‑carbon total.

**Step 5: Assemble SSS‑Retired Zero‑Carbon MWh (SSS Bundle)**\
Formula: SSS_REC_MWh = RPS_retired_MWh (0) + Eligible_public_asset_MWh (~29.3M nuclear) − RECs_sold_externally_MWh − Voluntary_program_RECs_MWh.\
Result: ~29.3 million MWh zero‑carbon (all nuclear) ≈ ~21–23% of retail sales.

**Step 6: Construct Supplier‑Specific Emission Factor (SSEF)**\
No published utility SSEF integrating RECs; apply bottom‑up residual method per methodology:

* Residual mix after subtracting nuclear ≈ ~79% fossil (primarily natural gas; <3% coal/oil).
* Treat unbundled solar as fossil‑equivalent for emissions (avoid free pass).
* Apply fuel‑specific factors (CO₂, CH₄, N₂O) from eGRID FRCC baseline with 2023 adjustments.\
Estimated SSEF ≈ 0.315 t CO₂e/MWh (~315 kg CO₂e/MWh).

**Step 7: Allocate Pro‑Rata Entitlement to Reporting Customer**\
For customer load L_customer (MWh):

* Claimable zero‑carbon MWh = (29.3M / 127.5M) × L_customer ≈ 23% of load.
* Apply SSEF to remaining ~77% for market‑based Scope 2.

**Step 8: Optional Hourly Proxy**\
Not implemented (no hourly residual‑mix factors for FRCC). If future hourly residuals become available, apply subtraction per hour and disclose limitations when using annual proxies.

**Step 9: QA/QC & Documentation**\
Cross‑verify nuclear and retail sales vs. EIA and FPL filings; confirm zero compliance obligations; ensure no double‑counting (exclude voluntary RECs). Version‑stamp inputs; archive calculations (notebook/audit sheet).

***

### 4. Data‑Quality Hierarchy

1. Utility‑attested data and certificate‑tracking verification (not available; not used).
2. Regulatory filings and official statistical datasets (EIA, PSC, eGRID) — used.
3. Bottom‑up reconstructions with documented assumptions — applied for SSEF.\
Overall confidence: High for volumes; Medium‑High for SSEF estimate.

***

### 5. Region‑ / Utility‑Specific Adaptations

* **Policy context**: Florida has no RPS/CES; voluntary solar programs strip RECs from SSS.
* **Market structure**: Vertically integrated, non‑ISO regulated utility; SSS encompasses default service.
* **Voluntary programs**: SolarTogether subscribers receive associated RECs; excluded from SSS bundle.
* **Fuel mix quirks**: Heavy nuclear/gas; minimal coal/oil in 2023; limited hydro.

***

### 6. Limitations & Future Work

* Annual baseline; hourly extension pending availability of hourly residual factors for FRCC.
* Nuclear output approximated via EIA/filings; minor variations possible.
* Treating sold solar attributes as fossil‑equivalent is conservative; refine if utility‑verified SSEF becomes available.
* Plan annual refresh; monitor Florida policy changes; evaluate hourly proxies if credible datasets emerge.

***

### 7. Citations and Source Log

Provide full references with stable links and retrieval dates (primarily retrieved early 2024):

* EIA Form 861 (2023): FPL retail sales volumes.
* EIA Form 923 (2023): Nuclear generation (Turkey Point, St. Lucie, Farley).
* EPA eGRID (2021, FRCC baseline): Fuel‑specific emission factors; adjusted to 2023.
* Florida PSC dockets: FPL Ten‑Year Site Plan (2023) and fuel mix disclosures.
* DSIRE Florida: Confirmation of no RPS/CES mandate.
* NextEra Energy (FPL parent) Form 10‑K (2023): Ownership and portfolio context.
* FRCC Load & Resource Plan (2023): Regional planning context.
* FPL SolarTogether program FAQ: REC treatment for subscribers/non‑subscribers.

***

### 8. Versioning and Change Log

* v0.2 (2025‑09‑28): Refactored to updated SSS methodology/template; added At‑a‑Glance metrics, clarified SSEF method, and citations log.
* v0.1 (2024‑Q1): Initial public‑source estimate and narrative for 2023.
