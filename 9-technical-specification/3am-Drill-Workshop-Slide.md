# 🕒 3 A.M. Drill Workshop — Slide Outline

---

## **Slide 1 — Workshop Title & Goals**

**🕒 3 A.M. Drill: AI‑Era System Owner**

**Purpose:**
Equip engineers to **diagnose, remediate, and harden systems** under realistic failures using **human-first investigation + AI-assisted fixes**.

**Learning Goals:**

* Root cause identification under pressure
* Responsible AI-assisted remediation
* Strengthened observability and spec updates
* Crisis investigation muscle memory

---

## **Slide 2 — Workshop Agenda (180 Min)**

| Time      | Activity                                                                 |
| --------- | ------------------------------------------------------------------------ |
| 0:00–0:10 | **Welcome & Orientation** – Goals, rules, team setup                     |
| 0:10–0:15 | **Tea Break / Setup** – Dashboards & AI tooling ready                    |
| 0:15–1:00 | **Phase 1: Dark Room Investigation** – Human-only troubleshooting        |
| 1:00–1:10 | **Tea Break** – Share early observations                                 |
| 1:10–1:50 | **Phase 2: Deep Dive & Verification** – Logs, trace IDs, stress testing  |
| 1:50–2:00 | **Tea Break** – Hydrate & reset mental context                           |
| 2:00–2:30 | **Phase 3: AI-Assisted Fix Implementation** – Apply verified fixes       |
| 2:30–2:50 | **Phase 4: Post-Mortem & Spec Update** – Update team spec, PR guardrails |
| 2:50–3:00 | **Wrap-Up & Metrics Review** – Debrief, discuss lessons learned          |

---

## **Slide 3 — Workshop Phases (Visual Flow)**

```
0:15 ──► PHASE 1: DARK ROOM INVESTIGATION
  Human-only troubleshooting
      ├─ FP Drift → Detect float vs Decimal
      ├─ Circular Deadlock → Trace A→B→C→A
      └─ N+1 Storm → Identify N+1 loops & blocking calls
1:10 ──► PHASE 2: DEEP DIVE & VERIFICATION
      ├─ Logs, metrics, trace IDs
      ├─ Stress testing & replication
      └─ Root cause verification
2:00 ──► PHASE 3: AI-ASSISTED FIX IMPLEMENTATION
      ├─ FP Drift → Decimal fix + idempotency
      ├─ Circ Deadlock → Circuit breakers / async queue
      └─ N+1 Storm → Batch / async refactor + caching
2:30 ──► PHASE 4: POST-MORTEM & SPEC UPDATE
      └─ Update spec template, PR guardrails, lessons learned
2:50 ──► WRAP-UP & METRICS REVIEW
```

---

## **Slide 4 — Scenario 1: Floating-Point Drift**

**Fault:** Float arithmetic causes subtle precision drift.

**Objectives:**

* Detect drift
* Replace `float` with `Decimal`
* Validate idempotency

**Sample Code:**

```python
# ⚠️ Float used instead of Decimal
running_total = sum(t.amount for t in TRANSACTIONS_DB) + tx.amount
```

**Visual Aid:**

* **Graph:** Running total drift over time (pre/post fix)
* **Highlight:** Trace IDs for verification

---

## **Slide 5 — Scenario 2: Circular Dependency Deadlock**

**Fault:** Service circular calls → deadlock under load
**Objectives:**

* Detect circular chain: `A→B→C→A`
* Implement circuit breakers / async queues

**Visual Aid:**

```
ServiceA → ServiceB → ServiceC → ServiceA (Deadlock)
```

**Tip:** Highlight **call trace logs & timeouts**

---

## **Slide 6 — Scenario 3: N+1 Query / Latency Storm**

**Fault:** N+1 queries + blocking external API calls → latency spikes

**Objectives:**

* Detect N+1 loops
* Batch requests / async / caching

**Visual Aid:**

* Table of queries per user → latency impact
* Diagram: Sequential calls → batched calls → async handling

---

## **Slide 7 — Tea Break Reflection**

**Questions for Teams:**

* What early signals did you observe?
* Which tracing methods were most effective?
* Any assumptions that delayed root cause detection?

**Purpose:** Reinforce **reflection & peer learning**

---

## **Slide 8 — Success Metrics**

* Root cause identified **within 40 min human-only investigation**
* Spec guardrails implemented: Decimal, circuit breakers, async/batch handling
* Fixes verified via stress tests & latency SLAs
* Logs & trace_ids fully correlate request flows

**Visual Aid:** KPI Dashboard Mockup:

* FP Drift Accuracy
* Deadlock Resolution
* N+1 Latency Before/After

---

## **Slide 9 — Instructor Notes**

* Rotate scenarios for **adversarial thinking**
* Emphasize **manual tracing first**
* Reinforce **post-mortem updates**
* Tea breaks as **reflection checkpoints**
* Encourage **failure-mode mindset**: AI is a tool; humans own production

---

