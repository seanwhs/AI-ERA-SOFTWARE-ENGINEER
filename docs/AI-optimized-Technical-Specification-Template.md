# 📄 Technical Specification: [System / Module Name]

**Target Persona:** AI Senior Lead Engineer / Agentic Coder
**Context Density:** High
**Primary Objective:** Ensure AI-generated code is **correct, secure, auditable, and production-ready**

---

## 1. Meta-Context & Constraints

*Prevents generic or unsafe AI solutions. Sets the operational “sandbox.”*

| Constraint Type            | Description / Rules                                                                                          |
| -------------------------- | ------------------------------------------------------------------------------------------------------------ |
| **Runtime Environment**    | e.g., Node.js 22.x, Python 3.13, AWS Lambda, Kubernetes Pod v1.28                                            |
| **Mandatory Libraries**    | e.g., `Zod` for validation, `Prisma` for ORM, `Winston` for logging                                          |
| **Forbidden Patterns**     | e.g., No `any` types, no direct external fetch calls; use internal Axios wrapper; avoid global mutable state |
| **Performance Budget**     | e.g., Max execution time: 200ms, Max memory: 512MB, Max DB queries per request: 3                            |
| **Compliance Constraints** | GDPR/CCPA enforced; audit logging required for all PII access                                                |
| **Deployment Targets**     | e.g., Production, Staging, Canary only after approval                                                        |
| **Observability Mandates** | Logs, metrics, distributed traces mandatory for each critical path                                           |

> ⚡ Tip: The more explicit the constraints, the less likely AI outputs hallucinate or introduce hidden technical debt.

---

## 2. Data Contract (Input / Output Anchor)

*Defines strict schemas to anchor AI output and prevent phantom fields.*

```typescript
// Input Schema
interface InputPayload {
  user_id: string;           // UUID v4, required
  action: "create" | "update"; // must match exact strings
  metadata: Record<string, string>; // key-value pairs
  request_id: string;        // idempotency key
}

// Output Schema
interface SuccessResponse {
  status: 200;
  data_id: string;           // UUID of persisted entity
  timestamp: string;         // ISO 8601 format
}

interface ErrorResponse {
  status: number;
  message: string;
  retry_after?: number;      // seconds, optional
}
```

**Best Practices:**

* Always include examples for **edge cases**.
* Explicitly define **idempotency keys**, **nullable fields**, and **required properties**.

---

## 3. Logic Flow & Failure Modes

*Step-by-step Execution Chain. AI must follow in order.*

1. **Input Validation**

   * Validate `InputPayload` against schema. Reject invalid data with `400 Bad Request`.
2. **Authorization Check**

   * Call `AuthService.verify(user_id)`. Return `403 Forbidden` if unauthorized.
3. **Persistence Layer**

   * Insert/update `Transactions` table via `Prisma`.
4. **Failure Mode A – DB Unreachable**

   * Return `503 Service Unavailable` and include `retry_after` header. Log incident.
5. **Failure Mode B – Blacklisted User**

   * Return `403`, log security alert, do **not** persist data.
6. **Failure Mode C – Constraint Violation**

   * Return `422 Unprocessable Entity`, include field-level errors in response.
7. **Success Path**

   * Return `SuccessResponse` with `data_id` and `timestamp`.

> ⚡ Tip: AI can generate repetitive boilerplate for each step but humans must review **Failure Mode handling**.

---

## 4. Adversarial Guardrails (Anti-Hallucination)

*Explicit anti-patterns, security rules, and observability requirements.*

| Category                    | Guardrail                                                                                    |
| --------------------------- | -------------------------------------------------------------------------------------------- |
| **Security**                | Sanitize all string inputs; use parameterized queries; escape logs for XSS.                  |
| **Idempotency**             | Ensure `request_id` prevents duplicate DB inserts.                                           |
| **Logging / Observability** | Every catch block must call `Logger.error()` with stack trace, input payload, and `user_id`. |
| **External Calls**          | Only call internal services; forbidden to call external endpoints directly.                  |
| **Performance**             | Fail gracefully if execution exceeds 200ms. Do not silently drop requests.                   |
| **Testing**                 | Unit & integration tests must cover all failure modes, edge cases, and invalid inputs.       |
| **Documentation**           | Auto-generate OpenAPI / JSON Schema based on the exact Data Contract.                        |

> ⚡ Principle: AI is **a capable intern, not a system owner**. Explicit guardrails are mandatory.

---

## 5. Definition of Done (DoD)

*Final checklist the AI must satisfy before human review.*

* [ ] Unit tests cover 100% of **Failure Modes** in Section 3.
* [ ] Integration tests validate data flow through all services.
* [ ] Code conforms to **Team Style Guide** (functional patterns preferred, immutability enforced).
* [ ] No phantom dependencies added. `package.json` / `requirements.txt` audited.
* [ ] README updated with local setup, usage, and rollback instructions.
* [ ] Observability verified: logs, metrics, tracing implemented.
* [ ] Security audit passed: SQL injection, XSS, IDOR, prompt injection mitigated.

---

## 6. How to Use This Template with AI

1. **System Prompt Phase:**

   * Paste the spec. Ask the AI: *“Summarize failure modes and guardrails to prove understanding before generating code.”*

2. **Drafting Phase:**

   * Prompt: *“Generate the implementation for Section 3. Focus on Section 4 guardrails. Do not skip validation or logging.”*

3. **Adversarial Phase:**

   * Prompt: *“Act as a Senior Security Auditor. Identify two potential failure scenarios under load or malicious input. Suggest mitigation.”*

4. **Observability Check:**

   * Verify logging, metrics, and tracing are correctly implemented and human-readable.

---

## 7. Spec-First Challenge

**Next Task:** Document your next feature using this template. Spend 15–20 minutes on:

1. **Data Contract** — explicit schema, constraints, and examples.
2. **Adversarial Guardrails** — idempotency, security, observability, anti-patterns.

> The first AI draft now becomes **“Senior Engineer Ready”** rather than “Junior Intern Level.”

---
