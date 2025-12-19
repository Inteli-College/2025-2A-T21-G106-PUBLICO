## Financial Model — Sprint 1: Detailed Submission Plan

### Business Overview (from PMF, brief)
WhatsApp‑first fintech acting as a banking correspondent that automates sales of the FGTS Saque‑Aniversário. A conversational AI agent replaces the human seller inside WhatsApp, driving the end‑to‑end flow (balance inquiry → proposal → lien/annotation → e‑signature → funding). Revenue is per‑operation commission from partner banks. Operations are asset‑light (outsourced/non‑core activities, scalable variable costs). We must respect bank rules (e.g., inquiries:sales efficiency thresholds) and we will operate under Brazil’s Simples Nacional regime.

### 1) Objective and Context
- **Objective**: Produce a clear plan and acceptance criteria for the financial model that supports an asset‑light business targeting **30% EBITDA margin**, operating under **Brazil’s Simples Nacional** tax regime.
- **Why now**: This plan anchors assumptions, model architecture, KPIs/success metrics, and review criteria to accelerate Sprints 2–5 (assumptions, projections, DCF, governance, and public report).

### 2) Business Constraints and Modeling Principles
- **Business model**: Asset‑light (minimal fixed assets, outsourced/non‑core functions, scalable variable costs).
- **Channel**: WhatsApp‑first, AI agent replaces the human seller with human fallback on request.
- **Product**: FGTS Saque‑Aniversário origination via partner bank APIs.
- **Profitability target**: Base‑case EBITDA margin of **≥ 30%** by Month 12, sustained thereafter.
- **Tax regime**: Simples Nacional (configurable annex and brackets). We will compute monthly taxes using the official effective rate formula and progressive brackets.
- **Time granularity**: Monthly model; base horizon 36 months (12+ months required; 60-month skeleton to support Sprint 4 DCF).
- **Transparency**: All drivers centralized in an `Inputs & Assumptions` section; all formulas open and traceable.
- **Scenario-first**: Base, Upside, Downside toggles affect demand, pricing, churn, CAC, and cost elasticity.
- **Compliance guardrail**: Track and respect partner bank constraints (e.g., inquiries:sales ratio) in the funnel and KPI validation.

### 3) Deliverable Scope (Sprint 1)
Deliver a complete plan plus a working model skeleton (tabs/links/structures) ready to be populated in Sprints 2–4.
- Documented KPI definitions and acceptance criteria (this file).
- Model skeleton (no final numbers yet): tabs, key ranges, formula stubs, scenario toggles, Simples Nacional logic placeholders.
- Checklist for data capture and validations.

### 4) Model Architecture (Sheets/Tabs)
1. `Cover & ReadMe`: model purpose, versioning, change log, scenario selector.
2. `Inputs & Assumptions`: prices, funnel, churn, payment fees, headcount plan, annex selection, bracket ranges, PD (parcela a deduzir), operating working‑capital days.
3. `Demand & Funnel`: leads → MQL → SQL → customers; conversion rates; sales cycle; inquiries:sales guardrail.
4. `Revenue`: pricing tiers, ARPU/ARPA, new vs. expansion revenue, churn/downsells.
5. `COGS`: variable costs (e.g., provider/API fees, hosting, payment gateway MDR), per‑unit cost curves.
6. `OPEX`: headcount costs (salaries, benefits, taxes), marketing, G&A, R&D; asset‑light emphasis.
7. `Taxes — Simples Nacional`: effective tax rate computation by month, annex selection logic.
8. `P&L`: gross margin, EBITDA, EBIT proxies.
9. `Cash Flow`: operating cash flow, basic capex, tax payments, working capital.
10. `Unit Economics`: CAC, LTV, contribution margin, payback.
11. `Scenarios & Sensitivities`: drivers table and data tables for elasticities.
12. `Validation`: consistency checks and KPI pass/fail.

### 5) Key Assumptions to Establish (Sprint 2 handoff readiness)
- **Pricing & Packaging**: initial list and net prices, discount policy, ramp schedule; freemium/trial rules if any.
- **Demand Drivers**: lead volume, conversion rates, sales cycle (months), churn and expansion rates.
- **Payment & Gateway Fees**: MDR %, fixed fees, chargeback rate; settlement lags.
- **COGS**: hosting/unit, third‑party API/unit, support costs, any revenue‑share.
- **OPEX**: lean headcount plan; contractor vs. FTE mix; salary bands and hiring cadence.
- **Working Capital**: DSO/DPO; prepayments; gateway settlement days.
- **Taxes (Simples Nacional)**:
  - Track RBT12 (receita bruta acumulada em 12 meses) monthly.
  - Store official brackets (aliquota nominal and parcela a deduzir — PD) as parameters.
  - Compute effective monthly rate using the statutory formula:
    - Aliquota Efetiva = (RBT12 × Aliquota Nominal − PD) ÷ RBT12
  - Select Annex (I/III/V etc.) as a parameter; if services, allow Fator R logic to switch Annex per rules (configurable, with documentation link in model).
  - Output month‑level tax as `Aliquota Efetiva × Receita Bruta do mês`.

### 6) Methodology and Formulas (high level)
- **Revenue**: Customers by cohort × ARPU; account for churn/downsells/expansion; price ramp over time.
- **Gross Margin**: 1 − (COGS ÷ Net Revenue); asset‑light target ≥ 70% by Month 6.
- **EBITDA**: Gross Profit − OPEX; exclude depreciation/amortization, interest, and taxes by definition.
- **Unit Economics**: LTV = ARPU × Gross Margin × average customer lifetime; CAC from paid/organic mix; payback = CAC ÷ (ARPU × gross margin − variable costs per unit).
- **Taxes (Simples)**: Apply effective rate monthly, independent from EBITDA by construction.
- **Scenarios**: Apply percentage overrides to key drivers (demand ±X%, churn ±Y pp, CAC ±Z%, price elasticity).

### 7) KPIs & Success Metrics (with justification)
- **Primary KPI — EBITDA Margin**: ≥ 30% from Month 12 onward (Base Case).
  - Rationale: Asset‑light models with high gross margin and disciplined OPEX can achieve ~30–40% EBITDA at scale; we target 30% as a minimum viable profitability threshold.
- **Gross Margin**: ≥ 70% by Month 6; ≥ 75% by Month 12.
  - Rationale: Minimal COGS (hosting, gateways, third‑party SaaS) with price power.
- **LTV/CAC**: ≥ 3.0 by Month 12 (base), ≥ 4.0 (upside); minimum ≥ 2.0 in downside.
  - Rationale: Industry standard for sustainable growth with limited dilution.
- **CAC Payback**: ≤ 6 months by Month 12; stretch ≤ 4 months.
  - Rationale: Capital efficiency for asset‑light, faster reinvestment cycles.
- **Contribution Margin per Unit**: ≥ 50% by Month 3; ≥ 60% by Month 6.
- **Net Revenue Growth (MoM)**: 8–15% average in Year 1 Base; parameterized.
- **Burn Multiple**: ≤ 1.0 if negative EBITDA early on; else maintain positive EBITDA.
- **Cash Runway**: ≥ 12 months if burning; N/A if cash‑generative.
- **Tax Accuracy (Simples)**: Aliquota efetiva variance vs. manual check < 0.5 pp in all months.
- **Operational Guardrail (API efficiency)**: inquiries:sales maintained within partner thresholds in Base and Upside cases.


### 8) Data Sources and References
- Simples Nacional official tables and guidance (Annexes, PD, Fator R).
- Industry benchmarks for CAC, LTV, gross margin for comparable asset‑light businesses.
- Payment gateway documentation for MDR and settlement.
- Vendor contracts for variable cost schedules.
- PMF docs for WhatsApp‑first funnel constraints and definitions (shots, FRT, TTM, CSAT).

### 9) Risks and Mitigations
- **Annex Classification Uncertainty**: Implement annex selection + Fator R logic; document assumption and keep as a toggle.
- **Price Elasticity**: Add sensitivities; test lower price points vs. conversion lift.
- **COGS Variability**: Parameterize provider tiers; include step‑function costs and volume discounts.
- **Churn Assumptions**: Use conservative base; include downside sensitivity and cohort decay.
- **API Efficiency Rule (inquiries:sales)**: Pre‑qualify before balance checks; monitor and throttle based on guardrail.


### 10) Handoff to Next Sprints
- **Sprint 2**: Populate cost and revenue assumptions; finalize pricing strategy; validate gateway fees.
- **Sprint 3**: Produce 12+ month detailed projections with scenarios.
- **Sprint 4**: Build 5‑year DCF, scenarios, and sensitivity analysis.
- **Sprint 5**: Governance processes, legal compliance notes, final presentation, and public report.



