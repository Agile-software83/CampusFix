# CampusFix — Database Design

## 1. Purpose
This document defines the database structure needed to support the functional and data requirements defined in the CampusFix Requirements Specification. It covers entities, fields, relationships, and constraints — not business justification or user-facing behavior.

---

## 2. Entity Overview

| Entity | Description |
|---|---|
| Student | A student who can submit reports |
| Staff | A staff member who manages and resolves reports |
| Building | A physical building on campus |
| Room | A room within a building |
| IssueType | A predefined category of facility issue |
| Report | A single submitted issue report |
| StatusHistory | A log of status changes for a report |
| Notification | A message sent to a user about a report update |

---

## 3. Entity Details

### 3.1 Student
| Field | Type | Constraints |
|---|---|---|
| student_id | INT | Primary Key, Auto Increment |
| name | VARCHAR(100) | Not Null |
| email | VARCHAR(150) | Not Null, Unique |
| created_at | DATETIME | Not Null, Default: current timestamp |

### 3.2 Staff
| Field | Type | Constraints |
|---|---|---|
| staff_id | INT | Primary Key, Auto Increment |
| name | VARCHAR(100) | Not Null |
| email | VARCHAR(150) | Not Null, Unique |
| role | VARCHAR(50) | e.g., "Maintenance", "Admin" |
| created_at | DATETIME | Not Null, Default: current timestamp |

### 3.3 Building
| Field | Type | Constraints |
|---|---|---|
| building_id | INT | Primary Key, Auto Increment |
| name | VARCHAR(100) | Not Null, Unique |

### 3.4 Room
| Field | Type | Constraints |
|---|---|---|
| room_id | INT | Primary Key, Auto Increment |
| building_id | INT | Foreign Key → Building(building_id), Not Null |
| room_number | VARCHAR(20) | Not Null |

*Unique constraint on (building_id, room_number) to prevent duplicate rooms per building.*

### 3.5 IssueType
| Field | Type | Constraints |
|---|---|---|
| issue_type_id | INT | Primary Key, Auto Increment |
| name | VARCHAR(50) | Not Null, Unique (e.g., "AC", "Lighting", "Wi-Fi", "Plumbing", "Other") |

### 3.6 Report
| Field | Type | Constraints |
|---|---|---|
| report_id | INT | Primary Key, Auto Increment |
| student_id | INT | Foreign Key → Student(student_id), Not Null |
| room_id | INT | Foreign Key → Room(room_id), Not Null |
| issue_type_id | INT | Foreign Key → IssueType(issue_type_id), Not Null |
| description | TEXT | Nullable (optional field) |
| status | ENUM('Reported','In Progress','Fixed') | Not Null, Default: 'Reported' |
| assigned_staff_id | INT | Foreign Key → Staff(staff_id), Nullable |
| submitted_at | DATETIME | Not Null, Default: current timestamp |
| updated_at | DATETIME | Not Null, Auto-updated on change |

### 3.7 StatusHistory
| Field | Type | Constraints |
|---|---|---|
| history_id | INT | Primary Key, Auto Increment |
| report_id | INT | Foreign Key → Report(report_id), Not Null |
| old_status | ENUM('Reported','In Progress','Fixed') | Nullable (null for initial creation) |
| new_status | ENUM('Reported','In Progress','Fixed') | Not Null |
| changed_by_staff_id | INT | Foreign Key → Staff(staff_id), Nullable |
| changed_at | DATETIME | Not Null, Default: current timestamp |

### 3.8 Notification
| Field | Type | Constraints |
|---|---|---|
| notification_id | INT | Primary Key, Auto Increment |
| report_id | INT | Foreign Key → Report(report_id), Not Null |
| recipient_type | ENUM('Student','Staff') | Not Null |
| recipient_id | INT | Not Null (references Student or Staff depending on recipient_type) |
| message | VARCHAR(255) | Not Null |
| is_read | BOOLEAN | Not Null, Default: false |
| created_at | DATETIME | Not Null, Default: current timestamp |

---

## 4. Relationships

| Relationship | Type |
|---|---|
| Building → Room | One-to-Many |
| Room → Report | One-to-Many |
| IssueType → Report | One-to-Many |
| Student → Report | One-to-Many |
| Staff → Report (assigned_staff_id) | One-to-Many |
| Report → StatusHistory | One-to-Many |
| Staff → StatusHistory (changed_by_staff_id) | One-to-Many |
| Report → Notification | One-to-Many |

---

## 5. Entity Relationship Diagram (Text Form)

```
Building (1) ───< Room (1) ───< Report (many) >─── (1) IssueType
                                     │
                                     ├──< StatusHistory
                                     │
                                     └──< Notification

Student (1) ───< Report
Staff (1) ───< Report (assigned_staff_id)
Staff (1) ───< StatusHistory (changed_by_staff_id)
```

---

## 6. Keys and Constraints Summary
* Every entity has a surrogate primary key (`*_id`, auto-incremented integer).
* Foreign keys enforce referential integrity between Report and its related entities (Student, Room, IssueType, Staff).
* `status` is constrained to a fixed set of values (Reported, In Progress, Fixed) to match the defined report lifecycle.
* `(building_id, room_number)` is unique to prevent duplicate room entries.
* `email` is unique for both Student and Staff to prevent duplicate accounts.

---

## 7. Notes and Assumptions
* `StatusHistory` is included to support auditability (who changed a report's status and when), even though it wasn't explicitly listed as a requirement — recommended for tracking accountability.
* `Notification` supports FR-17/FR-18 from the Requirements Specification (status change and new report alerts).
* Authentication-related fields (e.g., password hashes, session tokens) are intentionally excluded here and would belong in a separate Auth/Users schema.
* This design assumes one issue type per report; if multiple issue types per report are needed, a junction table (Report_IssueType) would replace the direct foreign key.
