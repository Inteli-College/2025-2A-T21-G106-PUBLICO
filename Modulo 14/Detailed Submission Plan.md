
# Detailed Submission Plan

## Purpose

This document outlines the **Detailed Submission Plan** for Module 13 (*Product-Market Fit Assessment*). It provides an overview of the project, all sprint deliverables, explaining **what each is, why it exists, and how it works** within the PMF validation cycle. The plan includes comprehensive **KPIs and Success Metrics** within the justification framework, which are essential components of Sprint 2 delivery and critical for measuring the fintech's product-market fit through quantifiable performance indicators and acceptance criteria.



### Project Overview

**Project Plan:** Entrepreneurship

**Project Team Members:** Felipe Martins Moura

**Executive Summary:** Fintech operating as a **banking correspondent** focused on **automating sales of the FGTS Saque-Aniversário** through an **AI agent** that imitates a human salesperson in conversations (e.g., WhatsApp). The solution integrates **banking APIs** for (i) **balance inquiry**, (ii) **lien/annotation at Caixa**, and (iii) **formalization** with anti-fraud and e-signature. The goal is to enable **high throughput with lower commission**, reducing the end customer's cost while preserving the **minimum conversion rules** required by banks — understood as the **relationship between the number of executed balance inquiries and the number of closed sales**, given that the **Caixa API is limited** and **indiscriminate balance checks are not allowed**.

### Problem Statement

* **Low average ticket** of the FGTS Saque-Aniversário → lower priority for sales reps.
* **High operational volume** that is not viable manually.
* **High commissions** (to incentivize sales) increase the customer's total cost.
* **Minimum operational conversion**: need to keep the **inquiries:sales ratio** within the bank-accepted threshold (e.g., **≤ 10:1**, i.e., **conversion rate ≥ 10%**), because the **Caixa API has limits** and **inquiries without sales** can trigger **access restrictions/blocks**.
* **Regulatory risk** of product alteration or extinction.

### Venture Description

**Fintech** operating as a **banking correspondent**, using a **conversational AI agent** orchestrated by **LangGraph or n8n** + an LLM (e.g., **GPT-3.5**), integrated with **banking APIs** and **anti-fraud/e-signature** providers. The agent drives the end-to-end journey (**balance inquiry → proposal → lien/annotation → formalization**), focusing on **efficiency, conversion, and security**.

**Importance of balance inquiry:** this check is **critical for accuracy**, because it **prioritizes customers with eligible balances**, increasing the **likelihood of sale**; at the same time, it must be **used sparingly** to **respect API limits** and maintain the **inquiries:sales relationship**.

**Sector:** credit/advance (FGTS).
**Business model:** **per-operation commission** as a banking correspondent (paid by the bank).
**Costs** are mainly **infrastructure** and **AI providers**.

### Value Proposition

* **Operations (correspondent):** increase **capacity via automation**, enabling **lower commissions** and higher **aggregate margin through efficiency**.
* **Banks/Investors:** origination at scale with **efficient conversion** (respecting the **inquiries:sales** relationship) and integrated **anti-fraud tracks**.
* **CLT Customer:** **lower effective cost**, improved experience, and **100% digital** journey.

### Customer Segments

* **Primary:** **CLT employees** with FGTS balance eligible for Saque-Aniversário.
* **Strategic partners:** banks operating the product; **promotoras** (origination partners).

### Key Constraints & Considerations

* **Premises:** access to a **bank API**; **ANEPS certification**; **server** (cloud/dedicated); available **LLM**; **anti-fraud/e-signature**; **encryption** in transit and at rest.
* **Restrictions:**
  * **Minimum operational conversion:** maintain **inquiries:sales ≤ 10:1** (≈ **conversion ≥ 10%**), since the **Caixa API is limited** and **excessive inquiries without sales** can lead to **access restriction**.
  * **Regulatory risk**; API **rate-limit/cost**; **partner dependency**.
* **Key note on accuracy:** **balance inquiry** is **essential** to **target customers with balance**, increasing **accuracy** and **conversion**; it must be **governed by responsible-use policies** (prioritization, pre-qualification, and metric monitoring).

---

## Sprint 1 — Project Plan & Project Submission

**Deliverables:**

1. **Project Plan**

   * **What it is:** A structured planning document defining scope, objectives, premises, constraints, and timelines for Module 13.
   * **Why it exists:** Sets the foundation, aligns stakeholders, and establishes the academic/entrepreneurial expectations of the project.
   * **How it works:** Provides the roadmap against which subsequent deliverables are assessed, ensuring all PMF activities tie back to original objectives.

2. **Project Submission**

   * **What it is:** Formal submission of the project description, problem statement, objectives, and scope to academic evaluators.
   * **Why it exists:** Establishes an official baseline that makes the project auditable and comparable across teams.
   * **How it works:** Functions as the anchor document for validation, against which hypotheses, metrics, and testing plans are checked for coherence.

---

## Sprint 2 — Detailed Submission Plan & PMF Hypotheses

**Deliverables:**

1. **Detailed Submission Plan**

   * **What it is:** An overview document explaining each deliverable, why it matters, and how it supports PMF validation.
   * **Why it exists:** To provide clarity on the *rationale and role* of every output in Module 13, ensuring the project team and evaluators share the same understanding.
   * **How it works:** Serves as a reference guide for the entire module; ties individual deliverables to PMF validation goals.

2. **PMF Hypotheses**

   * **What it is:** A set of testable statements about the fintech’s product-market fit (channel preference, AI vs human parity, recurrence, and value proposition).
   * **Why it exists:** Hypotheses are the backbone of PMF testing; they make assumptions explicit and measurable.
   * **How it works:** Each hypothesis is linked to specific KPIs, enabling empirical validation in Sprint 3 and beyond.

---

## Sprint 3 — PMF Testing Plan & Technology Justification Reports

**Deliverables:**

1. **PMF Testing Plan**

   * **What it is:** A detailed plan describing *how each PMF hypothesis will be tested* (methods, sample sizes, data sources, timelines).
   * **Why it exists:** Ensures testing is systematic, reproducible, and directly aligned with hypotheses.
   * **How it works:** Provides the blueprint for validation activities; bridges the gap between defined KPIs (Sprint 2) and execution.

2. **Technology Justification Reports**

   * **What it is:** Written justifications for the choice of frameworks, languages, and technologies (LLM, orchestration tool, CRM, etc.).
   * **Why it exists:** To defend architectural and technological decisions in light of PMF objectives (e.g., scalability, cost-efficiency, compliance).
   * **How it works:** Links technical stack decisions back to business drivers, ensuring validation is not only about conversion metrics but also feasibility.

---

## Sprint 4 — APIs, Interfaces & Architecture Updates

**Deliverables:**

1. **APIs & Integrations (Detailed Interfaces, Service Contracts, Communication Protocols)**

   * **What it is:** Documentation of how the AI agent, banking APIs, and auxiliary services (anti-fraud, e-signature) interact.
   * **Why it exists:** APIs are the operational backbone; without them, PMF testing cannot reach “real” conditions.
   * **How it works:** Defines service contracts and communication flows, ensuring that every validation metric (e.g., TTM, flow completion) reflects actual API constraints.

2. **Updated Architectural Models & Diagrams**

   * **What it is:** Refined system architecture diagrams showing components, integrations, and scaling approach.
   * **Why it exists:** PMF results may require architectural adjustments (e.g., to reduce latency or improve reliability).
   * **How it works:** Provides a living model of the system; documents how technical infrastructure supports PMF validation.

---

## Sprint 5 — Final Presentation & Public Report

**Deliverables:**

1. **Final Presentation**

   * **What it is:** A presentation summarizing findings, validation outcomes, and lessons learned.
   * **Why it exists:** To communicate project results clearly to evaluators, partners, and stakeholders.
   * **How it works:** Synthesizes KPIs, hypotheses validation, and architectural learnings into a single narrative.

2. **Public Report**

   * **What it is:** A written, publicly accessible report detailing Module 13 outcomes.
   * **Why it exists:** Promotes transparency, peer learning, and dissemination beyond the project team.
   * **How it works:** Consolidates all findings into an artifact that proves whether PMF was achieved and under what conditions.

---

## KPIs and Success Metrics

### Objective 1: Complete WhatsApp-Only Funnel (E2E) with Human Fallback on Request

**Scope:** Opt-in/entry → pre-qual message → balance inquiry (CPF) → proposal → lien → e-signature → funded → closing message.

**KPIs:**
- **Flow completion (no human):** ≥ 70% of conversations reach "funded" without human intervention
- **First Response Time (FRT):** median ≤ 5 seconds
- **Time-to-Money (TTM):** ≤ 24 hours median from "start" → "funded"

**Acceptance Criteria:** Demo 10 full E2E runs; dashboard shows FRT/TTM and completion rate.

### Objective 2: Establish Baseline Conversion with Constraint "≤ 60:1 Shots-per-Sale"

**Definition:** "Shot" = a lead we engage via WhatsApp session (inbound or outbound) that reaches pre-qual + balance inquiry.

**KPIs:**
- **Shots:Sale ≤ 60:1** (i.e., conversion ≥ 1.67%)
- **Leads/week:** ≥ 100 (all channels combined)

**Acceptance Criteria:** At least 4 funded sales in the sprint (given 200 leads/2 weeks, 1.67% → 3–4 sales).

### Objective 3: Unit Economics Don't Go Negative at Sprint Scale

**Formulae:**
- Revenue/sale = ticket × commission% = R$ 250 × 0.16 = R$ 40
- Variable cost/sale = (avg conversations & messages per sale × message prices) + R$ 0.15 LLM/conversation + share of R$ 400/mo CRM

**KPI:** Contribution/sale ≥ R$ 20 (post-variable costs, pre-media)

**Acceptance Criteria:** 80% of funded sales meet the contribution floor; if not, flag for Sprint 3 pricing/flow tweaks.

### Objective 4: Experience Quality & Reliability

**KPIs:**
- **Customer satisfaction (CSAT):** ≥ 4.5/5 (1-click rating post-funding)
- **System error rate:** < 2% (hard failures in any step)
- **Rate-limit headroom:** daily balance checks < 70% of 1,500 (not capacity-constrained)

**Acceptance Criteria:** Report with these three metrics by end of sprint.

**Note:** Compliance KPIs are omitted from acceptance criteria as requested, but risks will still be logged in Section E.


