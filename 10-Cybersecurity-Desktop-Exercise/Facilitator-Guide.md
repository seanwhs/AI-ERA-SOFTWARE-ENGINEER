# 🖥 **Cybersecurity Desktop Exercise — Facilitator Guide**

**Objective:**
Guide engineering and security teams through a hands-on exercise focused on detecting, analyzing, and mitigating a cybersecurity incident. This exercise emphasizes **human-first investigation** combined with AI-assisted response and decision-making.

---

## **Roles & Responsibilities**

| Role                        | Responsibilities                                                                                                 |
| --------------------------- | ---------------------------------------------------------------------------------------------------------------- |
| **Lead Facilitator**        | Guide the entire workshop, ensure objectives are met, and keep time                                              |
| **Threat Scenario Monitor** | Trigger incidents, inject red herrings, and provide context for the exercise                                     |
| **AI Moderator**            | Provide AI prompts, assist with AI-based suggestions, and observe the interaction between human and AI responses |
| **Observer/Note-Taker**     | Capture decisions made, the timing of events, and document lessons learned                                       |

---

## **Timings & Phases**

| **Phase**                | **Duration** | **Key Notes**                                                                                                               |
| ------------------------ | ------------ | --------------------------------------------------------------------------------------------------------------------------- |
| **Orientation**          | 0:00–0:10    | Assign roles, explain the **human-first** approach to incident response.                                                    |
| **Setup**                | 0:10–0:15    | Prepare dashboards, log access, and AI prompts. Ensure that everything is ready for the threat detection phase.             |
| **Threat Detection**     | 0:15–1:00    | Begin human-only investigation. Observe how teams react to initial signs of incidents. Note missed alerts and red herrings. |
| **Reflection**           | 1:00–1:10    | Discuss early detection techniques, assumptions made, and use of dashboards for monitoring.                                 |
| **Deep Dive**            | 1:10–1:50    | Teams will analyze logs, correlate events, and validate the root cause of the incident.                                     |
| **Break**                | 1:50–2:00    | Reset the environment, prep AI prompts for the next phase.                                                                  |
| **AI Remediation**       | 2:00–2:30    | Teams will apply AI-generated remediation strategies. Human verification is required to confirm AI decisions.               |
| **Post-Incident Review** | 2:30–2:50    | Finalize the incident report, update guardrails, and discuss lessons learned.                                               |
| **Wrap-Up**              | 2:50–3:00    | Review metrics, assess team performance, and discuss takeaways.                                                             |

---

## **Red-Herring Triggers**

Red herrings are fake incidents that can confuse or distract the team from the true root cause of the issue. They test the team's ability to focus and avoid jumping to conclusions based on false indicators.

| **Red-Herring**                        | **Description**                                                                  |
| -------------------------------------- | -------------------------------------------------------------------------------- |
| **High CPU Usage on a Benign Process** | An increase in CPU usage due to normal system processes (e.g., batch job).       |
| **Spike in Harmless Network Traffic**  | An unexpected spike in traffic due to scheduled data sync or internal updates.   |
| **False-Positive Malware Alert**       | A security system flags a benign file as malicious, causing unnecessary concern. |

**Facilitator Tip:** Introduce these red herrings **strategically** to test if teams **validate the source** of the alert before acting on it. For example, if the system shows high CPU usage, check if the team investigates whether it’s related to a scheduled task.

---

## **AI-Assisted Intervention**

During the **AI Remediation** phase, the team will interact with AI tools that provide suggestions or recommendations for how to proceed. The key here is **human verification**: teams must confirm that the AI’s suggestions align with the situation before applying the changes.

### **AI Prompts May Include:**

* **Identifying Malicious Activity:** AI identifies unusual login patterns and suggests blocking suspicious IPs.
* **Mitigation Recommendations:** AI suggests firewall rules or configuration changes in response to detected attacks.
* **Log Correlation Assistance:** AI cross-references logs for anomalies, offering insights into potential breach points.

**Facilitator Tip:** Ensure that **AI-assisted decisions** do not override critical human judgment. Remind the team that AI is a tool for **augmentation**, not replacement.

---

## **Metrics & Reflection**

After the exercise, review the **metrics** that highlight the effectiveness of the response. This will help teams identify areas of improvement for future exercises or real-world incidents.

### **Metrics to Track:**

| **Metric**                          | **Target**  | **Observed** | **Notes**                                               |
| ----------------------------------- | ----------- | ------------ | ------------------------------------------------------- |
| **Incident Detection Accuracy**     | ≥90%        |              | Did the team identify critical incidents early?         |
| **Red-Herring Identification Rate** | ≥80%        |              | How well did the team spot false alerts?                |
| **AI Integration Effectiveness**    | Medium-High |              | Was the AI used effectively without causing confusion?  |
| **Root Cause Identification Time**  | ≤30 mins    |              | How quickly was the true cause identified?              |
| **Remediation Accuracy**            | 100%        |              | Was the correct action taken in response to the threat? |

---

## **Post-Incident Review**

Following the AI-assisted remediation, take the time to **review** the entire incident response:

1. **What went well?**
   Were there any particularly strong detections or mitigations? What helped speed up the response?

2. **What could be improved?**
   Were there any missed signals early in the process? Were any red herrings confused with real incidents?

3. **What lessons were learned?**
   Based on the exercise, how can the team improve their future responses? What changes should be made to monitoring or escalation processes?

4. **Updating Guardrails**
   Based on lessons learned, update any **guardrails** or **alert configurations** to prevent similar incidents in the future.

---

### **Facilitator Tips:**

* **Human-First:** Stress the importance of human decision-making. AI should **support**, not replace, human investigators.
* **Escalation Process:** Remind teams about the escalation process. If they can’t resolve the issue, they should be able to **escalate** with the right context.
* **Keep the Atmosphere Collaborative:** These exercises are about learning, not pointing out failures. Make it clear that everyone, from the facilitator to the note-taker, is part of the process.

---

**End of Guide**
**Good luck with your cybersecurity desktop exercise!**
