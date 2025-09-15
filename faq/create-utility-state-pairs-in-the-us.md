# Create Utility-State pairs in the US

## Overview and Purpose

The EIA Form 861 collects annual data on electric power industry participants, including utilities' operations, sales, and characteristics. We use it to create unique utility-state pairs by focusing on active service areas—defined as states where a utility reports positive retail sales (MWh) or customers. This avoids including inactive or headquarters-only states, aligning with SSS requirements for traceable financial relationships (e.g., regulated cost recovery tied to load-serving).

Pairs are generated at the utility\_number + state level, prioritized by sales volume for SSS calcs (e.g., filtering for investor-owned or municipal with RPS mandates). For multi-state utilities like Duke Energy, this yields separate pairs (e.g., Duke-NC, Duke-SC) to account for state-specific RPS/CES.

## Inputs

* **Primary Files**: Two Excel files from the EIA Form 861 dataset:
  * Utility\_Data\_\[YEAR]\_Data\_Early\_Release.xlsx: Provides utility characteristics (e.g., name, ownership type, NERC region) but lists only a primary state per utility.
  * Sales\_Ult\_Cust\_\[YEAR]\_Data\_Early\_Release.xlsx: Breaks down retail sales (MWh), revenues, and customers by state, sector (residential, commercial, industrial, transportation), and service type (bundled, energy-only, delivery-only). This is the key file for identifying multi-state operations via non-zero sales.
* **Temporal Scope**: Use the most recent early release (e.g., for calendar year 2024 data, released August 2025). Final edited data follows later, but isn't required for our preliminary pairs.
* **Additional Context**: EIA's data dictionary (embedded in files or via their site) for column mappings; we filter for US states/territories, excluding withheld utilities (ID 88888) or adjustments (ID 99999).

## Public Data URLs

All data is publicly available from the U.S. Energy Information Administration (EIA). The primary download page is:

* [https://www.eia.gov/electricity/data/eia861/](https://www.eia.gov/electricity/data/eia861/) – Download the ZIP archive (e.g., f8612024er.zip for 2024 early release), which contains the two Excel files.

For monthly updates or related data (e.g., Form 861M for interim sales):

* [https://www.eia.gov/electricity/data/eia861m/](https://www.eia.gov/electricity/data/eia861m/) – But we prioritize annual for comprehensive pairs.

Historical or revised data (e.g., corrections):

* [https://www.eia.gov/electricity/data/eia861/correction.html](https://www.eia.gov/electricity/data/eia861/correction.html)

Third-party archives (for reference, not primary use):

* Catalyst Cooperative PUDL (processed EIA data): [https://catalystcoop-pudl.readthedocs.io/en/stable/data\_sources/eia861.html](https://catalystcoop-pudl.readthedocs.io/en/stable/data_sources/eia861.html)

We download fresh each year to ensure currency, archiving with timestamps for audits.

## Step-by-Step Process to Create the List

We process the data in code (e.g., Python with pandas) or manually in Excel for validation. Here's the reproducible method:

1. **Download and Extract Data**:
   * Access the ZIP from the EIA URL above.
   * Extract the two XLSX files. Note EIA's disclaimer: Early releases are unedited; do not aggregate to totals without caution.
2. **Prepare Utility Characteristics (from Utility\_Data File)**:
   * Load the 'States' and 'Territories' sheets (skip first 2-3 rows for headers/notes).
   * Key columns: Utility Number (ID), Utility Name, State (primary), Ownership Type (e.g., Investor Owned, Municipal).
   * This file gives \~3,300 utilities but only one state per row—use for joining names/ownership later.
3. **Identify Active States (from Sales\_Ult\_Cust File)**:
   * Load the 'States' and 'Territories' sheets (skip 3-4 rows for headers/notes).
   * Key columns: Utility Number, Utility Name, State, Ownership, TOTAL Sales (Megawatthours), TOTAL Customers.
   * Filter rows where TOTAL Sales > 0 or TOTAL Customers > 0 (to confirm active retail service).
   * Aggregate across Parts (A: Bundled, B: Energy-only, C: Delivery-only, D: Other)—sum A+B+D for sales/customers per EIA notes to avoid double-counting delivery.
   * Drop adjustments (Utility Number 99999) and withheld (88888).
4. **Generate Unique Pairs**:
   * Group by Utility Number + State.
   * Deduplicate to create pairs (e.g., \~4,000 total US pairs, including territories).
   * Join with Utility\_Data for enriched details (name, ownership, NERC region).
   * Prioritize: Sort by total\_sales descending for SSS focus (e.g., top IOUs like PG\&E-CA with high RPS load).
5. **Validation and Outputs**:
   * Cross-check: Pairs should match known multi-state ops (e.g., AEP in OH, TX).
   * Export: CSV or SQL table (e.g., utility\_state\_pairs with columns: utility\_number, state, utility\_name, ownership, total\_sales\_mwh).
   * Usage in SSS: Pairs feed pro-rata calcs (customer\_load / total\_sales\_mwh per state); filter for CA to isolate PG\&E-CA.

This yields a clean list for our registry—e.g., PG\&E-CA with \~33 TWh sales in 2023. For audits, we archive raw files and code; refresh annually post-EIA release.
