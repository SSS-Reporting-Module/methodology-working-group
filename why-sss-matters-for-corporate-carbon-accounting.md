# Why SSS Matters for Corporate Carbon Accounting

For corporations pursuing accurate Scope 2 emissions reporting under the GHG Protocol, SSS plays a critical role in market-based accounting, serving as the default baseline for uncontracted electricity loads. It enables companies to claim embedded clean energy attributes (e.g., mandated renewables or nuclear) without additional procurement, but its limitations—especially under emerging hourly matching rules—highlight the need for granular data and potential supplementation via platforms like the Granular Registry and Marketplace.

## In dual-reporting Scope 2 frameworks:

* **Location-Based Accounting**: SSS is irrelevant here, as emissions are calculated using regional grid-average factors (e.g., eGRID subregions in the U.S.). This method reflects the physical grid's carbon intensity, unaffected by supplier choices.
* **Market-Based Accounting**: SSS excels by allowing the use of supplier-specific emission factors (SSEFs) that incorporate retired attributes, often resulting in lower reported emissions compared to grid averages. For example, if your utility retires RECs to achieve 30% RPS compliance, you can claim that share as zero-emission, thereby reducing your SSEF (e.g., from 0.4 kg CO₂/kWh to 0.32 kg CO₂/kWh). Pro-rata allocation is straightforward: Claimable REC MWh = (Total SSS REC MWh / Utility Retail Sales MWh) × Your Load MWh.

## Why it matters strategically:

* **Credible Claims Without Extra Cost**: SSS credits mandatory clean energy (e.g., RPS RECs, ZECs for nuclear) backed by retired certificates, meeting GHG Protocol quality criteria. This avoids double-counting and supports auditable reports, as seen in utilities like PG\&E (96% GHG-free in 2022 due to RPS, nuclear, and hydro).
* **Fallback to Residual Mix**: If no SSEF is available, use residual factors (e.g., AIB in Europe, Green-e in the U.S.), which strip out claimed renewables, potentially increasing your emissions if clean attributes are sold elsewhere. This ensures market integrity but underscores SSS's variability.
* **Hourly Matching Challenges**: Under draft GHG Protocol updates requiring Granular Certificates (GCs) for time-matched claims, SSS's annual averages fall short—e.g., solar attributes can't offset nighttime fossil use. Without hourly data, default to hourly residual mixes, potentially aligning market-based emissions more closely with location-based ones. To bridge gaps, procure time-stamped GCs via the Granular Marketplace.
* **Risks and Opportunities**: Over-reliance on SSS may limit ambitious goals (e.g., 100% renewable claims), as it lacks additionality and temporal precision. However, it provides a defendable baseline; enhance it by estimating retired RECs using public sources (e.g., EIA Form 861, RPS reports) when utilities don't submit data to the Granular Registry.

## Summary

SSS simplifies baseline accounting but demands rigorous documentation to substantiate claims. For Clean Incentive clients, integrating SSS data into the Registry ensures transparency, while Marketplace tools enable upgrades to hourly-matched procurement for deeper decarbonization.

## How our platform helps

* **Easy, audit-ready reports**: Centralized SSEFs, RPS retirements, utility attestations, and calculation logs—exportable in minutes.
* **Save your team time**: We automate data collection (EIA 861, utility plans, attestations) and calculations, cutting manual effort and back-and-forth with auditors.
* **Cheaper path to zero market-based Scope 2**: By crediting SSS CFE and optionally issuing EACs for SSS attributes, you purchase fewer unbundled RECs to reach 0 tCO₂e.

## Case study: Data center in CPS Energy territory (San Antonio, TX)

### Overview

A hypothetical operator consumes 100,000 MWh/year. 40,000 MWh comes from a bundled wind PPA with RECs (zero-emission claims). The remaining 60,000 MWh is from CPS Energy Standard Supply Service (SSS), a regulated mix that is \~46% GHG-free (≈comprising \~28% nuclear and \~ ≈18% renewables), with the balance consisting of natural gas and coal. Using public data, a supplier-specific emissions factor (SSEF) of \~0.27 tCO₂e/MWh[^1] is defensible for SSS, lower than ERCOT’s residual mix (\~0.48 tCO₂e/MWh). CPS’s RPS compliance and nuclear allocation avoid double-counting for SSS customers under the current Scope 2 rules.

Our platform supports three phases to improve claims quality and reduce REC needs progressively.

### Phase one: Calculate SSEF from Public Sources

* **Improved SSEF**: Use a documented SSEF with public sources (e.g., EIA 861, CPS plans) for pro‑rata CFE credit.

### Phase two: Utility‑verified reporting

* Secure CPS attestations on REC retirements and nuclear allocation to SSS, achieving audit‑level rigor with the same emissions math.

### Phase three: Tradable certificates for SSS CFE

* Use our Granular Registry to issue EACs for the SSS clean share (nuclear/RPS). Claim zero for that share and treat the residual fossil separately. This reduces the unbundled RECs needed to reach zero market‑based Scope 2.

### Comparison across phases (SSS portion = 60,000 MWh)

| Scenario                                                      | Description                                                                         | Emissions Factor for SSS Portion (tCO₂e/MWh) | Emitting Portion (MWh) | Unbundled RECs Needed for 0 Scope 2 (MWh) | Total Scope 2 Emissions Without RECs (tCO₂e) |
| ------------------------------------------------------------- | ----------------------------------------------------------------------------------- | -------------------------------------------- | ---------------------- | ----------------------------------------- | -------------------------------------------- |
| **No SSS Reporting** (Status Quo)                             | Use residual mix for full SSS; no CFE credits.                                      | 0.48                                         | 60,000                 | 60,000                                    | 28,800                                       |
| <p><strong>SSS Reporting Only</strong> </p><p>(Phase One)</p> | Use SSEF crediting blended CFE; cannot split for partial zero.                      | 0.27                                         | 60,000                 | 60,000                                    | 16,200                                       |
| **Utility Verified Reporting** (Phase Two)                    | CPS-verified SSEF with attestation; audit-rigor enhances credibility but same math. | 0.27                                         | 60,000                 | 60,000                                    | 16,200                                       |
| **Tradable GCs for All SSS Resources** (Phase Three)          | Nuclear/RPS as EACs (zero for \~27,600 MWh); residual fossil at higher EF.          | 0.50 (residual after EACs)                   | 32,400                 | 32,400                                    | 16,200                                       |

### What this means for you

* **Immediate reduction in reported emissions**: Moving from residual mix to SSEF reduces the SSS portion by \~43% (28,800 → 16,200 tCO₂e without RECs).
* **Fewer RECs to buy**: With SSS EACs (Phase Three), only \~32,400 unbundled RECs are needed vs 60,000—a \~46% reduction.
* **Lower cost to 0 market-based Scope 2**: At $4/MWh RECs, savings are roughly \~$110k per 60,000 MWh SSS load; larger fleets scale proportionally.
* **Faster, cleaner audits**: Our exports include sources, attestations, calculation lineage, and versioned SSEFs for audit trails.

### Get started

* Share your load data; we’ll generate a CPS‑specific SSEF with documentation in hours, not weeks.
* Optionally engage CPS for verification via our standardized attestation workflow.
* When ready, enable issuance of SSS EACs in our Granular Registry to minimize residual REC purchases.
* Questions? Email info@granular-registry.com.

[^1]: Emissions factors shown (e.g., \~0.27 and \~0.48 tCO₂e/MWh; 0.50 residual after SSS EACs) are illustrative estimates based on public sources and standard calculations for the stated period. Actual values vary by year, data source, methodology, and verification status.
