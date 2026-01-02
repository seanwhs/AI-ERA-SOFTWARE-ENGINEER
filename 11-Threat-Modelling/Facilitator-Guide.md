# 🛡️ Threat Modeling Exercise — Facilitator’s Guide

**Exercise Name:** Threat Modeling – Payments Microservice / AI-Era System
**Duration:** 90–120 minutes
**Participants:** 4–8 engineers per team
**Facilitator Ratio:** 1:4 recommended

---

## 1️⃣ Facilitator Roles & Responsibilities

| Role                     | Responsibilities                                                                       |
| ------------------------ | -------------------------------------------------------------------------------------- |
| Lead Facilitator         | Introduce threat modeling concepts, guide exercises, manage timing                     |
| Threat Scenario Designer | Prepare attack vectors, red-herrings, and scoring criteria                             |
| Observer/Note-Taker      | Record observations, participant reasoning, decisions, and metrics                     |
| AI Moderator (Optional)  | Support teams with AI-assisted threat identification while ensuring human verification |

**Tip:** Rotate roles in repeated exercises to develop facilitator expertise and maintain unbiased observation.

---

## 2️⃣ Threat Modeling Exercise Phases

| Phase                         | Duration  | Description                                                       | Facilitator Actions                                                   |
| ----------------------------- | --------- | ----------------------------------------------------------------- | --------------------------------------------------------------------- |
| Orientation                   | 0:00–0:10 | Introduce STRIDE framework, threat agents, assets, and scoring    | Provide printed or ASCII diagrams; clarify human-first approach       |
| Asset & Scope Identification  | 0:10–0:25 | Teams define system boundaries, critical assets, and entry points | Ask guiding questions: "What data or services matter most?"           |
| Threat Agent Analysis         | 0:25–0:45 | Identify likely threat agents and their motivations               | Encourage categorization: external, insider, automated, AI/automation |
| Threat Enumeration            | 0:45–1:10 | Apply STRIDE to enumerate threats                                 | Use prepared examples and red-herrings to test team thinking          |
| Risk Assessment & Scoring     | 1:10–1:25 | Likelihood × Impact → Risk Score; prioritize threats              | Review scores for consistency; highlight high-risk areas              |
| Mitigation & Control Planning | 1:25–1:50 | Define preventive, detective, and corrective measures             | Guide teams to include AI-assisted monitoring where appropriate       |
| Wrap-Up & Reflection          | 1:50–2:00 | Teams present findings and mitigation plan                        | Capture lessons learned and recommendations                           |

---

## 3️⃣ ASCII Diagrams for Quick Reference

**System / Service Flow:**

```
                         +-------------------+
                         |   External User   |
                         +-------------------+
                                  |
                                  v
                         +-------------------+
                         |     API Gateway    |
                         +-------------------+
                         |           |
                         v           v
                 +----------------+  +----------------+
                 | Payments Micro |  | Admin API      |
                 | service        |  | (internal)     |
                 +----------------+  +----------------+
                 |           |               |
                 v           v               v
         +------------+   +------------+  +------------+
         | Transaction|   | Audit Logs|  | CI/CD/DevOps|
         | DB         |   | DB        |  | Pipelines   |
         +------------+   +------------+  +------------+
                 |
                 v
            +-----------+
            | Reporting |
            | / BI      |
            +-----------+
```

**Attack Surface Mapping Example:**

```
Entry Points: External API, Admin API, CI/CD
Data Flows: User -> Gateway -> Microservice -> DB -> Reporting
Dependencies: Payment SDK, PostgreSQL, Logging Service
Threat Agents: External Hacker, Insider, Automated Bot, AI/Automation
```

---

## 4️⃣ Threat Modeling Quick Reference (STRIDE + AI)

| STRIDE                     | Example Threat                       | Potential Impact          | Likelihood | Impact | Risk Score |
| -------------------------- | ------------------------------------ | ------------------------- | ---------- | ------ | ---------- |
| S – Spoofing               | Fake API requests / stolen tokens    | Unauthorized transactions | 4          | 5      | 20         |
| T – Tampering              | Modify transaction totals            | Financial loss            | 3          | 5      | 15         |
| R – Repudiation            | Deleted logs by admin                | Compliance risk           | 2          | 5      | 10         |
| I – Information Disclosure | Sensitive data in logs               | Confidentiality breach    | 3          | 5      | 15         |
| D – Denial of Service      | API flooding / microservice overload | Service downtime          | 4          | 4      | 16         |
| E – Elevation of Privilege | Exploit admin API / CI/CD            | Full system compromise    | 2          | 5      | 10         |

**Facilitator Tip:** Encourage participants to **include AI misuse or misconfiguration** as a threat vector.

---

## 5️⃣ Red-Herrings & Scenario Enhancements

* CPU spike on a non-critical microservice
* QA script generating fake API traffic
* Scheduled maintenance logs appearing as errors
* Misleading AI agent recommendation (simulate misconfigured LLM)

**Tip:** Use red-herrings **strategically** to see if teams validate threats before applying fixes.

---

## 6️⃣ Metrics & Observation Guidelines

| Metric                       | Target      | Observed | Notes                                               |
| ---------------------------- | ----------- | -------- | --------------------------------------------------- |
| Threat Detection Accuracy    | ≥90%        |          | Did teams identify all critical threats?            |
| Red-Herring Handling         | ≥80%        |          | Did teams distinguish symptom vs root cause?        |
| Risk Scoring Alignment       | High        |          | Were high-risk threats prioritized correctly?       |
| Mitigation Plan Completeness | 100%        |          | Preventive, detective, corrective measures included |
| AI Integration Effectiveness | Medium-High |          | Was AI assistance validated by humans?              |

**Tip:** Use metrics during debrief to reinforce best practices.

---

## 7️⃣ Facilitation Tips

* Stress **human-first analysis**: AI suggestions should be reviewed, not blindly accepted
* Encourage **adversarial thinking**: consider attackers’ motivations
* Rotate **scenario complexity**: from Level 1 (basic) to Level 4 (advanced)
* Record **observations in real-time**: timing, red-herring handling, decision points
* Emphasize **post-exercise reflection**: update threat models and mitigation plans

---

## 8️⃣ Post-Exercise Reporting Checklist

* Completed **Threat Model Template** per team
* Documented **risk scores and priority mitigations**
* Captured **lessons learned and red-herring observations**
* Included **AI-assistance evaluation**
* Updated **system / service ASCII diagrams** as reference

---
