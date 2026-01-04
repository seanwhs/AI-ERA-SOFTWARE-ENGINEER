## 📝 **3 A.M. Drill Workshop — Post-Workshop Report Template (Enhanced)**

---

### **Workshop Date:** ___________________

### **Facilitator / Instructor:** ___________________

### **Team / Participants:** ___________________

---

### 1️⃣ **Workshop Overview**

#### **Objective:**

> Summarize the purpose of the drill, including **human-first investigation**, **AI-assisted remediation**, and **adversarial thinking** under realistic failure conditions.

#### **Scenarios Covered:**

* [ ] Floating-Point Drift — Billing Engine
* [ ] Circular Dependency Deadlock — Microservices
* [ ] N+1 Query / Latency Storm — REST API
* [ ] Red Herring — Misleading alert / CPU spike

#### **Severity Levels Tested:**

* [ ] Low
* [ ] Medium
* [ ] High / Production-critical

#### **Workshop Duration:** 180 minutes

#### **Brief Description:**

> **One to two sentences** summarizing the team's focus, approach, and initial observations.

---

### 2️⃣ **Timeline & Activities**

| **Phase**                     | **Start–End** | **Activity**                                        | **Key Observations / Notes**                  | **Metrics / KPIs** |
| ----------------------------- | ------------- | --------------------------------------------------- | --------------------------------------------- | ------------------ |
| **Orientation**               | 0:00–0:10     | Welcome & rules, team assignment                    |                                               |                    |
| **Setup**                     | 0:10–0:15     | Tea break / environment check                       |                                               |                    |
| **Dark Room Investigation**   | 0:15–1:00     | Human-only troubleshooting                          | Root cause detection time, false positives    |                    |
| **Tea Break**                 | 1:00–1:10     | Reflection                                          |                                               |                    |
| **Deep Dive & Verification**  | 1:10–1:50     | Logs, metrics, stress test, root cause verification | Correlation completeness, stress test success |                    |
| **Tea Break**                 | 1:50–2:00     | Reset                                               |                                               |                    |
| **AI-Assisted Fix**           | 2:00–2:30     | Apply AI-guided remediation                         | Fix success vs predicted, AI accuracy %       |                    |
| **Post-Mortem & Spec Update** | 2:30–2:50     | Update templates, guardrails, lessons               | Number of guardrails updated, IaC corrections |                    |
| **Wrap-Up**                   | 2:50–3:00     | Debrief & metrics review                            | Overall TTR (Time to Resolution)              |                    |

---

### 3️⃣ **Scenario Analysis**

#### **3.1 Floating-Point Drift — Billing Engine**

**Root Cause Identified:** ___________________

**Human-Only Investigation Notes:**

> Methods used, logs/metrics reviewed, challenges encountered, correlation across trace IDs and business metrics.

**Red Herring / Noise Observed:**

> e.g., unrelated alerts, background tasks that appeared to affect totals.

**AI-Assisted Fix Implemented:**

> Steps applied, code changes (`float → Decimal`), idempotency verification, AI suggestion evaluation.

**Success Metrics:**

* Root cause identified time: ______ min
* AI-assisted fix: [ ] Successful / [ ] Partial / [ ] Failed
* Observability logs trace correlation: [ ] Complete / [ ] Partial
* Stress test validation: [ ] Passed / [ ] Failed

**Lessons Learned / Recommendations:**

> Logging improvements, guardrails, preventive measures, dashboard alerts, traceable metrics.

---

#### **3.2 Circular Dependency Deadlock — Microservices**

**Root Cause Identified:** ___________________

**Human-Only Investigation Notes:** ___________________

**Red Herring / Noise Observed:** ___________________

**AI-Assisted Fix Implemented:** ___________________

**Success Metrics:**

* Root cause identified time: ______ min
* Circuit breakers / async queue applied: [ ] Yes / [ ] No
* AI-assisted prediction accuracy: ______ %
* Stress test / latency check passed: [ ] Yes / [ ] No

**Lessons Learned / Recommendations:** ___________________

---

#### **3.3 N+1 Query / Latency Storm — REST API**

**Root Cause Identified:** ___________________

**Human-Only Investigation Notes:** ___________________

**Red Herring / Noise Observed:** ___________________

**AI-Assisted Fix Implemented:** ___________________

**Success Metrics:**

* Root cause identified time: ______ min
* Batch / async / caching implemented: [ ] Yes / [ ] No
* Observability logs correlation: [ ] Complete / [ ] Partial
* SLA / latency targets met: [ ] Yes / [ ] No

**Lessons Learned / Recommendations:** ___________________

---

### 4️⃣ **Team Reflection**

#### **Reflection Questions:**

1. Which investigative techniques were most effective?
2. Were there assumptions that delayed root cause identification?
3. How did AI assist or mislead during resolution?
4. Were dashboards, logs, alerts, and metrics sufficient?
5. How did red herrings affect team decisions?

#### **Team Summary:**

> **Short paragraph** capturing overall experience, surprises, and key takeaways.

---

### 5️⃣ **Post-Mortem & Spec Updates**

#### **Updated Templates / Guardrails:**

* E.g., logging fields, traceability, alert thresholds, circuit breaker rules

#### **Preventive Actions / Recommendations:**

* Fix recurring issues
* Add new alerting rules / dashboards
* Address IaC drift
* Schedule follow-up training if needed

#### **Next Steps / Follow-Up:**

* Assign owners for each preventive action
* Timeline for metric re-evaluation
* Plan for repeated drill / difficulty scaling

---

### 6️⃣ **Instructor / Facilitator Notes**

#### **Performance Highlights:** ___________________

#### **Areas for Improvement:** ___________________

#### **AI Workflow Observations:** ___________________

#### **Red Herring Handling:** ___________________

#### **Overall Rating:**

* [ ] Excellent
* [ ] Good
* [ ] Needs Improvement

#### **Additional Comments:** ___________________

---

### ✅ **Key Enhancements in This Template**

* **Red Herring Section:** Tracks misdirection alerts to teach symptom vs root cause analysis.
* **Observability & Metrics:** Captures correlation completeness, SLA/latency checks, stress test results.
* **AI Workflow Evaluation:** Notes AI-assisted effectiveness vs human resolution.
* **Severity & Follow-Up Tracking:** Adds risk grading and actionable next steps.
* **Structured Preventive Actions:** Ensures lessons are actionable and maintainable in spec updates.

---

## 🖥 **3 A.M. Drill Workshop — Dashboard Mockup**

---

### **Slide 1 — FP Drift: Running Total Over Time**

**Scenario:** Floating-Point Drift — Billing Engine

**Goal:** Show drift pre-fix and post-fix

```
Running Total Drift (USD)
+--------------------------------------------------+
| 1000.000                                   ╭───+
| 1000.005                                ╭───+   |
| 1000.010                              ╭──+     |
| 1000.015                           ╭──+        |
| 1000.020                        ╭──+           |
| 1000.000  (Post-Fix) ────────────╯             |
+--------------------------------------------------+
Time → 
```

---

### **Slide 2 — Circular Dependency Deadlock**

**Scenario:** Service Circular Calls — Microservices

```
Service Call Trace (Pre-Fix)
A ──► B ──► C ──► A (Deadlock)
Timeouts: 15% of requests

Service Call Flow (Post-Fix)
A ──► B ──► C ──► Async Queue
Circuit Breaker Enabled
Timeouts: 2% of requests
```

---

### **Slide 3 — N+1 Query Latency Storm**

**Scenario:** REST API Latency

```
Latency per User (ms)
Pre-Fix (Sequential Calls)       Post-Fix (Batched / Async)
User 1: ███████████████████      ███
User 2: ████████████████████     ███
User 3: ██████████████████       ███
...
P95 Latency: 1.8s → 0.35s
P99 Latency: 3.2s → 0.45s
```

---

### **Slide 4 — Red Herring Timeline**

**Scenario:** Background CPU Spike

```
Time → 
0:15  0:30  0:45  1:00  1:15
CPU Alert █████████        (Background Worker)
N+1 Latency █████████████  (Actual Outage)
```

---

### **Slide 5 — AI-Assisted Fix Performance**

| Scenario  | AI Recommendation             | Accuracy | Human Override      | Time Saved |
| --------- | ----------------------------- | -------- | ------------------- | ---------- |
| FP Drift  | Decimal + logging             | 100%     | None                | 5 min      |
| Deadlock  | Async queue + circuit breaker | 92%      | Minor timeout tweak | 6 min      |
| N+1 Storm | Batch + async + caching       | 95%      | Verification needed | 4 min      |

---

### **Slide 6 — KPI Summary Radar**

| Metric


| Pre-Fix  | Post-Fix  | Target |
| ---------------------- | -------- | --------- | ------ |
| Root Cause Detection   | 28–35m   | —         | ≤40m   |
| Fix Success Rate       | 0%       | 100%      | 100%   |
| Observability Logs     | Partial  | Complete  | 100%   |
| Stress Test Compliance | Fail     | Pass      | Pass   |
| AI Assistance Accuracy | N/A      | 92–100%   | ≥90%   |
| Red-Herring Handling   | Confused | Effective | ✅      |

---

### **Slide 7 — Team Reflection Dashboard**

**Reflection Questions & Scores (0–5)**

| Question                    | Score | Notes                           |
| --------------------------- | ----- | ------------------------------- |
| Investigative Techniques    | 4     | Trace ID + Logs most effective  |
| AI Assistance Effectiveness | 5     | Accurate, reduced TTR ~15 min   |
| Red Herring Handling        | 4     | Required cross-check of metrics |
| Dashboards / Alerts Quality | 3     | Need real-time drift/N+1 alerts |

---

### **Slide 8 — Summary & Next Steps**

**Key Takeaways:**

* Human-first investigation critical before AI-assisted remediation
* Observability dashboards, trace IDs, and business metrics saved time
* Red-herring alerts reinforced symptom vs root cause analysis
* AI suggested actionable fixes; human verification remained essential

**Next Steps:**

* Implement preventive alerts for FP Drift, N+1, circular calls
* Schedule Level 3 drill in 6 weeks
* Update runbooks with AI suggestions & post-mortem lessons

---

This **enhanced report and dashboard** layout combines both **actionable insights** and **visual clarity**, perfect for post-drill debriefs and future workshops! Let me know if you'd like any adjustments!
