# Learning Management System — Group 07

## 1. Group Info

- **Group Number:** 07
- **Case Study:** Group 07 — Learning Management System (LMS)
- **Course:** Software Engineering — CS13477 — Spring 2026
- **Instructor:** *Dr. Samer Elkababji*

| # | Name | Student ID |
| :---: | :--- | :--- |
| 1 | *Mohammad Tabba'a* | *20220005* |
| 2 | *Tala Hammouri* | *20210061* |
| 3 | *Lojain Hamdan* | *20210576* |
| 4 | *Jude Mamoon* | *20210415* |

---

## 2. Overview

### System Purpose

The Learning Management System (LMS) is a web-based platform that supports online teaching, learning, and academic management. It enables instructors to deliver course content, create assessments, grade submissions, and distribute feedback, while students access course resources, submit assignments, and track their academic performance. Administrators manage user accounts, course offerings, and platform operations. The system is integrated with an external Authentication System, a University Student Information System (SIS), and an Email & Notification Service to support a complete academic workflow.

### Tools Used

- **Visual Studio Code (VS Code)** — primary IDE for editing diagrams, Markdown, and report files.
- **PlantUML** — text-based UML modelling for all diagrams; sources kept under `/uml/`.
- **C4-PlantUML library** — used for C4 Level 1 (Context) and C4 Level 2 (Container) diagrams.
- **Pandoc** — conversion of the Markdown report into the final PDF deliverable.
- **Git & GitHub** — version control, per-member commits, tagged releases (`v1.0.0`, `v2.0.0`).

---

## 3. Diagrams

All diagram sources are stored as `.puml` files under `/uml/` and exported to `.png` for embedding in the report.

### Part I — Context

- **C4 Level 1 — System Context Diagram** (`lms_c4_l1.puml`): shows the LMS as a single black box and its three human actors (Student, Instructor, Administrator) together with the three external systems it integrates with (Authentication System, University SIS, Email & Notification Service).
- **C4 Level 2 — Container Diagram** (`c4_l2_container_lms.puml`): decomposes the LMS into its internal containers — Web Application (React SPA), Backend API Server (Python/Django), Relational Database (PostgreSQL), and File Storage Service (Object Storage) — and their protocols.
- **Activity Diagrams with Swimlanes** — one per key scenario:
  - `act_submit_assignment.puml` — Student submission flow including deadline and validation branches.
  - `act_grade_submissions.puml` — Instructor grading loop with regrade-request sub-flow.
  - `act_enroll_students.puml` — Administrator enrollment with prerequisite check, seat availability, and waitlisting.

### Part II — Interactions

- **Composite Use Case Diagrams** (one per actor):
  - `student_usecase.puml`
  - `instructor_usecase.puml`
  - `administrator_usecase.puml`
- **Individual Use Case Diagrams** (with `<<include>>` / `<<extend>>`):
  - Student: `student_submit_assignment.puml`, `student_access_course_materials.puml`, `student_view_performance_report.puml`
  - Instructor: `instructor_upload_lecture_material.puml`, `instructor_grade_submission.puml`, `instructor_create_assessment.puml`
  - Administrator: `admin_enroll_student.puml`, `admin_assign_instructor.puml`, `admin_generate_report.puml`
- **Use Case Descriptions** (tabular): provided in the report for each individual use case.
- **Sequence Diagrams — High-Level (stakeholder view):**
  - `lms_seq_hl_submit_assignment.puml`
  - `lms_seq_hl_grade_submissions.puml`
  - `lms_seq_hl_enroll_students.puml`
- **Sequence Diagrams — Detailed (developer view):**
  - `lms_seq_dev_submit_assignment.puml`
  - `lms_seq_dev_grade_submissions.puml`
  - `lms_seq_dev_enroll_students.puml`

---

## 4. Repo Structure

```
.
├── README.md              # This file — title page of the report
├── docs/
│   ├── se_report_group_07.md    # Full Markdown report (source)
│   └── se_report_group_07.pdf   # Final PDF report (Pandoc output)
└── uml/
    ├── *.puml             # PlantUML source for every diagram
    └── *.png              # Rendered images embedded in the report
```

- **`/README.md`** — the team’s title page; embedded as the first page of the report.
- **`/docs/`** — the report in Markdown source form and the final PDF deliverable.
- **`/uml/`** — all PlantUML sources and their rendered PNG exports; the report references these PNGs via relative paths (`../uml/*.png`).

---

## 5. Contributions

### Member Roles

| Member | Role |
| :--- | :--- |
| *Mohammad Tabba'a* | *Activity diagrams & report editing* |
| *Tala Hammouri* | *Use case diagrams & descriptions* |
| *Lojain Hamdan* | *Sequence diagrams (HL & developer)* |
| *Jude Mamoon* | *C4 L1(Context) & L2(Container) modelling* |

### Commits per Team Member

| Member | Number of Commits |
| :--- | :---: |
| *Mohammad Tabba'a* | *6* |
| *Tala Hammouri* | *6* |
| *Lojain Hamdan* | *6* |
| *Jude Mamoon* | *6* |
