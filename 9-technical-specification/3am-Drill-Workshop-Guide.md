# 🕒 3 A.M. Drill Workshop Guide — AI‑Era System Owner

### **High-Pressure, Hands-On Training for AI-Augmented Systems**

> **Purpose:** Equip engineers to **diagnose, remediate, and harden systems** under realistic failure conditions, emphasizing **human-first investigation** and **AI-assisted remediation**.

---

## 1️⃣ Drill Overview

**Duration:** 60 Minutes | **Format:** Simulation + Supervised AI Implementation

**Workflow:**

1. **Alerting (0:00–0:05)** – Pager / Metrics spike; display dashboards.
2. **Dark Room Investigation (0:05–0:30)** – **No AI**; human traces root cause.
3. **AI-Assisted Fix (0:30–0:45)** – AI enabled **only to implement fixes** based on verified root cause.
4. **Post-Mortem & Spec Update (0:45–1:00)** – Update specs, PR guardrails, and lessons learned.

---

## 2️⃣ Drill Scenarios

### 2.1 Floating-Point Drift — Billing Engine

* **Fault:** float arithmetic causes subtle precision drift.
* **Objective:** Detect drift, replace `float` with `Decimal`, validate idempotency.

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

### 2.2 Circular Dependency Deadlock — Microservices

* **Fault:** `ServiceA → ServiceB → ServiceC → ServiceA` circular calls; deadlock under load.
* **Objective:** Detect circular chain; implement circuit breakers or async queues.

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

*(ServiceB & ServiceC similar, completing circular chain.)*

### 2.3 Latency Amplification / N+1 Query Storm — REST API

* **Fault:** N+1 queries + blocking external API calls; P95/P99 latency spikes.
* **Objective:** Detect N+1 queries, batch requests, implement async/caching.

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

## 3️⃣ 3 A.M. Drill Timeline & ASCII Diagram

```
0:00 ──► ALERTING PHASE
  Pager / Metrics Spike / Dashboard
       │
0:05 ──► DARK ROOM INVESTIGATION (HUMAN ONLY)
       │
       ├─ Floating-Point Drift → Detect float vs Decimal
       ├─ Circular Deadlock → Trace A→B→C→A
       └─ N+1 Storm → Identify N+1 loops & blocking calls
       │
0:30 ──► AI-ASSISTED FIX PHASE
       │
       ├─ FP Drift → Decimal fix + idempotency check
       ├─ Circ Deadlock → Circuit breakers / async queue
       └─ N+1 Storm → Batch / async refactor + caching
       │
0:45 ──► POST-MORTEM & SPEC UPDATE
       │
       └─ Update Team Spec Template, PR guardrails, lessons learned
0:60 ──► DRILL COMPLETE
```

### ✅ Success Metrics

* Root cause identified within 20 minutes.
* Spec guardrails implemented (Decimal, circuit breakers, async/batch handling).
* Fixes verified via stress testing, latency SLAs, idempotency.
* Observability: logs & trace_ids fully correlate request flows.

---

### 🔹 Instructor Notes

1. Rotate scenarios to maintain **adversarial thinking**.
2. Emphasize **manual tracing before AI-assisted remediation**.
3. Reinforce **post-mortem spec updates**.
4. Encourage **failure-mode mindset**; AI is a tool, humans own production.
