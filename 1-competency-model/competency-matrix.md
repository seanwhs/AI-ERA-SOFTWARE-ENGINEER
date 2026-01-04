# 📊 AI-Era Software Engineering Competency Matrix

This competency matrix defines **what good looks like** for software engineers in the AI era.
It is designed for **self-assessment, coaching, and hiring calibration**.

> In the AI era, competence is measured by **judgment, ownership, and system-level thinking**, not just code.

---

## 🧠 Dimension 1: System Thinking

| Level                  | Observable Behavior                                                             |
| ---------------------- | ------------------------------------------------------------------------------- |
| **Foundational**       | Understands individual components in isolation; follows examples.               |
| **Functional**         | Can trace requests across layers with guidance; understands dependencies.       |
| **Bridge Engineer**    | Independently reasons about data flow, state, and failure modes.                |
| **Senior / Architect** | Designs systems with explicit trade-offs, failure containment, and scalability. |

---

## 🔧 Dimension 2: Backend Ownership (Python / Django)

| Level                  | Observable Behavior                                                               |
| ---------------------- | --------------------------------------------------------------------------------- |
| **Foundational**       | Writes views and models following examples.                                       |
| **Functional**         | Avoids common ORM pitfalls; understands serializers and validation.               |
| **Bridge Engineer**    | Treats APIs as contracts; enforces validation, authorization, and data integrity. |
| **Senior / Architect** | Designs schemas, services, and APIs resilient to change and systemic failure.     |

---

## 🎨 Dimension 3: Frontend Integration (React / TypeScript)

| Level                  | Observable Behavior                                                                     |
| ---------------------- | --------------------------------------------------------------------------------------- |
| **Foundational**       | Builds components that work visually.                                                   |
| **Functional**         | Manages state and effects with discipline; connects to backend services.                |
| **Bridge Engineer**    | Aligns frontend types and validation with backend contracts.                            |
| **Senior / Architect** | Designs long-term data flow, observability, and maintainability for complex UI systems. |

---

## 🔐 Dimension 4: Integration & Security

| Level                  | Observable Behavior                                                              |
| ---------------------- | -------------------------------------------------------------------------------- |
| **Foundational**       | Uses authentication libraries without fully understanding lifecycle or risks.    |
| **Functional**         | Understands JWT, session management, and basic permissions.                      |
| **Bridge Engineer**    | Enforces security boundaries across layers; audits AI-generated code.            |
| **Senior / Architect** | Designs systems assuming hostile input; applies Zero Trust and defense-in-depth. |

---

## 🤖 Dimension 5: AI Orchestration

| Level                  | Observable Behavior                                                                        |
| ---------------------- | ------------------------------------------------------------------------------------------ |
| **Foundational**       | Uses AI as a code generator.                                                               |
| **Functional**         | Reviews AI output superficially for correctness.                                           |
| **Bridge Engineer**    | Audits AI code for logic, contracts, and security implications.                            |
| **Senior / Architect** | Designs workflows that constrain AI safely; defines boundaries for autonomous AI behavior. |

---

## 🚨 Dimension 6: Failure & Production Readiness

| Level                  | Observable Behavior                                                                          |
| ---------------------- | -------------------------------------------------------------------------------------------- |
| **Foundational**       | Reacts to failures without clear strategy.                                                   |
| **Functional**         | Can debug with logs when guided; escalates appropriately.                                    |
| **Bridge Engineer**    | Anticipates failures; designs graceful degradation.                                          |
| **Senior / Architect** | Designs systems to fail predictably; leads postmortems and improves reliability system-wide. |

---

# Core Competencies — AI-Era Software Engineer

Each competency focuses on **decision-making, system thinking, and accountability**, which cannot be delegated to AI.

---

## 1. Problem Solving & Requirements Engineering

**Description**
Translate ambiguous business needs into precise, testable technical requirements.

**Key Skills**

* Requirements elicitation and clarification
* Problem decomposition
* Constraint identification (cost, time, compliance)
* Success metrics definition

**Typical Tasks**

* Write functional and non-functional requirements
* Identify edge cases and failure scenarios
* Define acceptance criteria
* Translate business goals into measurable system objectives

---

## 2. System Design & Software Architecture

**Description**
Design the high-level structure of software systems, including components, interactions, and trade-offs.

**Key Skills**

* Architectural pattern selection (monolith, microservices, event-driven, serverless)
* API and contract design
* Data flow and state management
* Scalability, reliability, and performance planning
* Trade-off analysis and documentation

**Typical Tasks**

* Create architecture diagrams (C4, component, sequence)
* Define service boundaries and ownership
* Design APIs and integration contracts
* Plan for failure, retries, and degradation
* Document architectural decisions (ADRs)

**AI-Era Shift**
Engineers increasingly **specify systems** while AI assists with implementation.
Human judgment prevents accidental complexity and systemic risk.

---

## 3. Technical Specification & Execution

**Description**
Bridge architecture to implementation through precise specifications guiding humans and AI tools.

**Key Skills**

* Interface and contract definition
* Data schema design
* Performance and SLA specification
* Dependency and version management

**Typical Tasks**

* Write technical design documents
* Define API schemas (OpenAPI, GraphQL)
* Specify error handling and retry behavior
* Constrain AI-generated code through precise specifications

---

## 4. Security Engineering (Secure by Design)

**Description**
Embed security from design, not as an afterthought.

**Key Skills**

* Threat modeling and attack surface analysis
* Secure defaults and least privilege
* Identity and access management (IAM)
* Defense-in-depth strategies

**Typical Tasks**

* Perform threat modeling (STRIDE, attack trees)
* Design authentication and authorization flows
* Apply least-privilege access controls
* Review AI-generated code for vulnerabilities

---

## 5. Zero Trust Architecture

**Description**
Design systems that **assume no implicit trust**, continuously verify identity, context, and intent.

**Key Skills**

* Identity-centric design
* Micro-segmentation
* Policy enforcement points
* Continuous verification

**Typical Tasks**

* Design systems with no trusted network perimeter
* Enforce authentication and authorization for all requests
* Reduce blast radius of compromise

---

## 6. Verification, Testing & Risk Management

**Description**
Ensure correctness, safety, and reliability, particularly for AI-assisted systems.

**Key Skills**

* Test strategy design
* Automated testing
* Observability and monitoring
* Failure analysis

**Typical Tasks**

* Define unit, integration, and contract tests
* Validate AI-generated code
* Monitor production behavior
* Conduct post-incident reviews

---

## 7. AI Usage Policies

**Allowed Uses**

* Code scaffolding with review
* Refactoring existing code
* Test generation
* Documentation drafts
* Exploratory design alternatives

**Restricted Uses**

* Direct production deployment without review
* Security-critical logic without human validation
* Infrastructure or IAM changes without approval

**Prohibited Uses**

* Autonomous production changes
* Self-modifying systems without controls
* Blind trust in AI outputs

---

## 8. Postmortem Examples

### Example 1 — Silent Data Corruption

* **Incident:** AI-generated transformation passed tests but violated invariants
* **Impact:** Incorrect financial reports
* **Fix:** Introduce property-based tests, document invariants, review AI output

### Example 2 — Over-Permissive IAM

* **Incident:** AI Terraform granted wildcard permissions
* **Impact:** Unauthorized access to internal resources
* **Fix:** Secure-by-default templates, mandatory review, least-privilege enforcement

### Example 3 — Automation Cascade

* **Incident:** AI retry logic triggered feedback loop
* **Impact:** Self-inflicted outage
* **Fix:** Retry budgets, circuit breakers, kill switches, observability

---

## Core Principle

AI accelerates implementation.
Engineers remain responsible for **design, security, and outcomes**.

> Ownership is the differentiator in the AI era.

