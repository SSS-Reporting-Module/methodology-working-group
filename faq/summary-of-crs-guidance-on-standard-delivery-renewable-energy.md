# Summary of CRS Guidance on Standard Delivery Renewable Energy

This CRS framework provides a robust foundation for credibly accounting for non-actively procured renewable energy attributes in default electricity service, aligning with GHG Protocol Scope 2 market-based principles and RE100 criteria. The Granular Registry incorporates this guidance by using it to inform our proxy estimation of retired Renewable Energy Certificates (RECs) and Supplier-Specific Emission Factors (SSEFs) from public data sources when direct supplier allocations are unavailable. Below is a concise summary tailored to our registry's SSS module, highlighting key principles, evaluation frameworks, and integration points.

## **1. Core Concepts and Claim Eligibility**

* **Definition and Scope:** Standard Delivery Renewable Energy refers to renewable attributes (e.g., RECs) delivered by default to all customers via load-serving entities (LSEs), often for RPS compliance or mandates. Claims are valid if attributes are retained/retired on behalf of the customer/group and meet credible usage requirements (e.g., traceability, no double-counting).
* **Distinction from Active Procurement:** Unlike voluntary purchases, SSS attributes are retired collectively (not individually), but consumers can still claim pro-rata shares if substantiated.
* **Registry Integration:** In our methodology, this underpins proxy bundles (retired REC volumes + SSEFs) for SSS customers. We apply it per energy-market region (e.g., U.S. state/ISO, EU Member State) to ensure claims reflect delivered electricity, not just generation.

## **2. Data Challenges and Sources**

* **Key Issues:** Data is often inconsistent, lacking transparency, or insufficiently granular (e.g., annual vs. hourly). U.S. sources include supplier-specific mixes, RPS compliance reports, residual mixes, and grid-average factors; variability arises in format, resource inclusion, methodologies, verification, and scope.
* **Registry Adaptation:** When LSEs do not submit data, we use public inventories (e.g., EIA Form 861 for retail sales, state RPS reports for REC retirements, EEI for SSEFs) to estimate SSS attributes. This mirrors CRS by prioritizing regulatory filings and tracking-system data, with fallbacks to bottom-up calculations.

## **3. Credibility Criteria for Data Evaluation**

* **Minimum Requirements (Must Meet All):**
  * Describes delivered electricity.
  * Accurate generation information.
  * Aggregates all ownable attributes.
  * Exclusive ownership/retirement (no double-counting/claiming).
  * Same market and timeframe as consumption (e.g., U.S./Canada as a single market; 21-month vintage window common).
* **Registry Incorporation:** These criteria are embedded in our QA/QC process (Step 9 of the methodology). We flag non-compliant sources and default to grid-average EFs for data-scarce regions, ensuring proxy bundles satisfy Scope 2 Quality Criteria.

## **4. Quality Considerations for Source Selection**

* **Additional Factors to Weigh:**
  * Oversight (e.g., third-party verification).
  * Methodology transparency.
  * Scope/specificity (e.g., LSE-level vs. regional; temporal granularity).
  * Included resources/environmental quality (e.g., varying renewable definitions; emissions from biomass as zero).
  * Publication frequency/age.
  * Consistency across sources.
* **Registry Use:** Applied in our data-quality hierarchy (Section 4), prioritizing supplier-attested data, then compliance filings, residual mixes, and plant-level reconstructions. This helps evaluate trade-offs like accuracy vs. feasibility, reducing reputational risks for registry users.

## **5. Reporting, Integration, and Calculations**

* **Summing with Active Procurement:** SSS and actively procured renewables are equivalent if credible; aggregate by assigning percentages to consumed MWh, disaggregating mixed products.
* **Pro-Rata Allocation:** Claimable RECs = (SSS REC MWh / Retail Sales MWh) × Customer Load.
* **SSEF Construction:** Preferred: Use published factors; Fallback: Bottom-up (owned/contracted mix minus retired RECs, multiplied by fuel-specific CO₂ intensities).
* **Registry Alignment:** Directly adopted in Steps 5-7 of our workflow for annual proxies, with optional hourly extensions (Step 8) using residual mix factors where available (e.g., GB/Nordics). Ensures no double-counting between compliance/voluntary markets.
