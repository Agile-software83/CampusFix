# CampusFix — Requirements Specification

## 1. Introduction

### 1.1 Purpose
This document defines the functional and non-functional requirements for CampusFix, a web-based platform that allows students to report campus facility issues and allows university staff to track and resolve them.

### 1.2 Scope
CampusFix covers three areas of functionality:
* Student-facing issue reporting
* Staff-facing issue tracking and management
* An AI chatbot that assists both groups in using the platform

CampusAI, Freshman AI, and the Digital Map are out of scope for this version.

### 1.3 Intended Audience
* Students (report issues)
* University maintenance staff (resolve issues)
* Lecturers (indirect users / viewers of classroom condition data)

### 1.4 Definitions
| Term | Meaning |
|---|---|
| Report | A single submitted record of a facility issue |
| Status | The current state of a report: Reported, In Progress, or Fixed |
| Issue Type | The category of problem being reported (e.g., AC, lighting, Wi-Fi, plumbing) |

---

## 2. Overall Description

### 2.1 Product Perspective
CampusFix is a standalone web application with two primary interfaces: a student reporting form and a staff dashboard, both backed by a shared set of report data. An AI chatbot layer supports both interfaces.

### 2.2 User Classes
| User Class | Description |
|---|---|
| Student | Submits reports and may check their status |
| Staff | Views, prioritizes, and updates reports |
| Lecturer | Views issue history relevant to specific rooms (optional/future) |

### 2.3 Assumptions and Dependencies
* A predefined list of buildings and rooms is available to populate the room-selection field.
* Staff have accounts or access credentials to reach the dashboard.
* The chatbot has access to report data to answer status questions.

---

## 3. Functional Requirements

### 3.1 Student Reporting
| ID | Requirement |
|---|---|
| FR-1 | The system shall allow a student to select a building and room from a predefined list. |
| FR-2 | The system shall allow a student to select an issue type from a predefined list (e.g., AC, lighting, fan, toilet, Wi-Fi, other). |
| FR-3 | The system shall allow a student to add an optional free-text description of the issue. |
| FR-4 | The system shall allow a student to submit a report with a single action. |
| FR-5 | The system shall confirm to the student that a report was submitted successfully. |
| FR-6 | The system shall allow a student to view the status of a report they submitted. |

### 3.2 Staff Management
| ID | Requirement |
|---|---|
| FR-7 | The system shall display a dashboard listing all submitted reports. |
| FR-8 | The system shall display a count of reports by status (Reported, In Progress, Fixed). |
| FR-9 | The system shall allow staff to change the status of a report (Reported → In Progress → Fixed). |
| FR-10 | The system shall allow staff to view report details, including room, issue type, description, and time submitted. |
| FR-11 | The system shall allow staff to sort or filter reports (e.g., by status, building, or issue type). |
| FR-12 | The system shall display a feed of recent report activity. |

### 3.3 AI Chatbot
| ID | Requirement |
|---|---|
| FR-13 | The chatbot shall guide a student through submitting a report step by step. |
| FR-14 | The chatbot shall allow a user to check the status of an existing report. |
| FR-15 | The chatbot shall answer basic questions about how to use the platform. |
| FR-16 | The chatbot shall be accessible from both the student and staff interfaces. |

### 3.4 Notifications (Proposed)
| ID | Requirement |
|---|---|
| FR-17 | The system shall notify a student when the status of their report changes. |
| FR-18 | The system shall notify staff when a new report is submitted. |

---

## 4. Non-Functional Requirements

| ID | Category | Requirement |
|---|---|---|
| NFR-1 | Usability | The reporting form shall be completable in three steps or fewer. |
| NFR-2 | Usability | The interface shall require no prior training or instructions to use. |
| NFR-3 | Performance | Report submission shall be confirmed to the user within 2 seconds under normal load. |
| NFR-4 | Availability | The platform shall be accessible 24/7, excluding scheduled maintenance windows. |
| NFR-5 | Reliability | Status updates made by staff shall be reflected to students in real time. |
| NFR-6 | Compatibility | The platform shall be accessible from both desktop and mobile browsers. |
| NFR-7 | Security | Staff-only functions (status updates, dashboard access) shall require authentication. |
| NFR-8 | Data Integrity | Submitted reports shall not be editable or deletable by students after submission. |
| NFR-9 | Scalability | The system shall support reporting across multiple buildings and an expanding number of rooms without redesign. |

---

## 5. Data Considerations
At a conceptual level, the system needs to track: reports, the rooms/buildings they relate to, issue types, report status, and the students and staff associated with each report. The full data structure (tables, fields, and relationships) is defined separately in the CampusFix Database Design document.

---

## 6. Constraints
* The initial version does not include CampusAI, Freshman AI, or Digital Map functionality.
* The system relies on accurate, up-to-date room and building reference data being maintained.
* No requirement is currently defined for anonymous vs. identified reporting; this should be clarified with the project group before development.

---

## 7. Future Considerations (Out of Current Scope)
* Integration with a digital campus map to visually display report locations
* A general-purpose AI assistant (CampusAI) for broader campus questions
* A dedicated onboarding assistant for first-year students (Freshman AI)
* Analytics for lecturers to identify rooms with recurring issues

---

## 8. Related Documents
* **Project Charter** — defines the purpose, background, and goals behind this project
* **Acceptance Criteria** — defines the specific testable conditions used to verify each requirement above
* **Database Design** — defines the technical data structure supporting these requirements
