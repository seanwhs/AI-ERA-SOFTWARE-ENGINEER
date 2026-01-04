# 🛡️ **AI-Augmented PR Review Template**

**PR Title:** [Feature / Fix / Refactor]
**Author:** [Your Name]
**Reviewer:** [Assigned System Owner]

---

## 1️⃣ **AI Hallucination Verification**

* [ ] All imported libraries and APIs exist and are approved for production.
* [ ] No phantom dependencies introduced by AI code.
* [ ] AI-generated code does not introduce new unreviewed side-effects.

**Notes / Findings:**

* Ensure that all libraries have been checked against the **approved libraries list** and are updated to the latest stable versions.
* Double-check that no unnecessary dependencies have been added. If any were added, confirm their use case and relevance to the project.

---

## 2️⃣ **Authentication & Authorization**

* [ ] Auth/ACL checks implemented for all endpoints and functions.
* [ ] Permission levels validated against RBAC/ACL standards.
* [ ] No elevated privileges granted without explicit review.

**Notes / Findings:**

* Verify that all API endpoints are protected with proper authentication (e.g., OAuth, JWT).
* Ensure the **RBAC/ACL** permissions are explicitly checked for each user action, especially for any endpoint that modifies sensitive data.
* Elevation of privileges should never happen implicitly, and any such modification should be checked by a security lead.

---

## 3️⃣ **Injection & Input Safety**

* [ ] SQL / NoSQL queries are fully parameterized.
* [ ] Shell / command execution sanitized; no `eval` or raw `exec`.
* [ ] HTML / template rendering escaped or sanitized.
* [ ] Input type guards applied (e.g., Zod, Pydantic).

**Notes / Findings:**

* Ensure that **SQL queries** are parameterized to prevent SQL injection attacks.
* No code should use unsafe `eval()` or `exec()` functions to execute dynamic code. If present, immediately replace with safer alternatives.
* Ensure that any **HTML rendering** uses secure templating engines (e.g., Django templates) and escapes untrusted data.
* Use **input validation** libraries (e.g., `Pydantic` or `Zod`) to ensure the data entering the system is in the correct format and secure.

---

## 4️⃣ **Logic & Resiliency**

* [ ] Idempotency enforced for all write operations.
* [ ] Race conditions accounted for in distributed or multi-threaded flows.
* [ ] Timeouts and circuit breakers implemented on external service calls.
* [ ] Pagination or streaming applied for large data operations.

**Notes / Findings:**

* Every write operation should be idempotent to prevent duplicate or unintended updates. Implement **idempotency keys** or other mechanisms where needed.
* **Race conditions** must be detected and mitigated, particularly in distributed systems or multi-threaded scenarios.
* For all external service calls (e.g., third-party APIs), implement **timeouts** and **circuit breakers** to ensure the system doesn’t become blocked or delayed indefinitely.
* Large datasets should be processed using **pagination** or **streaming** to avoid performance bottlenecks.

---

## 5️⃣ **Observability & Logging**

* [ ] Structured logging included for all error cases (context + stack trace + request id).
* [ ] Metrics and alerts configured for critical failure points.
* [ ] Logging avoids sensitive data exposure (PII, secrets).

**Notes / Findings:**

* Ensure that all errors are logged with sufficient context (e.g., **stack trace**, **request ID**) so they can be traced back easily. The **trace_id** and **request_id** should be used consistently across logs.
* **Metrics and alerts** must be configured, especially for high-priority failure points like timeouts or 500 errors.
* **Sensitive data** (e.g., personal identifiable information, passwords, and API keys) should never be logged. Always use **environment variables** or **vaults** for sensitive information.

---

## 6️⃣ **Secrets & Environment**

* [ ] No hardcoded secrets or credentials.
* [ ] All environment variables or vault secrets used correctly.
* [ ] Secret scanning run (e.g., TruffleHog, Gitleaks) and passed.

**Notes / Findings:**

* Ensure **no secrets** are hardcoded directly in the source code or configuration files. Always use environment variables or vault solutions for handling sensitive information.
* Run a **secret scanning tool** (e.g., **TruffleHog**, **Gitleaks**) to ensure no secrets have accidentally been pushed to the repository.
* Verify that all **environment variables** are used securely and that they are defined in the correct configuration files.

---

## 7️⃣ **Testing & Definition of Done**

* [ ] Unit tests cover **100%** of failure modes defined in the **Technical Spec**.
* [ ] Integration tests simulate edge cases, concurrency, and malicious input.
* [ ] AI-generated code reviewed with **Adversarial Testing** approach.
* [ ] PR approved by **System Owner / Security Lead**.

**Notes / Findings:**

* All **unit tests** must ensure that every defined failure mode from the technical specification is covered and properly tested.
* **Integration tests** should simulate **real-world scenarios**, including edge cases, high concurrency, and malicious inputs.
* Review the AI-generated code for **adversarial testing**. This ensures the code has been tested against common attack vectors and high-stress conditions.
* Ensure that the **System Owner** or **Security Lead** approves the PR before merging.

---

## ✅ **Sign-Off**

**Author:** ____________________
**Reviewer:** ____________________
**Date:** ____________________

> ⚠️ **Blocking Rule:** Do not merge until all items are checked or mitigations documented.

---

### ⚡ **Key Features of This Template:**

1. **Enforces an adversarial mindset:** Each section prompts reviewers to act as if the AI-generated code might contain issues or vulnerabilities.
2. **Security-first approach:** Critical areas such as **injections**, **auth**, and **secrets** are prioritized to prevent fundamental flaws.
3. **Clear documentation:** Each checklist item is followed by a “Notes / Findings” section for clear tracking of any issues.
4. **Blocking rule:** **No merge** until a System Owner verifies all checklist items or documents exceptions.
5. **CI/CD integration-ready:** The template can be automated through secret scanning, testing, and observability tools in the CI/CD pipeline.

---

