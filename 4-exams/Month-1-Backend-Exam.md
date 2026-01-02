# Month 1 Backend Exam — AI-Era Bridge Engineer

> **Goal:** Assess real-world readiness for backend ownership, API design, system reasoning, and AI integration.

**Duration:** 3 hours (self-paced)

**Environment:** Local Django project, AI tools optional for guidance only, not generation.

---

## Section 1: API Design & Contracts (30 pts)

1. Design a REST API for a simple book management system.

   * Endpoints: list, retrieve, create, update, delete
   * Validate request data using serializers
   * Implement permissions: admin vs regular user

2. Document request/response schema clearly for frontend developers.

**Deliverable:** Working endpoints + API documentation

---

## Section 2: Database & Query Optimization (20 pts)

1. Create models for Book, Author, and Publisher.
2. Populate sample data (at least 50 books).
3. Implement a view that lists books with author info.
4. Detect and fix potential N+1 query issues.

**Deliverable:** Query analysis + optimized code

---

## Section 3: Async Task Handling (20 pts)

1. Implement a background task to fetch book metadata from an external API.
2. Ensure tasks handle network errors gracefully.
3. Demonstrate how task status is reported back to the main application.

**Deliverable:** Async task code + demo output

---

## Section 4: AI Orchestration (15 pts)

1. Use AI to draft a serializer or validation function.
2. Review AI-generated code for correctness, completeness, and security.
3. Refactor as needed and document changes.

**Deliverable:** Annotated AI code + final working version

---

## Section 5: Testing & Failure Simulation (15 pts)

1. Write unit tests for API endpoints.
2. Simulate failures (e.g., invalid data, missing auth) and demonstrate handling.
3. Document unexpected behaviors and fix them.

**Deliverable:** Test suite + evidence of handling failures

---

**Scoring:** 100 points total, see `grading-rubric.md` for breakdown of ownership, correctness, and system thinking.
