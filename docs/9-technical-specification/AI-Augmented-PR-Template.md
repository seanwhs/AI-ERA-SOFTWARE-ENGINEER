# 📌 AI-Augmented PR Template — System Owner Enforcement

**Purpose:** Ensure every AI-generated or AI-assisted PR undergoes **adversarial review** before merging. Protects against hallucinations, security vulnerabilities, and logic flaws.

**Instructions for Engineers:** Complete all sections before requesting a review. Treat missing or unchecked items as **blocking issues**.

---

```markdown
# 🛡️ AI-Augmented PR Review Template

**PR Title:** [Feature / Fix / Refactor]  
**Author:** [Your Name]  
**Reviewer:** [Assigned System Owner]  

---

## 1️⃣ AI Hallucination Verification

- [ ] All imported libraries and APIs exist and are approved for production.
- [ ] No phantom dependencies introduced by AI code.
- [ ] AI-generated code does not introduce new unreviewed side-effects.

**Notes / Findings:**

---

## 2️⃣ Authentication & Authorization

- [ ] Auth/ACL checks implemented for all endpoints and functions.
- [ ] Permission levels validated against RBAC/ACL standards.
- [ ] No elevated privileges granted without explicit review.

**Notes / Findings:**

---

## 3️⃣ Injection & Input Safety

- [ ] SQL / NoSQL queries are fully parameterized.
- [ ] Shell / command execution sanitized; no `eval` or raw `exec`.
- [ ] HTML / template rendering escaped or sanitized.
- [ ] Input type guards applied (e.g., Zod, Pydantic).

**Notes / Findings:**

---

## 4️⃣ Logic & Resiliency

- [ ] Idempotency enforced for all write operations.
- [ ] Race conditions accounted for in distributed or multi-threaded flows.
- [ ] Timeouts and circuit breakers implemented on external service calls.
- [ ] Pagination or streaming applied for large data operations.

**Notes / Findings:**

---

## 5️⃣ Observability & Logging

- [ ] Structured logging included for all error cases (context + stack trace + request id).  
- [ ] Metrics and alerts configured for critical failure points.  
- [ ] Logging avoids sensitive data exposure (PII, secrets).  

**Notes / Findings:**

---

## 6️⃣ Secrets & Environment

- [ ] No hardcoded secrets or credentials.  
- [ ] All environment variables or vault secrets used correctly.  
- [ ] Secret scanning run (e.g., TruffleHog, Gitleaks) and passed.  

**Notes / Findings:**

---

## 7️⃣ Testing & Definition of Done

- [ ] Unit tests cover 100% of failure modes defined in Technical Spec.  
- [ ] Integration tests simulate edge cases, concurrency, and malicious input.  
- [ ] AI-generated code reviewed with **Adversarial Testing** approach.  
- [ ] PR approved by **System Owner / Security Lead**.

**Notes / Findings:**

---

## ✅ Sign-Off

**Author:** ____________________  
**Reviewer:** ____________________  
**Date:** ____________________  

> ⚠️ **Blocking Rule:** Do not merge until all items are checked or mitigations documented.
```

---

### ⚡ Key Features of This Template:

1. **Enforces adversarial mindset:** Every section prompts reviewers to assume AI is fallible.
2. **High-priority vulnerabilities upfront:** Injection, auth, and phantom dependencies are at the top.
3. **Structured logging of findings:** Each section has a “Notes / Findings” area to document issues.
4. **Blocking rule:** Cannot merge until a System Owner verifies all items or documents exceptions.
5. **Ready for CI/CD integration:** Secret scanning, automated tests, and observability checks can be enforced programmatically.

---

