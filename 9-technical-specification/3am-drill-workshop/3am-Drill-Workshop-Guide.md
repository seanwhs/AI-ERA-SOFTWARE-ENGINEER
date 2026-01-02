# 🕒 3 A.M. Drill Workshop Guide — AI‑Era System Owner

### **High-Pressure, Hands-On Training for AI-Augmented Systems**

> **Purpose:** Equip engineers to **diagnose, remediate, and harden systems** under realistic failure conditions, emphasizing **human-first investigation** and **AI-assisted remediation**.

---

## 1️⃣ Workshop Overview

**Duration:** 180 Minutes | **Format:** Simulation + Supervised AI Implementation + Reflection
**Participants:** 6–12 engineers per cohort
**Instructor Ratio:** 1:6 recommended

**Learning Goals:**

1. Diagnose complex system failures **without AI first**.
2. Apply AI-assisted solutions responsibly **after root cause verification**.
3. Strengthen system observability, reliability, and post-mortem documentation.
4. Build **muscle memory for crisis investigation**, including cross-service tracing.

---

## 2️⃣ Workshop Agenda

| Time      | Activity                                                                                                                                                                                                                                            |
| --------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 0:00–0:10 | **Welcome & Orientation** – Explain workshop goals, safety rules, team assignment, overview of scenarios.                                                                                                                                           |
| 0:10–0:15 | **Tea Break / Setup** – Ensure all workstations, dashboards, and AI tooling are ready.                                                                                                                                                              |
| 0:15–1:00 | **Phase 1: Alerting & Dark Room Investigation** – **Human-only troubleshooting**. Teams investigate the following: <br>• Floating-Point Drift <br>• Circular Dependency Deadlock <br>• N+1 Query Storm                                              |
| 1:00–1:10 | **Tea Break** – Quick refresh, share early observations among teams.                                                                                                                                                                                |
| 1:10–1:50 | **Phase 2: Deep Dive Investigation & Verification** – Teams analyze: <br>• Logs, metrics, trace IDs <br>• Stress testing / replication of failures <br>• Verification of hypothesized root causes                                                   |
| 1:50–2:00 | **Tea Break** – Hydrate and reset mental context.                                                                                                                                                                                                   |
| 2:00–2:30 | **Phase 3: AI-Assisted Fix Implementation** – Teams leverage AI for: <br>• FP Drift → Decimal replacement + idempotency checks <br>• Circular Deadlock → Circuit breakers / async refactor <br>• N+1 Storm → Batch queries, async handling, caching |
| 2:30–2:50 | **Phase 4: Post-Mortem & Spec Update** – Teams update: <br>• System spec templates <br>• PR guardrails <br>• Lessons learned                                                                                                                        |
| 2:50–3:00 | **Wrap-Up & Metrics Review** – Debrief, discuss failures and successes, reinforce learning objectives.                                                                                                                                              |

---

## 3️⃣ Drill Scenarios (Expanded)

### 3.1 Floating-Point Drift — Billing Engine

**Fault:** Float arithmetic causes subtle precision drift.
**Objectives:**

* Detect drift.
* Replace `float` with `Decimal`.
* Validate idempotency and cumulative totals.

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

---

### 3.2 Circular Dependency Deadlock — Microservices

**Fault:** `ServiceA → ServiceB → ServiceC → ServiceA` circular calls; deadlock under load.
**Objectives:**

* Detect circular chain.
* Implement circuit breakers or async queues.

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

*(ServiceB & ServiceC similar.)*

---

### 3.3 Latency Amplification / N+1 Query Storm — REST API

**Fault:** N+1 queries + blocking external API calls; P95/P99 latency spikes.
**Objectives:**

* Detect N+1 queries.
* Batch requests, implement async/caching.

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

---

## 4️⃣ Workshop Timeline 

```
0:00 ──► WELCOME & ORIENTATION
  Goals, rules, team assignment
0:10 ──► TEA BREAK / SETUP
0:15 ──► PHASE 1: DARK ROOM INVESTIGATION
  Human-only troubleshooting
    ├─ Floating-Point Drift → Detect float vs Decimal
    ├─ Circular Deadlock → Trace A→B→C→A
    └─ N+1 Storm → Identify N+1 loops & blocking calls
1:00 ──► TEA BREAK
1:10 ──► PHASE 2: DEEP DIVE & VERIFICATION
  Analyze logs, metrics, trace IDs
  Stress testing / replication
1:50 ──► TEA BREAK
2:00 ──► PHASE 3: AI-ASSISTED FIX IMPLEMENTATION
    ├─ FP Drift → Decimal fix + idempotency check
    ├─ Circ Deadlock → Circuit breakers / async queue
    └─ N+1 Storm → Batch / async refactor + caching
2:30 ──► PHASE 4: POST-MORTEM & SPEC UPDATE
    └─ Update Team Spec Template, PR guardrails, lessons learned
2:50 ──► WRAP-UP & METRICS REVIEW
3:00 ──► WORKSHOP COMPLETE
```

---

### ✅ Success Metrics

* Root cause identified **within 40 minutes** of human investigation.
* Spec guardrails implemented (Decimal, circuit breakers, async/batch handling).
* Fixes verified via stress testing, latency SLAs, idempotency.
* Observability: logs & trace_ids fully correlate request flows.

---

### 🔹 Instructor Notes

1. Rotate scenarios to maintain **adversarial thinking**.
2. Emphasize **manual tracing before AI-assisted remediation**.
3. Reinforce **post-mortem spec updates**.
4. Encourage **failure-mode mindset**; AI is a tool, humans own production.
5. Use tea breaks as **reflection points**—teams can discuss approaches, early mistakes, or strategies.

---

