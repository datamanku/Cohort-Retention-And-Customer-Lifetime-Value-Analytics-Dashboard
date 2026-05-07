
---

# Cohort Retention & Customer Lifetime Value Analytics Dashboard

<img width="1248" height="710" alt="image" src="https://github.com/user-attachments/assets/25bb044e-9e4c-4dc3-a8c7-918bb56b9e7d" />

---

## Navigation

- [Purpose](#purpose) 
- [Business Problem](#business-problem) 
- [Executive Questions](#executive-questions)
- [Dataset](#dataset)
- [Data Preparation](#data-preparation) 
- [Data Model](#data-model)
- [DAX Measures](#dax-measures)
- [Dashboard KPIs](#dashboard-kpis) 
- [Dashboard Design (Business Problem -> Analysis -> Insights & Recommendations -> Action)](#dashboard-design-business-problem---analysis---insights--recommendations---action)
- [Executive Business Insights](#executive-business-insights) 
- [Actionable Business Recommendations](#actionable-business-recommendations) 
- [Business Value Delivered](#business-value-delivered)
- [Tools & Skills Used](#tools--skills-used)

---

## Executive Summary
This work presents an executive-grade **Cohort Analysis Dashboard** built in Power BI to evaluate customer retention quality, revenue durability, and customer lifetime value across acquisition cohorts. Instead of reporting only topline sales performance, the solution reframes transactional data into a strategic customer-lifecycle view, enabling stakeholders to understand whether newly acquired customers remain active, sustain revenue contribution, and create sufficient long-term value to support profitable growth.

The dashboard is positioned as a leadership-facing analytics solution for retention, growth, and commercial strategy teams. It combines cohort-based customer tracking, revenue retention analysis, cumulative value progression, and lifetime value estimation to support sharper acquisition and lifecycle investment decisions.

---

## Business Context
In many retail and commerce environments, new customers are acquired continuously, but topline revenue alone does not reveal whether those customers are retained, monetized effectively, or converted into durable long-term value. This creates a strategic blind spot for leadership, because high acquisition volume does not always translate into healthy retention, profitable cohorts, or strong payback economics.

This project addresses that gap by organizing customers into monthly cohorts based on their first purchase month and tracking their behavior over time. The resulting analysis helps answer not just how much revenue was generated, but which cohorts stayed engaged, which cohorts retained spending power, and which cohorts produced the strongest customer lifetime value.

---

## Business Problem
Leadership needed a more strategic way to assess customer acquisition quality beyond total orders and sales volume. Specifically, the underlying business challenge was to determine whether newly acquired customers were remaining active after acquisition, sustaining revenue contribution over subsequent months, and generating enough long-term value to justify continued commercial investment.

### Executive Questions Solved
- Which acquisition cohorts demonstrate the strongest customer retention over time?
- Which cohorts maintain revenue contribution most effectively after the initial purchase month?
- Are newer cohorts outperforming or underperforming earlier cohorts in terms of monetization quality?
- Which cohorts generate the highest cumulative revenue and customer lifetime value?
- Do cohort-level lifetime value patterns support continued scaling of acquisition efforts under an assumed CAC benchmark?

---

## Purpose
The purpose of this dashboard is to convert raw transactional data into an executive decision system for **retention analytics and customer economics**. It enables leadership to measure how customer value evolves after acquisition by cohort, identify where retention decays, and evaluate whether the business is acquiring customers who create sustainable commercial value over time.

---

## Dataset
The project uses a transactional retail dataset structured around customer purchases, including customer identifiers, transaction dates, quantity, unit price, and derived order value fields used for cohort analysis. The video workflow also derives month-level purchase logic required to group customers into acquisition cohorts and to measure activity period by period after first purchase.

### Dataset Characteristics
- Transaction-level sales records with customer and date granularity.
- Month-based cohort logic derived from the first observed purchase month for each customer.
- Revenue-ready fields created to support retention, revenue retention, cumulative revenue, and CLV analysis.

---

## Data Preparation
Data preparation is performed in **Power Query**, where the transaction dataset is cleaned and shaped to support monthly cohort analysis. The tutorial workflow includes date standardization, month-level transformation logic, and preparation of revenue-ready fields for downstream DAX measures.

### Preparation Steps
- Cleaned and standardized the source transaction data for analytical use.
- Created an `OrderMonth` field to align purchases to monthly cohort periods.
- Prepared revenue fields required for retention and lifetime value calculations.
- Structured the model so customer first-purchase logic could be used to assign `CohortMonth` values.

---

## Data Model
The Power BI model is designed to support cohort-based lifecycle analysis rather than simple transactional reporting. It combines a transaction-level analysis table, a customer-level cohort mapping layer, and a Calendar table used for date logic and reporting consistency.

### Model Components
| Table / Layer | Role in Model |
|---|---|
| Main transaction table | Stores customer purchase activity, revenue fields, and month-level transaction logic. |
| Customer cohort table | Stores each customer's first purchase month as `CohortMonth` for cohort assignment. |
| Calendar table | Supports time logic, date relationships, and consistent monthly analysis. |

### Relationship Logic
- Customer-level cohort attribution is linked through `Customer ID`.
- Reporting date logic is supported through a relationship between the analysis table and the Calendar table.
- A cohort index is derived from the difference between transaction month and cohort month to measure lifecycle progression across months.

---

## DAX Measures
The dashboard relies on a focused set of business measures that convert cohort activity into executive-level retention and value signals. The video explicitly covers measures for customer counts, retention percentages, revenue persistence, cumulative revenue, customer lifetime revenue, and customer lifetime value.

### Core Measures Used
- `Cohort Size` — counts the number of customers in each original acquisition cohort.
- `Customers Active` — counts customers active in each subsequent cohort period.
- `Customer Retention %` — measures active customers against original cohort size.
- `Revenue in Period` — captures revenue generated in each cohort-period intersection.
- `Revenue Retention %` — compares subsequent-period revenue with month-0 revenue.
- `Cumulative Revenue` — accumulates revenue over the customer lifecycle by cohort.
- `CLR` (Customer Lifetime Revenue) — converts cumulative cohort revenue into per-customer lifetime revenue.
- `CLV` (Customer Lifetime Value) — estimates lifetime value using a 60% gross-margin assumption.

---

## Dashboard KPIs
The dashboard is organized around metrics that a leadership audience can use to assess customer acquisition quality and long-term cohort value creation.

### KPI Framework
- Cohort Size.
- Active Customers.
- Customer Retention %.
- Revenue by Cohort Period.
- Revenue Retention %.
- Cumulative Revenue.
- Customer Lifetime Revenue.
- Customer Lifetime Value.

These KPIs move the conversation from simple sales monitoring to a more strategic view of customer durability, monetization quality, and value realization after acquisition.

---

## Dashboard Design Logic
The dashboard follows a business-first analytical structure that can be communicated in an executive portfolio context as **Business Problem -> Cohort Analysis -> Executive Insights -> Commercial Action**.

### Design Narrative
1. **Acquisition Cohorts** — define the customer starting point based on first purchase month.
2. **Retention Analysis** — measure how customer participation changes over time.
3. **Revenue Durability** — evaluate whether retained cohorts continue to generate meaningful revenue.
4. **Value Realization** — track cumulative revenue and convert it into lifetime value signals.
5. **Commercial Action** — identify which cohort patterns justify scaling, optimization, or intervention.

---

## Visuals and Executive Interpretation

### 1) Customer Retention Matrix
**Business Question:** Which acquisition cohorts remain active over time, and where does customer participation decline most sharply after acquisition?

**Business Insight:** The retention matrix tracks customer activity month by month after each cohort’s acquisition point and reveals the natural drop-off pattern that follows month 0, while also highlighting where certain cohorts show more durable engagement than others.

**Executive Decision:** Focus lifecycle retention strategy on the first few post-acquisition months, where early drop-off becomes visible and where intervention can have the greatest commercial impact.

### 2) Customer Retention % Matrix
**Business Question:** Which cohorts are genuinely more “sticky” when normalized against their original cohort size?

**Business Insight:** Cohort retention percentage removes the distortion caused by different cohort sizes and enables like-for-like comparison of retention quality across acquisition periods.

**Executive Decision:** Prioritize customer acquisition sources, offers, or campaigns that produce smaller but more durable cohorts over channels that deliver scale with weak retention quality.

### 3) Revenue by Cohort Period Matrix
**Business Question:** Which cohorts continue to monetize effectively after acquisition, and how quickly does revenue contribution fade over time?

**Business Insight:** Revenue patterns across cohort periods show that customer count decline and revenue decline do not always move at the same pace, indicating that some retained cohorts continue to generate stronger spend per active customer.

**Executive Decision:** Investigate high-performing cohorts to identify commercial drivers such as product mix, campaign quality, timing, or customer profile characteristics that can be repeated at scale.

### 4) Revenue Retention % Matrix
**Business Question:** Are customer cohorts retaining spending power over time, rather than simply retaining customer presence?

**Business Insight:** Revenue retention highlights whether subsequent months are preserving, shrinking, or rebuilding cohort revenue relative to the acquisition month baseline, making it a more financially meaningful view of customer quality.

**Executive Decision:** Use revenue retention, not only headcount retention, as the key benchmark for lifecycle health when evaluating retention programs and post-acquisition monetization strategy.

### 5) CLR / CLV Cohort Matrix
**Business Question:** Which cohorts generate the strongest long-term economics, and do they create enough value to justify acquisition investment?

**Business Insight:** The dashboard converts cumulative revenue into customer lifetime revenue and then into CLV using a 60% gross-margin assumption, allowing leadership to compare cohort value creation against an assumed CAC benchmark discussed in the tutorial.

**Executive Decision:** Scale acquisition channels that generate faster CLV build-up and stronger payback characteristics, while reevaluating cohorts that lag in lifetime value creation.

---

## Executive Business Insights
- Customer acquisition performance should be judged not only by new customer volume, but by post-acquisition retention and value creation quality.
- Cohort analysis provides a clearer signal of sustainable growth than topline sales reporting alone.
- Revenue retention is often more strategically important than simple customer retention because it reflects the commercial health of retained cohorts.
- CLV-based cohort evaluation strengthens decision-making around acquisition efficiency, retention spending, and long-term growth prioritization.

---

## Actionable Business Recommendations
- Strengthen onboarding and early lifecycle engagement programs for the first months after acquisition, where retention decay is most visible.
- Benchmark acquisition channels not only by customer volume, but by downstream cohort retention and revenue retention performance.
- Identify high-performing cohorts and replicate the product, offer, pricing, or timing conditions that drove stronger monetization quality.
- Use CLV progression to inform acquisition budget allocation and prioritize cohorts that reach healthy payback faster.
- Monitor weak cohorts early to reduce spend on acquisition patterns that generate volume without durable economic value.

---

## Business Value Delivered
This solution delivers value by transforming raw transaction history into a strategic lens on customer quality, retention durability, and lifetime value generation. For an executive audience, the dashboard makes it possible to evaluate whether growth is being created through genuinely valuable customer acquisition or through short-lived revenue spikes with weak long-term economics.

In a portfolio context, the project demonstrates the ability to frame analytics around stakeholder decisions rather than just dashboard construction. It showcases business-oriented data modeling, DAX-based metric engineering, and the conversion of operational data into boardroom-ready performance narratives.

---

## Tools & Skills Used
- Power BI Desktop.
- Power Query.
- DAX.
- Data Modeling.
- Cohort Analysis.
- Retention Analytics.
- Customer Lifetime Value Modeling.
- Executive Dashboard Design.
- Business Storytelling and Insight Communication.

---
---


