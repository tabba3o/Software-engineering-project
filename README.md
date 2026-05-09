# Learning Management System — Group 07

## 1. Group Info

- *Group Number:* 07
- *Case Study:* Group 07 — Learning Management System (LMS)
- *Course:* Software Engineering — CS13477 — Spring 2026
- *Instructor:* Dr. Samer Elkababji
- *Repository:* https://github.com/tabba3o/Software-engineering-project

| # | Name | Student ID |
| :---: | :--- | :--- |
| 1 | Mohammad Tabba'a | 20220005 |
| 2 | Tala Hammouri | 20210061 |
| 3 | Lojain Hamdan | 20210576 |
| 4 | Jude Mamoon | 20210415 |

---

## 2. Overview

### System Purpose

The Learning Management System (LMS) is a web-based platform that supports online teaching, learning, and academic management. It enables instructors to deliver course content, create assessments, grade submissions, and distribute feedback, while students access course resources, submit assignments, and track their academic performance. Administrators manage user accounts, course offerings, and platform operations. The system is integrated with an external Authentication System, a University Student Information System (SIS), and an Email & Notification Service to support a complete academic workflow.

### Tools Used

- *Visual Studio Code (VS Code)* — primary IDE for editing diagrams, Markdown, and report files.
- *PlantUML* — text-based UML modelling for all diagrams; sources kept under /uml/.
- *C4-PlantUML library* — used for C4 Level 1 (Context) and C4 Level 2 (Container) diagrams.
- *Pandoc* — conversion of the Markdown report into the final PDF deliverable.
- *Git & GitHub* — version control, per-member commits, tagged releases (v1.0.0, v2.0.0).

---

## 3. Diagrams

All diagram sources are stored as .puml files under /uml/ and exported to .png for embedding in the report.

### Part I — Context

- *C4 Level 1 — System Context Diagram* (lms_c4_l1.puml): the LMS as a single black box with its three human actors (Student, Instructor, Administrator) and three external systems (Authentication System, University SIS, Email & Notification Service).
- *C4 Level 2 — Container Diagram* (c4_l2_container_lms.puml): decomposes the LMS into Web Application (React SPA), Backend API Server (Python/Django), Relational Database (PostgreSQL), and File Storage Service (Object Storage).
- *Context Activity Diagram with swimlanes* (lms_act_context_enrollment.puml): cross-system student enrollment process, with each swimlane being one of the four C4 L1 «system» participants (LMS, University SIS, Authentication System, Email & Notification Service).

### Part II — Interactions

- *Composite Use Case Diagrams* — one per actor: student_usecase.puml, instructor_usecase.puml, administrator_usecase.puml.
- *Individual Use Case Diagrams* with <<include>> / <<extend>> relationships:
  - Student: student_submit_assignment.puml, student_access_course_materials.puml, student_view_performance_report.puml.
  - Instructor: instructor_upload_lecture_material.puml, instructor_grade_submission.puml, instructor_create_assessment.puml.
  - Administrator: admin_enroll_student.puml, admin_assign_instructor.puml, admin_generate_report.puml.
- *Use Case Descriptions* — tabular format, one per individual use case, embedded in the report.
- *Sequence Diagrams — High-Level (stakeholder view):* lms_seq_hl_submit_assignment.puml, lms_seq_hl_grade_submissions.puml, lms_seq_hl_enroll_students.puml.
- *Sequence Diagrams — Detailed (developer view):* lms_seq_dev_submit_assignment.puml, lms_seq_dev_grade_submissions.puml, lms_seq_dev_enroll_students.puml.

### Part III — Structure

- *Class Diagram* (lms_class_diagram.puml): ten domain classes with attributes, operations, and three relationship kinds — generalization (User → Student / Instructor / Administrator), composition (Course owns Enrollment / Assessment; Assessment owns Submission; Submission owns Grade), and aggregation (Course contains Material).

### Part IV — Behavior

The LMS is a hybrid system. Its dominant character is data-driven and a discrete event-driven slice exists in the submission lifecycle. Part IV combines both:

- *Internal-scope Activity Diagrams with swimlanes* — the data-driven view at scenario scope:
  - act_submit_assignment.puml — student submission scenario (UC-S1) with deadline and validation branches.
  - act_grade_submissions.puml — instructor grading scenario (UC-I3) with regrade-request sub-flow.
  - act_enroll_students.puml — administrator enrollment scenario (UC-A1) with prerequisite, capacity, and waitlist branches.
- *State Diagram* (submission_state.puml) — the event-driven view: lifecycle of a Submission from Draft → Submitted → Under Review → Graded → Released with an optional Regrade Requested branch.
- *State-Stimulus Table* — tabular companion to the state diagram listing every transition with current state, stimulus, guard, next state, and action.

---

## 4. Repo Structure


.
+-- README.md                          # Title page of the report
+-- docs/
|   +-- se_report_group_07.md          # Full Markdown report (source)
|   \-- se_report_group_07.pdf         # Final PDF report (Pandoc output)
\-- uml/
    +-- *.puml                         # PlantUML source for every diagram
    \-- *.png                          # Rendered images embedded in the report


- */README.md* — the team's title page; embedded as the first page of the report.
- */docs/* — the report in Markdown source form and the final PDF deliverable.
- */uml/* — all PlantUML sources and their rendered PNG exports; the report references these PNGs via relative paths (../uml/*.png).

---

## 5. Contributions

### Member Roles

Work was distributed across the four parts of the project, with each member owning approximately one quarter of the deliverables and contributing to report editing.

| Member | Role |
| :--- | :--- |
| Jude Mamoon | Part I — C4 L1 (Context) & C4 L2 (Container) modelling; context-scope swimlane activity diagram; report editing. |
| Tala Hammouri | Part II — Composite and individual use case diagrams; tabular use case descriptions; sequence diagrams; report editing. |
| Lojain Hamdan | Part II — Sequence diagrams (HL & developer); class diagram; report editing. |
| Mohammad Tabba'a | Part IV — Behaviour-scope activity diagrams, state diagram, and state-stimulus table; report editing. |

### Commits per Team Member

| Member | Number of Commits |
| :--- | :---: |
| Jude Mamoon | 10 |
| Tala Hammouri | 11 |
| Lojain Hamdan | 11 |
| Mohammad Tabba'a | 10 |
