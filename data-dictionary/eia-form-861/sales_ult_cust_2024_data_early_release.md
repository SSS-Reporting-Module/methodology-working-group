# Sales\_Ult\_Cust\_2024\_Data\_Early\_Release

## Data Dictionary for Sales\_Ult\_Cust\_2024\_Data\_Early\_Release.xlsx

This file is an early release of the U.S. Energy Information Administration (EIA) Form 861 data for calendar year 2024, focused on retail sales to ultimate customers. It provides detailed breakdowns of electricity revenues, sales (in megawatthours), and customer counts by utility, state, sector (residential, commercial, industrial, transportation), and service type (e.g., bundled vs. delivery-only). The data is segmented into sheets for U.S. states, territories, and decoupled utilities. Note that this is preliminary data—not fully edited—and should not be aggregated to state or national totals without caution, as per EIA guidelines. Adjustments (e.g., utility\_number 99999) are included to correct for imputation or double-counting issues.

**File Structure**

* **Format**: Microsoft Excel (.xlsx) with multiple sheets.
* **Key Notes**:
  * Data is observational (O) or imputed (I).
  * Revenues are in thousand dollars.
  * Sales are in megawatthours (MWh).
  * Customers are counts (e.g., number of accounts).
  * To calculate totals: Sum Parts A, B, C, D for revenues; sum Parts A, B, D for sales and customers (to avoid double-counting delivery-only scenarios).
  * Behind-the-meter ownership (e.g., third-party solar) customer counts are excluded from aggregates to prevent double-counting.
  * Current as of early release (August 2025); final data expected later in 2025.

**Sheets**

1. **States**:
   * Primary sheet for U.S. states (excluding territories).
   * Rows: One per utility-part-service combination (e.g., multiple rows per utility if they have bundled and delivery services).
   * Purpose: Breaks down retail electricity activity by sector and service type for SSS pro-rata calculations (e.g., allocating clean energy based on load share).
2. **Territories**:
   * Similar to "States" but for U.S. territories (e.g., PR, VI, AS).
   * Fewer rows; includes bundled data primarily.
   * Purpose: Extends coverage for SSS in non-contiguous areas, though SSS applicability may vary (e.g., public ownership in PR).
3. **Decoupled**:
   * Lists utilities with revenue decoupling mechanisms (where revenues are decoupled from sales volumes, often for energy efficiency or renewables integration).
   * Rows: One per utility-state-BA code combination.
   * Purpose: Identifies utilities where SSS interactions with policies (e.g., RPS compliance) might involve adjustments; useful for SSS clarifications on regulated cost recovery.

**Columns (Common Across Sheets, with Variations)**

* **Data Year**: Integer (e.g., 2024). The reporting year.
* **Utility Number**: Integer (e.g., 55 for City of Aberdeen - (MS); 99999 for adjustments). Unique EIA-assigned ID for the utility; use as primary key.
* **Utility Name**: String (e.g., "City of Aberdeen - (MS)"). Full name of the utility.
* **Part**: String (A, B, C, D). Segments data by service category:
  * A: Bundled (full service: generation + delivery).
  * B: Energy-only (competitive supply without delivery).
  * C: Delivery-only (transmission/distribution without energy supply).
  * D: Behind-the-meter or other special cases.
* **Service Type**: String (e.g., "Bundled", "Delivery"). Indicates the type of service provided.
* **Data Type**: String ("O" for Observed, "I" for Imputed). Flags if data is directly reported or estimated.
* **State**: String (2-letter code, e.g., "MS" for Mississippi; "PR" for Puerto Rico in Territories sheet).
* **Ownership**: String (e.g., "Municipal", "Investor Owned", "Cooperative", "State", "Behind the Meter"). Critical for SSS categorization (e.g., public ownership qualifies as SSS).
* **BA Code**: String (e.g., "TVA" for Tennessee Valley Authority). Balancing Authority code; useful for SSS deliverability boundaries.
* **Revenues (by Sector)**: Numeric (thousand dollars). Broken into:
  * Residential Revenues
  * Commercial Revenues
  * Industrial Revenues
  * Transportation Revenues
* **Sales (by Sector)**: Numeric (MWh). Broken into:
  * Residential Sales
  * Commercial Sales
  * Industrial Sales
  * Transportation Sales
* **Customers (by Sector)**: Integer (count). Broken into:
  * Residential Customers
  * Commercial Customers
  * Industrial Customers
  * Transportation Customers
* **TOTAL (Revenues/Sales/Customers)**: Numeric/Integer. Aggregates across sectors for the row.

For the "Decoupled" sheet (unique columns):

* **Residential/Commercial/Industrial/Transportation**: String ("Yes"/"No"). Indicates if decoupling applies to that sector.
* **Revenue Adjustment Method (by Sector)**: String (e.g., "Proceeding", "Automatic"). Method for adjusting revenues (e.g., via regulatory proceedings).

**Usage Notes for SSS**

* **Relevance to SSS**: This data supports proxy thresholds for SSS-CFE allocations (e.g., pro-rata share = customer load / total retail sales). Filter for non-zero sales/customers to identify active utility-state pairs. Ownership and BA Code help classify SSS categories (e.g., regulated cost recovery for investor-owned in monopoly areas).
* **Data Quality**: Imputed values (I) may need flagging in SSS calcs. Adjustments (utility\_number 99999) should be applied to raw sums.
* **Volume**: \~2,200 rows in "States"; smaller in others. Handle concatenations carefully.
