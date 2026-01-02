# 🕒 3 A.M. Drill Workshop Guide — AI‑Era System Owner

### **High-Pressure, Hands-On Training for AI-Augmented Systems**

> **Purpose:** Equip engineers to **diagnose, remediate, and harden systems** under realistic failure conditions, emphasizing **human-first investigation**, **AI-assisted remediation**, and **post-mortem governance**.

---

## 1️⃣ Workshop Overview

**Duration:** 180 Minutes | **Format:** Simulation + Supervised AI Implementation + Reflection
**Participants:** 6–12 engineers per cohort
**Instructor Ratio:** 1:6 recommended

**Learning Goals:**

1. Diagnose complex system failures **without AI first**, reinforcing human-first troubleshooting.
2. Apply AI-assisted solutions responsibly **after root cause verification**.
3. Strengthen **system observability**, reliability, and post-mortem documentation.
4. Build **muscle memory for crisis investigation**, including cross-service tracing and business-level metrics analysis.
5. Recognize **symptoms vs. root causes**, including red herrings.

**Success Metrics:**

* Root cause identified **within 40 minutes** of human investigation.
* Fixes verified via stress testing, latency SLAs, and idempotency checks.
* Observability: logs, trace IDs, and metrics fully correlate request flows.
* Post-mortem completed with **blameless analysis, "Five Whys", and prevention plans**.

---

## 2️⃣ Workshop Agenda

| Time      | Activity                                                                                                                                                                                                                                                     |
| --------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| 0:00–0:10 | **Welcome & Orientation** – Goals, safety rules, team assignments, overview of scenarios.                                                                                                                                                                    |
| 0:10–0:15 | **Setup Check / Tea Break** – Verify dashboards, logs, AI tooling, and workstations.                                                                                                                                                                         |
| 0:15–1:00 | **Phase 1: Human-Only Troubleshooting ("Find It")** – Teams investigate: <br>• Floating-Point Drift <br>• Circular Dependency Deadlock <br>• N+1 Query Storm <br>• Red Herring: Background worker CPU spike                                                  |
| 1:00–1:10 | **Tea Break** – Discuss early observations, share hypotheses.                                                                                                                                                                                                |
| 1:10–1:50 | **Phase 2: Deep Dive & Verification ("Cause")** – Teams analyze: <br>• Logs, metrics, trace IDs, business-level metrics <br>• Stress test / reproduce failures <br>• Correlate alerts vs root cause                                                          |
| 1:50–2:00 | **Tea Break** – Hydrate, reflect, prep for AI-assisted phase.                                                                                                                                                                                                |
| 2:00–2:30 | **Phase 3: AI-Assisted Fix Implementation ("Fix It")** – Leverage AI for: <br>• Decimal replacement + idempotency <br>• Circuit breakers / async refactor <br>• Batch / async / caching optimization <br>• Compare human vs AI resolution path ("Shadow AI") |
| 2:30–2:50 | **Phase 4: Post-Mortem & Spec Update ("Govern")** – Teams update: <br>• System spec templates <br>• PR guardrails <br>• IaC drift fixes <br>• Lessons learned & Five Whys analysis                                                                           |
| 2:50–3:00 | **Wrap-Up & Metrics Review** – Debrief, discuss failures, successes, and learning outcomes.                                                                                                                                                                  |

---

## 3️⃣ Drill Scenarios (Expanded)

### 3.1 Floating-Point Drift — Billing Engine

**Fault:** Float arithmetic causes subtle precision drift.
**Objectives:** Detect drift, replace `float` with `Decimal`, validate idempotency and cumulative totals.

```python
# billing_service.py
import logging, random, uuid
from decimal import Decimal
from datetime import datetime

logger = logging.getLogger("billing_service")

class Transaction:
    def __init__(self, user_id: str, amount: float):
        self.user_id = user_id
        self.amount = amount  # ⚠️ Float used instead of Decimal
        self.timestamp = datetime.utcnow()
        self.trace_id = str(uuid.uuid4())

TRANSACTIONS_DB = []

def process_transaction(user_id: str, amount: float):
    tx = Transaction(user_id, amount)
    logger.info(f"[{tx.trace_id}] Processing: {user_id} -> {amount:.2f}")
    running_total = sum(t.amount for t in TRANSACTIONS_DB) + tx.amount
    TRANSACTIONS_DB.append(tx)
    logger.info(f"[{tx.trace_id}] Running total: {running_total:.6f}")
    return running_total
```

**Enhancements:**

* Correlate `trace_id` across logs with Prometheus metrics like `billing_failure_total`.
* Introduce latency or partial failures in a subset of transactions to mimic real-world drift detection.

---

### 3.2 Circular Dependency Deadlock — Microservices

**Fault:** `ServiceA → ServiceB → ServiceC → ServiceA` circular calls; deadlock under load.
**Objectives:** Detect circular chain, implement circuit breakers or async queues.

```python
# service_a.py
import logging, requests, time
logger = logging.getLogger("ServiceA")

def call_b(data):
    return requests.post("http://localhost:5002/service_b", json=data, timeout=5).json()

def handle_request(data):
    time.sleep(0.1)
    return call_b(data)
```

**Enhancements:**

* Visualize service calls with Kiali/Honeycomb; include hidden upstream dependencies.
* Introduce **network partition** to complicate detection.

---

### 3.3 Latency Amplification / N+1 Query Storm — REST API

**Fault:** N+1 queries + blocking external API calls; P95/P99 latency spikes.
**Objectives:** Detect N+1 queries, batch requests, implement async/caching.

```python
# orders_service.py
import logging, time, random
logger = logging.getLogger("orders_service")
USERS_DB = [{"id": i} for i in range(1, 101)]
ORDERS_DB = [{"user_id": u["id"], "order_total": random.randint(10, 100)} for u in USERS_DB]

def fetch_user_orders(user_id):
    orders = []
    for order in ORDERS_DB:
        if order["user_id"] == user_id:
            time.sleep(0.01)  # Simulated external call
            orders.append(order)
    return {"user_id": user_id, "orders": orders}

def handle_batch(user_ids):
    return [fetch_user_orders(uid) for uid in user_ids]
```

**Enhancements:**

* Include business metrics like `p99_latency_seconds` for monitoring spikes.
* Inject artificial API latency for a more realistic 3 AM scenario.

---

### 3.4 Red Herring — Background Worker CPU Spike

**Fault:** Background job consumes CPU; unrelated to API outage.
**Objective:** Teach engineers to distinguish **symptoms vs root cause**.

---

## 4️⃣ Observability & Chaos Enhancements

* **Structured Logging:** Include `trace_id`, `span_id`, request metadata.
* **Custom Metrics:** Business-level Prometheus metrics.
* **Service Graph:** Visualize multi-hop dependencies.
* **Chaos Injection:** Latency, network partition, log disk full.

---

## 5️⃣ AI Workflow Integration

* **Automated Runbook Generation:** Use AI to draft runbook from spec.
* **Log-to-Prompt Pipeline:** Feed logs/events to AI for suggested diagnosis.
* **Shadow AI On-Call:** Compare human vs AI response; evaluate fix quality.

---

## 6️⃣ Post-Mortem & Governance

* **Blameless Analysis:** Track detection vs resolution time.
* **Five Whys Analysis:** Root cause dissection.
* **IaC Drift Detection:** Ensure fixes propagate to Terraform/CloudFormation.
* **Prevention Plan:** Update alerting rules, dashboards, and spec guardrails.

---

## 7️⃣ Instructor Notes

1. Rotate scenarios to maintain **adversarial thinking**.
2. Emphasize **manual tracing before AI-assisted remediation**.
3. Reinforce **post-mortem spec updates**.
4. Encourage **failure-mode mindset**; humans own production.
5. Use tea breaks as **reflection points**—discuss strategies, mistakes, or early observations.

---

## 8️⃣ Scenario Difficulty Levels (Optional)

| Level | Description                                                  |
| ----- | ------------------------------------------------------------ |
| 1     | Intern: process crash, simple restart.                       |
| 2     | Junior: OOM killer or memory leak.                           |
| 3     | Senior: Upstream API failure, no fallback/circuit breaker.   |
| 4     | Staff: Silent data corruption, system "Green" but incorrect. |

---

