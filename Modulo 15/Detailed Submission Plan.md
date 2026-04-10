# Project Document — Commission Advance for Real Estate Ecosystem

## Sumário

- [1) Project Team Members](#1-project-team-members)
- [2) Executive summary](#2-executive-summary)
- [3) Problematic](#3-problematic)
- [4) Description of the enterprise](#4-description-of-the-enterprise)
- [5) Business objectives](#5-business-objectives)
- [6) Work Schedule](#6-work-schedule)
- [7) Scope](#7-scope)
  - [a) Preliminary Value Proposition](#a-preliminary-value-proposition)
  - [b) Customer Segments](#b-customer-segments)
- [8) General observations](#8-general-observations)

## 1) **Project Team Members**

**Full name:** Felipe Martins Moura

---

## 2) **Executive summary**

This venture creates a **digital liquidity rail** for real estate brokers and agencies by **advancing sales commissions** secured by the **purchase-and-sale agreement** through structured **credit assignment**. We solve a systemic credit gap—caused by informality, short maturities, regional payment heterogeneity, and rescission risk—by combining a **governed underwriting model**, **API-enabled data collection** from partner agencies, and a **capital structure via FIDC**. The business monetizes through a discount rate and service fees, while enforcing concentration, tenor, and flow-of-funds controls to protect investor capital and ensure scale.

---

## 3) **Problematic**

Brazil's real estate value chain locks significant working capital inside commissions that are **hard for banks to underwrite**. Reasons include: (i) limited/fragmented credit history for brokers and small agencies, (ii) **rescission risk** in purchase-and-sale agreements (e.g., title/financing issues), (iii) **short, variable tenors** with **regional payment practices**, (iv) **low ticket averages** with operational idiosyncrasies (e.g., land/rural/incorporation commissions have bigger tickets but higher rescission uncertainty), and (v) **traceability gaps** on receivables flow that raise perceived default risk.
Traditional lenders avoid the segment; as a result, **productive professionals remain illiquid**, unable to fund expenses or invest in growth—even when they hold **financeable receivables**.

---

## 4) **Description of the enterprise**

We are a **fintech platform** that purchases/advances real estate **commission receivables** via **credit assignment** backed by the underlying **purchase-and-sale contract**.
**What we do:** digitize onboarding, eligibility, and funding for commission advances; **formalize assignment** (terms with the agency and the broker) and **route payment** via the agency or a split mechanism.
**Sector:** Real Estate × Fintech (Receivables Finance).
**Solution:** governed underwriting + API integrations + electronic formalization; investor visibility via dashboards.
**Business model:** discount rate on advanced value + service fees; FIDC acquires eligible receivables.
**Benchmark references:** RLTY Capital (US), PipeImob and Imobitech (BR). Our focus is **commission advance as the core product**, not as a side feature of a pay-out system.

---

## 5) **Business objectives**

* **Build a functional MVP** that validates core user flows: broker/agency onboarding, commission receivable submission, eligibility assessment, and funding execution.
* **Establish technical foundation**: relational data model, simplified architecture, infrastructure setup, and API integrations for partner agencies.
* **Deliver a low-fidelity prototype** for user validation and feedback collection.
* **Produce user feedback report** with insights on usability, conversion barriers, and feature priorities.
* **Complete compliance analysis** covering regulations and ethics relevant to commission advance operations.
* **Create investor-ready technical documentation** demonstrating scalable architecture and operational readiness.

---

## 6) **Work Schedule** 

> **Sprint cadence:** 2-week sprints; **deliveries every second Friday**. **Sprint 1 starts:** **02 Feb 2026**.

| Sprint | Window (Mon–Fri)          | Delivery (Friday) | Focus (Module 3 — MVP Development)                                                                                                               |
| -----: | ------------------------- | ----------------- | ------------------------------------------------------------------------------------------------------------------------------------------------- |
|      1 | 02 Feb 2026 → 13 Feb 2026 | **13 Feb 2026**   | Detailed Submission Plan; relational model; simplified architecture.                                |
|      2 | 16 Feb 2026 → 27 Feb 2026 | **27 Feb 2026**   | Product Development Plan (Requirements, Roadmap); setup infrastructure.                                          |
|      3 | 02 Mar 2026 → 13 Mar 2026 | **13 Mar 2026**   | Low-Fidelity Prototype.                                  |
|      4 | 16 Mar 2026 → 27 Mar 2026 | **27 Mar 2026**   | Functional MVP. |
|      5 | 30 Mar 2026 → 10 Apr 2026 | **10 Apr 2026**   | User Feedback Report on MVP; Product Benchmarking; Compliance Analysis (regulations & ethics); Final Presentation; Public Report. |

---

## 7) **Scope**

### a) **Preliminary Value Proposition**

**For brokers and agencies:** immediate, compliant liquidity against commission receivables—**no traditional collateral**, minimal friction, transparent pricing, and **end-to-end digital** formalization.
**For investors (FIDC):** a **governed, data-rich asset** with clear eligibility, **controlled concentrations**, and **auditable payment flows**, yielding attractive risk-adjusted returns.

### b) **Customer Segments**

* **Primary:** independent real estate brokers and small-to-mid agencies with recurring sales yet limited access to working capital.
* **Secondary:** investors/allocators (FIDC managers) seeking short-duration, granular exposure to real estate commission receivables.
* **Channel partners:** real estate agencies (as originators and payment routers), pay-out/split processors.

**Priority sub-segments & nuances:**

* **Southern Brazil agencies** with faster cash cycles (less bank financing dependency).
* **Incorporation/land/rural commissions** (higher tickets; tighter eligibility due to rescission uncertainty).
* **Urban financed transactions** (longer cycle; require strict split/escrow to ensure traceability).

---

## 8) **General observations**

**Premises:** interested **FIDC** buyer(s); signed **partnership agreement with agencies**; **broker adhesion term**; **deal-level assignment term** per purchase-and-sale contract; **agency health/validation** (operational confirmation).
**Restrictions:** **ticket ≥ R$250k**; **≤25% concentration** per client or agency; **no direct payments to brokers** (agency receipt or payment split required); **tenor ≤ 6 months**; preference for **low rescission risk** profiles.
**Key risks & mitigations:** rescission/default (eligibility filters, split/escrow, concentration caps); data gaps (API intake, document standards, audit trails); operational scale (automation first, exception handling playbooks); regulatory fit (document templates, KYC/AML routines).
**Hypotheses to validate:** conversion vs. pricing elasticity; default vs. rescission correlation; agency willingness to route payments; investor appetite at target IRR; broker repeat-usage drivers.
**Strategic insight:** by **owning the underwriting & payment flow rules**, the platform converts an opaque receivable into an **institutional asset class**, unlocking liquidity for producers and predictable performance for capital.
