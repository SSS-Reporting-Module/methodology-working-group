# Step 3: Compile Public Data Sources for ETL

This document outlines Step 3 in the evaluation process for Supplier-Specific Scope 2 (SSS) reporting under GHG Protocol discussions. Following Step 1 (compiling a list of unique supplier-region pairs from the spreadsheet) and Step 2 (assigning SSS resource categories: Regulated Cost Recovery, Non-Bypassable Charges, and/or Customer Funding), Step 3 focuses exclusively on pairs that qualify for at least one category. For these qualifying pairs, analysts will systematically gather and document publicly available data on three key metrics: (1) Resource Mix (generation sources and emissions factors), (2) EAC Retirements (Energy Attribute Certificates, including RECs, GOs, and I-RECs), and (3) Sales Volume (electricity delivered/sold). This data supports granular SSS emissions calculations, such as supplier-specific allocation and temporal/deliverability matching, aligning with Scope 2 updates (e.g., Technical Working Group proposals as of August 2025).

Analysts should compile data for the most recent available years (e.g., 2023–2025), prioritizing supplier-specific granularity over aggregates. Use a standardized template for each pair (e.g., Supplier: \[Name], Region: \[State/Country], Qualifying Categories: \[List], Resource Mix: \[Table/Data], EAC Retirements: \[Summary], Sales Volume: \[Figures], Sources: \[List with URLs], Uncertainties: \[Notes]). Aggregate data into a master dashboard (e.g., Excel with pivot tables) for cross-pair analysis. Re-verify data quarterly, as energy markets evolve (e.g., post-IRA extensions or EU RED III implementations).

Key principles:

* **Public Data Only**: Restrict to freely accessible sources; avoid paywalls or proprietary APIs (use open datasets or public reports).
* **Granularity and Relevance**: Seek supplier-level data; fallback to regional averages if unavailable, noting the downgrade (e.g., <50% supplier-specific = flag as partial).
* **Multi-Angle Verification**: For each metric, cross-check with at least three independent sources (e.g., government, NGO, industry). Challenge assumptions (e.g., assume data staleness in emerging markets; test via sensitivity analysis on emissions impacts).
* **Uncertainties Documentation**: Explicitly note gaps (e.g., incomplete EAC tracking in Asia), regulatory risks (e.g., pending CSRD reporting mandates), and alternatives (e.g., satellite-derived mix vs. self-reported).
* **Threshold for Completeness**: Require data covering >70% of the supplier's operations in the region; otherwise, classify as "insufficient" and recommend further investigation.

## 1. Resource Mix

**Definition**: The composition of the supplier's electricity generation sources (e.g., % from coal, natural gas, nuclear, renewables) and associated emissions factors (e.g., gCO2e/kWh). Include breakdowns by fuel type, renewable subcategories (e.g., wind vs. solar), and any SSS-specific allocations (e.g., pro-rata for regulated resources).

### **What to Collect**:

* Annual generation mix percentages (e.g., 40% coal, 30% renewables).
* Emissions intensity (location-based and market-based, if available).
* Temporal data if granular (e.g., hourly mix for 2024–2025).
* Verification of ties to SSS categories (e.g., RPS-funded renewables under Non-Bypassable Charges).

### **Verification Steps**:

* Start with supplier-specific reports (e.g., sustainability disclosures or IRPs).
* Cross-verify with aggregate datasets (e.g., compare supplier data to national averages; flag discrepancies >10%).
* Use mathematical checks: Calculate weighted averages (e.g., via Python: import pandas; df.groupby('fuel').sum()) and compare to independent benchmarks (e.g., IEA vs. Ember).
* Challenge assumptions: Test for underreporting renewables (e.g., search for audits); consider improbable angles like unreported imports (verify via trade data).
* Triple-check: Browse primary source PDFs, run web searches for "\[Supplier] resource mix \[Region] 2025 audit", and use code execution for emissions modeling (e.g., factor \* generation = total emissions; validate against EDGAR database).

### **Data Sources** (Global and Regional):

* **Global**: IEA Electricity 2025 Report (iea.org/reports/electricity-2025) and Global Energy Review 2025 Dataset (iea.org/data-and-statistics); Ember Global Electricity Review 2025 (ember-energy.org/latest-insights/global-electricity-review-2025); REN21 GSR 2025 (ren21.net/gsr-2025); Our World in Data (ourworldindata.org/grapher/share-electricity-renewables); Enerdata Global Energy Trends (enerdata.net/publications/reports-presentations/world-energy-trends.html); Energy Institute Statistical Review (energyinst.org/statistical-review).
* **U.S.**: EIA eGRID (epa.gov/egrid) for subregional mix; EIA Form 860/861 (eia.gov/electricity/data.php) for utility-specific generation; EEI Industry Data (eei.org/resources-and-media/industry-data).
* **EU**: ENTSO-E Transparency Platform (transparency.entsoe.eu) for generation data; Eurostat Energy Balances (ec.europa.eu/eurostat/web/energy/data).
* **Asia (e.g., China, India)**: National Energy Administration (nea.gov.cn) for China; CEA India Reports (cea.nic.in); IRENA Country Profiles (irena.org).
* **Other**: World Bank Energy Data (databank.worldbank.org); RFF Global Energy Outlook (rff.org/publications/reports/global-energy-outlook-2025).
* **Tools**: Web searches for real-time updates (e.g., " \[Supplier] generation mix 2025"); browse PDFs (e.g., Ember report at ember-energy.org/app/uploads/2025/04/Report-Global-Electricity-Review-2025.pdf); code execution for aggregation.

**Uncertainties and Mitigations**: Data may lag (e.g., 2024 prelims in 2025 reports)—mitigate by averaging last two years. Regional biases (e.g., overreported renewables in EU)—cross-check with NGOs like Ember. Logical gaps (e.g., excluding T\&D losses)—adjust via IEA factors (±5–15%).

## 2. EAC Retirements

**Definition**: Records of retired Energy Attribute Certificates (e.g., RECs in U.S., GOs in EU, I-RECs globally), including volume (MWh), type (e.g., solar REC), retirement date, and supplier association. Focus on retirements tied to SSS categories (e.g., for RPS compliance under Non-Bypassable Charges).

### **What to Collect**:

* Total retired EACs by supplier (e.g., 500,000 MWh RECs in 2024).
* Breakdown by attribute (e.g., vintage year, generation source).
* Public claims or audits (e.g., for market-based Scope 2 reporting).
* Link to resource mix (e.g., % of renewables backed by retired EACs).

### **Verification Steps**:

* Query public registries for supplier-specific retirements.
* Cross-verify with compliance reports (e.g., RPS filings) and third-party audits (e.g., RE100 validations).
* Mathematical validation: Calculate coverage ratio (retired EACs / renewable generation); expect >90% for credible claims.
* Challenge assumptions: Probe for double-counting (e.g., search for controversies); consider alternatives like unretired EACs (verify via tracking systems).
* Triple-check: Use semantic searches on X for recent issues (e.g., " \[Supplier] REC retirement scandal 2025"); browse registry dashboards; code execution for trend analysis (e.g., SymPy for ratio equations).

### **Data Sources** (Global and Regional):

* **Global**: RECS Energy Certificate Association Public Info (recs.org/public-information/); I-REC Standard Registry (irecstandard.org); EPA Energy Attribute Certificates (epa.gov/green-power-markets/energy-attribute-certificates-eacs); RE100 Technical Criteria (there100.org/sites/re100/files/2025-04/RE100%20technical%20criteria%20%2B%20appendices%20%2815%20April%202025%29.pdf).
* **U.S.**: Regional registries like M-RETS (mrets.org/public-reports), NAR (nar.recstrack.com), PJM-GATS (gats.pjm-eis.com), WREGIS (wregis.org); EPA eGRID for bundled RECs; CRS Reports (resource-solutions.org).
* **EU**: AIB Guarantees of Origin Registry (aib-net.org); ENTSO-E for EAC data; EU ETS Public Reports (ec.europa.eu/clima/eu-action/eu-ets).
* **Asia/Other**: APX TIGRs (apx.com/tigrs) for Asia-Pacific; National registries (e.g., India's REC Registry at recregistryindia.nic.in).
* **Additional**: 3Degrees EAC FAQs (3degreesinc.com/what-we-do/implement-your-strategy/energy-attribute-certificates/energy-attribute-certificate-faqs/); World Kinect REC Role (world-kinect.com/blog/understanding-eacs-north-america-role-renewable-energy-certificates-recs).
* **Tools**: Browse registry URLs for search functions (e.g., instructions: "Extract retirement data for \[Supplier] in \[Region]"); web searches for "\[Supplier] EAC retirements 2025 report".

**Uncertainties and Mitigations**: Limited public access in some registries (e.g., aggregated only)—mitigate by using NGO summaries (e.g., Climate Impact Partners at climateimpact.com). Expiration risks (EACs valid 1 year)—focus on recent vintages. Oversights (e.g., non-disclosed retirements)—seek counter-evidence via web snippets.

## 3. Sales Volume

**Definition**: Annual electricity sales/deliveries by the supplier in the region (e.g., GWh sold to retail customers), including breakdowns by sector (e.g., residential, industrial) and ties to SSS (e.g., volumes under regulated rates).

### **What to Collect**:

* Total sales volume (e.g., 100 TWh in 2024).
* Growth trends (e.g., +5% YoY).
* Proportion tied to SSS categories (e.g., 60% under cost recovery).
* Load profiles if available (e.g., peak demand).

### **Verification Steps**:

* Extract from utility filings or national stats.
* Cross-verify with consumption data (e.g., match sales to IEA demand figures; discrepancy <5%).
* Mathematical checks: Normalize per capita (sales / population); compare to benchmarks (e.g., via NumPy arrays).
* Challenge assumptions: Account for self-generation offsets (e.g., search for net metering impacts); explore improbables like unreported exports.
* Triple-check: Use code execution for projections (e.g., linear regression on historical data); web searches for "\[Supplier] electricity sales \[Region] 2025"; browse state reports.

### **Data Sources** (Global and Regional):

* **Global**: IEA Data and Statistics (iea.org/data-and-statistics); Ember Global Electricity Review 2025 (ember-energy.org/app/uploads/2025/04/Report-Global-Electricity-Review-2025.pdf); IEA Electricity 2025 (iea.org/reports/electricity-2025).
* **U.S.**: EIA Electricity Data (eia.gov/electricity/data.php) and Historical State Data (eia.gov/electricity/data/state/); EIA Form 861M (monthly sales); Public Power Statistical Report (publicpower.org/system/files/documents/2025-Public-Power-Statistical-Report.pdf); EEI Industry Data (eei.org/resources-and-media/industry-data); FERC Electric Power Markets (ferc.gov/electric-power-markets).
* **EU**: Eurostat Electricity Sales (ec.europa.eu/eurostat/web/energy/data); ENTSO-E Consumption Data (entsoe.eu/data).
* **Asia (e.g., China, India)**: NEA China (nea.gov.cn); CEA India (cea.nic.in/reports); ASEAN Energy Database (aseanenergy.org).
* **Other**: World Bank (databank.worldbank.org); SEIA Solar Data (seia.org/research-resources/solar-industry-research-data) for renewables sales.
* **Tools**: Web searches for aggregate trends; browse PDFs (e.g., instructions: "Summarize sales volumes by utility in \[Region]").

**Uncertainties and Mitigations**: Seasonal variations (e.g., weather impacts)—use annual averages. Regional fragmentation (e.g., state vs. national)—aggregate via weighted sums. Pitfalls (e.g., excluding transmission sales)—include via FERC data; scenario-test ±10% variances.

## Evaluation Process

1. **Filter Qualifying Pairs**: From Step 2 output, select only those with ≥1 category.
2. **Parallel Data Gathering**: For each metric, assign subtasks; use tools concurrently.
3. **Integration and Analysis**: Compile into reports; flag incomplete pairs (>20% data gaps).
4. **Final Review**: Reconsider chain—verify one pair end-to-end from scratch.

This step ensures data-driven SSS insights, feeding into GHG Protocol recommendations.
