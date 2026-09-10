# CampusFix — Acceptance Criteria

## 1. Purpose
This document defines the specific, testable conditions used to verify that each requirement in the CampusFix Requirements Specification has been implemented correctly. Each item follows a Given / When / Then format and maps back to its related requirement ID.

---

## 2. Student Reporting

### AC-1 — Select building and room (FR-1)
- **Given** a student is on the report form
- **When** they open the room selection field
- **Then** they see a list of valid buildings and rooms to choose from
- **And** they cannot proceed without selecting one

### AC-2 — Select issue type (FR-2)
- **Given** a student is on the report form
- **When** they open the issue type field
- **Then** they see a predefined list of issue types (e.g., AC, Lighting, Wi-Fi, Plumbing, Other)
- **And** they cannot submit the form without selecting one

### AC-3 — Optional description (FR-3)
- **Given** a student is filling out the report form
- **When** they leave the description field blank
- **Then** the form still allows submission
- **And** when they enter text, it is saved along with the report

### AC-4 — Submit report (FR-4)
- **Given** a student has selected a room and issue type
- **When** they press "Submit"
- **Then** a new report is created with status "Reported"
- **And** the submission completes in a single action, with no additional required steps

### AC-5 — Submission confirmation (FR-5)
- **Given** a student has submitted a report
- **When** the submission is processed successfully
- **Then** the student sees a clear confirmation message
- **And** if submission fails, the student sees an error explaining why

### AC-6 — View report status (FR-6)
- **Given** a student has previously submitted a report
- **When** they check their report list or ask the chatbot
- **Then** they see the current status (Reported, In Progress, or Fixed)

---

## 3. Staff Management

### AC-7 — View all reports (FR-7)
- **Given** a staff member logs into the dashboard
- **When** the dashboard loads
- **Then** all submitted reports are visible in a list or table

### AC-8 — Status counts (FR-8)
- **Given** reports exist in the system with different statuses
- **When** a staff member views the dashboard
- **Then** they see a count of reports for each status: Reported, In Progress, Fixed
- **And** the counts match the actual number of reports in each status

### AC-9 — Update report status (FR-9)
- **Given** a staff member is viewing a report
- **When** they change its status
- **Then** the report only moves through Reported → In Progress → Fixed (no invalid transitions)
- **And** the change is saved and reflected immediately on the dashboard

### AC-10 — View report details (FR-10)
- **Given** a staff member selects a report
- **When** the detail view opens
- **Then** they see the room, issue type, description (if provided), and submission timestamp

### AC-11 — Sort/filter reports (FR-11)
- **Given** a staff member is viewing the dashboard
- **When** they apply a filter (e.g., by status, building, or issue type)
- **Then** only matching reports are displayed
- **And** clearing the filter restores the full list

### AC-12 — Recent activity feed (FR-12)
- **Given** reports have been submitted or updated
- **When** a staff member views the dashboard
- **Then** a feed shows the most recent report activity, ordered by most recent first

---

## 4. AI Chatbot

### AC-13 — Guided reporting (FR-13)
- **Given** a first-time user opens the chatbot
- **When** they ask to report an issue
- **Then** the chatbot walks them through selecting a room, issue type, and optional description without needing outside instructions

### AC-14 — Status check via chatbot (FR-14)
- **Given** a user has an existing report
- **When** they ask the chatbot for its status
- **Then** the chatbot returns the current status of that report

### AC-15 — Platform help (FR-15)
- **Given** a user asks a basic "how do I..." question
- **When** the chatbot processes the question
- **Then** it returns a relevant, accurate answer about using CampusFix

### AC-16 — Chatbot availability (FR-16)
- **Given** a user is on either the student or staff interface
- **When** they look for the chatbot
- **Then** it is accessible from both interfaces

---

## 5. Notifications

### AC-17 — Student notified of status change (FR-17)
- **Given** a staff member updates a report's status
- **When** the update is saved
- **Then** the student who submitted the report receives a notification of the change

### AC-18 — Staff notified of new report (FR-18)
- **Given** a student submits a new report
- **When** the submission completes
- **Then** relevant staff receive a notification that a new report has come in

---

## 6. Non-Functional Acceptance Criteria

### AC-19 — Form simplicity (NFR-1)
- **Given** a student begins a report
- **When** they complete it
- **Then** the entire process takes no more than 3 steps

### AC-20 — No training required (NFR-2)
- **Given** a new user has never used CampusFix before
- **When** they use the platform without any instructions
- **Then** they are able to successfully submit a report

### AC-21 — Submission response time (NFR-3)
- **Given** a student submits a report under normal system load
- **When** the submission is processed
- **Then** confirmation is shown within 2 seconds

### AC-22 — Real-time status sync (NFR-5)
- **Given** a staff member updates a report's status
- **When** the student views their report
- **Then** the updated status is reflected without requiring a manual refresh delay beyond a few seconds

### AC-23 — Cross-device access (NFR-6)
- **Given** a user accesses CampusFix
- **When** they use either a desktop or mobile browser
- **Then** the platform is fully usable on both

### AC-24 — Staff authentication (NFR-7)
- **Given** an unauthenticated user
- **When** they attempt to access the staff dashboard or update a report status
- **Then** access is denied until they authenticate

### AC-25 — Report immutability for students (NFR-8)
- **Given** a student has submitted a report
- **When** they try to edit or delete it afterward
- **Then** the system does not allow this action

---

## 7. Notes
* Each acceptance criterion should be validated during QA/testing before a feature is marked complete.
* Criteria are written to be testable as-is; some (e.g., response time, cross-device support) may require specific test environments or tools to verify.
* Any new functional requirement added later should have corresponding acceptance criteria added here before development begins.
