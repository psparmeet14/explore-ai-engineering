**Context Engineering**
- Providing the right information to the LLM in the right format so it can complete the task effectively. (Setting the stage for success)
- Good context engineering involves a mix of :
   - Prompt engineering
   - State/history
   - Long term memory
   - RAG
   - Structured Outputs
 

### Global Rules

Prompt 1:

Generate a DEVELOPMENT_STANDARDS.md file that defines universal development standards applicable to all projects.
The document should include:
Code Style Guidelines: Standardize naming conventions, indentation, commenting, and file organization.

Version Control Practices: Outline branching strategies, commit message formats, and merge protocols.

Testing Requirements: Specify unit testing, integration testing, and code coverage expectations.

Documentation Standards: Define requirements for code comments, README files, and API documentation.

Security Best Practice: Include guidelines for input validation, authentication, and dependency management.

Continuous Integration/Continuous deployment (CI/CD): Describe automated build, test, and deployment processes.

Code Review Procedures: Set expectations for peer reviews, approval processes, and code quality checks.

Ensure the DEVELOPMENT_STANDARDS.md is clear, concise, and provides actionable guidelines that can be uniformly applied across diverse projects.

---

### Creating a service using agentic coding: (One-shot prompt)

Prompt 1

Create a Product Requirements Document (PRD.md file) in Markdown format for a lightweight web service that enables incident reporting and management. The service should be written in Java 21 with the latest version of Spring Boot and support the following:
Key Functional Requirements:
Users or systems can report incidents (e.g., app crashses, failed jobs, customer complaints).
Incidents are stored in a relational database.
Endpoints must allow:
Listing incidents
Viewing a single incident by ID
Marking incidents as resolved
Assigning a category or tag to an incident

Non-Functional Requirements:
Lightweight and easy to run locally
Follow RESTful API conventions
Use standard Spring Boot practices
Clearly document each endpoint

Technical Constraints:
Language: Java
Framework: Spring Boot
Database: Use in-memory H2 for the demo

The PRD should be clear and structured with the followign sections:
Overview
Functional Requirements
Non-Functional Requirements
API Specification (with sample endpoints and expected payloads)
Data Model
Technical Stack
Out of Scope

---


Prompt 2

Using the content of the file PRD.md as the authoritative product requirements, implement a Java + Spring Boot project for an Incident Reporting Web Service.
The service should:
Allow reporting, listing, resolving, and categorizing incidents.
Use an in-memory H2 database for persistence.
Be lightweight and demo-ready with clear, annotated code.

Please generate:
Java source code: models, controllers, servicers, repositories (Spring Data JPA).

A minimal application.properties for Spring Boot configuration.

A README.md explaining how to run the project (build, dependencies, port).

Only REST endpoints, no UI.

Constraints:
Skip test implementation for now.
Follow idiomatic Spring Boot conventions.
Structure the code in a Maven-style layout: src/main/java, src/main/resources.
Reference the PRD.md file directly for endpoint specs, data models, and tech stack decisions.

---

### Reverse Engineering

Prompt 1

Summarize what this project does. Include main features, tech stack, and key components.

--- 

Prompt 2

Outline the project's architecture. List main controllers, servicers, and how data flows through them.

---

Prompt 3

Find and explain the GET /api/incidents/{id} endpoint. Show which controller handles it, what it does, and how it interacts with services and DB.

---

### Automated Test Generation
(prefer incremental approach)

Prompt 1

Create unit tests for the getIncidentById method from the IncidentService class.

---

### Documentation

Prompt 1

Review README.md and suggest improvements. Check for clarity, completeness, outdated steps, and missing setup or usage info.

Prompt 2 (Rewriting documentation for different audiences)

Rewrite the API documentation to be suitable for external partners in an EXTERNAL_DOCUMENTATION.md file. Make it concise, formal, and remove internal implementation notes.

---

### Refactoring
(make small incremental changes)

Prompt 1

Refactor all Java classes to remove boilerplate getters, setters, constructors and toString. Use Lombok annotations like @Data, @AllArgsConstructor, and @NoArgsConstructor.

---

### CI/CD Pipelines
(build and deploy pipelines)

- Use SDK in a pipeline
- Eg., self-healing pipeline; Fix tests; Test generation; Code implementation; Code reviews; Report generation; Documentation


---



