# Instructions for Finding Supplier Sales Volume

This document provides comprehensive, step-by-step instructions for analysts to identify, verify, and document sales volume for each qualifying supplier-region pair (e.g., from a spreadsheet of utilities/suppliers by country/state). The process is designed for the Granular Registry SSS Reporting platform, aligning with GHG Protocol Scope 2 updates (as of September 13, 2025). Sales volume refers to the supplier's annual electricity deliveries/sales in the region (e.g., GWh or TWh sold to customers), including breakdowns by sector (e.g., residential, industrial, commercial, agricultural), growth trends (e.g., YoY %), peak demand if available, and proportions tied to SSS categories (e.g., volumes under regulated rates for cost recovery). Focus on public data for the most recent years (2023–2025), prioritizing supplier-specific over aggregated data to support SSS emissions allocation (e.g., pro-rata calculations per Scope 2 revisions).

Analysts must process one pair at a time, documenting in a standardized template (see Section 6). Aim for >70% coverage of the supplier's regional sales; flag incomplete data (e.g., seasonal estimates only). Re-evaluate annually or upon events like market reforms (e.g., post-2025 EU Electricity Market Design updates or U.S. IRA extensions). Allocate 2–4 hours per pair, depending on region.

## 1. Preparation

* **Review Pair Details**: From the spreadsheet, note supplier name, region (e.g., Duke Energy - North Carolina), qualifying SSS categories (from Step 2), and related data (e.g., resource mix or EAC retirements for cross-linkage, such as sales-to-generation ratios).
* **Define Scope**: Target retail/wholesale electricity sales (delivered to end-users); include net of losses if specified. Exclude non-electricity (e.g., gas sales) or non-regional volumes (e.g., exports).
* **Gather Tools**: Use web browsers, PDF readers, and analysis software (e.g., Excel for trends, Python/Pandas for aggregation if needed). No proprietary tools.
* **Ethical Note**: Rely solely on public sources; do not contact suppliers or access paywalled data without approval.

## 2. Initial Search and Data Identification

* **Step 2.1: Keyword Formulation**: Craft targeted queries, e.g., "\[Supplier] electricity sales volume \[Region] 2025" or "\[Supplier] retail deliveries GWh \[Year]". Include variants: "customer sales data", "energy consumption by utility", "annual revenue report" (for volume-derived estimates).
* **Step 2.2: Primary Source Search**:
  * Start with supplier's website: Navigate to investor relations, annual reports, or regulatory filings (e.g., search "sales volume report 2025").
  * Check regulatory bodies: E.g., U.S. PUC/FERC for utility data; EU national agencies for consumption stats.
* **Step 2.3: Secondary Database Query**:
  * Use global aggregators for context: IEA Electricity 2025 (iea.org/reports/electricity-2025) for country trends; Ember Global Electricity Review 2025 (ember-energy.org/latest-insights/global-electricity-review-2025/) for demand overviews.
  * If supplier-specific unavailable, use as proxy but note limitations.
* **Step 2.4: Explore Alternatives**: If initial searches fail, try semantic variations (e.g., "load served" for non-U.S.); check news/academic sources for indirect data (e.g., via Reuters or S\&P Global for 2025 forecasts).

## 3. Regional-Specific Guidance

Adapt searches to regional data ecosystems; prioritize supplier-level sales where possible.

* **United States**:
  * Primary: EIA Electric Sales, Revenue, and Average Price (eia.gov/electricity/sales\_revenue\_price/) for annual utility sales (2023 data; 2025 release October); Electric Power Monthly (eia.gov/electricity/monthly/) for monthly/rolling data.
  * Forms: EIA-861 (annual sales by utility) and EIA-861M (monthly) at eia.gov/electricity/data.php.
  * Additional: EEI Industry Data (eei.org/resources-and-media/industry-data) for aggregates; State PUC sites for filings.
  * Verification: Cross-check with Annual Energy Outlook 2025 (eia.gov/outlooks/aeo/) for projections.
* **European Union**:
  * Primary: ENTSO-E Power Statistics (entsoe.eu/data/power-stats/) for monthly/yearly consumption by country/operator (export as CSV).
  * Eurostat Energy Balances (ec.europa.eu/eurostat/web/energy/data) for sales/consumption; Ember European Electricity Review 2025 (ember-energy.org/latest-insights/european-electricity-review-2025/) for trends.
  * National: E.g., Ofgem (U.K.) or BNetzA (Germany) for utility reports.
  * Note: Post-2025 Electricity Market Design, enhanced demand reporting.
* **China**:
  * Primary: National Energy Administration (nea.gov.cn) for provincial sales data; Ember China Energy Transition Review 2025 (ember-energy.org/latest-insights/china-energy-transition-review-2025/) for overviews.
  * Aggregators: CEC (China Electricity Council) reports; IEA China profiles.
  * Challenges: Less supplier-specific; use state-owned enterprise annuals (e.g., State Grid PDFs).
* **India**:
  * Primary: Central Electricity Authority Dashboard (cea.nic.in/dashboard/) for monthly/annual sales; MoSPI Energy Statistics India 2025 (mospi.gov.in/sites/default/files/publication\_reports/Energy\_Statistics\_2025/).
  * Additional: POSOCO for grid data; State DISCOM reports.
  * Note: Focus on FY 2024-25 data (April-March).
* **Brazil**:
  * Primary: ANEEL (aneel.gov.br) for distribution data; ONS (ons.org.br) for system consumption.
  * EPE (epe.gov.br) for energy reports; Ember for monthly insights (e.g., wind/solar impacts on demand).
* **Australia**:
  * Primary: AEMO NEM Data Dashboard (aemo.com.au/energy-systems/electricity/national-electricity-market-nem/data-nem/data-dashboard-nem) for regional sales; Quarterly Energy Dynamics (aemo.com.au) for Q2 2025 averages.
  * AER (aer.gov.au) for state data.
* **Other Regions (e.g., Southeast Asia, Africa)**: Default to IEA/IRENA country profiles; national ministries (e.g., Indonesia's PLN reports). For emerging markets, use World Bank Energy Data (databank.worldbank.org).
* **Global Fallbacks**: IEA Global Energy Review 2025 (iea.org/reports/global-energy-review-2025/); Energy Institute Statistical Review (energyinst.org/statistical-review); RFF Global Energy Outlook 2025 (rff.org/publications/reports/global-energy-outlook-2025/).

## 4. Data Extraction and Analysis

* **Step 4.1: Extract Raw Data**: Download PDFs/CSVs; parse volumes (e.g., GWh by sector). Note units and periods (e.g., fiscal vs. calendar year).
* **Step 4.2: Calculate if Needed**: Compute totals/trends (e.g., YoY %: (2025 - 2024)/2024 \* 100); use tools like Excel or Python (e.g., df\['growth'] = df\['sales'].pct\_change() \* 100).
* **Step 4.3: Link to SSS**: Proportion volumes to categories (e.g., 60% residential under customer funding).
* **Step 4.4: Adjust for Context**: Normalize (e.g., per capita) or include peaks (e.g., from AEMO dashboards).

## 5. Verification and Quality Assurance

* **Multi-Source Cross-Check**: Compare at least three sources (e.g., supplier report vs. EIA vs. IEA). Flag discrepancies >5% (e.g., due to net vs. gross metering).
* **Mathematical Validation**: Verify totals (e.g., sector sums = overall); perform sensitivity analysis (±10% on trends).
* **Challenge Assumptions**: Assume data is accurate—check for revisions (e.g., search "\[Supplier] sales correction 2025"). Consider improbables: Weather impacts skewing 2025? Verify via Ember reviews.
* **Triple-Verify**: Re-search independently; use alternative methods (e.g., derive from revenue/price if direct unavailable). Document uncertainties (e.g., "Preliminary 2025; full release October").
* **Logical Scrutiny**: Review for biases (e.g., underreported EVs in U.S.); seek counter-evidence (e.g., Reuters forecasts). Confirm alignment with GHG Protocol (e.g., consumption-based reporting).
* **Final Reconsideration**: After drafting, re-process the pair from Step 2 to confirm no oversights.

## 6. Documentation

Use this template for each pair (e.g., in Excel/Google Sheets):

| Field                     | Description                                   | Example                                                                                                               |
| ------------------------- | --------------------------------------------- | --------------------------------------------------------------------------------------------------------------------- |
| Supplier                  | Name                                          | Duke Energy                                                                                                           |
| Region                    | State/Country                                 | North Carolina                                                                                                        |
| Qualifying SSS Categories | From Step 2                                   | Regulated Cost Recovery                                                                                               |
| Sales Volume Breakdown    | Table of GWh by sector/trend (2023–2025 avg.) | Total: 100 TWh (Residential: 40%, Industrial: 30%); +5% YoY                                                           |
| Proportion Tied to SSS    | % by category                                 | 70% under Regulated                                                                                                   |
| Data Vintage              | Years covered                                 | 2023–2024 (2025 projected)                                                                                            |
| Sources                   | List with URLs                                | EIA-861 (eia.gov/electricity/data.php, accessed 09/13/2025); Duke Annual Report (duke-energy.com/investors, PDF p.32) |
| Uncertainties/Notes       | Gaps, assumptions                             | Excludes self-generation (5% offset); Pending demand growth from data centers                                         |
| Completeness Score        | % coverage                                    | 90% (supplier-specific)                                                                                               |

Compile into a master report; include visuals (e.g., line charts of trends).

## 7. Risks and Mitigations

* **Risk: Data Unavailability**: Emerging markets lack detail. _Mitigation_: Use aggregates as proxy; flag and recommend enhanced disclosures.
* **Risk: Inaccuracy/Staleness**: 2025 data preliminary. _Mitigation_: Prioritize latest releases; average with priors.
* **Risk: Regional Variations**: Definitions differ (e.g., gross vs. net sales). _Mitigation_: Standardize per IEA guidelines.
* **Risk: Sectoral Gaps**: Incomplete breakdowns. _Mitigation_: Infer from national shares (e.g., Eurostat).
* **Pitfalls Addressed**: Assumed constant growth—mitigated by YoY checks. Logical gaps (e.g., ignoring EVs)—adjust via EEI projections (±20% sensitivity). Oversights (e.g., losses)—include via IEA factors (5–15%).
