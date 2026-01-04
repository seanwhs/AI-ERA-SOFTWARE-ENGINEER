# 📄 **AI-Optimized Technical Specification: [System / Module Name]**

### **Target Persona**: Senior Lead AI Engineer / Full-Stack Engineer

**Context Density**: High
**Primary Objective**: Ensure AI-generated code is **correct**, **secure**, **auditable**, and **production-ready** for a **Django-based backend** with **Django REST Framework** (DRF).

---

## 1️⃣ **Meta-Context & Constraints**

*Defines the operational limits and critical constraints to ensure AI does not generate unsafe or ambiguous solutions.*

| Constraint Type            | Description / Rules                                                                                                     |
| -------------------------- | ----------------------------------------------------------------------------------------------------------------------- |
| **Runtime Environment**    | Python 3.10+ with Django 4.x, PostgreSQL or MySQL databases. DRF for API development.                                   |
| **Mandatory Libraries**    | Django ORM, `Django REST Framework`, `Celery` (for background tasks), `Winston` (for logging), `Pydantic` (validation). |
| **Forbidden Patterns**     | No `any` types, no `os.system` calls, no dynamic imports. Must avoid global mutable state or direct API calls.          |
| **Performance Budget**     | Max execution time: 200ms for API responses. Max memory usage: 512MB per request. Max DB queries per request: 3.        |
| **Compliance Constraints** | GDPR, CCPA, HIPAA (depending on context) compliance. Mandatory audit logging for all PII access.                        |
| **Deployment Targets**     | Deploy to production and staging environments only after explicit review and approval.                                  |
| **Observability Mandates** | Structured logging, metrics collection (e.g., Prometheus), and distributed tracing using OpenTelemetry.                 |

> ⚡ **Tip**: The more explicit the constraints, the less likely AI outputs will lead to production errors or untraceable issues.

---

## 2️⃣ **Data Contract (Input / Output Anchor)**

*Defines strict schemas for input and output to ensure AI doesn't generate incorrect or unsafe data structures.*

### **Input Schema**

```python
from pydantic import BaseModel
from uuid import UUID
from typing import Dict

class InputPayload(BaseModel):
    user_id: UUID  # UUID v4
    action: str     # 'create' or 'update'
    metadata: Dict[str, str]  # Key-value pairs
    request_id: str  # Idempotency key for ensuring repeatable actions
```

### **Output Schema**

```python
class SuccessResponse(BaseModel):
    status: int  # HTTP Status code
    data_id: UUID  # UUID of the persisted entity
    timestamp: str  # ISO 8601 format timestamp

class ErrorResponse(BaseModel):
    status: int
    message: str
    retry_after: int = None  # Optional field, shows when retry should be attempted
```

> ⚡ **Best Practices**: Always include **edge cases**, such as empty metadata, invalid user IDs, or missing fields. Define **nullable** fields clearly and **idempotency keys** for safety.

---

## 3️⃣ **Logic Flow & Failure Modes**

*AI must follow a well-defined execution path, and failure modes should be explicitly handled.*

### **Step-by-Step Execution Chain**

1. **Input Validation**

   * Validate `InputPayload` against the schema. If invalid, return a `400 Bad Request`.

2. **Authorization Check**

   * Call `AuthService.verify(user_id)` to check user permissions. Return `403 Forbidden` if the user is unauthorized.

3. **Persistence Layer**

   * Write to the database using Django ORM (preferably `Transaction` model or a related model), ensuring **idempotency**.

4. **Failure Mode A – DB Unreachable**

   * If the database is unreachable, return `503 Service Unavailable` with a `retry_after` header and log the incident.

5. **Failure Mode B – Blacklisted User**

   * If the user is blacklisted, return `403 Forbidden` and log the event but **do not** persist the data.

6. **Failure Mode C – Resource Collision**

   * If there’s a resource collision (e.g., concurrent write), return `409 Conflict`, specifying the conflicting resource.

7. **Success Path**

   * If all steps succeed, return `SuccessResponse` with a `data_id` and timestamp.

> ⚡ **Tip**: AI may generate boilerplate code, but **failure mode handling** must be reviewed carefully to ensure edge cases are addressed.

---

## 4️⃣ **Adversarial Guardrails (Anti-Hallucination)**

*Guardrails to prevent unsafe code generation, missed edge cases, or unobserved issues.*

| **Category**                | **Guardrail**                                                                                         |
| --------------------------- | ----------------------------------------------------------------------------------------------------- |
| **Security**                | Sanitize all string inputs; use parameterized queries; escape logs to prevent XSS.                    |
| **Idempotency**             | Ensure the `request_id` prevents duplicate entries in the database.                                   |
| **Logging / Observability** | Each `catch` block must log an error with full context (`user_id`, `request_id`, and `trace_id`).     |
| **External Calls**          | All external API calls should go through the internal API wrapper to ensure consistency and security. |
| **Performance**             | If response time exceeds 200ms, return a clear error response. Do not silently drop requests.         |
| **Testing**                 | Unit and integration tests must cover all failure modes, including edge cases and invalid inputs.     |
| **Documentation**           | Auto-generate OpenAPI / JSON Schema based on the exact data contract to ensure compliance.            |

> ⚡ **Principle**: AI is a **tool** to help, not the **system owner**. Explicit guardrails must always be enforced to avoid issues like hallucinations or forgotten validations.

---

## 5️⃣ **Definition of Done (DoD)**

*The checklist to ensure AI-generated code meets production standards.*

* [ ] Unit tests cover **100%** of failure modes defined in **Section 3**.
* [ ] Integration tests validate the entire data flow across all services (DB, external services, etc.).
* [ ] Code follows **Team Style Guide**, especially for functional patterns and immutability.
* [ ] No phantom dependencies are added. `requirements.txt` audited for unused or risky packages.
* [ ] `README` is updated with clear setup, usage instructions, and rollback guides.
* [ ] Observability has been validated: logs, metrics, and traces are fully implemented.
* [ ] Security audit passed: SQL injection, XSS, IDOR (Insecure Direct Object References), and prompt injection are mitigated.

---

## 6️⃣ **How to Use This Template with AI**

1. **System Prompt Phase:**

   * Paste this spec into your AI tool and ask: *“Summarize failure modes and guardrails to ensure understanding before code generation.”*

2. **Drafting Phase:**

   * Prompt: *“Generate the implementation for Section 3. Focus on Section 4 guardrails. Do not skip validation or logging.”*

3. **Adversarial Phase:**

   * Prompt: *“Act as a Senior Security Auditor. Identify two potential failure scenarios under load or malicious input. Suggest mitigation.”*

4. **Observability Check:**

   * Verify that logging, metrics, and distributed tracing are correctly implemented, human-readable, and follow the established conventions.

---

## 7️⃣ **Spec-First Challenge**

**Next Task:** Document your next feature using this template. Spend **15–20 minutes**:

1. **Data Contract** — Define explicit schema, constraints, and examples.
2. **Adversarial Guardrails** — Consider idempotency, security, observability, and avoid unsafe patterns.

> This AI-generated draft is now **"Senior Engineer Ready"** rather than just a first draft!

---

## **Summary:**

This technical specification ensures that AI-generated code for a Django-based backend with DRF is **correct**, **secure**, **auditable**, and **production-ready**. Through clearly defined **constraints**, **guardrails**, and **failure modes**, we enforce safe AI usage, ensure observability, and maintain production-grade reliability. Engineers have the final responsibility to **audit** AI outputs, focusing on **security**, **idempotency**, and **edge case handling**.

---

