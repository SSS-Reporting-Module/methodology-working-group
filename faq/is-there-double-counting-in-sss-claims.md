# Is There Double Counting in SSS Claims?

This FAQ addresses common questions about how Standard Supply Service (SSS) claims are structured to prevent double-counting of carbon-free electricity (CFE) attributes in Scope 2 market-based accounting. It draws from the proposed GHG Protocol Scope 2 Guidance updates, which emphasize preventing "resource shuffling" and double counting while allowing optional, pro-rata claims tied to traceable financial relationships. The Granular Registry uses credible third-party data and allocation methodologies to enforce these principles, ensuring accurate and transparent reporting.

## What is double-counting in the context of SSS claims?

Double counting occurs when the same CFE attributes (e.g., from mandated renewables or regulated nuclear/hydro) are claimed by more than one entity in their market-based Scope 2 inventories, leading to overstated decarbonization efforts across reporters. In SSS, this could occur if unclaimed shares were reassigned to voluntary markets or if residuals allowed multiple parties to benefit from the same attributes implicitly. The GHG Protocol's proposed rules prevent this by capping claims at pro-rata shares, requiring EAC retirement or supplier attestations, and excluding unclaimed SSS from voluntary eligibility—ensuring exclusive ownership and alignment with principles like scientific integrity and impact.

## How does the Granular Registry prevent double-counting in SSS claims?

The Registry enforces prevention through a structured claim hierarchy and order of operations: (1) Preferred supplier allocation using actual generation/load data; (2) Third-party proxies (e.g., EEI or Ember datasets) when unavailable; and (3) EAC tracking/retirement to substantiate ownership. Claims are optional and limited to a customer's pro-rata share (e.g., based on load ratio and SSS CFE percentage). Unclaimed shares remain unallocated and ineligible for voluntary claims by others, avoiding shuffling. Residual mixes are adjusted dynamically: Explicit claimants use a residual with SSS removed (Type A, fossil-heavier), while opt-outs use one with embedded SSS (Type B, diluted benefit). This ensures no CFE attribute is double-claimed, though fossil emissions in residuals may be conservatively higher for some users. All data meets Scope 2 Quality Criteria, including no double claiming and exclusive retirement.

## Can unclaimed SSS shares be reassigned to other companies or used in voluntary markets?

No. Per the proposed Guidance, unclaimed SSS shares are not eligible for voluntary claims by others, as SSS is tied to the financial relationship of the original customers (e.g., non-bypassable charges or regulated recovery). This prevents "resource shuffling" of existing CFE to those pursuing climate targets without payment. Instead, unclaimed portions may linger in supplier-specific emission factors (SSEFs) or Type B residuals for non-claimants, providing indirect, diluted credit—but never exclusive or additive claims. Suppose SSS CFE exceeds its load in any period (e.g., due to excess hydro exports). In that case, it may support voluntary markets only if the Scope 2 criteria are met and the allocation is not already in place.

## How does the example of Companies A, B, and C illustrate no double-counting?

Consider three companies, each with 10,000 MWh load in a market where SSS provides 25% CFE (e.g., from RPS compliance or regulated hydro). The full pro-rata allocation across them is 7,500 MWh (2,500 MWh each). However, due to optional claiming:

* **Company A** explicitly claims its 2,500 MWh SSS CFE, layers voluntary procurement on top, and applies a Type A residual mix (SSS-removed, e.g., fossil-only at 0.5 kg CO₂/MWh) to the remainder. This gives full credit for SSS without dilution.
* **Company B opts out of explicit SSS, claiming to to procure 80% voluntary CFE (8,000 MWh), and applies a Type B residual (with embedded SSS) to the 20% remainder (2,000 MWh).** This yields only \~5% effective SSS credit (500 MWh total CFE in that slice), less than its full share.
* **Company C** claims no voluntary but uses an SSEF including SSS, crediting 2,500 MWh CFE.

Total SSS claimed/used: 5,500 MWh—under the full 7,500 MWh allocation. The 2,000 MWh gap isn't reassigned; it prevents over-claiming. Residuals for A (Type A) are fossil-heavier (e.g., 3,750 tCO₂ remainder emissions assuming no voluntary and 0.5 kg/MWh). At the same time, B's Type B is lower (e.g., 800 tCO₂ at 0.4 kg/MWh)—but no CFE is double-counted, as attributes remain exclusive or unclaimed.

## What role do residual mixes play in preventing double-counting?

Residual mixes represent unclaimed grid electricity after allocations. In the Registry, we compute two types:

* **Type A (SSS-removed)**: Used post-explicit SSS claim; subtracts SSS CFE to create a fossil-only or higher-emission factor, ensuring claimants get exclusive credit without others benefiting.
* **Type B (SSS-included)**: For opt-outs; retains unclaimed SSS, providing indirect benefit but capped to avoid explicit double claims.

This aligns with the Guidance's order: SSS first, then voluntary, then residual. No CFE is double-claimed, as Type A excludes it entirely for non-claimants.

## Does hourly accounting change how double-counting is prevented in SSS?

SSS rules remain consistent for annual or hourly methods. In hourly scenarios, pro-rata shares use temporal profiles (e.g., PG\&E-style spreadsheets for load/generation matching). Unclaimed hourly SSS isn't reassigned, preventing shuffling. The Registry supports this via optional hourly proxies (e.g., subtracting SSS CFE hour-by-hour from residuals). While annual under-claiming is conservative, hourly mismatches (e.g., SSS hydro in off-peak hours) could amplify gaps—but caps and retirement ensure that no double CFE attribution occurs.

## What if data is unavailable or inaccurate—could that lead to double-counting?

The Registry mitigates this by implementing a data-quality hierarchy: supplier-attested data is prioritized first, followed by regulatory filings (e.g., RPS reports), certificate tracking, and bottom-up mixes. Flagged data-scarce regions default to grid-average EFs with high uncertainty notes. Users must document sources; audits via EAC retirement prevent errors. If inaccuracies arise (e.g., overestimating SSS%), the pro-rata cap limits exposure; however, we recommend third-party verification for compliance purposes.

For more details, refer to the Granular Registry Methodology Document or contact support for custom scenarios. This FAQ is based on the proposed GHG Protocol updates as of September 16, 2025; please verify against the final standards.
