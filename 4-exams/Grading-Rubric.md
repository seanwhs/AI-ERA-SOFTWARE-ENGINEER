# Grading Rubric — AI-Era Bridge Engineer Exams

> **Purpose:** Provide consistent scoring criteria across Month 1–3 exams, focused on real-world ownership, integration, and AI competency.

---

## Scoring Scale

| Score | Description                                                     |
| ----- | --------------------------------------------------------------- |
| 0     | Not attempted / incorrect / unsafe                              |
| 1     | Partial attempt, major gaps, minor unsafe patterns              |
| 2     | Mostly correct, safe, but lacks optimization or completeness    |
| 3     | Correct, secure, fully integrated, demonstrates system thinking |

---

## Section 1: Backend (Month 1)

| Criteria                      | Max Points | Notes                                                                |
| ----------------------------- | ---------- | -------------------------------------------------------------------- |
| API Design & Contracts        | 30         | Correct endpoints, serializers, permissions, and clear documentation |
| Database & Query Optimization | 20         | Efficient queries, N+1 detection, correct ORM usage                  |
| Async Task Handling           | 20         | Safe async execution, error handling, integration with app           |
| AI Orchestration              | 15         | Correct auditing of AI-generated code, safe integration              |
| Testing & Failure Simulation  | 15         | Unit tests, failure handling, documented unexpected behavior         |

---

## Section 2: Frontend (Month 2)

| Criteria                              | Max Points | Notes                                                               |
| ------------------------------------- | ---------- | ------------------------------------------------------------------- |
| TypeScript Contract Enforcement       | 20         | Correct interfaces, error detection for schema mismatch             |
| State Management & Async Data         | 20         | Proper use of `useState`, `useEffect`, and global state consistency |
| TanStack Query Integration            | 20         | Correct caching, retries, error handling, UI states                 |
| Component Reusability & Composition   | 15         | Functional decomposition, type correctness, code clarity            |
| Tailwind CSS Styling & Responsiveness | 15         | Responsive, accessible UI, production-ready look                    |
| AI Code Review                        | 10         | Accurate audit, secure and contract-aligned refactor                |

---

## Section 3: Integration (Month 3)

| Criteria                          | Max Points | Notes                                                             |
| --------------------------------- | ---------- | ----------------------------------------------------------------- |
| End-to-End Data Flow              | 20         | Complete mapping, failure points identified                       |
| Full-Stack Feature Implementation | 25         | Working feature, edge cases handled, clean integration            |
| Authentication & Security         | 15         | JWT flows, role-based permissions, token lifecycle handling       |
| AI-Orchestrated Feature           | 20         | Safe AI integration, validation, ethical/security considerations  |
| Testing & Observability           | 20         | Unit & integration tests, logging, monitoring, failure simulation |

---

## Key Notes

* **Ownership > Completion:** Partial features that demonstrate deep system understanding may score higher than completed but unsafe code.
* **AI Audit is Critical:** All AI-generated code must be reviewed; failing to audit lowers the score.
* **Edge Cases Matter:** Handling edge cases, failure modes, and graceful degradation is mandatory for full points.
* **Documentation Counts:** Clear documentation of APIs, flows, and decisions contributes to scoring.

> Use this rubric to standardize evaluation across exams, self-audits, and hiring assessments.
