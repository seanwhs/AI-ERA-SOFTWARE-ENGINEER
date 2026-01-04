# 🔍 **Failure Postmortem Template (Blameless)**

> **Purpose**: Convert failure into actionable insights and prevent recurrence by examining the root causes without assigning blame.

> This template is **mandatory** after any outage, regression, security incident, or near-miss.

---

## 📊 **Incident Metadata**

* **Incident Name**: ______________________
* **Date & Time**: ______________________
* **Severity**: Low / Medium / High / Critical
* **Systems Affected**: ______________________
* **Detected By**: Human / Monitoring / User Report

---

## 1️⃣ **What Happened (Objective Timeline)**

> This section should be purely factual. Avoid any interpretation or assumptions.

* **T-30m**:
* **T-15m**:
* **T0 (Failure)**:
* **T+15m**:
* **Resolution**:

---

## 2️⃣ **Impact Assessment**

* **Who was affected?**
* **What functionality was degraded or lost?**
* **Was data integrity or security compromised?**

---

## 3️⃣ **Root Cause Analysis (Systemic)**

> Root causes are often systemic and rarely confined to a single line of code.

Answer **all** that apply:

* What assumption failed?
* What contract was violated (e.g., SLA, team responsibility)?
* What dependency behaved unexpectedly?
* What human decision contributed to the failure (e.g., prioritization, lack of communication)?

> Root causes rarely lie in just the code itself. Look at the whole system.

---

## 4️⃣ **Contributing Factors**

Check all that apply and explain each:

* ☐ Missing tests
* ☐ Unclear ownership
* ☐ AI-generated code not reviewed
* ☐ Poor observability
* ☐ Ambiguous requirements
* ☐ Time pressure

**Explanation**:

---

## 5️⃣ **Detection & Response Quality**

* **How quickly was the issue detected?**
* **Was the alert actionable?** (If so, how was it handled? If not, why?)
* **What slowed down the resolution?**
* **Was the escalation process effective?**

---

## 6️⃣ **What Went Well**

> It's important to acknowledge the positives. Reflect on the things that helped mitigate damage or move toward resolution.

*
*

---

## 7️⃣ **What Failed Systemically**

* Which system-level guardrail or safety net should have caught this?
* Why didn’t it? (e.g., missed monitoring alert, lack of automated tests, etc.)

---

## 8️⃣ **Corrective Actions (Concrete)**

> For each corrective action, specify a clear **owner** and **deadline**.

| **Action** | **Owner** | **Due Date** |
| ---------- | --------- | ------------ |
|            |           |              |
|            |           |              |
|            |           |              |

---

## 9️⃣ **AI-Specific Review (If Applicable)**

* **Did AI generate or modify the failing code?**
  If yes, explain what role AI played in the failure.

* **Was the prompt insufficient?**
  Was the AI task well-defined, or was the scope unclear?

* **Was the AI output reviewed with the same rigor as human-written code?**
  Did we assume AI's output was flawless without sufficient testing?

---

## 🔟 **Preventing Recurrence**

* **What rule, test, or contract will change to prevent this failure?**
* **How will this change be enforced?**
  (e.g., adding automated tests, changing review processes, adding new system checks)

---

## Final Reflection

* **What signal did we ignore or misinterpret before the failure occurred?**
* **What would a Bridge Engineer (someone focused on reliability and system health) have questioned or caught earlier?**

---

> *“The cost of failure is paid once. The value is earned only if it is examined and learned from.”*

---

### Notes:

* **Blamelessness**: Focus on what can be improved and how to prevent future issues, not on who made the mistake.
* **Actionable Outcomes**: Ensure that each section leads to concrete actions, rather than theoretical conclusions.

---

