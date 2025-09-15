# Addressing Rate Class Variations in Utility Data

The Granular Registry's Standard Supply Service (SSS) module provides estimates of retired Renewable Energy Certificates (RECs) and supplier-specific emission factors (SSEFs) based on publicly available utility data. Utility rate classes (e.g., residential, commercial, industrial, or time-of-use tariffs) primarily influence billing structures, such as pricing tiers or demand charges. Below, we address common questions about how rate class variations are handled in our processes, ensuring alignment with GHG Protocol Scope 2 Guidance for market-based reporting.

## What are utility rate classes, and how do they affect SSS data in the Granular Registry?

Utility rate classes categorize customers based on usage patterns, load size, or sector (e.g., large commercial vs. small residential). These classes determine how bills are structured, including fixed fees, energy rates, and surcharges. In the context of SSS, the underlying energy mix—generation resources, REC retirements, and emission factors—is typically uniform across all default customers in a utility's service territory, as electricity is delivered from the same grid pool. Our module uses aggregate retail sales data (e.g., from EIA Form 861) to calculate pro-rata shares of SSS attributes, such as RPS-mandated renewables or zero-emission credits. Rate classes may introduce minor variations through non-bypassable charges (e.g., RPS fees), which can differ by class and subtly influence the implicit share of funded clean energy attributes.

## Does the Granular Registry differentiate SSEFs or REC allocations by rate class?

No, SSEFs are calculated at the supplier or utility level, reflecting the overall generation portfolio, contracted purchases, and REC deductions, as per GHG Protocol guidelines. This supplier-wide approach ensures consistency and avoids segmentation unless a rate class represents a distinct "differentiated product" (e.g., an opt-in green tariff with separate attributes). For standard default service, we apply uniform SSEFs and pro-rata REC allocations based on your total load relative to the utility's retail sales. This aligns with industry norms, where utilities like PG\&E or Dominion Energy publish a single SSEF for their default mix, applicable across classes.

## How are non-bypassable charges handled if they vary by rate class?

Non-bypassable charges—such as Renewable Portfolio Standard (RPS) fees, zero-emission credits (ZECs), or stranded-cost riders—are included in our SSS framework (Category 2) because they fund specific clean energy resources that customers cannot avoid. If these charges vary by rate class (e.g., higher for industrial users), it may imply a slightly adjusted pro-rata share of the underlying attributes (e.g., more RECs for classes paying higher fees). Our base estimates use aggregate utility data, but during onboarding or pilots, you can provide your specific rate class and bill details for refinements. We cross-reference public filings (e.g., state PUC dockets) to incorporate any variations, ensuring representativeness without overcomplicating calculations.

## What if my organization's rate class has unique attributes or exemptions?

If your rate class includes exemptions (e.g., from certain surcharges) or unique features (e.g., time-of-use pricing affecting attribute allocation), inform us during setup. The Granular Registry can customize estimates by incorporating your tariff specifics, such as from utility rate schedules or your energy bills. This ensures accurate pro-rata claims while maintaining compliance with GHG Protocol quality criteria like auditability. In rare cases where a rate class has a dedicated resource mix (e.g., municipal utilities with class-specific hydro allocations), we flag this in reports and recommend direct utility verification.

## How does addressing rate class variations impact my Scope 2 emissions reporting?

By using supplier-wide data with optional rate class adjustments, our outputs support defensible market-based Scope 2 claims, often resulting in lower SSEFs than residual mix factors when SSS includes embedded carbon-free energy. This can reduce your reported emissions and optimize REC purchases. For hourly or granular reporting, variations are minimal since attributes are time-stamped at the utility level. Always document any custom inputs in your GHG inventory to meet transparency requirements.

## Do auditors require rate class-specific data for SSS claims?

Auditors typically focus on the representativeness of your SSEF and REC claims under GHG Protocol criteria, verifying that the data reflects your default supply without double-counting. Since SSEFs are uniform, aggregate utility data suffices for most audits. If non-bypassable charges vary significantly by class, providing rate-specific details (as supported by our module) strengthens audit defensibility. Our upcoming attestations (e.g., SOC 2 and ISAE 3000/3410) will further assure auditors of our processes, allowing you to reference Granular Registry reports directly.
