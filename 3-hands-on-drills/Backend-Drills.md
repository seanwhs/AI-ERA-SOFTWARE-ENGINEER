# Backend Hands-On Drills — AI-Era Bridge Engineer

> **Purpose:** Convert checklist items into repeatable, concrete exercises. Each drill maps directly to real-world readiness.

Folder structure: `03-hands-on-drills/backend/`

---

## Drill 1: API Contract Audit

**Checklist Mapped:** API contracts, serializers, validation

* Take an existing Django REST Framework API.
* Document the expected request/response schema.
* Compare with actual serializers.
* Identify mismatches and propose corrections.
* Test edge cases manually and with automated tests.

**Deliverable:** Markdown doc of discrepancies + PR fixes

---

## Drill 2: ORM & Query Optimization

**Checklist Mapped:** N+1 detection, database reasoning

* Take a multi-model view.
* Identify all database queries generated.
* Refactor with `select_related` / `prefetch_related`.
* Measure query count before and after.

**Deliverable:** Benchmarked query count and explanation

---

## Drill 3: Async Task & Concurrency Reasoning

**Checklist Mapped:** Async / sync reasoning, task queues

* Implement a background task with Celery or asyncio.
* Simulate multiple simultaneous requests.
* Observe race conditions or data integrity issues.
* Add locks / transactions as needed.

**Deliverable:** Code demonstrating safe async behavior

---

## Drill 4: Authentication & Authorization

**Checklist Mapped:** JWT lifecycle, permissions

* Implement JWT login for API.
* Create endpoints with different permission levels.
* Write tests ensuring unauthorized access is blocked.
* Demonstrate token expiration and refresh handling.

**Deliverable:** Fully tested secure endpoints

---

## Drill 5: System Failure Simulation

**Checklist Mapped:** Failure thinking, degradation

* Simulate database downtime.
* Observe API behavior (timeouts, 500 errors).
* Implement graceful degradation / fallback data.

**Deliverable:** Demo showing stable system despite partial failures

---

## Drill 6: AI Code Review Exercise

**Checklist Mapped:** AI orchestration, code auditing

* Generate a Django view or serializer via AI.
* Audit line-by-line.
* Identify logic errors, missing validation, or security holes.
* Refactor and explain corrections.

**Deliverable:** Annotated AI code + final secure version

---

> Completion of these drills demonstrates **practical backend ownership**. Each should be scored against the checklist and discussed in weekly or monthly self-audits.
