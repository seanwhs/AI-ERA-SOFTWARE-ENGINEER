# 🕒 3 A.M. Drill Workshop — Slide Outline 

---

## **Slide 1 — Workshop Title & Goals**

**🕒 3 A.M. Drill: AI‑Era System Owner**

**Purpose:**
Equip engineers to **diagnose, remediate, and harden systems** under realistic failure conditions using **human-first investigation + AI-assisted fixes**.

**Learning Goals:**

* Identify **root cause under pressure**, including red herrings
* Apply **AI responsibly** after verifying hypotheses
* Strengthen **observability & spec updates**
* Build **crisis investigation muscle memory**
* Learn **adversarial thinking**: distinguish symptoms vs root cause

**Visual Idea:** Clock at 3AM with stressed engineer + AI assistant icon

---

## **Slide 2 — Workshop Agenda (180 Min)**

| Time      | Activity                                                                                      |
| --------- | --------------------------------------------------------------------------------------------- |
| 0:00–0:10 | **Welcome & Orientation** – Goals, rules, team setup                                          |
| 0:10–0:15 | **Tea Break / Setup** – Dashboards, logs, AI tooling ready                                    |
| 0:15–1:00 | **Phase 1: Dark Room Investigation** – Human-only troubleshooting                             |
| 1:00–1:10 | **Tea Break** – Share early observations                                                      |
| 1:10–1:50 | **Phase 2: Deep Dive & Verification** – Logs, metrics, trace IDs, stress testing              |
| 1:50–2:00 | **Tea Break** – Hydrate & reset mental context                                                |
| 2:00–2:30 | **Phase 3: AI-Assisted Fix Implementation** – Apply verified fixes, compare human vs AI paths |
| 2:30–2:50 | **Phase 4: Post-Mortem & Spec Update** – Update team spec, PR guardrails, IaC drift           |
| 2:50–3:00 | **Wrap-Up & Metrics Review** – Debrief, discuss lessons learned, KPIs                         |

**Visual Idea:** Timeline with colored phases (Human-only / AI / Post-mortem)

---

## **Slide 3 — Workshop Phases (Flow Diagram)**

```
0:15 ──► PHASE 1: DARK ROOM INVESTIGATION
  • Human-only troubleshooting
      ├─ FP Drift → Detect float vs Decimal
      ├─ Circular Deadlock → Trace A→B→C→A
      ├─ N+1 Storm → Identify loops & blocking calls
      └─ Red Herring → Background CPU spike

1:10 ──► PHASE 2: DEEP DIVE & VERIFICATION
  • Logs, metrics, trace IDs, business-level metrics
  • Stress testing & replication
  • Root cause verification

2:00 ──► PHASE 3: AI-ASSISTED FIX IMPLEMENTATION
  • FP Drift → Decimal fix + idempotency
  • Circ Deadlock → Circuit breakers / async queue
  • N+1 Storm → Batch / async refactor + caching
  • Compare Human vs Shadow AI path

2:30 ──► PHASE 4: POST-MORTEM & SPEC UPDATE
  • Update spec templates, PR guardrails
  • Blameless post-mortem & Five Whys
  • IaC drift correction
2:50 ──► WRAP-UP & METRICS REVIEW
```

**Visual Idea:** Swimlane diagram with Human / AI / Tools lanes

---

## **Slide 4 — Scenario 1: Floating-Point Drift**

**Fault:** Float arithmetic → subtle cumulative drift
**Objectives:** Detect drift, replace `float` with `Decimal`, validate idempotency

**Visual Aid:**

* Graph: Running total drift over time (pre/post fix)
* Trace ID correlation for each transaction

**Enhancements:**

* Inject partial transaction failures or delayed processing
* Map business metrics (`checkout_failure_total`) to logs

**Sample Code Snippet:**

```python
# ⚠️ Float used instead of Decimal
running_total = sum(t.amount for t in TRANSACTIONS_DB) + tx.amount
```

---

## **Slide 5 — Scenario 2: Circular Dependency Deadlock**

**Fault:** Service circular calls → deadlock under load
**Objectives:** Detect circular chain, implement circuit breakers / async queues

**Visual Aid:**

```
ServiceA → ServiceB → ServiceC → ServiceA
```

**Enhancements:**

* Visualize with service graph (Honeycomb/Kiali)
* Network partition injection: ServiceC unreachable → ServiceA timeout

**Tip:** Highlight **trace logs & timeout propagation**

---

## **Slide 6 — Scenario 3: N+1 Query / Latency Storm**

**Fault:** N+1 queries + blocking API calls → latency spikes
**Objectives:** Detect N+1 loops, batch requests, async / caching

**Visual Aid:**

* Table: Queries per user → latency impact
* Diagram: Sequential calls → batched calls → async handling

**Enhancements:**

* Track `p95`/`p99` latency metrics in Prometheus
* Add external API latency injection (chaos engineering)

---

## **Slide 7 — Scenario 4: Red Herring**

**Fault:** Background worker CPU spike, unrelated to main outage
**Objective:** Teach **symptom vs root cause differentiation**

**Visual Aid:** Alert graph showing misleading spike
**Discussion Prompt:** “Was this the cause or just noise?”

---

## **Slide 8 — Tea Break Reflection**

**Questions for Teams:**

* Early signals noticed?
* Most effective tracing methods?
* Assumptions that delayed root cause detection?
* How did business-level metrics help?

**Purpose:** Reinforce **reflection & peer learning**

---

## **Slide 9 — Success Metrics**

* Root cause identified **within 40 min human-only investigation**
* Spec guardrails implemented (Decimal, circuit breakers, async/batch)
* Fixes verified via stress tests & latency SLAs
* Observability: logs & trace IDs fully correlate request flows

**Visual Aid:** KPI Dashboard Mockup

* FP Drift Accuracy
* Deadlock Resolution
* N+1 Latency Before/After

---

## **Slide 10 — AI Workflow Integration**

* Automated Runbook Generation (LLM-based)
* Log-to-Prompt Pipeline → AI diagnosis suggestion
* Shadow AI On-Call → Compare time-to-resolution vs humans
* Lessons: strengths & limits of AI in production crisis

**Visual Idea:** Parallel lane diagram Human vs AI

---

## **Slide 11 — Instructor Notes**

* Rotate scenarios to maintain **adversarial thinking**
* Emphasize **manual tracing before AI-assisted remediation**
* Reinforce **post-mortem updates** & Five Whys
* Tea breaks as **reflection checkpoints**
* Encourage **failure-mode mindset**: humans own production, AI is a tool

---

## **Slide 12 — Scenario Difficulty Levels (Optional)**

| Level | Description                                               |
| ----- | --------------------------------------------------------- |
| 1     | Intern: process crash, simple restart                     |
| 2     | Junior: OOM / memory leak                                 |
| 3     | Senior: Upstream API failure, no fallback/circuit breaker |
| 4     | Staff: Silent data corruption, system green but incorrect |

**Purpose:** Support progressive cohorts & repeatable challenges

---

