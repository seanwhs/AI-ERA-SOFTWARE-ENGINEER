# 3 AM Outage Scenario — AI-Era Software Engineer

> **Purpose:** Simulate a high-pressure system outage to practice incident response, troubleshooting, and team coordination in an AI-augmented environment.

---

## **Scenario Setup**

* **Time:** 3 AM production outage.
* **System:** Full-stack app (Django backend, React frontend) with AI-assisted features.
* **Symptoms:**

  * API 500 errors.
  * Slow response times.
  * Failed AI tasks (e.g., image processing, recommendation engine).
* **Alerting:** Monitoring system triggers paging with critical severity. Alerts include system downtime, AI failures, and backend/API errors.

---

## **Objectives**

1. **Rapid Diagnosis**
   Quickly analyze the issue to identify the root cause.

   * **Initial Actions:**

     * Check logs (both backend and frontend).
     * Review monitoring dashboards for performance spikes or errors.
     * Examine AI pipeline metrics (latency, error rates).
     * Look for database connection issues, AI pipeline failures, or recent deployment issues.

   * **Root Cause Possibilities:**

     * Database connection errors (timeouts or outages).
     * AI pipeline issues (e.g., models hanging or failing).
     * Recently deployed code causing unforeseen issues.

2. **Mitigation & Containment**
   Limit the scope of the outage while investigating further.

   * **Initial Mitigation:**

     * Enable fallbacks or circuit breakers (e.g., use cached data, disable AI features).
     * Rollback the most recent deployments if they correlate with the issue.
     * Temporarily disable non-essential services to reduce load.
   * **Communication:**

     * Notify stakeholders (product owners, managers) with a status update.
     * Provide transparency regarding ongoing actions and estimated resolution time.

3. **Resolution**
   Apply the necessary fix to bring the system back online.

   * **Fix Actions:**

     * Reconnect the database or fix connection settings.
     * Retry AI tasks or restart AI services if the pipeline is stuck.
     * Validate that all relevant services (backend, AI, frontend) are functioning properly after adjustments.

   * **Validation:**

     * Run health checks and system tests to ensure the application is stable.
     * Verify that the AI pipeline is processing tasks as expected.
     * Confirm API endpoints are responding with the expected performance.

4. **Postmortem & Learning**
   Analyze the incident, document what happened, and implement lessons learned.

   * **Postmortem Actions:**

     * Document a detailed timeline of the incident, including initial symptoms, diagnosis, and resolution steps.
     * Identify the root cause and contributing factors.
     * Review communication and coordination during the incident.

   * **Learning Actions:**

     * Update monitoring thresholds, ensuring early alerts for similar issues in the future.
     * Update incident response playbooks based on what worked or failed.
     * Add additional observability for AI tasks if AI-specific failures were hard to detect.

---

## **Roles & Responsibilities**

| **Role**               | **Responsibilities**                                                                                                                                                                           |
| ---------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **On-Call Engineer**   | - Initial triage and diagnosis. <br> - Review logs, system metrics, and monitor services. <br> - Implement quick fixes, including fallbacks and service restarts.                              |
| **Backend Engineer**   | - Troubleshoot and resolve database/API issues. <br> - Monitor the AI tasks if the issue is related to AI model processing. <br> - Validate backend systems after resolution.                  |
| **Frontend Engineer**  | - Verify UI and user-facing errors. <br> - Ensure users are properly notified (e.g., through error messages or status alerts). <br> - Confirm frontend stability post-fix.                     |
| **Bridge Engineer**    | - Coordinate across teams, ensuring a comprehensive response. <br> - Oversee system-wide issue resolution and prevent siloed problem-solving. <br> - Maintain communication with stakeholders. |
| **Documentation Lead** | - Maintain a real-time incident timeline. <br> - Document decisions made and steps taken. <br> - Write the postmortem report with clear root cause analysis.                                   |

---

## **Key Takeaways**

* **Bridge Engineers** play a crucial role in ensuring **cross-team communication** and full-system visibility during high-pressure incidents.
* **Observability and logging** are critical in rapidly identifying issues, especially in distributed systems that include AI features.
* **Postmortems** provide a valuable opportunity to convert a crisis into long-term **systemic improvements**.
* **Regular drills** ensure that the team is prepared for real-world outages, fostering both **confidence** and **resilience** in handling critical incidents.

---

## **Final Reflection**

* By running regular **3 AM outage simulations**, you ensure that teams are not only equipped with the technical knowledge to respond to crises, but also trained in **coordinated problem-solving**, **AI troubleshooting**, and **clear communication**.
* The goal of the drill is not just to fix the problem at hand but to make the system more **robust** and the team more **prepared** for future incidents.

