# 3AM Outage Scenario — AI-Era Software Engineer

> **Purpose:** Simulate a high-pressure system outage to practice incident response, troubleshooting, and team coordination.

---

## Scenario Setup

* **Time:** 3 AM production outage.
* **System:** Full-stack app (Django backend, React frontend) with AI-assisted features.
* **Symptoms:** API 500 errors, slow response, failed AI tasks.
* **Alerting:** Monitoring system triggers paging with critical severity.

---

## Objectives

1. **Rapid Diagnosis**

   * Check logs, monitoring dashboards, and AI pipeline metrics.
   * Identify the root cause: DB connection errors, AI latency, deployment issue.

2. **Mitigation & Containment**

   * Enable fallbacks or circuit breakers.
   * Rollback recent deployments if necessary.
   * Notify stakeholders with clear status.

3. **Resolution**

   * Apply fix: configuration correction, DB reconnect, AI retry.
   * Validate system stability and functionality.

4. **Postmortem & Learning**

   * Document the incident, root cause, and corrective actions.
   * Update playbooks and monitoring thresholds.

---

## Roles & Responsibilities

| Role               | Responsibilities                                            |
| ------------------ | ----------------------------------------------------------- |
| On-Call Engineer   | Initial triage, logs analysis, mitigation decisions         |
| Backend Engineer   | Fix DB/API issues, monitor AI tasks                         |
| Frontend Engineer  | Verify UI functionality, error handling, user notifications |
| Bridge Engineer    | Coordinate cross-team, ensure full system audit             |
| Documentation Lead | Record timeline, decisions, and postmortem                  |

---

## Key Takeaways

* Bridge Engineers orchestrate response across systems and teams.
* Observability, logging, and AI monitoring are critical.
* Postmortems convert crises into systemic improvements.
* Regular drills build confidence and resilience for real-world outages.
