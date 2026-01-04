# Bad Requirements Workshop — AI-Era Software Engineer

> **Purpose:** Simulate handling poorly defined or conflicting requirements to practice clarification, prioritization, and iterative delivery in the context of AI-augmented systems.

---

## **Scenario Setup**

* **System:** Full-stack application (Django backend, React frontend) with AI-assisted features.
* **Problem:** Stakeholders have provided vague or conflicting requirements, e.g., "The AI summary feature must be fast and always accurate," without defining performance limits, user context, or specific accuracy targets.
* **Workshop Setting:** The team must clarify, prioritize, and plan incremental delivery to ensure alignment between stakeholder expectations, technical feasibility, and AI limitations.

---

## **Objectives**

### 1. **Requirement Clarification**

* **Engage Stakeholders with Structured Questions:**

  * What do "fast" and "accurate" mean in the context of this feature? Can we define them with measurable metrics?
  * Are there any specific trade-offs we can make between speed and accuracy, especially under load or in edge cases?
  * What are the acceptable failure modes? Can we define "acceptable accuracy" with confidence intervals or error margins?
  * What is the context for using this feature? Is it for real-time usage, batch processing, or something else?
  * Are there performance, cost, or infrastructure limitations we need to consider?

* **Define Acceptance Criteria:**

  * Define what success looks like. For example:

    * The AI summary must complete within X seconds for 90% of use cases.
    * Accuracy must exceed Y% under standard conditions (with exceptions for edge cases or limited data).
    * Error rates must be below Z%, with specific thresholds for fallbacks.

* **Identify Constraints:**

  * **Performance:** How fast does the AI need to generate summaries? Does it need to work in real time or can there be slight delays?
  * **Cost:** What is the budget for AI processing (e.g., cloud compute, model retraining)?
  * **AI Limitations:** Can the AI achieve "always accurate" summaries? What degree of accuracy is acceptable for different scenarios (e.g., summarizing news vs. medical reports)?

### 2. **Prioritization & Planning**

* **Break Requirements into MVP Features:**

  * Start by delivering a basic working feature that meets the minimum functional requirements (e.g., generate AI summaries for a limited set of use cases with defined speed and accuracy thresholds).
  * Example MVP:

    * Backend API to request summaries.
    * Frontend UI to display AI-generated summaries.
    * Basic error handling for when AI output is invalid.

* **Decide What Can Be Delivered First and What Must Be Deferred:**

  * Identify must-have features for initial delivery vs. nice-to-have improvements. For instance:

    * **First Iteration:** AI summary for simple text inputs, focusing on one use case (e.g., product descriptions or news articles).
    * **Deferred Features:** Enhanced accuracy for complex content, multi-language support, edge cases (e.g., technical jargon).

* **Assign Tasks to Backend, Frontend, and AI Teams:**

  * Backend Engineer: Build the API endpoints for requesting and delivering summaries.
  * Frontend Engineer: Design the UI for interacting with AI summaries and managing user input/output.
  * AI Engineer: Fine-tune the model for the specific task and ensure it meets the performance criteria.

### 3. **Iterative Implementation**

* **Implement Small, Testable Features:**

  * Develop each feature incrementally and ensure it is testable. For example:

    * First, implement an API that accepts a text input and returns a summary.
    * Then, add UI components to display the summary and handle errors.
    * Finally, refine AI performance by focusing on accuracy improvements in small iterations.

* **Use Feedback Loops to Adjust Requirements and Expectations:**

  * As new features are tested, gather feedback from users, stakeholders, and the AI model itself. Is the summary feature fast enough? Is the accuracy satisfactory?
  * If any problems arise (e.g., slow response or inaccurate results), revisit the requirements with stakeholders and adjust.

* **Document Assumptions and Decisions Made During Implementation:**

  * Keep track of technical decisions, including trade-offs made between performance and accuracy, AI limitations, and system design choices. This helps to manage expectations and provides context for future iterations.

### 4. **Post-Workshop Retrospective**

* **Review How the Team Managed Ambiguity:**

  * Did we ask the right questions? Were we able to extract actionable requirements from stakeholders despite the initial vagueness?
  * What improvements can we make to our requirements-gathering process?

* **Identify Communication and Decision-Making Improvements:**

  * Did we have clear, ongoing communication between product owners, AI engineers, and other stakeholders?
  * How well did we document and share our assumptions with the team and stakeholders?

* **Update Requirements Templates and Workshop Guidelines:**

  * Based on the workshop, update the team’s standard process for handling ambiguous or conflicting requirements.
  * Create a checklist or template for structured requirement clarification questions to streamline future workshops.

---

## **Roles & Responsibilities**

| **Role**                        | **Responsibilities**                                                                                           |
| ------------------------------- | -------------------------------------------------------------------------------------------------------------- |
| **Product Owner / Stakeholder** | Provide context, answer clarifying questions, prioritize features.                                             |
| **Backend Engineer**            | Estimate feasibility, implement MVP APIs for AI interaction.                                                   |
| **Frontend Engineer**           | Build UI/UX based on iterative specs and manage user interactions.                                             |
| **AI Engineer**                 | Clarify AI capabilities, fine-tune models, and test outputs against defined criteria.                          |
| **Bridge Engineer**             | Ensure alignment between AI capabilities, backend, and frontend. Facilitate communication and decision-making. |
| **Team Lead / Facilitator**     | Guide the workshop, resolve conflicts, ensure adherence to process and timelines.                              |

---

## **Key Takeaways**

* **Ambiguity is Normal:** The core goal of this workshop is to demonstrate how to **clarify, prioritize, and iterate** through ambiguity. Requirements aren’t always crystal clear from the start, and it’s okay to have uncertainties at first.
* **Bridge Engineers** play a critical role in aligning stakeholders’ desires with the technical and AI capabilities of the team. They ensure that all team members are working toward the same goal and that decisions are well-communicated.
* **Structured Workshops and Documented Decisions** help prevent miscommunication, reduce rework, and foster a shared understanding of requirements.
* **Continuous Feedback Loops** enhance delivery quality and reduce risks, allowing teams to deliver incrementally while adjusting as needed based on user and stakeholder feedback.

---

## **Final Reflection**

Handling unclear or conflicting requirements effectively is essential in the AI era, where the boundaries of technology and expectations constantly evolve. By focusing on **clarification, prioritization, and iteration**, teams can not only deliver more reliable products but also manage stakeholder expectations in a meaningful and scalable way.

This workshop is just one way to reinforce those practices within your team and ensure the success of AI-powered projects moving forward.
