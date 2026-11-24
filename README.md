```markdown
# SpreadZero — Fair Price Intelligence and Direct Procurement Network

## Submission Metadata
* **Date:** 24/11/2026
* **Reference Number:** 26006890
* **Name:** Mohamed Fatheen
* **Problem Title:** SIH 26033: Multiple intermediaries reduce farmers earnings and increase consumer prices
* **Problem Creator's Organization:** Ministry of Consumer Affairs, Food & Public Distribution
* **Theme:** Agriculture, FoodTech & Rural Development

---

## Proposed Solution

### Detailed Explanation of the Proposed Solution
**SpreadZero — Fair Price Intelligence and Direct Procurement Network** is built for **SIH 26033** (*Ministry of Consumer Affairs, Food & Public Distribution*). Rather than operating as just another generic e-commerce catalog or one-way delivery tool, SpreadZero acts as a **consumer-affairs price-spread intelligence and direct procurement network** that connects farms/clusters directly with **institutional buyers** in Phase 1 (hostels, canteens, hotels, restaurants, and food processors) and **consumer collectives** in Phase 2, while optimizing for **Farmer Realization Ratio (FRR)** and **grade-normalized, district-adjusted price spreads**.

We track **Farmer Realization Ratio (FRR)** explicitly as:

```text
FRR (%) = (Net Farmer Earnings ÷ Final Buyer Price) × 100

```

For example, if a farmer nets ₹28/kg and the institutional buyer pays ₹40/kg, the calculation is:

```text
FRR = (28 ÷ 40) × 100 = 70%

```

We are not eliminating every intermediary—we are eliminating **non-value-adding intermediary layers** while digitally preserving essential functions like aggregation, quality assurance, working capital access, and demand matching. Where an FPO lacks capacity or digital readiness, **Certified Collection Partners** act as fallback collection and grading operators—defined as verified logistics, aggregation, or rural procurement entities approved through platform compliance checks, service-level requirements, and periodic audit reviews. For institutional buyers who already have vendors, SpreadZero provides **shortage prediction**, **alternate sourcing recommendations**, and **supplier reliability scoring**, while supporting **T+0 / milestone settlements** via partner banks, NBFCs, or invoice-discounting rails.

### How It Addresses the Problem

Multi-layered trading chains add commissions, handling losses, and opaque markups between farmgate and final buyer while leaving smallholders exposed to distress sales when they need fast cash or perishable lots risk spoilage.

SpreadZero addresses this through active intervention rather than passive reporting:

* **Actionable Spread & FRR Intervention:** When **FRR** drops below a configurable threshold or spread widens beyond normal benchmarks, SpreadZero recommends alternative buyer corridors, pooled dispatch options, and benchmark-aligned procurement targets.
* **Resilient Sourcing & Fallback Aggregation:** Combines FPOs and **Certified Collection Partners** for lot aggregation, pairs **photo-verified grading + dispute resolution** with **short-hold/cool-buffer slots**, and supports **T+0 / milestone payouts** via partner financial rails.
* **Practical Freight & Backhaul:** Consolidates cluster runs to cut per-kg shipping overhead and uses **backhaul return-leg matching** as a secondary cost reducer on compatible round trips.

### Innovation and Uniqueness of the Solution

The platform's primary optimisation objective is maximizing Farmer Realization Ratio while maintaining procurement reliability, delivery performance, and supply continuity for buyers.

* **Explainable Fair-Spread Recommendation Engine:** Moves beyond static reporting by recommending buyer corridors, lot pools, and dispatch plans that improve **FRR** and keep spreads within fair bands—with clear explanations showing expected farmer realization gain, estimated transport savings, buyer reliability score, and benchmark comparison so recommendations are never a black box.
* **Grade-Normalized, District-Adjusted Benchmarking:** Adjusts price-spread checks for crop grade, district supply/demand conditions, and freshness/perishability so normal regional or grade variations do not trigger false anomaly alerts.
* **Fallback Collection + T+0 Liquidity Rails:** Prevents FPO bottlenecks via **Certified Collection Partners**, resolves quality disputes with pre-dispatch and delivery-time photo/weight logs, and pairs **T+0 / milestone settlements** with partner bank/NBFC/invoice-financing support instead of locking platform cash in manual escrow.

---

## Technical Approach

### Technologies to Be Used

* **Web & Mobile Clients:** Next.js / React web console for FPOs, **Certified Collection Partners**, institutional buyers, price-spread monitors, and ops teams; Flutter / React Native mobile app with low-bandwidth mode, vernacular UI, and SMS/WhatsApp alerts.
* **Backend & Core Services:** Python (FastAPI) services for pooling, **FRR** and spread calculation, explainable recommendations, quality/dispute logs, and dispatch scheduling; PostgreSQL + PostGIS for relational data, district/corridor geospatial queries, and reliability scores; Redis for caching normalized benchmarks and dispatch locks.
* **AI & Optimization Engines:**
* *Explainable Fair-Spread & Shortage Recommender:* Tabular/time-series models (e.g., LightGBM + statistical baselines) using historical orders, grade/district price series, and supply signals to flag real spread anomalies, predict supply shortages, rank buyer corridors/alternate sources by **FRR** and reliability, and output human-readable reason factors.
* *Pooled Routing & Secondary Backhaul Solver:* Constrained routing/matching engine (e.g., Google OR-Tools) handling capacity, delivery windows, perishability urgency, cargo compatibility, and return-leg backhaul pairing.


* **Payments, Maps & Messaging:** UPI / payment gateway / partner bank or NBFC settlement and invoice-discounting hooks, OpenStreetMap / routing APIs for distance and ETA, and SMS/WhatsApp alerts.
* **Infrastructure & Security:** Dockerized services, cloud deployment, JWT + RBAC authentication, and append-only audit logs for pricing, grading, recommendations, and settlement events.

### Methodology and Process for Implementation

1. **Core Procurement, Fallback Aggregation & Spread Ledger:** Build FPO and **Certified Collection Partner** onboarding, photo-verified grading/dispute workflows, **FRR** tracking with explainable corridor/pool recommendations, and partner liquidity/settlement hooks.
2. **Normalized Benchmark & Shortage Signals:** Ingest order history, reliability metrics, and public mandi/price reference data with **grade-normalized, district-adjusted** rules to surface spread alerts, shortage warnings, and alternate sourcing options with clear reason codes.
3. **Pooled & Backhaul Dispatch Engine:** Group cluster lots into multi-stop institutional routes within time windows and attach compatible backhaul return loads where schedule and cargo compatibility allow.
4. **Minimum Viable Pilot & Simulation Prototype:** Run a focused Phase 1 pilot across **2 FPOs**, **1 district**, **3 institutional buyers**, **5–10 commodities**, and **2 transport operators** over **1 crop cycle**, paired with a working prototype demonstrating **FRR** tracking, spread reduction, delivery reliability, and settlement speed.

### Technical Architecture Diagram

```text
+---------------------------------------------------------------------------------+
|                            CLIENT LAYER (WEB & MOBILE)                          |
|  [FPO / Partner App]    [Institutional Buyer Portal]      [Fleet & Ops Hub]     |
+----------------------------------------+----------------------------------------+
                                         | HTTPS / REST / WebSockets
                                         v
+---------------------------------------------------------------------------------+
|                           API GATEWAY & AUTH SERVICE                            |
|                   (JWT Auth, RBAC, Localization, Rate Limit)                    |
+---------------------+---------------------------------------+-------------------+
                      |                                       |
                      v                                       v
+---------------------------------------+  +--------------------------------------+
|   SPREAD & SETTLEMENT ENGINE          |  |   POOLING, QUALITY & DISPATCH ENGINE |
| - FRR Formula & Spread Alerts         |  | - FPO + Certified Partner Pooling    |
| - Grade/District-Adjusted Benchmarks  |  | - Photo Grading & Dispute Logs       |
| - T+0 / Milestone & Financing Hooks   |  | - Multi-Stop + Backhaul Solver       |
+-------------------+-------------------+  +-------------------+------------------+
                    |                                          |
                    +---------------------+--------------------+
                                          |
                                          v
+---------------------------------------------------------------------------------+
|                            AI & OPTIMIZATION LAYER                              |
|  [Explainable Spread & Shortage Engine]   [Capacity, Window & Backhaul Solver]  |
|  (Corridor Rank + Reason Factors)         (OR-Tools + Compatibility Rules)      |
+----------------------------------------+----------------------------------------+
                                         |
                                         v
+---------------------------------------------------------------------------------+
|                          DATA & EXTERNAL INTEGRATIONS                           |
|     PostgreSQL + PostGIS      Redis Cache      Bank/NBFC/UPI      SMS / Maps   |
+---------------------------------------------------------------------------------+

```

---

## Feasibility and Viability

### Analysis of the Feasibility of the Idea

Starting with a bounded B2B pilot keeps operational scope tight and avoids high-cost fragmented consumer deliveries in Phase 1. Using standard cloud/open-source tech, asset-light transport partnerships, and partner liquidity rails keeps pilot costs realistic before expanding to consumer collectives in Phase 2.

### Revenue & Sustainability Model

Post-pilot sustainability comes from a lean multi-stream model: a modest **transaction/fulfillment fee** on institutional orders, a **logistics coordination fee** per dispatched/backhaul-paired run, and **analytics/intelligence subscriptions** for institutional procurement teams, FPOs, or monitoring bodies needing shortage alerts, supplier reliability scores, and price-spread audits.

### Potential Challenges and Risks

* **Trader Loyalty & Liquidity Needs:** Farmers may stick with familiar traders if they need quick payouts, credit, or fast clearance of perishable lots.
* **Uneven FPO Readiness & Quality Disputes:** Some FPOs lack staff/tech capacity, and disputes over grading, moisture, weight, or transit damage can delay settlements.
* **False Spread Alerts & Perishability Limits:** Unadjusted regional/grade price differences can trigger noise, while high-spoilage produce can degrade without fast movement or holding buffers.
* **Regulatory & Working Capital Constraints:** State APMC/direct-marketing rules, GST/food-safety compliance, and payout liquidity require careful setup.

### Strategies for Overcoming These Challenges

* **Fallback Partners + T+0 / Partner Liquidity:** Use **Certified Collection Partners** alongside FPOs, enable vernacular/SMS workflows, and support **T+0 / milestone settlements** via partner banks, NBFCs, or invoice discounting.
* **Photo-Verified Grading & Normalized Baselines:** Require pre-dispatch and delivery-time photo/weight logs with clear dispute/partial-acceptance rules, and use **grade-normalized, district-adjusted** benchmarks to cut false alerts.
* **Short-Hold Buffers & Compliance Alignment:** Pair rapid institutional dispatch with cool/shaded short-hold buffers for perishables and align operations with applicable state direct-marketing/APMC rules, e-NAM/mandi baselines, GST, and food-safety standards.

---

## Impact and Benefits

### Target KPIs & Measurable Outcomes

Pilot targets—subject to commodity, grade, and corridor characteristics—include:

* **Farmer Realization Ratio (FRR):** Pilot target of **up to 70–80%** farmer share of final buyer price (versus typical fragmented-chain baselines around 40–60% depending on crop).
* **Price Spread Reduction:** Pilot target of **~15–25%** reduction in farmgate-to-buyer price spread by cutting redundant intermediary markups and handling losses.
* **Logistics & Utilization:** Pilot target of **~10–20%** lower per-kg freight cost through consolidated multi-stop runs, with **backhaul return matching** acting as a secondary efficiency lever to lift round-trip vehicle utilization by **~20–30%** on compatible corridors.
* **Operational Reliability:** Tracking **FRR improvement**, **spread reduction**, **delivery reliability**, and **settlement speed**.

### Potential Impact on the Target Audience

* **Farmers & FPOs:** Higher net realization per kg, explainable buyer/corridor recommendations when spreads lag, **Certified Collection Partner** fallback support, and faster digital payouts.
* **Institutional Buyers & Consumers (Phase 1 → Phase 2):** Better supply continuity, shortage alerts, supplier reliability scores, and lower markups for institutional buyers in Phase 1, expanding to consumer collectives in Phase 2.
* **Logistics Operators:** Better route predictability, fewer empty legs where compatible backhaul fits, and steadier round-trip earnings.

### Benefits of the Solution

* **Economic:** Improves farmer income retention, curbs excessive price markups, and reduces wasted freight capacity.
* **Social:** Broadens fair market access for smallholders and FPOs while supporting more transparent food pricing.
* **Environmental:** Reduces post-harvest food waste via faster dispatch and short-hold buffers, and cuts emissions per ton moved through load consolidation and secondary backhaul pairing.

---

## Research and References

* **Department of Consumer Affairs — Price Monitoring Division & Price Monitoring System:** Official wholesale and retail price monitoring and consumer price-stability framework — https://consumeraffairs.gov.in/pages/price-monitoring-division and https://fcainfoweb.nic.in/
* **Reserve Bank of India (RBI) Bulletin — *Agriculture Supply Chain Dynamics: Evidence from Pan-India Survey*:** Empirical findings on farmers' share in consumer prices, smallholder structure, and supply-chain cost markups — https://www.rbi.org.in/Scripts/BS_ViewBulletin.aspx?Id=22326
* **Agmarknet 2.0 & e-NAM (PIB / Ministry of Agriculture & Farmers Welfare):** National agricultural market price/arrival portal and electronic trading framework — https://www.pib.gov.in/PressReleaseDetail.aspx?PRID=2204750 and https://agriwelfare.gov.in/sites/default/files/eNAM_Guidlines_English%20Version.pdf
* **Operational Guidelines for FPOs & APMC Direct Marketing Context (Department of Agriculture & Farmers Welfare / DMI):** FPO governance, aggregation, and market framework references — https://dmi.gov.in/Documents/FPO_Scheme_Guidelines_FINAL_English.pdf
* **Open Network for Digital Commerce (ONDC) & Google OR-Tools Routing Documentation:** Open network commerce architecture and constrained vehicle routing reference — https://ondc.org/ and https://developers.google.com/optimization/routing

```

```
