# Supply Chain Management – Practitioner Cheat Sheet

> **Purpose**: A no-nonsense, end-to-end Supply Chain cheat sheet.
> Built for **analytics**, **planning**, **control towers**, and **agentic AI systems**.
> Practical, metric-driven, and decision-oriented.
> Designed to be **copy-paste usable in interviews, projects, and dashboards**.

---

## 1. Supply Chain Mental Model (Fix This First)

Supply Chain is a **flow system**, not a department.

Flows involved:

* **Material flow** (physical goods)
* **Information flow** (orders, forecasts, signals)
* **Cash flow** (payments, working capital)

If any one flow is broken, the system degrades.

---

## 2. Core Supply Chain Stages (End-to-End)

```text
Supplier → Manufacturing → Warehousing → Distribution → Retail/Customer
```

Key rule: **Local optimization breaks global performance**.

---

## 3. Demand Management (Where Most Errors Start)

### Demand Types

* Independent demand (customer-driven)
* Dependent demand (BOM-driven)

### Key Metrics

* Forecast Accuracy (%)
* Bias
* MAPE / WAPE
* Demand Variability (CV)

### Baseline Formula

```text
Forecast Error = Actual − Forecast
Bias = Avg(Forecast Error)
```

---

## 4. Forecasting Levels (Critical Design Choice)

* SKU
* SKU × Location
* SKU × Customer
* SKU × Channel

Higher granularity = higher noise.
Aggregate only when decision allows it.

---

## 5. Inventory Fundamentals (Non-Negotiable)

### Inventory Types

* Cycle Stock
* Safety Stock
* Pipeline Stock
* Buffer Stock

### Core Metrics

* Inventory Turns
* Days of Inventory (DOI)
* Fill Rate
* Stockout Rate

---

## 6. Safety Stock (Must Know)

### Classical Formula

```text
Safety Stock = Z × σLT
```

Where:

* Z = service level factor
* σLT = demand variability during lead time

Wrong safety stock destroys margins.

---

## 7. Service Levels (Business Decision, Not Math)

* Cycle Service Level (CSL)
* Fill Rate

Higher service level = exponentially higher inventory.

---

## 8. Replenishment Logic

### Reorder Point (ROP)

```text
ROP = Avg Demand × Lead Time + Safety Stock
```

### Replenishment Models

* Min–Max
* Periodic Review
* Continuous Review

---

## 9. Lead Time (Silent Killer)

Components:

* Order processing
* Production
* Transit
* Receiving

Lead time variability hurts more than long lead time.

---

## 10. Manufacturing Planning

### Planning Levels

* Strategic (network design)
* Tactical (capacity planning)
* Operational (scheduling)

### Key Metrics

* Capacity Utilization
* Throughput
* Yield
* OEE

---

## 11. Distribution & Logistics

### Transport Modes

* Road
* Rail
* Sea
* Air

### Metrics

* Cost per unit
* On-Time In-Full (OTIF)
* Transit Time Variance

---

## 12. Warehousing Basics

### Activities

* Inbound
* Putaway
* Storage
* Picking
* Packing
* Dispatch

### Metrics

* Pick Accuracy
* Dock-to-Stock Time
* Space Utilization

---

## 13. Network Design (High Impact, Rarely Done)

Decisions:

* Number of warehouses
* Warehouse locations
* Flow paths

Tools:

* Center of Gravity
* Optimization models

---

## 14. Bullwhip Effect (Classic Failure Mode)

Causes:

* Forecast smoothing
* Batch ordering
* Promotions
* Poor information sharing

Fix with:

* Shorter cycles
* Better visibility
* Demand sensing

---

## 15. Risk Management

Risk Types:

* Supplier risk
* Transport risk
* Demand shocks
* Geopolitical risk
* Cyber risk

Mitigation:

* Dual sourcing
* Buffers
* Scenario planning

---

## 16. Supply Chain KPIs (Executive Set)

* OTIF
* Inventory Turns
* Service Level
* Forecast Accuracy
* Cost-to-Serve
* Working Capital

Dashboards without actions are useless.

---

## 17. Control Tower Concept

A Control Tower provides:

* End-to-end visibility
* Alerts and exceptions
* Scenario simulation
* Decision support

Not just visualization. **Decision amplification**.

---

## 18. Data Model (Analytics Ready)

Fact tables:

* Sales
* Inventory
* Shipments

Dimensions:

* SKU
* Location
* Time
* Customer

Garbage data in = confident wrong decisions out.

---

## 19. Digital & AI in Supply Chain

High-value use cases:

* Demand sensing
* Inventory optimization
* ETA prediction
* Risk scoring
* Scenario simulation

AI without process clarity fails.

---

## 20. Common Anti-Patterns (Stop These)

* Forecast accuracy obsession without bias check
* Excess safety stock as a band-aid
* KPI overload
* Siloed planning
* Excel-only planning at scale

---

## 21. Absolute Emergency Formulas

```text
Inventory Turns = COGS / Avg Inventory
DOI = 365 / Inventory Turns
Fill Rate = Fulfilled Demand / Total Demand
```

---

## 22. Mental Model to Remember

> Supply Chain is about **trade-offs**, not perfection.
> Visibility without action is theater.
> Planning without execution feedback is fantasy.

---

**If your supply chain feels unstable, the problem is usually variability, not volume.**
