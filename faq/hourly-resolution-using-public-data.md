# Hourly Resolution Using Public Data

## **Overview of SSS Reports Based on Public Data**

SSS reports typically start with annual aggregates but can achieve hourly resolution depending on data availability. This granularity is essential for 24/7 carbon-free energy (CFE) matching, where emissions are tracked and matched hour-by-hour to support advanced decarbonization claims. Hourly resolution transforms SSS from a static baseline into a dynamic foundation for procurement strategies, allowing users to identify temporal gaps in CFE coverage and layer voluntary purchases accordingly.

The process for generating hourly SSS reports involves disaggregating annual CFE volumes (e.g., retired RPS Renewable Energy Certificates or RECs, publicly owned hydro/nuclear output) using public hourly grid profiles. This proxy method assumes SSS resources follow typical technology-specific dispatch patterns (e.g., solar peaks midday, nuclear provides baseload). While not as precise as meter-level data, it meets GHG Protocol quality criteria for exclusivity, deliverability, and transparency when properly documented.

## **Factors Influencing Hourly Resolution in SSS Reports**

The ability to produce hourly SSS reports hinges on the availability and quality of public data sources. Key considerations include:

* **Annual Baseline Data**: Public filings provide the foundation, such as utility Power Content Labels (PCLs), RPS compliance reports, and emission factors. These disclose annual CFE percentages, retired REC volumes, and resource mixes. Sources include state regulators (e.g., California Public Utilities Commission or CPUC), federal agencies (e.g., U.S. Energy Information Administration or EIA), and utility disclosures.
* **Hourly Grid Profiles**: To achieve temporal disaggregation, hourly datasets from grid operators or national statistics are layered on top. Examples include:
  * Hourly generation by fuel type (e.g., EIA's Hourly Electric Grid Monitor or Form 923 datasets).
  * System load and supply profiles (e.g., from Independent System Operators like CAISO in California).
  * Estimated technology-specific curves (e.g., solar/wind capacity factors from NREL or Ember).
* **Data Availability Spectrum**:
  * **High Availability Regions**: In data-rich markets like the U.S. (e.g., California via CAISO and EIA) or Europe (via ENTSO-E), hourly resolution is feasible with low uncertainty. Public datasets often cover >90% of grid activity, enabling accurate proxies.
  * **Medium Availability**: In regions like Canada or Australia, annual RPS data can be paired with partial hourly profiles (e.g., from Statistics Canada or AEMO), but assumptions may introduce ±10-20% uncertainty in variable renewable hours.
  * **Low Availability**: In emerging markets, hourly data may be absent, limiting reports to annual resolution. In such cases, users default to smeared annual averages (e.g., dividing CFE evenly across 8,760 hours) and disclose limitations.
* **Methodological Steps for Hourly Proxy**:
  1. Calculate annual SSS CFE share: (Retired RPS RECs + non-RPS zero-carbon SSS MWh) / Utility retail sales MWh.
  2. Disaggregate by technology: Allocate volumes based on public profiles (e.g., nuclear as flat baseload, wind as variable).
  3. Apply to hours: Hourly SSS CFE MWh = Annual SSS CFE by tech × (Hourly grid output % by tech / Annual grid output % by tech).
  4. Compute CFE%: (Hourly SSS CFE MWh / Hourly load MWh) × 100.
  5. Adjust for residual mix: Subtract SSS CFE from hourly residual emission factors (if available) to avoid double-counting.

This approach ensures SSS reports are credible proxies, but users must flag them as estimates and prioritize supplier-attested data when possible.

## **Example: Generating an Hourly SSS Report for PG\&E in California**

Pacific Gas and Electric Company (PG\&E), a major investor-owned utility in California, serves as an illustrative case for hourly SSS reports. PG\&E's SSS includes RPS-mandated renewables (e.g., wind, solar) and other carbon-free resources like large hydro and nuclear, recovered through regulated tariffs and non-bypassable charges (e.g., Power Charge Indifference Adjustment or PCIA). California’s robust public data ecosystem—via CPUC, CAISO, and EIA—enables high-resolution proxies.

### **Step 1: Gather Annual Baseline Data**

* From PG\&E's 2023 Power Content Label (PCL, as the most recent available in public records as of mid-2025; 2024 PCL expected later this year): PG\&E's delivered mix was approximately 33% eligible renewables (e.g., RPS-compliant wind/solar/geothermal), 14% large hydro, 50% nuclear, and 3% natural gas. This results in nearly 100% GHG-free electricity under CEC methodology, with RPS compliance at \~33% renewables.
* RPS Compliance: Per CPUC's 2024 RPS Annual Report, PG\&E retired sufficient RECs to meet California's 60% RPS target trajectory (actual 2023 compliance \~44% renewables, exceeding the interim mandate). Retired REC volumes: \~100 TWh equivalent for PG\&E's \~200 TWh retail sales (pro rata \~50% CFE annually, focusing on zero-carbon attributes).
* Sources: CPUC RPS compliance filings, PG\&E PCL PDFs, and EIA Form 861 for retail sales.

### **Step 2: Access Hourly Profiles**

* CAISO provides hourly generation data by fuel type (e.g., EIA's 2024 CAISO Hourly Renewable Fuel Mix Generation dataset, covering solar, wind, hydro, nuclear, and gas).
* System-wide hourly load: CAISO's Historical EMS Hourly Load files (e.g., December 2024 data available by March 2025).
* Utility-specific estimation: PG\&E represents \~40% of CAISO load; scale system profiles proportionally, or use EEI's supplier-specific estimated hourly profiles if available.

### **Step 3: Disaggregate to Hourly Proxy**

* Assume a facility with 10,000 MWh annual load on PG\&E SSS.
* Annual SSS CFE share: \~97% (33% RPS renewables + 64% hydro/nuclear).
* Hourly breakdown (using 2024 CAISO data):
  * Nuclear (\~50% baseload): Flat \~0.5 MWh/hour proxy per MWh load.
  * Hydro (\~14%): Variable, peaking in spring/summer evenings per CAISO profiles.
  * Renewables (\~33%): Solar peaks 10 AM–4 PM (\~80% of output); wind mostly at night.
* Example Hourly Calculation (Hypothetical Hour 12:00 PM, July 2024):
  * Grid profile: Solar 30% of supply, hydro 10%, nuclear 40%, gas 20%.
  * SSS CFE MWh = (0.33 × solar profile) + (0.14 × hydro) + (0.50 × nuclear) = 0.73 MWh per MWh load.
  * CFE% = 73% (residual 27% from gas, EF \~0.4 kg CO₂e/MWh).
* Aggregate: Over 8,760 hours, average CFE% \~80% in sunny hours, \~50% at night.

This proxy uses public CAISO/EIA datasets without meter access, with uncertainty noted for curtailment events.

## **Using Hourly SSS Data for 24/7 Hourly Matching Coverage Estimation**

Hourly SSS reports serve as the baseline for calculating 24/7 CFE matching coverage, which measures the percentage of hourly load matched by zero-carbon attributes. This aligns with emerging standards like the GHG Protocol's hourly matching requirements and supports claims such as "80% 24/7 CFE."

* **Estimation Process**:
  1. Input hourly load profile (e.g., from facility meters or standard shapes).
  2. Overlay SSS CFE proxy: For each hour, match SSS CFE MWh against load.
  3. Compute Coverage: Annual CFE Score = (Sum of matched hourly CFE MWh / Total annual load MWh) × 100.
     * Unmatched hours (e.g., nighttime gaps) use residual mix EF (e.g., CAISO hourly residuals, often fossil-heavy).
  4. Example with PG\&E: For a data center with a flat 1 MWh/hour load, SSS might cover 90% of daytime hours (solar/hydro) but only 60% overnight (nuclear baseload). Overall: \~75% 24/7 CFE coverage, with Scope 2 emissions reduced proportionally.

This reveals scarcity (e.g., peak evening hours with low CFE), driving targeted procurement.

## **Building to 100% Hourly Matching with Voluntary Procurement**

SSS provides a "free" foundation (e.g., 75% coverage in the PG\&E example), but gaps require voluntary additions via the Granular Registry and Marketplace. Layering procurement achieves 100% 24/7 matching:

* **Identify Gaps**: Use SSS report to pinpoint low-CFE hours (e.g., winter evenings with minimal solar).
* **Add Voluntary Instruments**:
  * Procure time-stamped Granular Certificates (GCs) for unmatched hours (e.g., wind GCs for nights, storage-backed solar for peaks).
  * Options: PPAs, unbundled RECs, or green tariffs matching SSS boundaries (e.g., CAISO-deliverable).
* **Stacked Calculation**:
  1. Baseline: SSS CFE% per hour.
  2. Add Voluntary: Total CFE% = SSS CFE% + Voluntary GC% (capped at 100% per hour).
  3. Example: PG\&E SSS covers 60% at night; buy 40% wind GCs → 100% matched.
* **Benefits**: Reduces over-procurement (e.g., no need to buy annual RECs, ignoring SSS). In the Marketplace, users can filter GCs by time/region to complement SSS, ensuring incrementality and compliance.
