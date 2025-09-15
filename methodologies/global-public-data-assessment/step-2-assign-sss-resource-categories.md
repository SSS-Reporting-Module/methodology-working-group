# Step 2: Assign SSS Resource Categories

## Criteria for Evaluating Supplier-Region Pairs for SSS Resource Categories

This document provides detailed, actionable criteria for analysts to assess whether unique supplier-region pairs (from the provided spreadsheet of utilities and suppliers by country or state) qualify for one or more of the three SSS (Supplier-Specific Scope 2) resource categories: Regulated Cost Recovery, Non-Bypassable Charges, and Customer Funding. These categories are derived from GHG Protocol Scope 2 guidance discussions (e.g., Technical Working Group proposals as of March 2025), where SSS refers to "Standard Supply Service" electricity supplied under specific funding mechanisms that tie emissions allocation to supplier-specific data.

Analysts should evaluate each supplier-region pair independently, using publicly available sources such as regulatory filings, utility reports, government databases, and legal statutes. For each category, apply a yes/no qualification based on evidence, documenting sources and any uncertainties (e.g., pending regulatory changes). If a pair qualifies for multiple categories, note overlaps. Re-evaluate annually or upon major policy shifts (e.g., post-2025 Scope 2 updates).

Key principles:

* **Focus on Public Data**: Prioritize verifiable, non-proprietary sources like utility commission websites, IEA/IRENA reports, and national energy agencies.
* **Regional Specificity**: Criteria vary by jurisdiction (e.g., U.S. states vs. EU countries); cross-check against local laws.
* **Expiration Checks**: Funding may cease if customers switch suppliers/products or legislative support expires—include a "durability" assessment.
* **Documentation**: For each pair, record evidence in a standardized template (e.g., Supplier: \[Name], Region: \[State/Country], Category: \[Yes/No], Sources: \[List], Notes: \[Uncertainties]).
* **Threshold for Qualification**: Qualification requires at least 50% of the supplier's resources in the region to meet the category's criteria, based on generation mix data (e.g., from EIA Form 860 for U.S.).

## 1. Regulated Cost Recovery

**Definition**: Resources funded by a monopoly supplier or for facilities tied to an external decision-making process, such as an Integrated Resource Plan (IRP), government entity oversight, or similar regulated mechanisms. This category applies where costs are recovered through rates approved by a regulatory body, ensuring supplier-specific allocation of emissions.

**Detailed Criteria**:

* **Monopoly Supplier Status**: Confirm if the supplier operates as a regulated monopoly in the region (e.g., no retail competition or limited choice). Indicators include: exclusive service territories, rate-of-return regulation, or vertically integrated structure.
  * **Verification Steps**: Review utility commission (e.g., U.S. PUC/FERC) filings for franchise agreements or monopoly designations. Check if the supplier is an Investor-Owned Utility (IOU) with regulated rates.
  * **Examples**: U.S. examples like Duke Energy in North Carolina (monopoly via IRP); EU examples like state-owned utilities in France (EDF under regulated tariffs).
* **Tied to External Decision-Making**: Evidence that resource procurement/acquisition is governed by an external process, such as IRP filings, government approvals, or public utility commissions.
  * **Verification Steps**: Search for IRP documents (e.g., on state energy office sites) showing supplier's facilities (e.g., power plants) approved via public processes. Confirm involvement of government entities (e.g., via EIA data or national registries).
  * **Examples**: Facilities approved in California's IRP process; nuclear plants under U.K. government oversight.
* **Cost Recovery Mechanism**: Costs (e.g., for generation, transmission) are passed to customers via regulated rates, not market-based contracts.
  * **Verification Steps**: Analyze tariff sheets or rate cases (e.g., FERC Form 1) for cost passthrough clauses. Quantify recovery (e.g., >80% of costs recovered via rates).
* **Durability Check**: Assess if qualification persists if customers switch (e.g., in deregulated markets, recovery may shift to non-bypassable if mandated).
  * **Red Flags**: Deregulated markets (e.g., Texas ERCOT) where competition exists; private PPAs bypassing regulation.
* **Data Sources**: U.S. EIA (eGRID, Form 861); EU ENTSO-E; national regulators (e.g., Ofgem U.K., CPUC California). Use tools like web searches for "\[Supplier] IRP \[Region] 2025".

## 2. Non-Bypassable Charges

**Definition**: Charges required by legislation or regulation, appearing in utility bills or supplier contracts, such as: (1) To comply with Renewable Portfolio Standards (RPS) or Clean Energy Standards (CES); (2) To extend the economic lives of nuclear generation assets. These are fees on every kWh consumed, non-avoidable even if switching suppliers.

**Detailed Criteria**:

* **Legislative/Regulatory Mandate**: Charges must be statutorily required, not voluntary (e.g., embedded in energy laws or utility codes).
  * **Verification Steps**: Review state/federal laws (e.g., U.S. state RPS statutes via DSIRE database; EU directives like RED III). Confirm charges are non-optional via bill breakdowns.
  * **Examples**: California's DWR Bond Charge for energy crisis recovery; U.K. Nuclear RAB Levy for new nuclear funding.
* **RPS/CES Compliance**: Charges fund RPS/CES targets (e.g., minimum renewable/clean energy shares).
  * **Verification Steps**: Check RPS/CES status (e.g., EIA summaries for U.S. states; IRENA for global). Quantify if >20% of supplier's mix is RPS/CES-funded (e.g., via REC tracking systems like M-RETS).
  * **Examples**: New York's CES funding nuclear via ZECs; 28 U.S. states with RPS as of 2025.
* **Nuclear Life Extension**: Charges specifically for maintaining/extending nuclear assets (e.g., decommissioning or operational subsidies).
  * **Verification Steps**: Search for nuclear-specific fees (e.g., NRC regulations, 10 CFR 50.2 for decommissioning). Confirm via utility reports (e.g., non-bypassable nuclear decommissioning fees in California for SONGS/Diablo Canyon).
  * **Examples**: Illinois ZES preserving nuclear plants; global IMF estimates of nuclear subsidies.
* **Appearance in Bills/Contracts**: Charges must be itemized (e.g., as $/kWh surcharges) and non-bypassable (apply regardless of supplier switch).
  * **Verification Steps**: Sample utility bills or tariffs (e.g., from supplier websites). Calculate proportion (e.g., >5% of bill as non-bypassable).
* **Durability Check**: Confirm charges persist post-switch (e.g., via escape clauses in RPS laws) but expire if legislation ends (e.g., bond payoffs).
  * **Red Flags**: Voluntary programs; regions without RPS/CES (e.g., some Southeast U.S. states); bypassable via self-generation.
* **Data Sources**: DSIRE (rpsdata.org); U.S. EIA RPS/CES maps; IEA subsidy databases; utility filings (e.g., "\[Supplier] non-bypassable charges \[Region]").

## 3. Customer Funding

**Definition**: Such as taxes or subsidies for majority government-owned resources in a region used to serve the load in that region. This includes public funding mechanisms that support resources directly benefiting regional consumers.

**Detailed Criteria**:

* **Government Ownership**: Resources must be majority (>50%) government-owned (e.g., state/federal utilities or assets).
  * **Verification Steps**: Check ownership via annual reports or databases (e.g., EIA Form 860 for U.S.; ENTSO-E for EU). Confirm public entity control (e.g., TVA in U.S. Southeast).
  * **Examples**: China's state-owned grids; Brazil's Eletrobras assets.
* **Taxes/Subsidies Mechanism**: Funding via taxes (e.g., surcharges) or subsidies (e.g., grants, tax credits) targeted at regional load-serving resources.
  * **Verification Steps**: Review tax codes (e.g., IRS for U.S. credits like PTC/ITC; IMF subsidy reports). Quantify subsidies (e.g., >10% of resource costs subsidized per IEA data).
  * **Examples**: U.S. Inflation Reduction Act subsidies for renewables; EU state aid for government-owned nuclear.
* **Regional Load Service**: Resources must primarily serve the region's load (e.g., >70% of output consumed locally, not exported).
  * **Verification Steps**: Analyze generation vs. consumption data (e.g., EIA state profiles; IEA World Energy Balances). Confirm via utility integrated plans.
  * **Examples**: Subsidized hydro in India serving state grids; tax-funded wind in Texas.
* **Public Funding Tie**: Evidence that customer rates include embedded taxes/subsidies (e.g., via bill surcharges or reduced rates from grants).
  * **Verification Steps**: Cross-check with DOE/EIA subsidy estimates (e.g., $4.6B U.S. fossil subsidies in 2022). Include R\&D grants if tied to operations.
* **Durability Check**: Assess if funding expires (e.g., IRA credits phase out post-2032) or if customer switches negate benefits (e.g., opt-out provisions).
  * **Red Flags**: Privately owned resources; export-focused (e.g., Canadian hydro to U.S.); non-targeted subsidies (e.g., general R\&D not resource-specific).
* **Data Sources**: IMF/IEA subsidy trackers; U.S. EIA subsidy reports; national tax authorities (e.g., "\[Region] energy subsidies 2025").

## Evaluation Process

1. **Iterate Over Pairs**: For each unique supplier-region (e.g., Excel pivot for uniqueness), apply criteria sequentially.
2. **Scoring**: Use a checklist (e.g., 4/5 indicators met = Qualifies). Flag uncertainties (e.g., pending EU CSRD rules).
3. **Cross-Verification**: For high-stakes pairs, consult multiple sources (e.g., web search + PDF browse of regulations).
4. **Output**: Compile into a report/table, e.g.:

| Supplier        | Region     | Regulated Cost Recovery | Non-Bypassable Charges | Customer Funding | Notes                            |
| --------------- | ---------- | ----------------------- | ---------------------- | ---------------- | -------------------------------- |
| Example Utility | California | Yes                     | Yes                    | No               | RPS-mandated; check 2026 updates |

This ensures robust, defensible assessments aligned with GHG Protocol Scope 2 revisions.
