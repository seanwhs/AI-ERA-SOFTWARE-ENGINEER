# Failure Postmortem Template (Blameless)

> **Purpose**: Convert failure into durable engineering insight.
>
> This template is **mandatory** after outages, regressions, security incidents, or near-misses.

---

## Incident Metadata

* **Incident Name:** ______________________
* **Date & Time:** ______________________
* **Severity:** Low / Medium / High / Critical
* **Systems Affected:** ______________________
* **Detected By:** Human / Monitoring / User Report

---

## 1. What Happened (Objective Timeline)

> Facts only. No interpretation.

* T-30m:
* T-15m:
* T0 (Failure):
* T+15m:
* Resolution:

---

## 2. Impact Assessment

* Who was affected?
* What functionality was degraded or lost?
* Was data integrity or security compromised?

---

## 3. Root Cause Analysis (Systemic)

Answer **all** that apply:

* What assumption failed?
* What contract was violated?
* What dependency behaved unexpectedly?
* What human decision contributed?

> Root causes are rarely a single line of code.

---

## 4. Contributing Factors

Check all that apply:

* ☐ Missing tests
* ☐ Unclear ownership
* ☐ AI-generated code not reviewed
* ☐ Poor observability
* ☐ Ambiguous requirements
* ☐ Time pressure

Explain:

---

## 5. Detection & Response Quality

* How quickly was the issue detected?
* Was the alert actionable?
* What slowed down resolution?

---

## 6. What Went Well

> Always fill this section.

*
*

---

## 7. What Failed Systemically

* Which guardrail should have caught this?
* Why didn’t it?

---

## 8. Corrective Actions (Concrete)

Each item must have an **owner** and **deadline**.

| Action | Owner | Due Date |
| ------ | ----- | -------- |
|        |       |          |
|        |       |          |

---

## 9. AI-Specific Review (If Applicable)

* Did AI generate or modify the failing code?
* Was the prompt insufficient?
* Was the output reviewed with the same rigor as human code?

---

## 10. Preventing Recurrence

* What rule, test, or contract will change?
* How will this be enforced?

---

## Final Reflection

* What signal did we ignore?
* What would a Bridge Engineer have questioned earlier?

---

> *“The cost of failure is paid once. The value is earned only if it is examined.”*
