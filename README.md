# William Cook | Software Portfolio

I’m a software engineer building practical applications across backend, full-stack, desktop, systems, and AI-assisted workflows.

My recent work includes distributed C#/.NET services, authenticated ASP.NET Core APIs, event-driven processing, SQL-backed persistence, React and TypeScript interfaces, Java and Spring Boot, native C++ and Qt desktop development, Python, hosted AI API integration, automated testing, Docker, and application observability.

This repository is the central landing page for the portfolio projects most relevant to the remote software engineering roles I am targeting. The projects emphasize practical problem-solving, reliable application behavior, clear documentation, and technologies commonly used in real business software.

### Approach to AI-Assisted Development

My education and professional experience are grounded primarily in object-oriented software development, including application design, debugging, data modeling, and maintainable code structure. More recently, I have incorporated AI-assisted development into my workflow as a practical engineering tool.

I use AI to accelerate research, compare implementation approaches, identify edge cases, improve documentation, and work more effectively in technologies where I have less experience, particularly frontend development. I remain responsible for the final design and implementation: I review generated code, adapt it to the existing architecture, validate behavior through builds and tests, and make sure I can explain the decisions represented in the finished work.

Used carefully, AI reinforces my established strengths while helping me broaden my technical range and deliver more complete applications. I view it as a force multiplier for engineering judgment—not a replacement for fundamentals, testing, or ownership of the result.

## Featured Projects

### Event-Driven Inventory Reorder Platform

**Tech:** C#, ASP.NET Core Web API, ASP.NET Core Identity, JWT Authentication, Worker Service, React, TypeScript, Entity Framework Core, SQL Server, Docker, Docker Compose, .NET Aspire, OpenTelemetry, OpenAPI, Azure Service Bus Emulator, typed HttpClient, xUnit

A distributed inventory operations platform built around an ASP.NET Core API, a background Processor, SQL-backed business state, queue-based reorder processing, and an independently hosted mock supplier service.

The application models a practical internal business workflow for organizations that need to monitor inventory and begin reordering before stock runs out. It includes a React/TypeScript operations dashboard, persistent application accounts, JWT bearer authentication, role-based authorization, Administrator-controlled account management, SQL-backed audit records, health monitoring, and correlated diagnostics across the API, message queue, Processor, supplier client, and supplier API.

The system is designed with eventual cloud deployment in mind. Its API, background Processor, supplier integration, databases, message queue, health checks, and distributed tracing are separated into independently deployable responsibilities. The complete application remains reproducible locally through .NET Aspire, Docker, SQL Server, and the Azure Service Bus Emulator without requiring paid cloud infrastructure.

Inventory items support configurable reorder quantities. When an item enters a low-stock state, the platform captures the configured amount as an immutable requested-quantity snapshot in the reorder event and message. This preserves historical workflow accuracy even when the inventory item’s configuration changes later.

The Processor consumes reorder messages and submits requests to the supplier service through a typed HTTP client. Stable Service Bus message identifiers are reused as supplier idempotency keys, allowing duplicate delivery, retries, and ambiguous-response recovery without creating duplicate supplier orders.

Supplier acceptance details and permanent rejection reasons are persisted and exposed through the API and Workflow interface. Retryable supplier failures leave the reorder event pending and eligible for Service Bus redelivery, while permanent rejection is recorded as a terminal business outcome.

Reorder processing also includes SQL-backed duplicate protection, persisted failure records, configurable retries, dead-letter handling, correlation propagation, and distributed tracing. Automated tests cover supplier acceptance, rejection, delayed responses, transient recovery, duplicate delivery, idempotent replay, and recovery when supplier acceptance succeeds before the local database update initially fails.

The project includes complete human-readable API documentation, generated OpenAPI contracts with JWT bearer and supplier idempotency metadata, and an operational runbook covering both Aspire and Docker/local execution. Final verification covered both runtime modes, supplier simulation behaviors, distributed tracing, committed configuration safety, and durable duplicate-submission handling.

It is one of the strongest examples in my portfolio of:
- distributed API, queue, background Processor, and external-service architecture
- ASP.NET Core Identity, JWT authentication, and role-based authorization
- Administrator account management and SQL-backed audit history
- event-driven workflow and service-to-service HTTP integration
- mutable configuration versus immutable workflow snapshots
- idempotent processing across both queue and HTTP boundaries
- duplicate-delivery and ambiguous-response recovery
- retryable technical failures versus terminal business rejection
- SQL-backed business, identity, audit, processing, and supplier state
- React visibility for pending, accepted, and rejected supplier workflows
- OpenTelemetry tracing and correlation across API, queue, Processor, and supplier boundaries
- cloud-ready service boundaries with fully reproducible local infrastructure
- complete OpenAPI contracts, API reference documentation, and operational runbooks
- verified Aspire and Docker/local runtime workflows
- production-informed integration and reliability testing
- Azure-oriented architecture demonstrated through zero-cost local emulation

**Repository:** [Event-Driven Inventory Reorder Platform](https://github.com/w-cook/event-driven-inventory-reorder-platform)

### TraceScope — Cross-Platform Desktop Log Analysis Workbench

**Tech:** C++17, Qt 6, Qt Widgets, Qt Charts, Qt Model/View, Qt Concurrent, CMake, Qt Test, GitHub Actions, AppImage

TraceScope is a cross-platform native desktop application for importing, normalizing, filtering, visualizing, inspecting, and exporting structured telemetry and diagnostic logs. It supports multiple source formats through a common investigation model, with reusable import profiles for source-specific mappings and an offline workflow designed for application, service, QA, field-support, and engineering diagnostic logs.

It is a strong example in my portfolio of:

- native C++ desktop application development with Qt
- configurable, multi-format log ingestion and normalization
- JSON Lines, structured JSON, CSV/TSV, Syslog, IIS W3C, structured XML, key-value/logfmt, and configurable text-log support
- Windows Event XML detection and profile-based mapping
- reusable versioned JSON import profiles for canonical and source-specific fields
- mapping-aware preview, validation, and raw-source inspection before import
- Qt model/view architecture with sortable dynamic columns and optional canonical fields
- severity, subsystem, and full-record text filtering
- selected-record inspection with preserved raw source data
- grouped warning/error analysis and filter-aware timeline visualization
- automatic and manual timeline resolutions from millisecond through day scale
- bounded fine-resolution timeline rendering with horizontal navigation
- background importing so long-running parses do not block the desktop UI
- streamed import paths with progress reporting and cooperative cancellation where supported
- measured large-file scenarios documented with conservative performance claims rather than unsupported maximum-size guarantees
- a multi-session investigation workspace with independent per-session state
- session switching, closing, and reloading without replacing unrelated open investigations
- persistent recent-file and recent-profile history
- CSV export with canonical and custom fields
- automated Qt Test coverage across importing, profiles, workspace behavior, filtering, analysis, and export
- GitHub Actions builds and tests on Windows and Linux
- automated Release-mode packaging for portable Windows x64 and Linux AppImage distributions
- package-content verification and automated startup smoke tests
- versioned prereleases with downloadable Windows, Linux, and samples artifacts produced from verified CI builds

The current `v0.9.0` prerelease adds a multi-session investigation workspace on top of the configurable import and large-file responsiveness foundations established in earlier releases. Multiple related log sources can remain open simultaneously with independent investigation state, while recent files and profiles provide a faster path back into recurring analysis workflows.

Development is now focused on **advanced filtering and navigation**, including richer filtering dimensions, saved filter presets, warning/error navigation, surrounding-event context, and drill-down from charts and summaries. Later roadmap phases add findings, deterministic analytics, session comparison, workspace persistence, live file following, and reporting.

**Repository:** [TraceScope — Qt Telemetry Log Inspector](https://github.com/w-cook/tracescope-qt-log-inspector)

### AI Research Brief Generator
**Tech:** Python, Streamlit, Pydantic, SQLite, pytest, Google Gemini API

This project demonstrates hosted-AI application integration through a local document analysis workflow that loads documents, chunks content, retrieves relevant context, builds structured prompts, and validates generated research briefs.

It is one of the strongest examples in my portfolio of:
- Python application development
- hosted AI API integration
- document loading, chunking, and retrieval
- structured prompt construction
- Pydantic validation of generated output
- local persistence for generated brief history

**Repository:** [AI Research Brief Generator](https://github.com/w-cook/ai-research-brief-generator)

### Job Application Pipeline Manager
**Tech:** Java, Spring Boot, Spring Data JPA, PostgreSQL, Flyway, JUnit 5, Mockito, Testcontainers, Docker Compose, GitHub Actions, Vue 3, TypeScript, Vite

This project demonstrates full-stack business workflow application development through a system for tracking job applications, follow-up tasks, screening questions, prepared answers, application statuses, and archived records.

It is a strong example in my portfolio of:
- Java/Spring Boot backend application structure
- layered API design with entities, repositories, services, DTOs, and controllers
- PostgreSQL-backed persistence with Flyway migrations
- validation-aware request handling
- service, controller, and Testcontainers-based repository testing
- Vue/TypeScript frontend workflow for a practical internal tool
- CI-backed build/test checks with GitHub Actions

**Repository:** [Job Application Pipeline Manager](https://github.com/w-cook/job-application-pipeline-api)

### FDA Recall Monitoring Dashboard
**Tech:** C#, ASP.NET Core Web API, Entity Framework Core, SQL Server, Vue 3, TypeScript, xUnit, GitHub Actions

This project demonstrates practical full-stack business application development through a dashboard for monitoring FDA recall data, saving watchlist criteria, syncing external API results, and reviewing imported records.

It is one of the strongest examples in my portfolio of:
- ASP.NET Core API development
- Vue/TypeScript frontend work
- external API integration
- SQL-backed persistence with Entity Framework Core
- integration testing and CI-backed build/test checks
- workflow-oriented internal application design

**Repository:** [FDA Recall Monitoring Dashboard](https://github.com/w-cook/fda-recall-monitoring-dashboard)

### ASP.NET Core Expense Tracker API
**Tech:** C#, ASP.NET Core Web API, Entity Framework Core, SQL Server, JWT Authentication, xUnit

This project demonstrates protected backend API development through registration/login, JWT authentication, user-scoped expense records, DTO validation, and integration-tested CRUD workflows.

It is a strong example in my portfolio of:
- JWT authentication and protected endpoints
- user-scoped data access
- REST-style API design
- validation and request handling
- integration testing

**Repository:** [ASP.NET Core Expense Tracker API](https://github.com/w-cook/dotnet-expense-tracker-api)

### ASP.NET Core Support Ticket API
**Tech:** C#, ASP.NET Core Web API, Entity Framework Core, SQL Server, xUnit

This project demonstrates backend application fundamentals through API development, validation, relational data handling, business logic implementation, and automated integration testing.

It is a strong example in my portfolio of:
- REST-style API design
- business logic implementation
- Entity Framework Core data access
- validation and request handling
- integration testing

**Repository:** [ASP.NET Core Support Ticket API](https://github.com/w-cook/dotnet-support-ticket-api)

### ASP.NET MVC Service Request Portal
**Tech:** C#, ASP.NET Core MVC, Entity Framework Core, SQL Server

This project demonstrates server-rendered business workflow development through form handling, validation, status transitions, and audit-style history tracking.

It is a useful example in my portfolio of:
- ASP.NET Core MVC application structure
- server-rendered business forms
- workflow status transitions
- validation-aware form handling
- SQL Server-backed application development through Entity Framework Core

**Repository:** [ASP.NET MVC Service Request Portal](https://github.com/w-cook/aspnet-mvc-service-request-portal)

## Additional C# / Unity Work

### Rogue Tactics — Unity/C# Technical Prototype
**Tech:** C#, Unity

Experimental tactical RPG prototype demonstrating grid-based movement, camera-relative perspective rotation, multi-height A* pathfinding, equipment interaction, fog of war, dialog, shader experiments, and gameplay systems design.

This project remains visible as additional C# technical work rather than as my primary job-targeting portfolio focus. It demonstrates complex problem-solving, debugging, and systems thinking in a larger interactive codebase, while the main portfolio emphasis is now the backend, full-stack, and AI-enabled business application projects above.

**Repository:** [Rogue Tactics Unity](https://github.com/w-cook/RogueTacticsUnity)

### Unity Bug-Fix Showcase
**Tech:** C#, Unity

This project demonstrates debugging and focused problem solving inside an existing Unity codebase.

It remains visible as additional work, but the main portfolio emphasis is now the backend, full-stack, and AI-enabled business application projects above.

**Repository:** [Unity Bug-Fix Showcase](https://github.com/w-cook/unity-bugfix-showcase)

## What These Projects Demonstrate

Across these projects, my portfolio demonstrates:

- object-oriented application design and maintainable code organization
- backend, full-stack, desktop, and internal business application development
- C#/.NET and ASP.NET Core application development
- Java and Spring Boot backend development
- native C++ and Qt desktop application development
- Python application development and hosted AI API integration
- React, Vue, and TypeScript frontend development
- SQL-backed persistence with Entity Framework Core and Spring Data JPA
- API design, validation, authentication, authorization, and role-based access
- background processing, event-driven workflows, and service-to-service integration
- idempotency, retries, failure recovery, and dead-letter handling
- automated unit, integration, relational database, and Testcontainers-based testing
- Docker-based local environments and .NET Aspire orchestration
- structured logging, health checks, correlation identifiers, and distributed tracing
- OpenAPI contracts and practical operational documentation
- external API integration and structured response validation
- file parsing, filtering, visualization, and export workflows
- CI build and test automation with GitHub Actions
- debugging and problem solving across business applications, desktop software, and Unity/C#

## Technologies Used

- C#
- .NET
- ASP.NET Core
- ASP.NET Core MVC
- ASP.NET Core Web API
- ASP.NET Core Identity
- JWT authentication
- Entity Framework Core
- SQL Server
- xUnit
- Java
- Spring Boot
- Spring Data JPA
- PostgreSQL
- Flyway
- JUnit 5
- Mockito
- Testcontainers
- Python
- Streamlit
- Pydantic
- pytest
- C++
- Qt Widgets
- Qt Charts
- Qt Test
- CMake
- TypeScript
- React
- Vue 3
- Vite
- Docker
- Docker Compose
- .NET Aspire
- Azure Service Bus Emulator
- OpenTelemetry
- OpenAPI
- GitHub Actions
- Google Gemini API
- openFDA API
- SQLite
- Unity

## What I’m Targeting

I’m targeting remote software engineering roles where I can contribute to practical, maintainable applications across areas such as:

- backend and full-stack application development
- APIs, background services, and event-driven systems
- SQL-backed business applications and internal tools
- desktop applications and developer-facing utilities
- external service and API integrations
- automated testing, debugging, and reliability improvements
- cloud-ready application architecture and containerized development
- AI-enabled workflows where hosted models support a larger software system

My recent work is strongest in object-oriented development, backend systems, and business application architecture, but I am open to roles across C#/.NET, Java, C++, Python, and modern frontend technologies.

## Notes on Project Demonstration

The featured repositories are demonstrated through their individual README files, including screenshots and project-specific writeups.

This hub is meant to make it easier to review the portfolio at a glance and quickly navigate to the most relevant repositories.

## Contact

This repository is the central entry point to my work. The best way to review the portfolio is through the featured repositories above.