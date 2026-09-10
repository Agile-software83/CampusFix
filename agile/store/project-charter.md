# Project Charter: CampusFix

**Tagline:** Report it. We'll fix it.  
**Website:** [www.campusfix.com](https://www.campusfix.com)

---

## 1. Project Overview

CampusFix is a simple issue-tracking platform that lets students report campus facility problems — such as broken air conditioners, lights, fans, toilets, and Wi-Fi — while giving university staff the tools to organize, prioritize, and resolve those reports in real time.

---

## 2. Background / Empathize Findings

Through discussions with students about the problems they face on campus, the team identified several recurring issues:

- Air conditioners sometimes do not work
- Lights or fans can be broken
- Toilets may have problems
- Wi-Fi can stop working
- Students don't always know who to contact about these problems
- Some problems take a long time to get reported

**Main finding:** Students need an easy way to report problems on campus.

---

## 3. Problem Statement

Students have difficulty reporting campus problems because they may not know who to contact or how to report them.

---

## 4. Purpose / Goal Statement

Students need a simple way to report maintenance problems on campus so that university staff can find and fix them quickly.

---

## 5. Why We Chose This Solution

Students often encounter problems on campus — broken air conditioners, lights, fans, toilets, or Wi-Fi — but they may not know how to report them. CampusFix gives students a simple way to report these problems and helps university staff know what needs to be fixed.

---

## 6. Solution Overview

CampusFix is a simple issue-tracking website where:

- Students report facility problems by selecting the room and issue type
- Staff update the status of each report from "Reported" to "Fixed" in real time
- An AI chatbot guides users through reporting, checking status, and navigating the platform, all through an easy-to-understand interface

### How It Works

| Step | Actor | Action |
| :---: | :--- | :--- |
| **1** | Student | Finds a problem on campus |
| **2** | Report | Problem is submitted through CampusFix (room, issue type, optional description) |
| **3** | University Staff | Receives the report and takes action to fix it |
| **4** | Fixed | The problem is fixed and the status is updated in real time |

---

## 7. Key Features (from prototype)

- **Report an Issue** — Select room, select issue type (e.g., light not working, water leak, AC not cooling, other), optional description field.
- **Staff Dashboard** — Overview of reported, in-progress, and fixed issue counts, plus a recent reports feed.
- **AI Chatbot Assistant** — Guides users through reporting and status checks.

---

## 8. Alternative Ideas Considered

During ideation, the team also discussed:

- **CampusAI** — An AI chatbot answering questions about classrooms, schedules, campus services, and university rules.
- **Freshman AI** — An AI assistant designed specifically for first-year students to answer common questions about university life.
- **Digital Map** — A digital map showing where courses take place and where problems have been reported.

*Additional potential benefit identified:* Lecturers could use issue data to choose which classrooms to teach in based on which room has the fewest reported issues.

> **Selected Direction:** CampusFix (Campus Maintenance Report) was selected as the primary direction.

---

## 9. Stakeholders

| Stakeholder | Role / Interest |
| :--- | :--- |
| **Students** | Report facility issues; need a simple, accessible reporting channel |
| **University Maintenance Staff** | Receive, prioritize, and resolve reported issues |
| **Lecturers** | Benefit from visibility into classroom condition/issue history |
| **First-year Students (future scope)** | Potential users of related support features (e.g., Freshman AI) |

---

## 10. Success Criteria

- Students can submit a facility issue report in a few simple steps (room + issue type).
- Staff can view, prioritize, and update the status of reports in real time.
- Reduced average time between an issue being found and being reported.
- Increased clarity for students on who to contact and how.

---

## 11. Scope

### In Scope

- Student-facing issue reporting form (room selection, issue type, description)
- Staff dashboard for tracking and updating report status
- AI chatbot for reporting guidance and status checks

### Out of Scope (for initial version)

- CampusAI general Q&A chatbot
- Freshman AI onboarding assistant
- Digital campus map

---

## 12. Next Steps

1. Finalize UI/UX design based on prototype.
2. Define full list of issue categories and room/building data structure.
3. Build staff-side workflow (accept/reject, status updates, notifications).
4. Pilot with a limited group of students and staff for feedback.
