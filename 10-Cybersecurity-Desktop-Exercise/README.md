# 🖥 Cybersecurity Desktop Exercise — AI-Era System Owner

**Exercise Name:** 🛡️ 3 A.M. Cybersecurity Desktop Exercise
**Duration:** 120–180 minutes
**Participants:** 6–12 engineers / security team
**Instructor Ratio:** 1:6

**Objective:**
Simulate a **critical cybersecurity incident** to train engineers in **threat detection, analysis, remediation, and post-incident reporting**, integrating AI tools **without replacing human judgment**.

---

## 1️⃣ Exercise Goals

**Primary Goals:**

1. Detect and analyze cybersecurity incidents under pressure.
2. Apply AI-assisted threat detection and remediation responsibly.
3. Strengthen **log correlation, threat hunting, and alerting dashboards**.
4. Build **muscle memory for incident response and post-mortem documentation**.

**Secondary Goals:**

* Practice **identifying false positives / red herrings**.
* Improve **post-incident report quality** for audits or management.
* Measure **AI-assisted detection accuracy and remediation speed**.

---

## 2️⃣ Exercise Logistics

| Item        | Description                                                                               |
| ----------- | ----------------------------------------------------------------------------------------- |
| Environment | Simulated network, endpoints, servers, cloud services, SIEM dashboards                    |
| Tools       | SIEM (Splunk/ELK), IDS/IPS, firewall logs, vulnerability scanner, AI agent (GPT-4/Claude) |
| Scenarios   | Phishing attack, ransomware execution, privilege escalation, data exfiltration            |
| Materials   | Post-Exercise Report Template, Facilitator Quick-Reference Sheet, Attack Scripts          |
| Roles       | Lead Facilitator, Threat Scenario Monitor, AI Moderator, Observer / Note Taker            |

---

## 3️⃣ Exercise Agenda

| Time      | Phase                            | Activities                                                                        | Facilitator Notes                                                          |
| --------- | -------------------------------- | --------------------------------------------------------------------------------- | -------------------------------------------------------------------------- |
| 0:00–0:10 | Orientation                      | Welcome, objectives, team roles                                                   | Emphasize human-first investigation                                        |
| 0:10–0:15 | Setup                            | Verify dashboards, logs, AI prompts                                               | Ensure simulated network & SIEM is live                                    |
| 0:15–1:00 | Phase 1: Threat Detection        | Inject incidents (malware alerts, suspicious login, network anomaly)              | Teams investigate **without AI**, identify indicators of compromise (IoCs) |
| 1:00–1:10 | Reflection Break                 | Discuss early detection signals                                                   | Identify missed vs captured alerts                                         |
| 1:10–1:50 | Phase 2: Analysis & Verification | Correlate logs, trace attacker path, prioritize threats                           | Encourage structured incident response                                     |
| 1:50–2:00 | Break                            | Reset mental context                                                              | Prepare AI prompts                                                         |
| 2:00–2:30 | Phase 3: AI-Assisted Remediation | AI suggests mitigation steps: isolate endpoints, block IPs, patch vulnerabilities | Human team verifies AI actions before implementation                       |
| 2:30–2:50 | Phase 4: Post-Incident Review    | Update incident report, mitigation procedures, preventive controls                | Encourage blameless review; include lessons learned                        |
| 2:50–3:00 | Wrap-Up                          | Debrief, metrics review                                                           | Highlight detection time, fix accuracy, red-herring handling               |

---

## 4️⃣ Scenarios & Threat Injection Examples

| Scenario             | Fault / Injection                        | Red-Herring / Twist                  | Observables                             |
| -------------------- | ---------------------------------------- | ------------------------------------ | --------------------------------------- |
| Phishing Email       | Malicious link sent to test accounts     | Simulated benign spam emails         | Email logs, click events, SOC alert     |
| Ransomware Execution | Simulated encryption process on endpoint | Background CPU spike (non-malicious) | Endpoint logs, AV alerts, SIEM events   |
| Privilege Escalation | Unauthorized sudo/root attempts          | Admin maintenance scripts            | Auth logs, sudo log, PAM alerts         |
| Data Exfiltration    | Large file transfer to external IP       | Legit file backup                    | Network logs, firewall logs, IDS alerts |

---

## 5️⃣ Learning Objectives by Scenario

| Scenario             | Human-First Skills                                  | AI-Assisted Skills                                          |
| -------------------- | --------------------------------------------------- | ----------------------------------------------------------- |
| Phishing             | Detect suspicious emails, confirm IoC               | Suggest quarantine, flag accounts, automated email analysis |
| Ransomware           | Identify encrypted files, correlate endpoint alerts | Recommend endpoint isolation, restore from backup           |
| Privilege Escalation | Trace abnormal login paths                          | Suggest account lock, patch known exploits                  |
| Data Exfiltration    | Monitor unusual network activity                    | Recommend firewall rules, IPS/IDS alerts                    |

---

## 6️⃣ Metrics & Success Criteria

| Metric                       | Target                       |
| ---------------------------- | ---------------------------- |
| Threat detection time        | ≤30 min per scenario         |
| Fix success rate             | 100%                         |
| AI suggestion accuracy       | ≥90%                         |
| Red-Herring Handling         | Correctly distinguished 80%+ |
| Post-Incident Report Quality | Complete & actionable        |

---

## 7️⃣ Post-Exercise Reflection

**Team Questions:**

1. Which indicators were most effective for early threat detection?
2. How accurately did AI assist without introducing risk?
3. Were any false positives or red herrings misleading?
4. How can dashboards, alerts, or logs be improved?

**Deliverables:**

* Completed Post-Incident Report per team
* Metrics dashboard for detection & remediation
* Updated incident response playbooks
* Lessons learned and preventive actions

---

## 8️⃣ Facilitator Notes & Quick Tips

* Keep **pressure realistic but safe** — encourage blameless decision-making.
* Rotate scenario difficulty and red herrings for senior teams.
* Track **metrics consistently**: detection time, AI effectiveness, red-herring handling.
* Reinforce **human-first mindset**; AI assists, but humans approve.
* Use breaks as **reflection checkpoints** — discuss assumptions, missteps, and learnings.

---

✅ **Outcome:** Teams learn to **detect, analyze, and remediate security incidents under pressure**, **evaluate AI assistance**, and **document actionable lessons** for future incidents.

---


