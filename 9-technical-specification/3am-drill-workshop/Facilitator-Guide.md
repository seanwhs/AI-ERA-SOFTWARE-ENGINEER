# 🧑‍🏫 **3 A.M. Drill Workshop — Facilitator’s Guide**

**Workshop Duration:** 180 minutes
**Recommended Cohort Size:** 6–12 engineers
**Instructor Ratio:** 1:6

**Purpose:**
Enable facilitators to **run a high-pressure, realistic production incident drill** that emphasizes **human-first investigation, AI-assisted remediation, observability, and post-mortem documentation**.

---

## 1️⃣ **Preparation Checklist**

| Item                      | Description                                                | Completed |
| ------------------------- | ---------------------------------------------------------- | --------- |
| **Scenario Environment**  | Ensure services for FP Drift, Deadlock, N+1 are deployed   | [ ]       |
| **Dashboards & Metrics**  | Pre-configure Grafana / Prometheus / ELK / Loki dashboards | [ ]       |
| **AI Tooling**            | Ensure GPT/Claude prompts & log-to-prompt pipeline ready   | [ ]       |
| **Communication Tools**   | Slack/Teams channels, Zoom breakout rooms                  | [ ]       |
| **Red Herring**           | Simulated alert or CPU spike ready to trigger              | [ ]       |
| **Post-Mortem Templates** | Print/fillable Markdown or Google Docs templates           | [ ]       |
| **Timer & Agenda**        | Visible countdown & phase timers                           | [ ]       |
| **Stress Test Scripts**   | Ready for scenario validation                              | [ ]       |

**Tip:** Run a **dry run** to ensure timing, alerts, and AI pipelines function as expected.

---

## 2️⃣ **Facilitator Roles**

1. **Lead Facilitator / Instructor:**
   Guides the entire workshop, explains objectives, monitors time, ensures the smooth execution of human and AI interventions.

2. **Scenario Monitor:**
   Triggers failure injections, red herrings, and chaos events. Monitors logs/metrics and checks for anomalies or issues.

3. **AI Moderator:**
   Oversees AI workflow, ensures that prompts are being used correctly, and observes AI-generated recommendations without overriding human decisions.

4. **Observer / Note Taker:**
   Captures decisions, actions, timing, and any lessons learned to share in the debrief.

---

## 3️⃣ **Workshop Agenda & Facilitation Notes**

### **0:00–0:10 | Welcome & Orientation**

* **Objectives:** Explain workshop purpose, learning goals, and safety rules.
* **Roles:** Assign roles (Investigator, Metrics Analyst, AI Liaison, Documentation Scribe).
* **Key Message:** Humans lead first, AI assists second.

**Facilitator Tips:**

* Emphasize time discipline.
* Encourage team discussions **before** engaging AI tools.

---

### **0:10–0:15 | Tea Break / Setup**

* Ensure all workstations, dashboards, and AI pipelines are functional.
* Verify that participants can access scenario services.

---

### **0:15–1:00 | Phase 1: Dark Room Investigation**

* **Scenario Injection:** Trigger **FP Drift, Deadlock, N+1 latency**.
* Participants investigate the incident **without AI assistance**.

**Facilitator Tips:**

* Observe teams and avoid providing direct answers.
* Use **subtle prompts** only if teams are stuck for over 10 minutes.
* Track red-herring alerts and see if teams detect real vs. false signals.

---

### **1:00–1:10 | Tea Break / Reflection**

* Encourage teams to **discuss initial findings**.
* Ask reflection questions:

  * Which signals were clear vs misleading?
  * How effective were logs and dashboards?

---

### **1:10–1:50 | Phase 2: Deep Dive & Verification**

* Teams analyze **logs, metrics, trace IDs** and **stress-test suspected causes**.
* Confirm root cause hypotheses **before introducing AI assistance**.

**Facilitator Tips:**

* Watch for premature AI dependency.
* Encourage **cross-referencing business metrics with technical logs**.
* Track detection times to evaluate success metrics.

---

### **1:50–2:00 | Tea Break / Reset**

* Allow mental reset.
* Prep AI prompts for the next phase.
* Teams should write down **root cause hypotheses**.

---

### **2:00–2:30 | Phase 3: AI-Assisted Fix Implementation**

* Teams leverage AI **after verifying root causes** for fix suggestions:

  * **FP Drift:** Replace `float` with `Decimal` and check idempotency.
  * **Deadlock:** Implement circuit breakers or async queues.
  * **N+1 Query Storm:** Refactor to batch requests, use async or caching.

**Facilitator Tips:**

* Observe the **AI suggestions** vs human decision.
* Ensure **human review before committing any fixes**.
* Capture **AI accuracy metrics** for reporting.

---

### **2:30–2:50 | Phase 4: Post-Mortem & Spec Update**

* Teams **update spec templates**, PR guardrails, and document **lessons learned**.
* Focus on **preventive actions** and **dashboard improvements**.

**Facilitator Tips:**

* Emphasize **blameless post-mortems**.
* Reflect on **red herrings**: How did teams avoid being misled?
* Document updated **guardrails** for future reference.

---

### **2:50–3:00 | Wrap-Up & Metrics Review**

* **Debrief:** Discuss root causes, fix effectiveness, AI workflow, red-herring handling.
* **Metrics Review:** Evaluate detection time, fix success, SLA adherence, AI accuracy.

**Facilitator Tips:**

* Highlight key takeaways for **human-first investigation**.
* Reinforce the importance of **observability**, **spec updates**, and **preventive actions**.

---

## 4️⃣ **Scenario Management & Chaos Injection**

| Scenario                         | Trigger / Fault                   | Key Facilitation Notes                                               |
| -------------------------------- | --------------------------------- | -------------------------------------------------------------------- |
| **Floating-Point Drift**         | Random transaction values         | Confirm cumulative totals drift; observe trace ID correlation        |
| **Circular Dependency Deadlock** | Service call loops under load     | Track timeouts; ensure async queue & circuit breaker not pre-applied |
| **N+1 Latency Storm**            | Sequential DB queries + API calls | Observe latency spike, ensure SLA targets clearly defined            |
| **Red Herring**                  | Background CPU spike              | Verify teams question vs confirm; do not directly reveal true cause  |

**Chaos Enhancements:**

* Inject **network latency** or partial **service outage** for advanced cohorts.
* Introduce **disk pressure** or **log rotation failures** as bonus challenges.

---

## 5️⃣ **AI Integration Guidelines**

1. **Human-First Approach:** Only allow AI after **root cause verification**.
2. **AI Prompts** should include:

   * Last 50 log lines + metrics snapshot.
   * Scenario description without providing explicit root cause.
3. **Key Observations**:

   * **Accuracy of AI suggestions**.
   * **Time saved** vs human-only resolution.
   * Watch for **misdirection** or over-reliance on AI.

---

## 6️⃣ **Instructor Notes & Tips**

* **Rotate Difficulty**: Vary the difficulty of scenarios and red herrings to **maintain adversarial thinking**.
* **Tea Breaks**: These are **reflection checkpoints**, not just downtime.
* **Track Metrics**: Continuously monitor and evaluate **detection times**, **fix success**, and **AI accuracy**.
* **Reinforce Human-First Mindset**: While AI provides support, **humans own production**.
* **Blameless Post-Mortems**: Focus on system and process improvements, not assigning blame.

---

## 7️⃣ **Post-Workshop Actions**

1. **Review Reports & Metrics**: Analyze team reports and review the **metrics dashboard**.
2. **Validate AI Recommendations**: Cross-check AI’s suggestions against implemented fixes.
3. **Assign Preventive Actions**: Ensure all identified action items are assigned to owners.
4. **Schedule Next Drill**: Plan the next drill with increased difficulty or new chaos injections.

---

# 📝 **3 A.M. Drill Workshop — Facilitator Quick-Reference Sheet**

**Duration:** 180 min | **Cohort Size:** 6–12 Engineers | **Instructor Ratio:** 1:6

---

## **1️⃣ Workshop Phases & Timers**

| Phase                  | Time      | Key Actions                   | Facilitator Prompts                                                       |
| ---------------------- | --------- | ----------------------------- | ------------------------------------------------------------------------- |
| **Orientation**        | 0:00–0:10 | Welcome, rules, team setup    | Assign roles: Investigator, Metrics Analyst, AI Liaison, Scribe           |
| **Setup / Tea Break**  | 0:10–0:15 | Environment check             | Confirm dashboards, AI prompts, log access                                |
| **Phase 1: Dark Room** | 0:15–1:00 | Human-only troubleshooting    | Observe log correlation; trigger red-herring alerts; avoid giving answers |
| **Tea Break**          | 1:00–1:10 | Reflection                    | Ask: early signals? Most effective tracing method?                        |
| **Phase 2: Deep Dive** | 1:10–1:50 | Logs, metrics, stress testing | Verify root cause hypotheses; track detection time                        |
| **Tea Break**          | 1:50–2:   |                               |                                                                           |


00 | Reset                         | Prep AI prompts; recap scenario faults                                    |
| **Phase 3: AI Fix**      | 2:00–2:30 | AI-assisted remediation       | Confirm human verification; monitor AI accuracy & time saved              |
| **Phase 4: Post-Mortem** | 2:30–2:50 | Spec & guardrail update       | Encourage blameless post-mortem; discuss preventive actions               |
| **Wrap-Up**              | 2:50–3:00 | Debrief & metrics review      | Highlight lessons, red-herring handling, KPI review                       |

---

## **2️⃣ Scenario & Fault Quick Lookup**

| Scenario                         | Fault / Injection                            | Key Observation / Red-Herring                           |
| -------------------------------- | -------------------------------------------- | ------------------------------------------------------- |
| **Floating-Point Drift**         | Subtle float precision drift                 | Cumulative totals; ensure trace ID correlation          |
| **Circular Dependency Deadlock** | Service A→B→C→A under load                   | Watch timeouts; network latency optional                |
| **N+1 Query / Latency Storm**    | Sequential DB queries + blocking API calls   | SLA spikes; verify batched fix                          |
| **Red Herring**                  | Background CPU spike                         | Teams may mis-prioritize; observe symptom vs root cause |
| **Optional Chaos**               | Network latency, disk pressure, log rotation | For advanced cohorts; monitor detection & fix           |

---

## **3️⃣ Facilitator Prompts**

* **Dark Room Phase:**

  * “What signals point to the root cause?”
  * “Can you trace the logs to find the root cause?”
* **Deep Dive Phase:**

  * “What metrics or logs help you confirm your hypothesis?”
  * “Can you correlate business metrics with the logs?”
* **AI Phase:**

  * “Does the AI suggestion align with your hypothesis?”
  * “Do you approve the AI fix? Why/why not?”
* **Reflection / Post-Mortem:**

  * “How can we improve for the next incident?”
  * “Did red herrings influence your troubleshooting?”

---

## **4️⃣ Metrics & KPI Checklist**

| Metric                     | Target                        | Status |
| -------------------------- | ----------------------------- | ------ |
| **Root Cause Detection**   | ≤40 min                       | ☐      |
| **Fix Success Rate**       | 100%                          | ☐      |
| **Observability Coverage** | Full logs & trace correlation | ☐      |
| **Stress Test Compliance** | Pass                          | ☐      |
| **AI Assistance Accuracy** | ≥90%                          | ☐      |
| **Red-Herring Handling**   | Effective                     | ☐      |

---

## **5️⃣ Quick Tips**

* **Rotate Scenarios / Red Herrings:** Keep adversarial thinking active
* **Tea Breaks:** Use as reflection checkpoints, not downtime
* **Record Metrics:** Track detection time, fix success, AI accuracy
* **Reinforce Human-First Mindset:** AI assists, humans own production
* **Blameless Post-Mortem:** Focus on system & process improvement

---

This sheet will act as a **real-time reference** for facilitators, keeping the session running smoothly and ensuring all necessary actions and metrics are tracked effectively. Let me know if you need further adjustments or have specific queries!
