🛡️ EduGuard – Student Dropout Risk & Intervention Management Platform

An early-warning, explainable AI, and intervention management platform designed to identify student disengagement early and empower educators with actionable retention strategies.

📖 Overview & Problem Statement

Schools and colleges frequently notice a student's disengagement only after they have already dropped out. While early warning signals—such as declining attendance, dropping assessment scores, fee delays, and reduced classroom engagement—exist, they are typically siloed across separate spreadsheets and legacy systems.

EduGuard bridges this gap by combining academic, behavioral, and socio-economic indicators into a unified, privacy-first platform. Using anonymised student data (UDISE+-style / Kaggle datasets), EduGuard predicts dropout risk tiers, explains the exact contributing factors behind every prediction, and orchestrates targeted interventions through an end-to-end case management workflow.

✨ Core Functionalities

👤 Student Profile Management: Maintain strictly anonymised student records (e.g., S-104) housing enrolment metadata, longitudinal attendance trends, and grade histories.

🔗 Unified Data Integration: Aggregate attendance logs, formative/summative assessments, fee/scholarship statuses, and extracurricular engagement metrics into a single 360-degree view.

🎯 Dropout Risk Prediction: Classify students into actionable risk tiers (Low, Medium, High) with a continuous probability score.

🔍 Risk Factor Explanation (XAI): Provide transparent, human-readable explanations highlighting the top contributing features for each student's risk profile.

💡 Intervention Recommendation Engine: Automatically prescribe tailored support actions—such as mentoring assignment, remedial subject classes, counselling referrals, or scholarship eligibility checks.

📋 Case Management Workflow: Enable staff to open, assign, track, annotate, and close student intervention cases with full audit trails.

📊 Cohort & Early-Trend Analytics: Identify systemic macro-trends across specific grades, sections, or bottleneck subjects (e.g., Class 9 Mathematics).

📈 Outcome & Effectiveness Dashboard: Measure post-intervention deltas in attendance and grades to evaluate whether specific support programs successfully reduced dropout risk.

🏢 Enterprise Microservices Architecture: Built on Java & Spring Boot, leveraging RESTful inter-service communication, relational database persistence, explainable AI/ML scoring, and a responsive Web UI.

🏗️ System Architecture

EduGuard utilizes a decoupled microservices architecture to separate core student data management from compute-intensive AI risk inference and intervention orchestration.

+-------------------------------------------------------------------------+
|                        EduGuard Web UI (Frontend)                       |
|       (Risk Tier Dashboard, Natural Language/Filter Query, Cases)       |
+------------------------------------+------------------------------------+
                                     | REST API (HTTP/JSON)
                                     v
+-------------------------------------------------------------------------+
|                   Microservice 2: Risk & Recommendation                 |
|                        (risk-recommendation-service)                    |
|  - Orchestrates Queries & Case Workflows                                |
|  - Executes AI/ML Classification & Feature Importance Engine            |
|  - Maps Risk Profiles to Tailored Interventions                         |
+-----------------+-------------------------------------+-----------------+
                  | REST (WebClient / RestTemplate)     | JPA / Hibernate
                  v                                     v
+------------------------------------+ +----------------------------------+
|   Microservice 1: Student Data     | |       Risk & Case Database       |
|       (student-data-service)       | | (Risk Scores, XAI Factors, Cases)|
|  - Enrolment, Attendance, Grades   | +----------------------------------+
|  - Fee & Engagement Aggregation    |
+-----------------+------------------+
                  | JPA / Hibernate
                  v
+------------------------------------+
|       Student Records Database     |
|  (Anonymised UDISE+ / Kaggle Data) |
+------------------------------------+
🛠️ Technology Stack

Backend Framework: Java 17+, Spring Boot 3.2.x (Spring Web, Spring Data JPA, Spring Validation)

Inter-Service Communication: Spring WebClient / RestClient (REST over HTTP/JSON)

AI / ML & Explainability: Java ML Engine (Tribuo / Smile / Custom Weighted Logistic & Tree Attribution Model) with local feature contribution scoring

Database: PostgreSQL (Production) / H2 In-Memory or File DB (Rapid 3-Hour PoC setup)

Frontend UI: React.js + Tailwind CSS (or Spring Boot Thymeleaf + Bootstrap 5 + Chart.js)

Build & Dependency Management: Apache Maven

API Documentation: SpringDoc OpenAPI (Swagger UI)

Prerequisites

JDK 17 or higher installed (java -version)

Apache Maven 3.8+ installed (mvn -version)

Node.js 18+ (if running the standalone React UI)
