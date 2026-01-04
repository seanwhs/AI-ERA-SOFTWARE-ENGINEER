## ✅ **AI-Era Software Engineering Competency Checklist**

### **I. Core Competencies**

#### **1. Requirements Engineering & Problem Decomposition**

* [ ] I can transform ambiguous business needs into clear, actionable technical requirements.
* [ ] I identify constraints and define success metrics for each project.
* [ ] I use AI to brainstorm edge cases but ensure the problem is well-framed and the acceptance criteria are defined.

#### **2. System Design & Architectural Sovereignty**

* [ ] I design systems with attention to scalability, reliability, and trade-offs.
* [ ] I ensure effective interaction between system components through architectural patterns and API contracts.
* [ ] I validate that my designs are resilient and aligned with long-term goals, while using AI to assist in implementation.

#### **3. Secure by Design & Zero Trust**

* [ ] I integrate security into every layer of the system, following a **Zero Trust** mindset.
* [ ] I model threats, enforce least-privilege policies, and manage identity and encryption.
* [ ] I audit AI-generated security policies to ensure they align with **Zero Trust** principles.

#### **4. Verification, Testing & Risk Management**

* [ ] I design robust test strategies, especially for AI-generated outputs.
* [ ] I apply automated testing and failure analysis techniques to ensure the safety and reliability of systems.
* [ ] I design for observability and risk management, especially for AI systems in production.

---

### **II. AI Usage & Governance**

#### **Allowed (Accelerants)**

* [ ] I use AI for code scaffolding and boilerplate generation.
* [ ] I leverage AI for refactoring and logic cleanup.
* [ ] I generate unit tests and documentation using AI for efficiency.
* [ ] I explore design alternatives with AI.

#### **Restricted (High-Stakes)**

* [ ] I do not deploy code directly to production without review.
* [ ] I ensure no AI-generated code handles security-critical logic or sensitive data (e.g., IAM, PII).
* [ ] I never blindly trust AI outputs and ensure human oversight before deployment.

#### **Prohibited (Liability)**

* [ ] I avoid using AI for autonomous production changes.
* [ ] I do not allow AI-generated code to self-modify systems or bypass human review.

---

### **III. Growth Dimensions**

#### **System Thinking**

* [ ] I understand basic workflows and follow established patterns (Foundational).
* [ ] I map data flows and dependencies across multiple layers (Functional).
* [ ] I anticipate failure modes and reason about system behavior in distributed environments (Bridge Engineer).
* [ ] I design for scalability and resilience while balancing trade-offs across the system (Senior/Architect).

#### **Backend Ownership (Python/Django)**

* [ ] I write basic views/models with error handling (Foundational).
* [ ] I understand serializers, validation, and authorization (Functional).
* [ ] I ensure APIs are immutable contracts, securing data integrity (Bridge Engineer).
* [ ] I design scalable, resilient backend systems and anticipate performance bottlenecks (Senior/Architect).

#### **Frontend Integration (React/TypeScript)**

* [ ] I build basic UI components and integrate them with mock data (Foundational).
* [ ] I manage state, handle side effects, and integrate with backend services (Functional).
* [ ] I ensure frontend validation aligns with backend contracts (Bridge Engineer).
* [ ] I design maintainable, scalable UIs with observability (Senior/Architect).

#### **Security Integration & Management**

* [ ] I understand basic security principles (JWT, session management) (Foundational).
* [ ] I implement advanced security mechanisms like OAuth, JWTs, and secure APIs (Functional).
* [ ] I audit AI-generated code for security flaws (Bridge Engineer).
* [ ] I design using **Zero Trust** principles, ensuring full compliance (Senior/Architect).

#### **AI Orchestration**

* [ ] I use AI for code scaffolding, documentation, and basic debugging (Foundational).
* [ ] I review AI-generated outputs for correctness and safety (Functional).
* [ ] I audit AI-generated code for compliance with system architecture and security standards (Bridge Engineer).
* [ ] I design AI workflows with defined boundaries, ensuring human oversight (Senior/Architect).

#### **Failure & Production Readiness**

* [ ] I react to failures but lack a clear recovery plan (Foundational).
* [ ] I can debug and escalate issues with guidance, identifying root causes (Functional).
* [ ] I anticipate failures and design for graceful degradation (Bridge Engineer).
* [ ] I lead postmortems and design systems that fail predictably and improve over time (Senior/Architect).

---

### **IV. Incident Anatomy (AI Failures)**

#### **Incident Type: Silent Data Corruption**

* [ ] I recognize when AI refactor violates business rules or data invariants.
* [ ] I implement **Property-Based Testing** to catch inconsistencies early.

#### **Incident Type: Over-Permissive IAM**

* [ ] I identify overly broad permissions granted by AI-generated code.
* [ ] I enforce **Mandatory Human Review** for all security-critical changes.

#### **Incident Type: Automation Cascade**

* [ ] I notice when AI retry loops cause cascading failures (e.g., DDoS).
* [ ] I design **Circuit Breakers** and set hard limits for retry loops.

---

### **V. The Growth Ladder**

#### **Senior / Architect**

* [ ] I take full lifecycle responsibility for the system’s design, architecture, and operations.
* [ ] I constrain and audit AI to ensure it aligns with operational standards, security, and system objectives.
* [ ] I focus on high-level architecture, trade-offs, mentorship, and long-term system design.

#### **Bridge Engineer**

* [ ] I own key system components and integrations.
* [ ] I review and audit AI outputs to ensure compliance with design, security, and architecture standards.
* [ ] I ensure system stability, manage dependencies, and enforce architectural decisions.

#### **Functional**

* [ ] I implement features or modules with a focus on quality and efficiency.
* [ ] I use AI as a co-pilot to speed up development, debugging, and testing.
* [ ] I maintain operational standards, ensuring systems work correctly and reliably.

#### **Foundational**

* [ ] I work under guidance, taking ownership of task-level responsibilities.
* [ ] I use AI for scaffolding, documentation, and learning.
* [ ] I focus on learning system design and solving basic problems in code.

---

### 💡 **Core Principle**

* [ ] I understand that **AI accelerates development**, but **I am ultimately responsible** for the direction, decisions, and outcomes of my systems.

---

