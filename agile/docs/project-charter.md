# CampusFix — Project Charter

## 1. Project Name
CampusFix

## 2. Overview
CampusFix is a lightweight web platform built to close the gap between students noticing a campus facility issue and that issue actually getting fixed. It gives students a quick way to flag problems — things like a broken AC unit, a flickering light, a jammed toilet, or spotty Wi-Fi — and gives university staff a shared view to organize and act on those reports.

## 3. Background
Early conversations with students surfaced a consistent set of pain points around campus facilities:

* AC units that stop cooling properly
* Lights and fans that break and stay broken
* Toilets with ongoing issues
* Unreliable or dropped Wi-Fi
* Uncertainty about who is actually responsible for fixing things
* Reports that take a long time to reach anyone

**Key takeaway:** the friction isn't the problems themselves — it's that students have no clear, easy path to report them.

## 4. Problem Statement
Students often run into maintenance issues on campus but have no clear or convenient way to report them, leaving problems unresolved for longer than necessary.

## 5. Goal
Give students a fast, low-friction way to flag facility problems, and give staff a clear system for tracking and resolving those reports.

## 6. Who This Is For
* Students — the primary reporters of issues
* University maintenance staff — the ones resolving them
* Lecturers — indirect beneficiaries through better classroom conditions

## 7. Core Features

**For Students**
* Pick the affected room or location
* Choose the type of issue from a set list
* Optionally add extra detail
* Submit the report in one step

**For Staff**
* See all incoming requests in one dashboard
* Track counts by status (reported / in progress / fixed)
* Prioritize and assign requests
* Move a request through its lifecycle: Reported → In Progress → Fixed

**AI Assistant**
* Walks new users through submitting a report
* Lets users check on an existing report's status
* Answers basic "how do I..." questions about the platform itself

## 8. Reporting Flow
| # | Who | What Happens |
|---|---|---|
| 1 | Student | Notices a problem on campus |
| 2 | Student | Submits it through CampusFix |
| 3 | Staff | Picks it up and works on a fix |
| 4 | System | Status updates to Fixed once resolved |

## 9. Other Concepts We Looked At
Before landing on CampusFix, a few other directions came up during ideation:

* **CampusAI** — a general-purpose chatbot for questions about classrooms, schedules, services, and rules
* **Freshman AI** — a Q&A assistant aimed specifically at first-year students navigating university life
* **Digital Map** — an interactive map showing class locations alongside any open facility reports

These could be worth exploring later, either as extensions of CampusFix or as separate tools.

## 10. Scope

**Included**
* Submitting facility reports (room + issue type + optional notes)
* Staff-side tracking and status management
* Chatbot support for reporting and status checks

**Not Included (for now)**
* CampusAI, Freshman AI, and the Digital Map are not part of this build. Adding any of them would need to be a separate decision by the team.

## 11. Stakeholders
| Group | Why They're Involved |
|---|---|
| Students | Need a simple channel to raise issues |
| Maintenance staff | Own the process of triaging and fixing reports |
| Lecturers | Benefit from fewer unresolved issues in classrooms they use |

## 12. What Success Looks Like
* Reporting a problem takes only a couple of taps
* Staff can see and update request status without extra back-and-forth
* Time between a problem occurring and it being reported drops noticeably
* Students no longer have to guess who to contact

## 13. Risks & Open Questions
* Adoption risk: the platform only works if students actually use it instead of defaulting to word-of-mouth
* Data risk: reporting relies on having accurate room/building info to choose from
* Follow-through risk: reports need real staff ownership or they'll pile up unresolved
* The chatbot needs to be intuitive enough that no onboarding or instructions are required

## 14. Expected Outcome
A simpler reporting experience for students and a clearer workload view for staff — ultimately fewer facility issues sitting unreported or unresolved.

## 15. Next Steps
* Lock down the final issue-type list and room/building dataset
* Build out the staff dashboard (assign, prioritize, update status)
* Test the chatbot against real reporting scenarios
* Run a small pilot with a subset of students and staff before wider rollout
