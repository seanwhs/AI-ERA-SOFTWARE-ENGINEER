# 📝 3 A.M. Drill Workshop — Full Workshop Plan

**Workshop Name:** 🕒 3 A.M. Drill — AI-Era System Owner
**Duration:** 180 minutes
**Cohort Size:** 6–12 engineers
**Instructor Ratio:** 1:6

**Workshop Objective:**
Simulate a high-pressure production incident to train engineers in **human-first troubleshooting, AI-assisted remediation, observability, and post-mortem analysis**.

---

## 1️⃣ Workshop Goals

**Primary Goals:**

1. Enable engineers to **diagnose complex failures without AI first**.
2. Apply AI-assisted solutions **responsibly after verification**.
3. Strengthen **system observability, alerting, and trace correlation**.
4. Build **muscle memory for crisis investigation** and decision-making under pressure.

**Secondary Goals:**

* Train teams to **identify and disregard red herrings**.
* Improve **post-mortem documentation** and **preventive guardrails**.
* Measure **AI-assisted fix accuracy and time-to-resolution (TTR)**.

---

## 2️⃣ Workshop Logistics

| Item        | Details                                                                             |
| ----------- | ----------------------------------------------------------------------------------- |
| Venue       | Lab or cloud-enabled remote setup with dashboards, terminals, and AI access         |
| Environment | Pre-deployed microservices, REST APIs, databases                                    |
| Tools       | Grafana/Prometheus, ELK/Loki logs, AI agent (GPT-4 / Claude), Slack/Teams           |
| Materials   | Post-Workshop Report Templates, Facilitator Quick-Reference Sheet, Scenario Scripts |
| Roles       | Lead Facilitator, Scenario Monitor, AI Moderator, Observer / Note Taker             |

---

## 3️⃣ Workshop Agenda

| Time      | Phase                              | Activities                                                       | Facilitator Notes                                       |
| --------- | ---------------------------------- | ---------------------------------------------------------------- | ------------------------------------------------------- |
| 0:00–0:10 | Orientation                        | Welcome, objectives, rules, team roles                           | Emphasize human-first mindset                           |
| 0:10–0:15 | Setup                              | Tea break, environment check                                     | Verify dashboards & AI prompts                          |
| 0:15–1:00 | Phase 1: Dark Room Investigation   | Trigger FP Drift, Deadlock, N+1; human-only troubleshooting      | Observe progress, red-herring alerts, no direct answers |
| 1:00–1:10 | Tea Break                          | Reflection                                                       | Ask: early signals? Most effective tracing?             |
| 1:10–1:50 | Phase 2: Deep Dive & Verification  | Logs, metrics, trace IDs, stress testing                         | Confirm hypotheses before AI intervention               |
| 1:50–2:00 | Tea Break                          | Reset                                                            | Prepare AI prompts, review red-herring signals          |
| 2:00–2:30 | Phase 3: AI-Assisted Fix           | Apply AI-guided fixes: Decimal, Circuit Breakers, Async batching | Human review required before committing fixes           |
| 2:30–2:50 | Phase 4: Post-Mortem & Spec Update | Update templates, PR guardrails, lessons learned                 | Blameless post-mortem, red-herring reflection           |
| 2:50–3:00 | Wrap-Up                            | Debrief, KPI & metric review                                     | Discuss TTR, fix accuracy, AI contribution              |

---

## 4️⃣ Scenarios Overview

| Scenario                     | Fault                                           | Key Observables                    | Red-Herring                 |
| ---------------------------- | ----------------------------------------------- | ---------------------------------- | --------------------------- |
| Floating-Point Drift         | Subtle float precision drift in Billing Engine  | Running total drift, trace IDs     | None                        |
| Circular Dependency Deadlock | Service A→B→C→A call loop under load            | Timeouts, service logs             | Optional: latency injection |
| N+1 Query / Latency Storm    | Sequential DB queries + external blocking calls | P95/P99 latency spikes, throughput | Background CPU spike        |

**Optional Chaos Enhancements:**

* Network latency injection
* Disk pressure / log rotation failure
* Upstream API dependency failure

---

## 5️⃣ Learning Objectives by Scenario

| Scenario    | Human-First Skills                                | AI-Assisted Skills                                |
| ----------- | ------------------------------------------------- | ------------------------------------------------- |
| FP Drift    | Detect drift, trace transactions, log correlation | Replace float → Decimal, idempotency verification |
| Deadlock    | Trace service calls, identify chain loops         | Circuit breaker implementation, async queues      |
| N+1 Latency | Detect N+1, measure latency, batch queries        | Async handling, caching, performance validation   |

---

## 6️⃣ Success Metrics & KPIs

| Metric                 | Target                                     |
| ---------------------- | ------------------------------------------ |
| Root cause identified  | ≤40 min human-only                         |
| Fix success rate       | 100%                                       |
| Observability coverage | Full logs & trace correlation              |
| Stress test compliance | Pass                                       |
| AI assistance accuracy | ≥90%                                       |
| Red-herring handling   | Symptom vs root cause correctly identified |

---

## 7️⃣ Reflection & Post-Mortem

**Team Reflection Questions:**

1. Which investigative techniques were most effective?
2. Which assumptions delayed root cause identification?
3. How well did AI assist without introducing risk?
4. What improvements are needed for dashboards, logs, or alerts?

**Post-Mortem Documentation:**

* Update templates & PR guardrails
* Capture lessons learned
* Assign preventive actions
* Record AI suggestions for future scenarios

---

## 8️⃣ Deliverables

* Completed **Post-Workshop Report** per team
* **Metrics Dashboard** (FP Drift, Deadlock, N+1, AI performance, red-herring handling)
* **Updated Spec & Guardrails**
* Facilitator notes & observation logs

---

## 9️⃣ Follow-Up / Next Steps

* Review post-mortem for continuous improvement
* Schedule next drill (higher difficulty / new chaos events)
* Implement preventive alerts and runbook updates
* Share lessons learned across engineering teams

---

💡 **Facilitator Notes:**

* Keep the pressure high, but environment safe & blameless
* Encourage discussion, reflection, and cross-team learning
* Monitor AI usage and human decision-making for reporting

---


Do you want me to do that next?
