# Estimating SSS from Public Sources

> Note: Public-data estimation is now a fallback path under `sss-methodology.md`. Use this file as an annex for the ETL fallback mapping and examples. The canonical schema, calculations, and decision tree live in `sss-methodology.md`.

## Annex scope (details-only)

Use this annex to populate the unified schema in `sss-methodology.md` when utility-submitted data are unavailable. Do not restate calculations; only map public sources to schema fields with fallback order and QA.

## Field-by-field ETL mapping (fallback order)

- retail_sales.total_mwh:
  1) Regulator filings (e.g., EIA 861, Eurostat)
  2) Utility annual reports / sustainability reports
  3) National statistical offices; modeled estimate (flag high-uncertainty)
- rec_retirements_for_sss.records:
  1) Tracking-system compliance/public reports (WREGIS, GATS, AIB, I-REC)
  2) Regulator RPS/CES reports
  3) Supplier disclosures (PCL, EEI); infer linkage to SSS where explicit
- rec_retirements_for_sss.external_sales_mwh:
  1) Registry voluntary sales reports
  2) Supplier financial notes; trade press
- non_rps_zero_carbon_for_sss.records:
  1) Public/regulated asset disclosures (IRPs, FERC Form 1, ZEC/legacy hydro dockets)
  2) Utility reports; government asset registries
- generation_mix (owned/contracted/purchases):
  1) Supplier PCL/EEI/sustainability disclosures
  2) National stats with ownership/purchase annotations
  3) Bottom-up reconstruction from plant-level datasets (eGRID, EU ETS, PRTR)
- emissions:
  1) Supplier-published SSEF
  2) Residual-mix EF (AIB/RE-DISS)
  3) Fuel-specific intensities applied to reconstructed mix (eGRID, national inventories)
- compliance:
  1) RPS/CES filings; DSIRE/policy databases
  2) Statutory percentages; compute obligation MWh from retail_sales
- provenance_and_quality:
  - Record sources, retrieval dates; compute confidence score; note banking/deadline assumptions

## QA checklist (public data)

- Triangulate each field with ≥2 independent sources; target 3 where available.
- Reconcile totals: generation mix sums to retail sales ± losses; REC retirements ≥ renewable claims.
- Validate vintages and retirement dates against jurisdictional deadlines.
- Document gaps and apply conservative defaults per `sss-methodology.md` when unresolved.

## Regional notes (abbrev.)

- California: CPUC PCL for supplier SSEF; WREGIS for compliance; strong transparency.
- PJM/NY: Hourly or granular timestamps available; watch for ZEC programs.
- EU: Use AIB GO cancellations and Residual Mix; verify supplier disclosures against AIB.

---

Legacy detailed methodology retained below for reference. For normative definitions and calculations, use `sss-methodology.md`.

As a renewable energy technical expert advising Clean Incentive, Inc., which owns and operates the Granular Registry and Marketplace, this methodology outlines a standardized, transparent process for estimating (i) the volume of Renewable Energy Certificates (RECs) and other zero-carbon attributes retired on behalf of SSS customers and (ii) a supplier-specific emission factor (SSEF) for market-based Scope 2 reporting. This approach is applied when a Load-Serving Entity (LSE) or utility does not submit structured data directly to the Granular Registry. It leverages publicly available sources to generate a defensible proxy bundle (retired RECs paired with SSEF), aligned with the draft GHG Protocol SSS guidance as a "credible third-party dataset." The process is conducted annually per energy-market region (e.g., U.S. state + ISO, Canadian province, EU Member State, etc.), with adjustments for local data transparency.

This methodology focuses on annual baselines; hourly extensions are addressed in Section 8 for regions with time-stamped data availability.

## **1. Scope and Definitions**

* **Standard Supply Service (SSS)**: Default electricity service with costs recovered via regulated tariffs or universal service obligations, including mandated clean energy (e.g., from Renewable Portfolio Standards or RPS).
* **Proxy Bundle**: Paired dataset of estimated retired RECs (MWh) and SSEF (kg CO₂e/MWh) derived from public sources when direct supplier allocation is unavailable.
* **Energy-Market Region**: Jurisdictional footprint for retail load service and REC retirements (e.g., California ISO, PJM Interconnection, or Ontario province).
* **REC**: Renewable Energy Certificate, representing 1 MWh of renewable generation; extended here to include other zero-carbon attributes (e.g., from nuclear or large hydro under certain programs).

Estimates adhere to GHG Protocol Scope 2 Quality Criteria, ensuring no double-counting and alignment with market-based accounting.

## **2. Data-Source Inventory**

Public sources are prioritized based on availability and reliability. Key information needs and representative sources include:

| Information Need                           | North America Examples                                                             | Europe Examples                                                           | Other OECD/Emerging Markets Examples                                |
| ------------------------------------------ | ---------------------------------------------------------------------------------- | ------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| Utility Retail-Sales Volumes               | EIA Form 861 (U.S.); Statistics Canada CANSIM 127 (CA)                             | Eurostat "Retail electricity sales"; Ofgem CCA data (UK)                  | AEMO NEM "Retail sales" (AU); IEA country energy balances           |
| Mandated RPS/CES Targets & REC Retirements | State compliance reports; PJM GATS "RPS Retired"; M-RETS "Compliance"; WECC WREGIS | AIB Disclosure "Residual Mix & Cancelled GOs"; National regulator reports | I-REC Public Reports; National renewables agency filings            |
| Publicly Owned Hydro/Nuclear Attributes    | Utility IRPs; Power Content Labels (CA); FERC Form 1 fuel mix                      | National statistical offices; ENTSO-E TSO disclosures                     | Provincial/state utility annual reports; Government asset registers |
| System/Supplier Emission Factors           | EEI "Carbon Emissions & Mix"; Climate Registry "Utility-Specific EF"               | AIB "Residual Mix EF"; RE-DISS                                            | Gov’t GHG inventories; Utility sustainability reports               |
| Plant-Level Emission Factors               | EPA eGRID & Form 923; Canada NIR                                                   | E-PRTR; EU ETS verified data                                              | National PRTRs; UNFCCC CRF tables                                   |

Data catalogs are maintained in the Granular Registry repository (/data/catalogue/), with source links, refresh cadences, and version stamps.

## **3. Workflow (Per Market-Utility Pair)**

Follow these steps sequentially, documenting assumptions and sources in a Jupyter notebook attached to the Registry entry.

### **Step 1: Define Market Boundary**

* Identify the balancing authority/ISO or regulated franchise area (e.g., PG\&E service territory in California).
* Record LSE legal entities (e.g., Pacific Gas & Electric).

### **Step 2: Extract Retail-Sales Volumes**

* Fetch latest calendar-year MWh from sources in Section 2 (e.g., EIA Form 861).
* Flag partial-year or estimated values.

### **Step 3: Quantify Compliance REC Obligations & Retirements**

* Retrieve statutory RPS/Clean Energy Standard (CES) percentage or absolute MWh obligation (e.g., from state regulator reports).
* Pull actual MWh retired (by technology tier) from certificate-tracking systems (e.g., WREGIS reports).
* Calculate Obligation Gap = Obligation – Actual Retired; document if non-zero (e.g., due to banking or penalties).

### **Step 4: Identify Non-RPS Zero-Carbon SSS Resources**

* Scan public filings for regulated or publicly funded zero-carbon assets not in RPS (e.g., legacy hydro, nuclear under ZEC programs).
* Record annual MWh from sources like utility IRPs or FERC Form 1 (e.g., large hydro output).

### **Step 5: Assemble SSS-Retired REC Volume**

* SSS\_REC\_MWh = RPS\_Retired + Public\_Asset\_Zero-Carbon\_MWh – RECs\_Sold\_Externally
* Subtract external sales evidenced in tracking-system voluntary market reports to avoid double-counting.

### **Step 6: Construct Supplier-Specific Emission Factor (SSEF)**

* **Preferred (6A)**: Use published SSEF integrating REC retirements (e.g., EEI, California Power Content Label, or AIB Residual Mix).
* **Fallback (6B)**: Bottom-up calculation:\
  a. Build generation mix = Owned Generation + Contracted + Net Purchases (from fuel mix disclosures).\
  b. Subtract volumes matched to RECs retired in Step 5 (zero-carbon adjustment).\
  c. Multiply residual fossil MWh by fuel-specific CO₂ intensity (e.g., from eGRID).\
  d. SSEF = (Total tons CO₂e) / Retail Sales MWh.
* Include CH₄ and N₂O if required by local protocols.

### **Step 7: Allocate Pro-Rata Entitlement to Reporting Customer**

* For customer load L\_customer (MWh):\
  Claimable\_REC\_MWh = (SSS\_REC\_MWh / Retail\_Sales\_MWh) × L\_customer
* SSEF applies directly to the customer's SSS-supplied load.

### **Step 8: Optional Hourly Proxy**

* Where hourly residual-mix factors (H-RMFs) exist (e.g., GB, Nordics):\
  H\_SSS\_EF\_t = H\_Residual\_EF\_t – (H\_SSS\_CFE\_MWh\_t × 0 / H\_Load\_MWh\_t)\
  (Zero-carbon volumes nullify emissions in matching hours.)
* If no H-RMF, disclose approximation using annual factors and flag uncertainty.

### **Step 9: QA/QC & Documentation**

* Cross-verify REC volumes against multiple sources (e.g., regulator + registry).
* Ensure no double-counting between compliance and voluntary retirements.
* Version-stamp datasets with retrieval dates.
* Attach calculation notebook to Registry entry.

## **4. Data-Quality Hierarchy**

Prioritize sources as follows:

1. Supplier-attested, verified data (preferred).
2. Regulatory compliance filings (e.g., RPS reports, Power Content Labels).
3. Certificate-tracking system/residual mix reports.
4. Bottom-up generation-mix reconstruction.
5. If unavailable, assign average grid EF and mark as high-uncertainty.

**5. Region-Specific Adaptations**

| Region        | Key Quirks                                                     | Additional Data Pointers                                       |
| ------------- | -------------------------------------------------------------- | -------------------------------------------------------------- |
| PJM (U.S.)    | Hourly REC timestamps available; includes ZEC nuclear schemes. | State ZEC dockets; PJM-EIS Bulletin Board.                     |
| California    | Power Content Label publishes SSEF per supplier.               | CPUC PCL database (released year +1).                          |
| EU            | AIB Residual Mix and GO cancellations; public hydro assets.    | ENTSO-E production; Eurostat ownership tagging.                |
| Australia NEM | No federal RPS; LRET/SRES RECs and state targets.              | Clean Energy Regulator "REC Surrenders"; AEMO Generation Info. |
| Latin America | Widespread I-REC; limited retail transparency.                 | I-REC Public Reports + utility annual reports.                 |

## **6. Limitations & Future Work**

* Annual estimates may under- or over-allocate clean energy hourly; transition to time-stamped certificates planned.
* Assumes dispatch parity; may mis-estimate if curtailment occurs.
* Public hydro data approximate in some markets; incorporate confidence scores.
* Methodology updated annually or on policy changes via stakeholder review.

## **Example Calculation: PG\&E (California, 2022 Data)**

Assume a hypothetical customer with 10,000 MWh annual SSS load from Pacific Gas & Electric (PG\&E) in California. Using public sources (e.g., CPUC Power Content Label, WREGIS reports, EIA Form 861).

**Step 1-2**: Market = CAISO (PG\&E territory). Retail Sales = 78,000 GWh (EIA Form 861, converted to MWh).

**Step 3**: RPS Obligation = 44% (CPUC report). Actual Retired = 34,320,000 MWh RECs (WREGIS compliance, including eligible renewables).

**Step 4**: Non-RPS Zero-Carbon = 38,220,000 MWh (nuclear 49% + large hydro 7% from PCL; total \~37.4 GWh, but adjusted for SSS inclusion).

**Step 5**: SSS\_REC\_MWh = 34,320,000 + 38,220,000 – 0 (no external sales evidenced) = 72,540,000 MWh.

**Step 6**: Published SSEF = 206 lbs CO₂/MWh (PCL; converted to 93.4 kg CO₂/MWh), reflecting REC retirements and zero-carbon assets (96% GHG-free mix).

**Step 7**: Claimable\_REC\_MWh = (72,540,000 / 78,000,000) × 10,000 ≈ 9,300 MWh (93% zero-carbon share).\
SSEF applies as 93.4 kg CO₂/MWh to full load. Market-Based Scope 2 = 10,000 MWh × 93.4 = 934 tCO₂e.

**QA/QC**: Verified against PCL and WREGIS; no double-counting as RPS RECs are retired for SSS. Hourly proxy: Use CAISO H-RMF if available; otherwise, annual approximation flagged.
