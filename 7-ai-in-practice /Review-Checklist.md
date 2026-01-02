# AI Code Review Checklist — AI-Era Software Engineer

> **Purpose:** Provide a structured approach for reviewing AI-generated code to ensure correctness, safety, and maintainability.

---

## 1. Correctness & Logic

* Verify that the code meets functional requirements.
* Ensure algorithms handle all edge cases.
* Confirm variable types, data structures, and flow are correct.
* Check for off-by-one errors, infinite loops, and common pitfalls.

---

## 2. Security & Permissions

* Validate user input handling to prevent injection attacks.
* Confirm proper authentication and authorization enforcement.
* Check for exposure of sensitive data (logs, API keys, passwords).
* Ensure AI-generated code does not bypass security checks.

---

## 3. Performance & Scalability

* Analyze time and space complexity.
* Identify unnecessary computations or repeated API calls.
* Check database queries for efficiency and N+1 problems.
* Evaluate caching and async handling for heavy tasks.

---

## 4. Style & Maintainability

* Confirm adherence to project coding standards.
* Ensure code readability and clear naming conventions.
* Check comments and documentation are accurate.
* Review modularity and reusability of functions and components.

---

## 5. AI-Specific Concerns

* Verify AI suggestions do not hallucinate data or logic.
* Confirm that AI-generated code aligns with system contracts.
* Ensure AI output is appropriately validated and tested before integration.

---

## 6. Testing

* Unit tests cover AI-generated functions and edge cases.
* Integration tests validate the interaction between AI code and existing systems.
* Mock AI inputs for predictable testing.
* Confirm CI/CD pipelines catch regressions or integration errors.

---

## 7. Documentation

* Update README or technical docs if AI-generated code introduces new endpoints, features, or patterns.
* Include rationale for accepting, modifying, or rejecting AI code.
* Maintain a clear audit trail for AI contributions.

---

> **Key Takeaway:** Treat AI output as a draft. Thorough review, testing, and documentation are mandatory to maintain system integrity and developer trust.
