# 🛡️ **System Owner’s Cheat Sheet: AI-Generated Security Vulnerabilities**

**Purpose:** Enable engineers to rapidly identify, triage, and mitigate the most frequent security and reliability risks in AI-generated code.

**Audience:** System Owners, Engineering Leads, AI-augmented development teams

---

## 1️⃣ **Input Validation & Injection Risks**

| **Vulnerability**                           | **Symptom / Hallucination**                                    | **Quick Mitigation**                                                        |
| ------------------------------------------- | -------------------------------------------------------------- | --------------------------------------------------------------------------- |
| **SQL Injection**                           | AI generates raw queries using string interpolation.           | Always use parameterized queries / ORM methods. Verify query strings.       |
| **XSS (Cross-Site Scripting)**              | AI outputs HTML or logs user input without escaping.           | Sanitize all strings before rendering; escape logs if user-controlled.      |
| **Command Injection**                       | AI calls `os.system()` or shell commands with user input.      | Use safe APIs; never pass raw input to shell. Validate against a whitelist. |
| **IDOR (Insecure Direct Object Reference)** | AI references object IDs directly without authorization check. | Always verify ownership or ACL before returning resources.                  |

### Quick Triage Tips:

* **SQL Injection**: Always use parameterized queries and ORM methods (e.g., SQLAlchemy, Django ORM).
* **XSS**: Use a templating engine that auto-escapes (e.g., Django templates, Jinja2).
* **Command Injection**: Validate input against a set of allowed commands or use API wrappers to sanitize input.
* **IDOR**: Implement ACL checks before exposing sensitive data.

---

## 2️⃣ **Authentication & Authorization Gaps**

| **Vulnerability**        | **Symptom / Hallucination**                      | **Quick Mitigation**                                        |
| ------------------------ | ------------------------------------------------ | ----------------------------------------------------------- |
| **Missing Auth Checks**  | AI omits `AuthService.verify()` or equivalent.   | Confirm every endpoint validates identity & roles.          |
| **Privilege Escalation** | AI allows admin-level actions for regular users. | Test RBAC thoroughly; audit AI-generated permissions logic. |
| **Token Leakage**        | AI logs or exposes API tokens / secrets.         | Ensure sensitive values are never logged or committed.      |

### Quick Triage Tips:

* **Missing Auth Checks**: Ensure that all endpoints validate JWT tokens, OAuth credentials, or other forms of authentication.
* **Privilege Escalation**: Review the **RBAC** (Role-Based Access Control) system to ensure no user can escalate privileges unexpectedly.
* **Token Leakage**: Use logging filters to prevent sensitive data from being exposed. Make sure tokens are stored securely (e.g., environment variables, vaults).

---

## 3️⃣ **Business Logic & Idempotency Flaws**

| **Vulnerability**            | **Symptom / Hallucination**                                | **Quick Mitigation**                                                               |
| ---------------------------- | ---------------------------------------------------------- | ---------------------------------------------------------------------------------- |
| **Duplicate Transactions**   | AI ignores `request_id` or idempotency keys.               | Enforce idempotency at DB / service layer.                                         |
| **Race Conditions**          | AI assumes synchronous execution; fails under concurrency. | Implement locks, transactions, or retry policies. Test high-concurrency scenarios. |
| **Data Integrity Violation** | AI writes invalid or inconsistent state.                   | Validate data schema strictly; run pre/post state assertions.                      |

### Quick Triage Tips:

* **Duplicate Transactions**: Ensure that the system generates and validates **idempotency keys** for any operations that may result in multiple requests (e.g., payments, file uploads).
* **Race Conditions**: Introduce locking mechanisms or **atomic transactions** to avoid concurrency issues, especially in distributed systems.
* **Data Integrity**: Use strict schema validation on both input and output to catch data inconsistencies early.

---

## 4️⃣ **External Service & Dependency Risks**

| **Vulnerability**               | **Symptom / Hallucination**                  | **Quick Mitigation**                                                            |
| ------------------------------- | -------------------------------------------- | ------------------------------------------------------------------------------- |
| **Phantom Dependencies**        | AI references non-existent packages or APIs. | Verify all dependencies exist; lock versions; audit license & security.         |
| **Uncontrolled External Calls** | AI calls 3rd-party APIs directly.            | Route all calls through internal service wrappers; whitelist allowed endpoints. |
| **Secrets in Code**             | Hardcoded API keys, DB passwords.            | Store secrets in vault/environment; rotate regularly.                           |

### Quick Triage Tips:

* **Phantom Dependencies**: Always verify that dependencies exist in the repository and are locked to stable versions.
* **Uncontrolled External Calls**: Use proxy services or internal wrappers for external calls and restrict access through an allowlist.
* **Secrets in Code**: Store API keys, passwords, and other secrets securely using environment variables or secret management tools (e.g., AWS Secrets Manager, HashiCorp Vault).

---

## 5️⃣ **Observability & Logging Gaps**

| **Vulnerability**               | **Symptom / Hallucination**                             | **Quick Mitigation**                                         |
| ------------------------------- | ------------------------------------------------------- | ------------------------------------------------------------ |
| **Missing Logging**             | AI omits error logs for failure modes.                  | Ensure every catch block logs stack trace + input + context. |
| **Insufficient Metrics**        | AI does not emit success/failure counters or latencies. | Integrate Prometheus/Grafana or similar telemetry hooks.     |
| **Over-Logging Sensitive Info** | AI logs PII or sensitive tokens.                        | Mask / redact sensitive fields; validate logging output.     |

### Quick Triage Tips:

* **Missing Logging**: Implement **structured logging** and include critical information such as request ID, stack trace, and error context.
* **Insufficient Metrics**: Ensure **metrics** are logged for every major event or transaction, such as timeouts, DB writes, or errors.
* **Over-Logging Sensitive Info**: Use filters or patterns to redact sensitive data (e.g., using `logrotate` for logs).

---

## 6️⃣ **Performance & Resource Risks**

| **Vulnerability**                  | **Symptom / Hallucination**                                | **Quick Mitigation**                                          |
| ---------------------------------- | ---------------------------------------------------------- | ------------------------------------------------------------- |
| **Infinite Loops / Heavy Queries** | AI generates loops or queries without limits.              | Set max iterations, timeouts, query limits.                   |
| **Memory Leaks**                   | AI creates large in-memory objects without cleanup.        | Profile memory; enforce streaming or chunking for large data. |
| **Unbounded External Calls**       | AI triggers exponential calls (e.g., recursive API calls). | Implement rate limiting and circuit breakers.                 |

### Quick Triage Tips:

* **Infinite Loops / Heavy Queries**: Always set timeouts for loops and queries. **Limit** the amount of data returned to avoid performance bottlenecks.
* **Memory Leaks**: Use tools like **profilers** or **heap dumps** to analyze memory consumption.
* **Unbounded External Calls**: Use **rate limiting** and **circuit breakers** to ensure external services aren’t overwhelmed and protect your system from being blocked.

---

## 7️⃣ **Adversarial Review Checklist**

1. **Run “Zero Trust” Tests**: Attempt to break AI assumptions with malicious or malformed input.
2. **Validate All Guardrails**: Check idempotency, auth, input validation, logging, and observability.
3. **Dependency Audit**: Confirm every external library or API exists and is safe.
4. **Stress Test / Load Test**: Simulate race conditions, high concurrency, and latency spikes.
5. **Security Scan**: Run static analysis and vulnerability scanners (e.g., SAST, OWASP ZAP).

> ✅ **Principle**: Treat AI output as **untrusted until human-reviewed**. This cheat sheet reduces review time while maximizing reliability.

---

### 📣 **Pro Tip for System Owners**

Integrate this cheat sheet as a **GitHub/GitLab PR template** or **pre-merge checklist**. Even junior engineers following it will consistently produce production-safe AI-augmented code.

---

