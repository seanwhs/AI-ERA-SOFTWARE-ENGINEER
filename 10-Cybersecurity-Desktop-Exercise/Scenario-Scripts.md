# 🖥 **Cybersecurity Desktop Exercise — Scenario Scripts & Red-Herring Triggers**

**Objective:**
Provide realistic, hands-on scenarios for cybersecurity response teams to simulate real-world threats, including **red-herrings** to test their decision-making, attention to detail, and use of AI tools for incident detection and remediation.

---

## **Scenario 1: Phishing Attack**

**Situation Overview:**
A series of simulated phishing emails are sent to employees, aiming to capture login credentials. The emails contain malicious links designed to trick users into visiting a fake website.

### **Actions to Simulate:**

1. **Email Campaign:** Send out fake phishing emails with malicious URLs.
2. **Sandbox Links:** The links lead to a **sandbox environment** designed to simulate a fake login page for credential capture.
3. **AI Monitoring:** The AI tool can flag emails that look suspicious (e.g., mismatched domains, unusual email addresses).
4. **Initial Detection:** Team should detect suspicious emails or user reports of strange login prompts.

### **Red-Herring:**

* **Benign Spam Emails:** Periodic benign emails with common offers or generic spam content, designed to distract the team and flood the inbox.

### **Facilitator Notes:**

* **Key Objective:** Ensure the team identifies phishing emails based on **email source**, **content analysis**, and **user reports**.
* Track whether the AI-assisted tools flag these emails as suspicious based on heuristics (e.g., suspicious links, unusual domains).
* Encourage **manual investigation** rather than relying on AI alone to detect phishing patterns.

---

## **Scenario 2: Ransomware Simulation**

**Situation Overview:**
A ransomware attack is simulated by encrypting files on an endpoint. The AV (antivirus) system triggers alerts about suspicious activity, and encryption warnings pop up on the infected machines.

### **Actions to Simulate:**

1. **File Encryption Simulation:** Simulate encryption of a few files on an endpoint (e.g., files becoming inaccessible or renamed).
2. **AV Alerts:** Generate antivirus system alerts indicating **potential ransomware** behavior (file modifications, suspicious executables).
3. **AI Monitoring:** AI-assisted monitoring may detect spikes in file encryption or known ransomware indicators (file types being locked, unusual file activity).
4. **Initial Detection:** The team should investigate whether files are genuinely being encrypted, and the AV alerts should prompt a more thorough investigation.

### **Red-Herring:**

* **Background CPU Spike:** Simulate a CPU spike from a non-malicious process, such as a batch job, to confuse the team. This will cause additional performance alerts but should not be treated as part of the ransomware attack.

### **Facilitator Notes:**

* **Key Objective:** Ensure the team distinguishes **true ransomware behavior** from a **non-malicious process**.
* **AI Assistance:** Track if AI can predict ransomware or flag an attack based on **file type activity** and **CPU usage patterns**.
* Encourage **manual investigation** into the AV logs and file types before jumping to conclusions.
* Ensure that AI recommendations are verified by the team and **cross-checked** with known ransomware behavior.

---

## **Scenario 3: Privilege Escalation**

**Situation Overview:**
An attacker (or a malicious insider) is attempting to escalate their privileges within a system. Fake **sudo/root attempts** are generated and logged in the system logs.

### **Actions to Simulate:**

1. **Generate Fake Logs:** Create sudo/root escalation attempts in the system logs (e.g., attempts to use `sudo` for unauthorized commands).
2. **AI Monitoring:** AI-assisted tools may flag suspicious `sudo` usage or privilege escalation events in real-time.
3. **Initial Detection:** The team should notice abnormal user activity, such as unauthorized attempts to gain administrative access.

### **Red-Herring:**

* **Admin Maintenance Scripts:** Simulate admin maintenance scripts running with high login activity. This is legitimate but will appear as if the system is being compromised.

### **Facilitator Notes:**

* **Key Objective:** Ensure the team is able to differentiate between legitimate admin activity and **suspicious privilege escalation** attempts.
* **AI Assistance:** Track if AI tools are able to detect **elevated privileges** and highlight potential vulnerabilities in the **privileged access** model.
* Encourage teams to **verify logs** thoroughly before taking corrective action.

---

## **Scenario 4: Data Exfiltration**

**Situation Overview:**
A large file transfer is happening from an internal system to an external IP address, potentially indicating **data exfiltration** by an attacker.

### **Actions to Simulate:**

1. **Large File Transfer Simulation:** Simulate a large file transfer to an external IP (could be a sensitive file).
2. **AI Monitoring:** AI can detect unusual data transfer patterns, especially if files are leaving the internal network without authorization.
3. **Initial Detection:** The team should detect large data transfers and investigate the destination, volume, and type of files being transferred.

### **Red-Herring:**

* **Legitimate Backup Process:** A scheduled **backup process** could generate similar traffic patterns as the exfiltration attempt, distracting the team.

### **Facilitator Notes:**

* **Key Objective:** Ensure the team investigates **data flows** and **IP destination** correctly to confirm whether the file transfer is malicious.
* **AI Assistance:** AI may suggest abnormal data transfer activity, but **human verification** is crucial to ensure the transfer is truly unauthorized.
* Encourage the team to examine **data source** and **destination IPs**, cross-checking against known systems (e.g., backup servers) and reviewing the **type of file** being exfiltrated.

---

## **Notes for Facilitators**

1. **Inject Red Herrings Strategically:**
   The purpose of the red herrings is to **test the team's focus** and ability to identify **real threats amidst distractions**. Ensure red herrings are introduced intermittently throughout the exercise and not all at once.

2. **Track Metrics:**
   As the exercise progresses, track key metrics such as:

   * **Detection Time:** How quickly can the team identify the issue?
   * **AI Assistance Usage:** Was AI helpful, and did the team validate AI suggestions before applying them?
   * **Decision Accuracy:** Did the team take the correct actions in response to the identified threat?

3. **Difficulty Scaling:**
   Start with **Scenario 1** (Phishing Attack) for less experienced teams, and gradually increase difficulty with **Scenario 2** (Ransomware) and **Scenario 3** (Privilege Escalation).
   For senior teams, **Scenario 4** (Data Exfiltration) can be more complex, involving cross-referencing multiple systems and distinguishing between legitimate and malicious traffic.

4. **Rotate Scenarios:**
   To ensure different skill sets are challenged, rotate scenarios every 60 minutes. This also ensures **fresh perspectives** and prevents fatigue from setting in.

5. **Post-Exercise Debrief:**
   After the exercise, gather feedback from the team on how they handled the scenarios. Discuss:

   * **What went well?**
   * **What could be improved?**
   * **How did the red herrings impact decision-making?**
   * **What improvements can be made to the AI-assisted monitoring tools?**

---

### **End of Guide**

**Good luck with your cybersecurity desktop exercise!**
