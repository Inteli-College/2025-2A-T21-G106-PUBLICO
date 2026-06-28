# Commission Advance Platform: Real-Estate Broker Liquidity

## Public Report — Module 16 Go-to-Market & Launch

---

## Executive Summary

**Giroo** is a fintech platform that provides **liquidity to real estate brokers and agencies** by advancing sales commissions secured by **purchase-and-sale agreements (CCVs)** through structured **credit assignment (cessão)**. Module 16 took the functional MVP delivered in Module 15 to **market**, designing and executing a structured go-to-market strategy and instrumenting the launch for measurement. The module progressed from a launch plan anchored on an **influence-network distribution model**, through a **two-sided customer onboarding journey** and a **five-pillar KPI framework**, to **stability/security indicators and a strategic log catalog**, culminating in a **Post-Launch Business Metrics Report** on the first launch cohort.

The launch reached **15 signed agencies and 148 activated brokers** in the São Paulo metro — inside the planned coverage envelope — while holding the credit guardrail (**3.8% rescission, 0% 90+ delinquency**) and clearing both customer-acquisition-cost ceilings. The cohort validated four of five strategic hypotheses, with the ambassador channel converting at roughly **5× lower cost than event-sourced acquisition**, and produced a clear **go decision** to transition from concierge to hybrid self-serve onboarding.

---

## Problem Statement

### Market Gap

Brazil's real estate value chain locks significant working capital inside commissions that are **hard for banks to underwrite**. Reasons include:

- **Limited/fragmented credit history** for brokers and small agencies
- **Rescission risk** in purchase-and-sale agreements (title/financing issues)
- **Short, variable tenors** with regional payment practices
- **Low ticket averages** with operational idiosyncrasies
- **Traceability gaps** on receivables flow that raise perceived default risk

Traditional lenders avoid the segment; as a result, **productive professionals remain illiquid** — unable to fund expenses or invest in growth, even when they hold financeable receivables.

### Go-to-Market Challenge

Beyond the credit gap, launching a **new financial product into a relationship-driven, trust-sensitive market** carries distinct adoption barriers:

- **Product distrust** among brokers wary of new financial instruments
- **Agency resistance** to participating in the commission payment flow
- **Broker liability fear** regarding recourse exposure on assigned commissions
- **Cold-acquisition inefficiency** — digital channels struggle to convert in a market where deals close on personal credibility

---

## Solution Overview

### Core Approach

**Fintech platform** operating as a **commission advance company**, purchasing/advancing real estate **commission receivables** via **credit assignment** backed by the underlying **purchase-and-sale contract**. Module 16 operationalized the launch through **trusted human intermediaries** — an ambassador network of respected industry figures — rather than cold digital acquisition, lowering the trust barrier inherent to a new financial product and converting industry credibility into a structured, measurable acquisition engine.

### Value Proposition

**For Brokers:**
- Immediate, compliant liquidity on earned commissions — no waiting 30–90 days
- No traditional collateral, transparent pricing, fully digital formalization
- Clear liability boundaries protecting the broker from recourse exposure

**For Agencies:**
- A differentiated benefit that strengthens broker loyalty and retention
- A governed payment-split mechanism that keeps the agency in the flow without operational burden

**For Key Accounts (large agencies / franchise networks):**
- A structured, scalable product with documented underwriting criteria and an institutional-grade capital structure — credible for high-volume distribution

### Customer Segments

- **Primary:** Independent real estate brokers and small-to-mid agencies in São Paulo with recurring sales activity and limited access to working capital
- **Secondary:** Regional franchise networks and large independent agencies in the Southeast and Midwest acting as distribution multipliers
- **Influence layer:** Former account managers and senior professionals from leading proptech platforms (e.g., QuintoAndar, Loft) who hold trusted relationships with agency decision-makers

---

## Go-to-Market Strategy

### Launch Through an Influence Network

The launch strategy leverages **trust-based relationships** with key industry figures from major real estate platforms. By activating an influence network of trusted intermediaries, the platform overcomes the inherent distrust in financial products within a relationship-driven market.

| Component | Approach |
|---|---|
| **Influencer identification** | Former account managers and senior professionals from QuintoAndar, Loft, Viva Real, Zap Imóveis, and franchise networks (Re/Max, Century 21) |
| **Selection criteria** | Proven real estate track record; existing trust with target agencies; willingness to act as ambassadors; alignment with the liquidity value proposition |
| **Compensation** | Tiered commission model (standard referrals → key-account conversions → high-volume partnerships) plus content collaboration and partnership recognition |
| **Channels** | Co-branded content, strategic partnerships, and sponsored anchor events (industry trade shows, franchise conventions, award ceremonies) |

### Two-Sided Customer Onboarding

The product has **two distinct customer roles** onboarded sequentially: the **agency** (counterparty controlling the payment flow) is signed first, then **brokers** within it are activated as the end-users of the advance.

The journey is organized in **five phases** with defined entry/exit criteria and ownership:

| # | Phase | Audience | Goal |
|---|---|---|---|
| 1 | **Kick-off** | Agency leadership | Validate process fit; secure pilot agreement |
| 2 | **Digital** | Agency network | Generate social proof and inbound interest |
| 3 | **Educational** | Individual brokers | Convert curiosity into informed intent |
| 4 | **Campaign** | Warm-lead brokers | Trigger first advance; activate referral loop |
| 5 | **Relationship** | Active brokers + agency | Retain, expand, and convert satisfaction into referrals |

The first cohort received **concierge onboarding** (founder + one operations analyst) prioritizing **coverage breadth and qualitative learning** over automated scale, with a target end-to-end median of **≤ 21 days from agency kick-off to first broker advance**.

---

## KPI Framework

The launch is measured through a **five-pillar KPI architecture** spanning 18 indicators, each with a definition, target, owner, and refresh cadence.

| Pillar | Decision question |
|---|---|
| **Acquisition & Funnel** | Is the influence network producing qualified pipeline at expected conversion rates? |
| **Activation & Time-to-Value** | Are onboarded accounts reaching first advance within SLA, and how quickly? |
| **Engagement & Retention** | Once activated, do brokers come back and refer peers? |
| **Credit Health & Portfolio Quality** | Is the portfolio safe to scale to FIDC-grade volumes? |
| **Unit Economics** | Is the channel mix economically defensible against the CAC ceilings? |

**Coverage** — signed agencies and activated brokers — was designated the **headline outcome** for cohort 1, deliberately preferred over volume-first or quality-first alternatives. A wide cohort exposes the credit model to heterogeneous agency types and rescission contexts, compounds the ambassador network's effect, and avoids the concentration risk of high volume in a few accounts. Volume and credit quality remained hard guardrails throughout.

---

## Stability, Security & Strategic Logs

The launch operation was instrumented across three layers, transforming Giroo into an **event-driven system** where every relevant action generates an immutable, queryable record.

### Operational Stability

Stability for a receivables-advance fintech is the **predictability of every step in the financial cycle**, from advance request to repayment confirmation. Headline targets: **≥ 99.5% uptime**, **≤ 24h advance cycle time**, and **≥ 90% SLA compliance** — the 24-hour disbursement SLA being the core competitive differentiator over manual and banking alternatives.

### Security & Compliance

Security operates across three interdependent layers — **fraud prevention** (protecting investor capital), **data protection** (LGPD compliance), and **access security**. The framework targets **MTTD ≤ 4h** and **MTTR ≤ 24h** for critical incidents, **100% MFA** for internal users, and **zero data-breach incidents**, with a **security-maturity target of Level 3 (Managed)** at Day 90.

### Strategic Log Catalog

A master event catalog spans four domains — **Customer Journey**, **Credit & Advance Cycle**, **Channel & Acquisition Performance**, and **Security & Audit**. Logs are **immutable**, follow a **standardized JSON schema**, and carry **retention policies** aligned with Brazilian regulation (Res. CMN 4.893/21, AML Law 9.613/98, LGPD). This catalog is the **primary raw material** for the Post-Launch Business Metrics Report — which is, by design, a structured query against the event catalog rather than an ad hoc data exercise.

---

## Post-Launch Results

The first launch cohort's measured performance against the cohort-1 targets:

| Dimension | Target | Result | Status |
|---|---|---|---|
| Signed agencies | 10–20 | **15** | ✅ |
| Activated brokers | ~150 | **148** | ✅ |
| Median kick-off → first advance | ≤ 21 days | **19 days** | ✅ |
| First-advance conversion (30 days) | ≥ 40% | **46%** | ✅ |
| Rescission rate | ≤ 5% | **3.8%** | ✅ |
| NPL 90+ | 0% | **0%** | ✅ |
| CAC, standard accounts | ≤ R$ 500 | **R$ 470** | ✅ |
| CAC, key accounts | ≤ R$ 2,000 | **R$ 1,840** | ✅ |
| Broker NPS | ≥ 50 | **56** | ✅ |
| Advances per active broker / month | ≥ 1.5 | **1.4** | ⚠️ |
| Agency commission-flow exposure | ≥ 30% | **28%** | ⚠️ |
| MGM referral rate | ≥ 25% | **22%** | ⚠️ |
| Platform uptime | ≥ 99.5% | **99.7%** | ✅ |
| Data-breach incidents | 0 | **0** | ✅ |

**Portfolio snapshot:** **R$ 684,000 cumulative advanced** across **95 advances** (average ticket R$ 7,200), with an average active portfolio of **R$ 236,000** and **73% of signed agencies producing live volume**.

### Channel Economics

| Channel | Share | CAC / activated broker |
|---|---|---|
| **Ambassador-sourced** | 64% | **R$ 390** |
| Inbound / digital | 15% | R$ 610 |
| Event-sourced | 21% | R$ 1,920 |

The ambassador channel converted at roughly **5× lower cost** than event-sourced acquisition — empirically validating the influence-network thesis as the lowest-cost, highest-trust channel and prompting a budget reallocation from events to ambassadors for the volume phase.

---

## Strategic Hypothesis Validation

| Hypothesis | Verdict | Evidence |
|---|---|---|
| **Acquisition** — ambassador CAC < digital; highest LTV/CAC | ✅ Confirmed | Ambassador R$ 390 vs event R$ 1,920 |
| **Onboarding** — ≤ 21-day cycle consistently met | ✅ Confirmed | Median 19 days; KYC document collection the main bottleneck |
| **Credit** — rescission < 5%; LTV policy protective | ✅ Confirmed | 3.8% rescission; 0% NPL 90+ |
| **Product** — 24h SLA ≥ 90%; NPS ≥ 50 | ✅ Confirmed | 92% SLA; NPS 56 |
| **Growth** — reactivation sustains the Year-1 path | ⚠️ Partial | Retention 52% met, but repeat frequency and referral fell just short |

The launch validated the **acquisition and credit theses decisively**; the open question carried into the next phase is **monetization depth per account** — repeat frequency, agency penetration, and peer referral.

---

## Risk Management Strategy

### Launch & Adoption Risks

- **Product distrust** → ambassador credibility, educational materials, transparent documentation, explicit liability-boundary clarity
- **Agency resistance to payment-flow participation** → standardized split agreements, minimal operational burden, framing around broker retention
- **Ambassador fraud / low engagement** → background checks, structured legal agreements, pilot-before-scale, performance dashboards, success-based incentives

### Credit & Portfolio Risks

- **Rescission/default** → eligibility filters, payment split/escrow, concentration caps (per-agency and per-broker)
- **Concentration** → automatic risk review triggered above 15% portfolio share for any single agency
- **Fraud vectors** (document tampering, identity spoofing, agency collusion, intentional rescission) → API cross-validation, biometric onboarding, CNPJ due diligence, repurchase clauses

### Operational & Regulatory Risks

- **Concierge bandwidth bottleneck** → cohort capped at 150 brokers; second analyst trigger at 120 active accounts
- **Regulatory compliance** → KYC/KYB completeness, 5-year audit-log retention, LGPD request fulfillment within 15 days

---

## Business Model Context

### Revenue Model
- **Discount rate** on advanced commission value (customer rate ~5–6% per month) plus complementary service fees
- **Capital structure** via FIDC (investment fund) acquiring eligible receivables

### Launch Economics (Cohort 1)
- **Standard-account CAC:** R$ 470 (ceiling R$ 500); **key-account CAC:** R$ 1,840 (ceiling R$ 2,000)
- **Take rate:** 5.9%; **contribution margin:** 3.6 pp per advance; **CAC payback:** ~5.4 months
- **Eligible ticket envelope:** R$ 1,000–R$ 50,000 per advance

### Coverage Targets
- **Year 1:** R$ 1M active portfolio; ≥ 60 agencies, ≥ 600 brokers
- **Year 2:** R$ 3M active portfolio, expanding into the Southeast and Midwest

---

## Module 16 Deliverables by Sprint

### Sprint 1 (Apr 20 – May 1, 2026)
1. **Detailed Submission Plan** — Go-to-market scope, business objectives, value proposition, customer segments, work schedule, premises, restrictions, and validation hypotheses

### Sprint 2 (May 4 – May 15, 2026)
1. **Launch Plan: Influence Network Mapping** — Influencer identification, value proposition, engagement strategies, tiered commission structure, event sponsorship, budget allocation, and risk mitigation

### Sprint 3 (May 18 – May 29, 2026)
1. **Customer Onboarding Plan** — Two-sided journey, five-phase architecture, agency and broker journeys, concierge cohort design, tooling/roles/SLAs
2. **KPI Definition and Expected Business Outcomes** — Five-pillar framework (18 indicators), coverage-first rationale, monitoring cadence, and data-source instrumentation

### Sprint 4 (Jun 1 – Jun 12, 2026)
1. **Stability & Security Indicators Analysis; Strategic Database Logs** — Operational/security indicator framework, master event taxonomy, log architecture, retention/compliance policies, and process-improvement cycle

### Sprint 5 (Jun 15 – Jun 26, 2026)
1. **Post-Launch Business Metrics Report** — Consolidated cohort-1 results against the KPI framework, channel/CAC analysis, hypothesis validation, learnings, and the go/no-go decision
2. **Final Presentation** — Summary of go-to-market outcomes and strategic decisions
3. **Public Report** (this document) — Written, publicly accessible report detailing Module 16 outcomes

---

## Future Roadmap

### Completed (Module 13 — Product-Market Fit)
- Project plan and PMF hypotheses; architecture design; technology stack selection

### Completed (Module 14 — Financial Model)
- Cost/revenue assumptions and pricing; 12-month P&L and 5-year DCF; governance and credit-policy framework

### Completed (Module 15 — MVP Development)
- Relational model (44+ entities); system architecture (modular monolith, 3 services); requirements specification; low-fidelity prototype; functional MVP; user feedback and compliance analysis

### Completed (Module 16 — Go-to-Market & Launch)
- Influence-network launch plan; two-sided customer onboarding plan; five-pillar KPI framework; stability/security indicators and strategic log catalog; post-launch business metrics report

### Upcoming (Post-Module — Volume Phase)
- Transition to hybrid self-serve onboarding
- Reallocate channel budget toward the ambassador program
- Activate repeat-usage levers (post-advance CRM cadence, in-flow referral trigger)
- Deepen agency commission-flow penetration past 30%
- Scale toward the R$ 1M Year-1 active-portfolio target

---

## Key Project Insights

### Strategic Positioning

**"Launch through trust, scale through data."** The go-to-market approach prioritizes:
1. **Trust-led distribution** — industry credibility converted into a structured acquisition engine, not cold digital acquisition
2. **Coverage-first learning** — breadth of validated accounts before volume optimization
3. **Instrumented operations** — every decision traceable through an immutable event catalog

### Launch Insights

1. **The ambassador channel is the economic engine** — roughly 5× cheaper than events; the unit-economics margin of safety depends on it
2. **Acquisition and credit are validated; depth is the open question** — repeat frequency, agency penetration, and referral are the binding constraints on the Year-1 path
3. **The binding constraint shifted from adoption to monetization** — the market will adopt; the work ahead is making each account monetize more deeply
4. **Credit health is non-negotiable and held** — 3.8% rescission and zero 90+ delinquency preserve the institutional-grade-asset thesis

---

## Conclusion

Module 16 took Giroo from a functional MVP to a **measured market launch**:

1. **Designed a trust-led go-to-market** — an influence-network distribution model that converts industry credibility into a low-cost, structured acquisition engine
2. **Built a two-sided onboarding journey** — agencies first as the payment-flow anchor, then brokers as end-users, converging inside a 21-day kick-off-to-first-advance corridor
3. **Established a five-pillar KPI framework** — 18 indicators anchored on coverage, with credit health and unit economics as hard guardrails
4. **Instrumented the operation** — stability/security indicators and an immutable strategic log catalog aligned with Brazilian financial and data-protection regulation
5. **Reported measured results** — coverage achieved, credit guardrail held, CAC ceilings cleared, and four of five strategic hypotheses confirmed, producing a clear go decision to scale

The launch demonstrated that Giroo can **acquire trust-led at low cost** and **underwrite safely at FIDC-grade quality** — reframing the path to the R$ 1M Year-1 portfolio from a question of market adoption to one of **monetization depth per account**.

---

## Contact Information

**Project Lead:** Felipe Martins Moura
**Project Type:** Entrepreneurship
**Current Module:** 16 — Go-to-Market & Launch
**Current Status:** First launch cohort delivered; transitioning to hybrid self-serve onboarding and the volume phase

---

## Appendix: Premises and Constraints

### Premises
- Operational platform ready for customer intake
- Capital structure (**FIDC** or equivalent facility) in place to fund advances
- Signed **agency partnership agreements** enabling payment-split or escrow routing
- **Ambassador network** contracted and briefed
- Event participation confirmed for at least two anchor channels

### Constraints
- **Ticket range R$ 1,000–R$ 50,000** per advance
- **Geographic focus** on the São Paulo metro in Year 1
- **CAC ceilings:** R$ 500 standard / R$ 2,000 key accounts
- **No direct payments to brokers** — all disbursements routed via agency or verified split mechanism
- **≤ 25% concentration** per client or agency
- **Academic deadlines** for deliverables (2-week sprint cadence)

---
