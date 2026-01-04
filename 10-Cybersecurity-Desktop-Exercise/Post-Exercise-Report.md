# 🖥 **Cybersecurity Desktop Exercise — Post-Exercise Report Template**

---

### **Exercise Details**

**Exercise Date:** _______
**Facilitator:** _______
**Team / Participants:** _______

---

## **1️⃣ Overview**

> **Objective**: Provide a brief summary of the exercise’s goals, the scenarios used to simulate real-world cyberattacks, and the human-first investigation approach emphasized throughout the exercise.

* **Objective of the Exercise**:
  The purpose of this exercise was to test the team's ability to detect, investigate, and mitigate cybersecurity threats using a combination of human-led investigation techniques and AI-assisted support tools. Participants were tasked with responding to a series of evolving incidents, with a focus on enhancing threat detection, analyzing root causes, and improving their response time under pressure.

* **Scenarios Covered**:
  The exercise involved several critical scenarios, including phishing, ransomware attacks, privilege escalation, and data exfiltration. Each scenario tested the team’s ability to identify and mitigate threats before they caused significant damage.

* **Human-First Investigation Approach**:
  Emphasizing the importance of human expertise in cybersecurity, the exercise encouraged participants to rely on investigative instincts, validate AI suggestions, and prioritize analysis over blind reliance on automation.

---

## **2️⃣ Scenarios & Analysis**

| **Scenario**             | **Root Cause**                                | **Human-Only Investigation Notes**                                               | **AI-Assisted Actions**                                    | **Success Metrics**                          | **Lessons Learned**                                                |
| ------------------------ | --------------------------------------------- | -------------------------------------------------------------------------------- | ---------------------------------------------------------- | -------------------------------------------- | ------------------------------------------------------------------ |
| **Phishing**             | (e.g., email spoofing)                        | (e.g., team initially mistook it for a legitimate email, delayed identification) | (e.g., AI flagged suspicious links)                        | (e.g., detection time, response time)        | (e.g., need for better phishing awareness, AI suggestion accuracy) |
| **Ransomware**           | (e.g., malicious file download)               | (e.g., human detection through file system anomalies, but delayed action)        | (e.g., AI flagged encryption pattern)                      | (e.g., fix success rate, time to isolate)    | (e.g., enhance endpoint monitoring)                                |
| **Privilege Escalation** | (e.g., unauthorized sudo attempt)             | (e.g., initial investigation focused on user behavior)                           | (e.g., AI alerted on suspicious login patterns)            | (e.g., time to resolve, root cause analysis) | (e.g., improve access control monitoring)                          |
| **Data Exfiltration**    | (e.g., large outbound traffic, rogue insider) | (e.g., investigation focused on traffic analysis, but false positive delays)     | (e.g., AI detected anomalous traffic and flagged transfer) | (e.g., data exfiltration response time)      | (e.g., better traffic monitoring tools needed)                     |

---

## **3️⃣ Team Reflection**

* **Most Effective Investigative Techniques**:
  (e.g., manual log reviews, traffic analysis, endpoint monitoring, etc.)

  * **What worked well?** (e.g., team's ability to analyze log anomalies early in the ransomware attack)
  * **What could be improved?** (e.g., reliance on automatic alerts without confirming root cause)

* **Assumptions That Delayed Detection**:
  (e.g., assuming that high traffic spikes were part of a normal system maintenance, or mistaking legitimate admin actions for a threat)

  * **What assumptions were made that hindered the detection process?** (e.g., missed alerts due to disregarding AI suggestions, delayed investigation due to assumptions about low-priority threats)

* **AI Assistance Effectiveness**:
  (e.g., did AI tools help in accelerating the threat detection and remediation process?)

  * **Was AI helpful in detecting threats?** (e.g., AI helped by pointing out unusual patterns in ransomware detection)
  * **Where did AI fall short?** (e.g., false positive alerts or inability to detect specific attack vectors like insider threats)

* **Dashboard, Log, or Alert Improvements**:
  (e.g., feedback on how the team interacted with dashboards, logs, and alerts during the exercise)

  * **What improvements are needed in monitoring systems or logs?** (e.g., adding more granular alerts for privilege escalation attempts, enhancing logs for better clarity)

---

## **4️⃣ Preventive Actions & Next Steps**

* **Updated Alerts, SIEM Rules, Guardrails**:
  (e.g., create new SIEM rules for suspicious admin logins, enhance traffic monitoring)

  * **Action Items**: (e.g., implement more refined filtering for phishing emails, update alert thresholds)

* **Runbook Improvements**:
  (e.g., enhance incident response procedures to cover new attack vectors identified in the exercise)

  * **Action Items**: (e.g., integrate AI suggestions more seamlessly into runbooks for quicker decision-making)

* **Follow-Up Drills**:
  (e.g., plan future exercises based on findings from this drill)

  * **Action Items**: (e.g., schedule additional phishing response drills, simulate insider threat scenarios, enhance collaboration between teams for post-incident analysis)

---

### **Facilitator Comments:**

(Here, facilitators can add any additional feedback, notable points from the exercise, or areas that may require further attention in future drills.)

---

### **Final Thoughts:**

This post-exercise report serves as an opportunity for teams to reflect on their performance, enhance future preparedness, and integrate lessons learned into their cybersecurity strategy. The focus on **human-first investigation** combined with **AI-assisted remediation** will continue to improve our ability to quickly and effectively respond to real-world cyber threats.
