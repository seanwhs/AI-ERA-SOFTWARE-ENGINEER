# 📊 Competency Matrix — AI‑Era Software Engineer

This matrix defines **what good looks like** at each capability level.
Use it for self‑assessment, coaching, and hiring calibration.

---

## 🧠 Dimension 1: System Thinking

| Level                  | Observable Behavior                                              |
| ---------------------- | ---------------------------------------------------------------- |
| **Foundational**       | Understands individual components in isolation                   |
| **Functional**         | Can trace a request across layers with guidance                  |
| **Bridge Engineer**    | Independently reasons about data flow, state, and failure modes  |
| **Senior / Architect** | Designs systems with explicit trade‑offs and failure containment |

---

## 🔧 Dimension 2: Backend Ownership (Python / Django)

| Level                  | Observable Behavior                                         |
| ---------------------- | ----------------------------------------------------------- |
| **Foundational**       | Writes views and models following examples                  |
| **Functional**         | Avoids obvious ORM pitfalls, understands serializers        |
| **Bridge Engineer**    | Treats APIs as contracts, enforces validation & permissions |
| **Senior / Architect** | Designs schemas and APIs resilient to change                |

---

## 🎨 Dimension 3: Frontend Integration (React / TypeScript)

| Level                  | Observable Behavior                                    |
| ---------------------- | ------------------------------------------------------ |
| **Foundational**       | Builds components that "work" visually                 |
| **Functional**         | Manages state and effects with some discipline         |
| **Bridge Engineer**    | Aligns frontend types precisely with backend contracts |
| **Senior / Architect** | Designs data flow for long‑term maintainability        |

---

## 🔐 Dimension 4: Integration & Security

| Level                  | Observable Behavior                                 |
| ---------------------- | --------------------------------------------------- |
| **Foundational**       | Uses auth libraries without understanding lifecycle |
| **Functional**         | Understands basic JWT usage and permissions         |
| **Bridge Engineer**    | Enforces security boundaries at correct layers      |
| **Senior / Architect** | Designs systems assuming hostile input              |

---

## 🤖 Dimension 5: AI Orchestration

| Level                  | Observable Behavior                               |
| ---------------------- | ------------------------------------------------- |
| **Foundational**       | Uses AI as a code generator                       |
| **Functional**         | Reviews AI output superficially                   |
| **Bridge Engineer**    | Audits AI code for logic, security, and contracts |
| **Senior / Architect** | Designs workflows that constrain AI safely        |

---

## 🚨 Dimension 6: Failure & Production Readiness

| Level                  | Observable Behavior                         |
| ---------------------- | ------------------------------------------- |
| **Foundational**       | Reacts to failures emotionally              |
| **Functional**         | Can debug with logs when guided             |
| **Bridge Engineer**    | Anticipates failure and degrades gracefully |
| **Senior / Architect** | Designs systems that fail predictably       |

---
# AI-Era Software Engineering Competency Matrix

This matrix defines the competencies required for software engineers in the AI era.
Each competency focuses on **decision-making, system thinking, and accountability** —
skills that cannot be delegated to AI.

---

## 1. Problem Solving & Requirements Engineering

**Description**  
Ability to translate ambiguous business needs into precise, testable technical requirements.

**Key Skills**
- Requirements elicitation and clarification
- Problem decomposition
- Constraint identification (cost, time, compliance)
- Success metrics definition

**Typical Tasks**
- Write functional and non-functional requirements
- Identify edge cases and failure scenarios
- Define acceptance criteria
- Translate business goals into system goals

---

## 2. System Design & Software Architecture

**Description**  
Designing the high-level structure of software systems, including components,
interactions, and trade-offs, to meet functional and quality requirements.

**Key Skills**
- Architectural pattern selection (monolith, microservices, event-driven, serverless)
- API and contract design
- Data flow and state management
- Scalability, reliability, and performance planning
- Trade-off analysis and documentation

**Typical Tasks**
- Create architecture diagrams (C4, component, sequence)
- Define service boundaries and ownership
- Design APIs and integration contracts
- Plan for failure, retries, and degradation
- Document architectural decisions (ADRs)

**AI-Era Shift**
Engineers increasingly **specify systems** while AI assists with implementation.
Human judgment is required to prevent accidental complexity and systemic risk.

---

## 3. Technical Specification & Execution

**Description**  
Bridging architecture to implementation through precise specifications that guide humans and AI tools.

**Key Skills**
- Interface and contract definition
- Data schema design
- Performance and SLA specification
- Dependency and version management

**Typical Tasks**
- Write technical design documents
- Define API schemas (OpenAPI, GraphQL)
- Specify error handling and retry behavior
- Constrain AI-generated code through specs

---

## 4. Security Engineering (Secure by Design)

**Description**  
Embedding security into systems from the earliest design stages rather than adding it later.

**Key Skills**
- Threat modeling and attack surface analysis
- Secure defaults and least privilege
- Identity and access management (IAM)
- Defense-in-depth strategies

**Typical Tasks**
- Perform threat modeling (STRIDE, attack trees)
- Design authentication and authorization flows
- Apply least-privilege access controls
- Review AI-generated code for vulnerabilities

---

## 5. Zero Trust Architecture

**Description**  
Designing systems that assume no implicit trust and continuously verify identity, context, and intent.

**Key Skills**
- Identity-centric design
- Micro-segmentation
- Policy enforcement points
- Continuous verification

**Typical Tasks**
- Design systems with no trusted network perimeter
- Enforce authentication for every request
- Apply fine-grained authorization policies
- Reduce blast radius of compromise

---

## 6. Verification, Testing & Risk Management

**Description**  
Ensuring correctness, safety, and reliability of systems — especially those built with AI assistance.

**Key Skills**
- Test strategy design
- Automated testing
- Observability and monitoring
- Failure analysis

**Typical Tasks**
- Define unit, integration, and contract tests
- Validate AI-generated code
- Monitor production behavior
- Conduct post-incident reviews

---

## Core Principle

AI accelerates implementation.  
Engineers remain responsible for **design, security, and outcomes**.
