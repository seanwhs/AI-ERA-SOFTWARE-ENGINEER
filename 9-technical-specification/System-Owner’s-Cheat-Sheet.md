# 🛡️ System Owner’s Cheat Sheet: AI-Generated Security Vulnerabilities

**Purpose:** Enable engineers to rapidly identify, triage, and mitigate the most frequent security and reliability risks in AI-generated code.

**Audience:** System Owners, Engineering Leads, AI-augmented development teams

---

## 1. Input Validation & Injection Risks

| Vulnerability                               | Symptom / Hallucination                                        | Quick Mitigation                                                          |
| ------------------------------------------- | -------------------------------------------------------------- | ------------------------------------------------------------------------- |
| **SQL Injection**                           | AI generates raw queries using string interpolation.           | Always use parameterized queries / ORM methods. Verify query strings.     |
| **XSS (Cross-Site Scripting)**              | AI outputs HTML or logs user input without escaping.           | Sanitize all strings before rendering; escape logs if user-controlled.    |
| **Command Injection**                       | AI calls `os.system()` or shell commands with user input.      | Use safe APIs; never pass raw input to shell. Validate against whitelist. |
| **IDOR (Insecure Direct Object Reference)** | AI references object IDs directly without authorization check. | Always verify ownership or ACL before returning resources.                |

---

## 2. Authentication & Authorization Gaps

| Vulnerability            | Symptom / Hallucination                          | Quick Mitigation                                            |
| ------------------------ | ------------------------------------------------ | ----------------------------------------------------------- |
| **Missing Auth Checks**  | AI omits `AuthService.verify()` or equivalent.   | Confirm every endpoint validates identity & roles.          |
| **Privilege Escalation** | AI allows admin-level actions for regular users. | Test RBAC thoroughly; audit AI-generated permissions logic. |
| **Token Leakage**        | AI logs or exposes API tokens / secrets.         | Ensure sensitive values are never logged or committed.      |

---

## 3. Business Logic & Idempotency Flaws

| Vulnerability                | Symptom / Hallucination                                    | Quick Mitigation                                                                   |
| ---------------------------- | ---------------------------------------------------------- | ---------------------------------------------------------------------------------- |
| **Duplicate Transactions**   | AI ignores `request_id` or idempotency keys.               | Enforce idempotency at DB / service layer.                                         |
| **Race Conditions**          | AI assumes synchronous execution; fails under concurrency. | Implement locks, transactions, or retry policies. Test high-concurrency scenarios. |
| **Data Integrity Violation** | AI writes invalid or inconsistent state.                   | Validate data schema strictly; run pre/post state assertions.                      |

---

## 4. External Service & Dependency Risks

| Vulnerability                   | Symptom / Hallucination                      | Quick Mitigation                                                                |
| ------------------------------- | -------------------------------------------- | ------------------------------------------------------------------------------- |
| **Phantom Dependencies**        | AI references non-existent packages or APIs. | Verify all dependencies exist; lock versions; audit license & security.         |
| **Uncontrolled External Calls** | AI calls 3rd-party APIs directly.            | Route all calls through internal service wrappers; whitelist allowed endpoints. |
| **Secrets in Code**             | Hardcoded API keys, DB passwords.            | Store secrets in vault/environment; rotate regularly.                           |

---

## 5. Observability & Logging Gaps

| Vulnerability                   | Symptom / Hallucination                                 | Quick Mitigation                                             |
| ------------------------------- | ------------------------------------------------------- | ------------------------------------------------------------ |
| **Missing Logging**             | AI omits error logs for failure modes.                  | Ensure every catch block logs stack trace + input + context. |
| **Insufficient Metrics**        | AI does not emit success/failure counters or latencies. | Integrate Prometheus/Grafana or similar telemetry hooks.     |
| **Over-Logging Sensitive Info** | AI logs PII or sensitive tokens.                        | Mask / redact sensitive fields; validate logging output.     |

---

## 6. Performance & Resource Risks

| Vulnerability                      | Symptom / Hallucination                                    | Quick Mitigation                                              |
| ---------------------------------- | ---------------------------------------------------------- | ------------------------------------------------------------- |
| **Infinite Loops / Heavy Queries** | AI generates loops or queries without limits.              | Set max iterations, timeouts, query limits.                   |
| **Memory Leaks**                   | AI creates large in-memory objects without cleanup.        | Profile memory; enforce streaming or chunking for large data. |
| **Unbounded External Calls**       | AI triggers exponential calls (e.g., recursive API calls). | Implement rate limiting and circuit breakers.                 |

---

## 7. Adversarial Review Checklist

1. **Run “Zero Trust” Tests**: Attempt to break AI assumptions with malicious or malformed input.
2. **Validate All Guardrails**: Check idempotency, auth, input validation, logging, and observability.
3. **Dependency Audit**: Confirm every external library or API exists and is safe.
4. **Stress Test / Load Test**: Simulate race conditions, high concurrency, and latency spikes.
5. **Security Scan**: Run static analysis and vulnerability scanners (e.g., SAST, OWASP ZAP).

> ✅ Principle: Treat AI output as **untrusted until human-reviewed**. This cheat sheet reduces review time while maximizing reliability.

---

### 📣 Pro Tip for System Owners

Integrate this cheat sheet as a **GitHub/GitLab PR template** or **pre-merge checklist**. Even junior engineers following it will consistently produce production-safe AI-augmented code.

---

