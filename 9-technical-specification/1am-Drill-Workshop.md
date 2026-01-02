# 🛠️ Workshop: The "3 A.M. Drill" — System Owner Simulation

**Duration:** 60 Minutes | **Format:** Hands-On Simulation | **Persona:** System Owner Training

> **Core Objective:** Transition engineers from passive AI users into **System Owners**. Participants debug a high-pressure production failure **without AI**, then orchestrate a verified, idempotent fix using AI **after human verification**.

---

## 📋 Prerequisites

* **The "Poisoned" Codebase:** Pre-configured repo with 3 microservices; one service contains an AI-generated **silent fault** (e.g., circular dependency, race condition, or floating-point precision bug).
* **Observability Dashboard:** Mock Grafana / Honeycomb board showing spiking latencies and 5xx errors.
* **No-AI Rule (Phase 1):** Participants must close all LLM tabs, Copilot, Cursor, and similar agents for the first 25–30 minutes.

> **Technical Depth Callout:** Restricting AI access forces **first-principles reasoning**, reinforces system mental models, and strengthens fault isolation skills.

---

## ⏱️ Timeline (60 Minutes)

### 0:00 – 0:05 | **Pager Notification — Alerting Phase**

* **Scenario:** 3:14 A.M. Core billing service is timing out; customers are double-charged. Yesterday’s AI-generated PR is suspected.
* **Action:** Display repo link & metrics dashboard.
* **Objective:** Immerse participants in a **production-pressure mindset**.

### 0:05 – 0:30 | **Dark Room Investigation — Adversarial Phase**

* **Rule:** **Strictly No AI.**
* **Task:** Engineers must identify root cause using **logs, traces, `ps`, `netstat`, `curl`**, and local inspection.
* **Goal:** Pinpoint the exact AI-generated logic fault (e.g., unhandled `Promise.all`, race condition, or floating-point drift).
* **Instructor Notes:**

  * Watch for “Prompt Withdrawal”—participants instinctively reaching for AI.
  * Reinforce tracing, reasoning from **first principles**, and observability-driven debugging.

### 0:30 – 0:45 | **Supervised Recovery — Orchestration Phase**

* **AI Re-enabled:** Participants can now use AI **only to implement a fix** based on a human-verified root cause.
* **Challenge:** Do **not** ask AI “What is wrong?” Instead, provide:

  1. Root cause analysis.
  2. **Technical Spec** for the fix.
* **Goal:** Generate robust, **idempotent fix** covering all missing failure modes.
* **Verification:** Execute a **Double-Execution Test** to validate idempotency.

### 0:45 – 0:55 | **Post-Mortem & Spec Update — Ownership Phase**

* **Discussion:**

  * Why did AI generate this fault? Contextual gaps, ambiguous spec, or over-optimization?
* **Action:** Update the **Team Technical Spec Template** with a new **Guardrail** preventing this specific hallucination in future PRs.

### 0:55 – 1:00 | **Closing: The System Owner Vow**

* **Takeaway:**

> “The AI wrote the code, but I allowed it into production. I own the fix.”

* **Action:** Each participant adds **one new check** to the team’s PR template derived from today’s drill.

---

## 🏆 Success Metrics

| Metric                           | Target                                                                   |
| -------------------------------- | ------------------------------------------------------------------------ |
| **Time to Isolation**            | < 20 minutes without AI                                                  |
| **Hallucination Identification** | Clearly name the AI’s logical gap                                        |
| **Spec Hardening**               | Successfully add a new constraint or guardrail to the Team Spec Template |
| **Fix Verification**             | Passes double-execution / idempotency check                              |

---

## 🔹 Technical Notes for Instructors

1. **Rotate Scenarios:** Use Circular Deadlocks, N+1 Storms, or Floating-Point Drift across sessions.
2. **Ensure Observability:** All exercises must include **traceable metrics** (logs, trace_ids, error codes).
3. **Enforce Discipline:** No AI during the investigative phase; human reasoning first.
4. **Debrief:** After drill, analyze why AI hallucinated; translate insights into **spec improvements** and **PR checklist updates**.

---

## 🏁 Outcomes

* Engineers practice **first-principles debugging under pressure**.
* Teams strengthen **distributed systems intuition**.
* System Owners internalize **failure-mode thinking** and **adversarial PR review**.
* Reinforces **ownership mindset**: AI is a tool, not a substitute for judgment.

---

