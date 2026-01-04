# 🕒 **3 A.M. Drill Workshop — AI-Era System Owner**

**Objective:**
Simulate a high-pressure production incident to train engineers in diagnosing failures, applying AI-assisted fixes, and executing effective post-mortem analysis. The focus is on **human-first troubleshooting**, **AI integration**, and **resilient system observability**.

**Duration:** 180 minutes
**Cohort Size:** 6-12 engineers per cohort
**Instructor Ratio:** 1:6

---

## 1️⃣ **Workshop Overview**

The **3 A.M. Drill** is designed to simulate a crisis where engineers must diagnose and resolve complex system failures under time pressure. The workshop provides hands-on experience with both **human-first investigative methods** and **AI-assisted remediation**.

### **Learning Objectives:**

1. **Human-First Troubleshooting**
   Develop the skill to independently diagnose failures before relying on AI, focusing on **log analysis**, **trace correlation**, and **system behavior**.

2. **AI-Aided Resolution**
   Utilize AI tools to enhance the speed and accuracy of problem-solving. Ensure that AI recommendations are **vetted** and **validated** by engineers.

3. **Observability and Metrics**
   Practice using **observability tools** (e.g., logs, metrics, tracing) to gather insights during incident investigations, emphasizing the importance of **end-to-end system visibility**.

4. **Post-Mortem and Preventive Action**
   Conduct a **blameless post-mortem** to analyze the incident, identify root causes, and update system specifications to prevent recurrence.

### **Success Metrics:**

* **Root Cause Identification:** Within 40 minutes of human troubleshooting.
* **Resolution Success Rate:** 100% successful fixes, validated through tests.
* **AI Assistance Accuracy:** At least 90% successful AI-generated fixes.
* **Observability Coverage:** Logs, metrics, and traces fully correlated for the entire incident flow.
* **Time-to-Resolution (TTR):** Target is less than 60 minutes from detection to fix.

---

## 2️⃣ **Workshop Agenda**

| Time      | Phase                                   | Activity                                                           | Facilitator Notes                                            |
| --------- | --------------------------------------- | ------------------------------------------------------------------ | ------------------------------------------------------------ |
| 0:00–0:10 | **Orientation**                         | Welcome, objectives, rules, team roles                             | Set expectations, emphasize **human-first mindset**          |
| 0:10–0:15 | **Setup**                               | Verify environments, dashboards, and workstations                  | Ensure all tools (logs, AI tools, etc.) are active           |
| 0:15–1:00 | **Phase 1: Human-Only Troubleshooting** | Teams investigate system failures using logs, metrics, and traces  | Encourage deep diving, **no AI assistance yet**              |
| 1:00–1:10 | **Tea Break**                           | Reflection, discuss early hypotheses and challenges                | Share observations, refine investigative approach            |
| 1:10–1:50 | **Phase 2: Deep Dive Verification**     | Validate hypotheses, correlate logs with traces, run tests         | Ensure team members verify causes before using AI            |
| 1:50–2:00 | **Tea Break**                           | Reflect, reset, prepare for AI-assisted phase                      | Discuss the AI role in remediation                           |
| 2:00–2:30 | **Phase 3: AI-Assisted Fix**            | Apply AI-assisted fixes (e.g., refactor code, optimize queries)    | Ensure fixes are validated by human review before committing |
| 2:30–2:50 | **Phase 4: Post-Mortem & Spec Update**  | Update spec templates, PR guardrails, and document lessons learned | Focus on **blameless post-mortem** and preventable action    |
| 2:50–3:00 | **Wrap-Up**                             | Review KPIs, share feedback, and plan next steps                   | Evaluate the performance and lessons learned                 |

---

## 3️⃣ **Scenarios Overview**

### 3.1 **Floating-Point Drift — Billing Engine**

**Fault:**
Subtle float precision drift accumulates in billing calculations.

**Key Observables:**

* Running total drift over time
* Inconsistent billing totals

**Challenge:**
Detect and replace `float` with `Decimal` to ensure precision and **validate idempotency**.

**Solution Steps:**

* Identify **trace ID correlations** across logs.
* Use **metrics** to track drift.
* Apply **Decimal** type for consistent floating-point operations.

---

### 3.2 **Circular Dependency Deadlock — Microservices**

**Fault:**
Service A → B → C → A circular dependencies cause deadlocks under load.

**Key Observables:**

* Service timeouts
* Deadlock or hang in service logs

**Challenge:**
Identify the **circular call loop**, and implement **circuit breakers** or **asynchronous messaging queues**.

**Solution Steps:**

* Use **trace-based visualizations** (e.g., Kiali) to spot circular dependencies.
* Introduce **circuit breakers** to avoid deadlocks under high load.

---

### 3.3 **N+1 Query / Latency Storm — REST API**

**Fault:**
Excessive database queries (N+1 pattern) and external API blocking cause high latency.

**Key Observables:**

* High latency spikes (P95/P99)
* High throughput with inconsistent response times

**Challenge:**
Detect N+1 query issues and refactor for **batch processing**, **asynchronous calls**, or **caching**.

**Solution Steps:**

* Use **Prometheus/Grafana** to visualize high-latency spikes.
* Introduce **batching or async handling** to reduce DB load.

---

### 3.4 **Red Herring — Background Worker CPU Spike**

**Fault:**
A background worker process consumes excessive CPU, leading to degraded performance elsewhere.

**Key Observables:**

* High CPU usage in background worker logs
* Slow or delayed external service responses

**Challenge:**
Disregard the red herring (background CPU spike) and focus on the real issue (e.g., external API failure).

**Solution Steps:**

* Ensure the investigation focuses on **actual symptoms** and avoids false positives.
* Re-align investigation to the correct failure point.

---

## 4️⃣ **Observability & Chaos Enhancements**

**Tools & Techniques:**

* **Structured Logging:**
  Implement structured logging with `trace_id`, `span_id`, and request context to correlate logs across services.

* **Custom Metrics:**
  Integrate business-level metrics like `latency`, `failure_rate`, and `transaction_count` for better visibility.

* **Service Graphs:**
  Use tools like **Kiali** or **OpenTelemetry** to visualize multi-hop service dependencies.

* **Chaos Injection:**
  Introduce latency, network partitioning, or API failures to simulate real-world chaos and improve troubleshooting skills.

---

## 5️⃣ **AI Workflow Integration**

**Tools to Leverage AI in Incident Resolution:**

1. **Automated Runbook Generation:**
   AI generates a runbook from the spec template that teams can reference during troubleshooting.

2. **Log-to-Prompt Pipeline:**
   Feed logs and events into AI tools (like GPT-4 or Claude) to generate potential diagnoses or remediation steps.

3. **Shadow AI On-Call:**
   Compare AI’s suggestions with human solutions to assess AI’s performance and reliability.

---

## 6️⃣ **Post-Mortem & Governance**

### **Blameless Post-Mortem:**

* Identify root causes and failure points without assigning blame.
* Use the **Five Whys** methodology to explore deeper causes.

### **IaC Drift Detection:**

* Ensure that fixes made during the drill are reflected in the infrastructure code, e.g., Terraform or CloudFormation templates.

### **Prevention Plan:**

* Add new **alerting rules** for failures that were detected.
* Update the **service specification** and **guardrails** to prevent similar issues from occurring.

---

## 7️⃣ **Facilitator Notes**

1. **Maintain High Pressure**
   Create a realistic, high-pressure environment that simulates the urgency of a production outage. However, always maintain a **blameless culture** for learning.

2. **Reflection Moments**
   Use **tea breaks** as critical reflection periods. Encourage engineers to discuss their methods, assumptions, and any insights that arise.

3. **Monitor AI Usage**
   Track AI’s role in the drill. Ensure that AI provides guidance and suggestions but is not relied upon as the primary decision-maker.

4. **Encourage Discussion**
   Foster a **collaborative** approach during each phase, allowing teams to share strategies and techniques.

---

## 8️⃣ **Follow-Up Actions**

1. **Post-Workshop Review:**
   Collect feedback on the workshop’s execution, team performance, and AI utility. Update future drills based on these insights.

2. **Implement Improvements:**
   Ensure that any **preventive measures** or **fixes** identified in the workshop are implemented in production, such as new alerting systems or refined debugging processes.

3. **Continuous Learning:**
   Schedule **regular follow-up drills** with escalating complexity or novel failure types.

---

By focusing on **human-first investigation**, **AI-assisted resolution**, and **post-mortem improvements**, this 3 A.M. Drill Workshop will enhance engineers’ ability to manage high-pressure production incidents while integrating AI into their workflows safely and effectively.

