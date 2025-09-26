# PG\&E

## Introduction

We are committed to providing transparent and credible estimates of Standard Supply Service (SSS) attributes through the Granular Registry and Marketplace. This public-facing documentation details the methodology for calculating SSS-related metrics for Pacific Gas and Electric Company (PG\&E) in California, including clean firm energy (CFE) allocations, pro-rata shares, emission factors, and scarcity analyses. These estimates support Scope 2 carbon accounting under frameworks like the GHG Protocol, ensuring customers can accurately reflect their share of mandated clean resources without double-counting or resource shuffling.

Our approach adheres to SSS guidance principles: traceable financial relationships (e.g., regulated cost recovery, non-bypassable charges), order of operations (SSS first, then voluntary procurement), and exclusions (e.g., no cost shifting). We rely exclusively on public data for reproducibility and auditability. This methodology is designed for auditors and stakeholders evaluating integration into corporate inventories, with all sources linked for verification.

For PG\&E in California, SSS primarily encompasses:

* RPS-eligible renewables via non-bypassable charges (e.g., Power Charge Indifference Adjustment - PCIA).
* Nuclear generation (Diablo Canyon) through regulated cost recovery.
* Large hydroelectric resources under public or utility ownership.

We update annually based on data releases (e.g., EIA early releases in August). Fallbacks use grid averages if specific data is unavailable. Hourly extensions are optional for advanced matching.

## Data Sources

All data is sourced from public, authoritative entities. We collect files annually and store them in versioned archives for traceability. Below are the key sources, with direct download links where available. For the most recent files, refer to the originating websites, as URLs may update.

### National and Regional Sources

These provide foundational data applicable across utilities, filtered for PG\&E-CA.

1. **EIA Form 861 (Annual Electric Power Industry Report)**
   * **Description**: Includes utility characteristics, retail sales (MWh), revenues, and customer counts by state and sector. Used for pro-rata share calculations and utility-state pair confirmation (PG\&E utility number: 14154).
   * **Files**: Utility\_Data\_\[YEAR]\_Data\_Early\_Release.xlsx, Sales\_Ult\_Cust\_\[YEAR]\_Data\_Early\_Release.xlsx.
   * **Source**: U.S. Energy Information Administration (EIA) - [https://www.eia.gov/electricity/data/eia861/](https://www.eia.gov/electricity/data/eia861/).
   * **Temporal Coverage**: Annual, early release in August (e.g., 2024 data released August 2025).
   * **Usage in SSS**: Aggregate sales across bundled and delivery services (Parts A, B, D per EIA notes) to derive total retail load; ownership type confirms regulated status.
2. **EIA eGRID (Emissions & Generation Resource Integrated Database)**
   * **Description**: Plant-level generation and emission factors (kg CO₂/MWh) for clean and fossil resources. Filtered for CA plants allocated to PG\&E (e.g., Diablo Canyon nuclear).
   * **Files**: eGRID\[YEAR-1].xlsx (e.g., eGRID2023 for 2024 calculations).
   * **Source**: U.S. Environmental Protection Agency (EPA) - [https://www.epa.gov/egrid/download-data](https://www.epa.gov/egrid/download-data).
   * **Temporal Coverage**: Biennial, with annual updates (latest: eGRID2023 released 2025).
   * **Usage in SSS**: Calculate supplier-specific emission factors (SSEF) for unspecified or fossil portions; verify zero-emission status for nuclear/hydro.
3. **EIA Hourly Electric Grid Monitor**
   * **Description**: Hourly generation by fuel type (e.g., renewables, nuclear, hydro) and load data for balancing authorities. Used for optional scarcity and time-matching analyses in CAISO.
   * **Files**: EBA.zip (bulk hourly data); CAISO-specific CSVs like caiso\_load\_act\_hr\_\[YEAR].csv.
   * **Source**: EIA - [https://www.eia.gov/electricity/gridmonitor/](https://www.eia.gov/electricity/gridmonitor/) and [https://www.eia.gov/opendata/bulkfiles.php](https://www.eia.gov/opendata/bulkfiles.php).
   * **Temporal Coverage**: Hourly, near real-time with historical archives (e.g., 2023-2024).
   * **Usage in SSS**: Compute hourly scarcity (% clean energy consumed after SSS allocation); derive hourly SSEF.

### PG\&E and California-Specific Sources

These capture mandated clean resources and compliance details unique to PG\&E.

1. **PG\&E Power Content Label (PCL)**
   * **Description**: Annual disclosure of power mix (% renewables, nuclear, hydro, fossil) and GHG-free claims, including unbundled RECs for offsets.
   * **Files**: \[YEAR] Power Content Label.pdf (e.g., 2023 PCL).
   * **Source**: PG\&E - [https://www.pge.com/assets/pge/docs/account/billing-and-assistance/bill-inserts/1224-power-content-label.pdf](https://www.pge.com/assets/pge/docs/account/billing-and-assistance/bill-inserts/1224-power-content-label.pdf).
   * **Temporal Coverage**: Annual, released fall (e.g., 2023 based on 2022 generation).
   * **Usage in SSS**: Breakdown SSS-CFE (% from RPS-eligible renewables, nuclear, large hydro); adjust for voluntary claims.
2. **CPUC Renewables Portfolio Standard (RPS) Annual Report**
   * **Description**: Statewide RPS progress, including PG\&E's REC retirements (MWh by resource), compliance status, and excess banking.
   * **Files**: California Renewables Portfolio Standard (RPS) Annual Report to the Legislature \[YEAR].pdf.
   * **Source**: California Public Utilities Commission (CPUC) - [https://www.cpuc.ca.gov/-/media/cpuc-website/divisions/office-of-governmental-affairs-division/reports/2023/2023-rps-annual-report-to-the-legislature.pdf](https://www.cpuc.ca.gov/-/media/cpuc-website/divisions/office-of-governmental-affairs-division/reports/2023/2023-rps-annual-report-to-the-legislature.pdf).
   * **Temporal Coverage**: Annual, released summer/fall.
   * **Usage in SSS**: Quantify non-bypassable RPS charges; subtract voluntary excess to avoid double-counting.
3. **PG\&E Integrated Resource Plan (IRP)**
   * **Description**: Long-term resource planning, including regulated cost recovery for nuclear, hydro, and renewables.
   * **Files**: PG\&E \[YEAR] IRP.pdf.
   * **Source**: PG\&E - [https://www.pge.com/en/about/doing-business-with-pge/integrated-resource-planning.html](https://www.pge.com/en/about/doing-business-with-pge/integrated-resource-planning.html) (latest filings).
   * **Temporal Coverage**: Biennial, with updates (e.g., 2023 cycle).
   * **Usage in SSS**: Identify resources tied to integrated resource planning (e.g., Diablo Canyon extension).
4. **PG\&E Nuclear Allocation Report**
   * **Description**: Allocation of Diablo Canyon nuclear MWh to load-serving entities, reflecting regulated recovery.
   * **Files**: PG\&E Nuclear Allocation \[YEAR].pdf.
   * **Source**: PG\&E or CPUC dockets - [https://avaenergy.org/wp-content/uploads/2024/04/Item-C9.-PGE-Nuclear-Allocationv1.pdf](https://avaenergy.org/wp-content/uploads/2024/04/Item-C9.-PGE-Nuclear-Allocationv1.pdf) (example from community aggregator; check PG\&E for official).
   * **Temporal Coverage**: Annual, tied to ERRA filings.
   * **Usage in SSS**: Allocate nuclear as SSS-CFE (government-mandated life extension).
5. **CPUC Power Charge Indifference Adjustment (PCIA) Reports**
   * **Description**: Details non-bypassable charges for RPS/CES compliance, ensuring no cost shifting to non-participants.
   * **Files**: Calculation of the Market Price Benchmarks for the Power Charge Indifference Adjustment \[YEAR].pdf.
   * **Source**: CPUC - [https://www.cpuc.ca.gov/-/media/cpuc-website/divisions/energy-division/documents/community-choice-aggregation-and-direct-access/calculation-of-mpb-2023-2024-final.pdf](https://www.cpuc.ca.gov/-/media/cpuc-website/divisions/energy-division/documents/community-choice-aggregation-and-direct-access/calculation-of-mpb-2023-2024-final.pdf).
   * **Temporal Coverage**: Annual, released October.
   * **Usage in SSS**: Confirm RPS as non-bypassable; calculate financial ties for pro-rata shares.

## SSS Classification and Methodology

We classify resources using SSS decision trees: Is the resource part of default service? Tied to mandates? Funded by customers? For PG\&E-CA:

1. **Regulated Cost Recovery**: Nuclear (Diablo Canyon) and large hydro from IRP filings; allocated if in regulated rate base.
2. **Non-Bypassable Charges**: RPS renewables via PCIA/RPS reports; RECs retired for compliance.
3. **Customer Funding**: Publicly owned hydro/nuclear where taxes/subsidies apply (cross-check with ownership in EIA 861).
4. **Exclusions**: Voluntary green tariffs (e.g., Solar Choice); subsidies without EAC retirement (disclose per Scope 2).

Step-by-Step Process:

* **Step 1: Identify Total Load**: Sum PG\&E-CA retail sales MWh from EIA 861 (bundled + delivery, excluding behind-the-meter).
* **Step 2: Quantify SSS Resources**: RPS retired RECs (from CPUC RPS) + nuclear/hydro MWh (from PCL/IRP/Nuclear reports).
* **Step 3: Allocate Pro-Rata Share**: SSS-CFE = (SSS resources MWh / total load) \* customer load (user-input or default).
* **Step 4: Calculate Emission Factor (SSEF)**: (Fossil MWh \* eGRID EF) / total MWh; adjust for unbundled REC offsets (from PCL).
* **Step 5: Prevent Double-Counting**: Subtract SSS from residual mix; disclose voluntary claims separately.
* **Step 6: Optional Hourly Matching**: For each hour (EIA Grid Monitor), H\_SSS\_EF = Hourly residual EF - (Hourly SSS-CFE / Hourly load); flag scarcity hours (>90% consumed).

Formulas:

* Pro-Rata Share (%) = (Customer Load MWh / Total Retail MWh) × 100
* SSS-CFE MWh = RPS Retired + Nuclear Alloc + Hydro Alloc - Voluntary Excess
* SSEF (kg CO₂/MWh) = Σ (Fossil Generation MWh × Plant EF) / Total MWh

## Validation and Transparency

* **Data Quality Checks**: Flag imputed values (EIA "I"); cross-verify totals (e.g., PCL % vs. RPS MWh).
* **Auditor Access**: All raw files archived; calculations reproducible via open-source scripts.
* **Disclaimers**: Estimates based on public data; not a substitute for supplier allocation. Disclose subsidies (e.g., nuclear extensions) and policy context.
* **Updates**: Reviewed annually; methodology evolves with GHG Protocol guidance.

## References

* GHG Protocol Scope 2 Guidance (WRI/WBCSD).
* SSS Supplemental Slides and Overview (internal drafts).
* All sources listed above with direct links.
