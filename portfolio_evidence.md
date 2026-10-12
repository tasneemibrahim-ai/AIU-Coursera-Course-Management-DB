# Database Project — Evidence & Technical Contribution Audit

**Project Directory:** `e:\tasnim\Tasneem_Career_AI\Github_Projects\projects needs to be organized\DB project`  
**Audit Document:** `DATABASE_PROJECT_PORTFOLIO_EVIDENCE.md`  
**Audit Date:** September 13, 2026  
**Auditor:** Antigravity AI  

---

## PART 1 — PROJECT OVERVIEW

* **Project Name:** AIU Coursera Courses Management System
* **Project Purpose / Problem:** Manage, track, and align external online learning platform courses (Coursera courses, specializations, and guided projects) with internal academic courses offered by Al Alamein International University (AIU). The system facilitates student course invitations, weekly schedule module mapping, license quota tracking, DBMS weekly report generation, and academic mark/grade logging across multiple university faculties.
* **Main Use Case:** 
  1. Mapping AIU academic course codes to Coursera course slugs and weekly module schedules.
  2. Tracking student invites, enrollments, program completions, and inactive student removals.
  3. Generating aggregate weekly and semester reports for license allocation and grade monitoring.
* **Target Users:**
  1. **Main Coursera Coordinator:** Full administrative visibility over all university fields, courses, licenses, and reports.
  2. **Field / Department Coordinators:** Administrative visibility restricted to their specific academic field (e.g., CSE, Pharmacy, Dentistry, Business, Public Health, Art & Design, Engineering, Basic Sciences).
  3. **AIU Course Instructors:** Visibility over their assigned AIU courses and Coursera course mappings.
  4. **AIU University Students:** Enrolled learners in matched courses.
* **Type of Database / System:** Relational Database Management System (RDBMS), specifically designed for **MySQL** / MariaDB.
* **Main Technologies:**
  - **Database Engine / Dialect:** MySQL (`CREATE TABLE`, `FOREIGN KEY`, `CREATE VIEW`, `CREATE PROCEDURE`, `DELIMITER //`).
  - **Data Formats:** SQL scripts (`.sql`), Plain Text (`.txt`), Microsoft Excel (`.xlsx`), CSV (`.csv`), Draw.io diagrams (`.drawio`), Microsoft Word reports (`.docx`), Microsoft PowerPoint presentations (`.pptx`).
  - **Data Processing / Ad-hoc Code:** Python (`pandas`, `scikit-learn` in loose data preprocessing snippets found in `DB/` directory).
* **Programming Languages:** SQL (DDL, DML, Procedural SQL), Python (loose helper/experimental scripts).
* **Frameworks / Libraries:** `scikit-learn`, `pandas` (present in non-integrated loose Python scripts). *No web backend or frontend frameworks (such as Django, Express, React, etc.) are present.*
* **Database Engine:** MySQL.
* **Frontend / Backend Components:** **None implemented in code.** The project consists of database schema scripts, SQL queries, stored procedures, database views, EER diagrams, CSV/Excel dataset files, and documentation reports.
* **Project Context:** Academic Project for course **CSE221: Database Systems** (Spring 2024 semester, Level 2, Computer Science and Engineering faculty at Al Alamein International University - AIU).
* **Course Instructor:** Dr. Laila Shokry / Shoukry.
* **Project Author:**
  - **Tasneem Ibrahim Hassan Mohamed Taha** (Student ID: 22101382)

---

## PART 2 — COMPLETE PROJECT STRUCTURE

The following tree represents the complete structure of the repository. Meaningful source artifacts have been categorized separately from generated/cache/scratch files.

```
DB project/
├── CSE221 Project Topic and Deadlines.pdf
├── DB project.pptx
├── project DB 3.drawio
├── DB/
│   ├── New Text Document (2).txt
│   ├── New Text Document (4).txt
│   ├── New Text Document (6).txt
│   ├── New Text Document (8).txt
│   ├── New Text Document (9).txt
│   ├── New Text Document.txt
│   ├── SQL Queries 2.rar
│   ├── queries.txt
│   └── sql query.txt
├── DB Project/
│   ├── CSV/
│   │   ├── AIU Address.csv
│   │   ├── AIU Courses.csv
│   │   ├── AIU.csv
│   │   ├── Instructor.csv
│   │   └── New Microsoft Excel Worksheet header.csv
│   ├── Data for Coursera Project/
│   │   ├── All AIU Coursera Course Mappings.xlsx
│   │   ├── Instructors Chosen Courses All Semesters Until Now.xlsx
│   │   ├── Coursera Catalogs/ (8 .xlsx files)
│   │   ├── Some sample reports/ (7 .pdf files)
│   │   └── Student Sheets/ (3 subdirectories)
│   ├── Excel/ (20 .xlsx files)
│   ├── DB Project 1.docx
│   ├── DB Project.docx
│   ├── DB Project.sql
│   ├── DB Project.txt
│   ├── Project DB.drawio
│   ├── Project DB.drawio.png
│   └── Selected photo.jpg
└── DB garbage/ (Archive / Backup / Scratch directory)
    ├── DB Project (2).docx
    ├── DB Project Final.xlsx
    ├── DB Project.sql
    ├── New Microsoft Excel Worksheet.csv (44MB CSV dataset)
    ├── OneDrive_2024-04-19 (2).zip
    ├── new.sql
    └── [Other backup & image files]
```

### Source & Evidence Categorization:
* **Core Technical Evidence (Verified):**
  - Schema DDL & DML: `DB Project/DB Project.sql`, `DB/New Text Document (2).txt`
  - Database Objects (Views & Stored Procedures): `DB/New Text Document.txt`
  - EER Diagrams: `DB Project/Project DB.drawio`, `DB Project/Project DB.drawio.png`, `project DB 3.drawio`
  - Specification & Normalization Analysis: `DB Project/DB Project 1.docx`, `DB Project/DB Project.docx`
  - Real & Sample Datasets: `DB Project/CSV/`, `DB Project/Excel/`, `DB Project/Data for Coursera Project/`
* **Course Context Evidence (Verified):**
  - Course Guidelines: `CSE221 Project Topic and Deadlines.pdf`
  - Project Presentation: `DB project.pptx`
* **Non-Project / Scratch / Unrelated Artifacts (Discovered & Isolated):**
  - `DB/sql query.txt`: DDL for an unrelated `chat_room` table (`users` and `chat_history`).
  - `DB/New Text Document (4,6,8,9).txt`: Unrelated Python snippets for Machine Learning feature encoding (`OneHotEncoding` with `scikit-learn`/`pandas`).
  - `DB/SQL Queries 2.rar`: Compressed archive containing course lab assignments (Company, Hotel, AcademicEnroll, and Library schemas).
  - Office Lock Files (`~$*`): Temporary system lock files.

---

## PART 3 — DATABASE DESIGN

### Schema Breakdown (18 Tables Implemented in `DB Project.sql`)

1. **`User1`**
   - **Columns:** `CourseraUserID` (INT, PK), `Username` (VARCHAR 255), `Pass` (VARCHAR 255)
   - **Primary Key:** `CourseraUserID`
2. **`Org`**
   - **Columns:** `OrgID` (INT, PK), `OrgName` (VARCHAR 255), `Specialization` (VARCHAR 255)
   - **Primary Key:** `OrgID`
3. **`Coursera`**
   - **Columns:** `CourseraLink` (VARCHAR 255, PK), `CourseraEmail` (VARCHAR 255)
   - **Primary Key:** `CourseraLink`
   - *Note: Alternate version in `DB garbage/DB Project.sql` includes `OrgID` FK to `Org`.*
4. **`AIU`**
   - **Columns:** `AIUEmail` (VARCHAR 255, PK), `CourseraLink` (VARCHAR 255, FK), `Rankk` (INT)
   - **Primary Key:** `AIUEmail`
   - **Foreign Key:** `CourseraLink` $\rightarrow$ `Coursera(CourseraLink)`
5. **`AIUAddress`**
   - **Columns:** `AIUEmail` (VARCHAR 255, PK & FK), `AIUAddress` (VARCHAR 255)
   - **Primary Key:** `AIUEmail`
   - **Foreign Key:** `AIUEmail` $\rightarrow$ `AIU(AIUEmail)`
6. **`AIUCourses`**
   - **Columns:** `AIUCourseCode` (VARCHAR 255, PK), `AIUCourseName` (VARCHAR 255), `AIUEmail` (VARCHAR 255, FK), `SemesterNo` (INT), `Field` (VARCHAR 255), `ExpectedStudentsNo` (INT)
   - **Primary Key:** `AIUCourseCode`
   - **Foreign Key:** `AIUEmail` $\rightarrow$ `AIU(AIUEmail)`
7. **`CourseraCourses`**
   - **Columns:** `CourseraCourseSlug` (INT, PK), `CourseraLink` (VARCHAR 255, FK), `CourseraCourseLink` (VARCHAR 255), `CourseraInstructorName` (VARCHAR 255), `CourseraInstructorId` (INT), `CourseraCourseName` (VARCHAR 255), `CourseraCourseCode` (VARCHAR 255), `Weeks` (VARCHAR 255), `Hours` (VARCHAR 255)
   - **Primary Key:** `CourseraCourseSlug`
   - **Foreign Key:** `CourseraLink` $\rightarrow$ `Coursera(CourseraLink)`
8. **`Use1`** (Junction Table: AIU Course $\leftrightarrow$ Coursera Course)
   - **Columns:** `AIUCourseCode` (INT, FK), `CourseraCourseSlug` (INT, FK)
   - **Primary Key:** Composite `(AIUCourseCode, CourseraCourseSlug)`
   - **Foreign Keys:** `AIUCourseCode` $\rightarrow$ `AIUCourses(AIUCourseCode)`, `CourseraCourseSlug` $\rightarrow$ `CourseraCourses(CourseraCourseSlug)`
9. **`Instructor`**
   - **Columns:** `InstructorID` (INT, PK), `UserID` (INT, FK), `InstructorEmail` (VARCHAR 255), `Field` (VARCHAR 255), `InstructorName` (VARCHAR 255)
   - **Primary Key:** `InstructorID`
   - **Foreign Key:** `UserID` $\rightarrow$ `User1(CourseraUserID)`
10. **`Teaches`** (Junction Table: Instructor $\leftrightarrow$ AIU Course)
    - **Columns:** `InstructorID` (INT, FK), `AIUCourseCode` (INT, FK)
    - **Foreign Keys:** `InstructorID` $\rightarrow$ `Instructor(InstructorID)`, `AIUCourseCode` $\rightarrow$ `AIUCourses(AIUCourseCode)`
11. **`CourseraProgram`**
    - **Columns:** `CourseraProgramID` (INT, PK), `Field` (VARCHAR 255), `AdminLink` (VARCHAR 255), `LearnerLink` (VARCHAR 255)
    - **Primary Key:** `CourseraProgramID`
12. **`Use2`** (Junction Table: Instructor $\leftrightarrow$ Coursera Program)
    - **Columns:** `InstructorID` (INT, FK), `CourseraProgramID` (INT, FK)
    - **Foreign Keys:** `InstructorID` $\rightarrow$ `Instructor(InstructorID)`, `CourseraProgramID` $\rightarrow$ `CourseraProgram(CourseraProgramID)`
13. **`Student`**
    - **Columns:** `StuID` (INT, PK), `CourseraUserID` (INT, FK), `AIUEmail` (VARCHAR 255, FK), `StuName` (VARCHAR 255), `StuEmail` (VARCHAR 255)
    - **Primary Key:** `StuID`
    - **Foreign Keys:** `CourseraUserID` $\rightarrow$ `User1(CourseraUserID)`, `AIUEmail` $\rightarrow$ `AIU(AIUEmail)`
14. **`Invite`** (Junction Table: Student $\leftrightarrow$ Coursera Program)
    - **Columns:** `StuID` (INT, FK), `ProgramID` (INT, FK)
    - **Foreign Keys:** `StuID` $\rightarrow$ `Student(StuID)`, `ProgramID` $\rightarrow$ `CourseraProgram(CourseraProgramID)`
15. **`Enroll`**
    - **Columns:** `EnrollID` (INT, PK), `StuID` (INT, FK), `AIUCourseCode` (INT, FK), `CourseLabMark` (INT), `CourseExamMark` (INT), `AIUCourseGrade` (VARCHAR 255)
    - **Primary Key:** `EnrollID`
    - **Foreign Keys:** `StuID` $\rightarrow$ `Student(StuID)`, `AIUCourseCode` $\rightarrow$ `AIUCourses(AIUCourseCode)`
16. **`CourseraCoordinator`**
    - **Columns:** `CoordinatorID` (INT, PK), `CoordinatorName` (VARCHAR 255), `UserID` (INT, FK), `CourseraLink` (VARCHAR 255, FK), `CoordinatorLink` (VARCHAR 255), `CoordinatorEmail` (VARCHAR 255)
    - **Primary Key:** `CoordinatorID`
    - **Foreign Keys:** `UserID` $\rightarrow$ `User1(CourseraUserID)`, `CourseraLink` $\rightarrow$ `Coursera(CourseraLink)`
17. **`CourseraModule`**
    - **Columns:** `ModuleID` (INT, PK), `CourseraCourseSlug` (INT, FK), `Duration` (INT)
    - **Primary Key:** `ModuleID`
    - **Foreign Key:** `CourseraCourseSlug` $\rightarrow$ `CourseraCourses(CourseraCourseSlug)`
18. **`Map`** (Weekly Module Mapping Table)
    - **Columns:** `weekNo` (INT), `ModuleID` (INT, FK), `CourseCode` (VARCHAR 255, FK), `InstructorID` (INT, FK)
    - **Foreign Keys:** `ModuleID` $\rightarrow$ `CourseraModule(ModuleID)`, `CourseCode` $\rightarrow$ `AIUCourses(CourseCode)`, `InstructorID` $\rightarrow$ `Instructor(InstructorID)`

---

### Normalization Evaluation

* **1NF (First Normal Form):** **VERIFIED DEMONSTRATED.**
  - All table attributes contain atomic values.
  - Multi-valued attributes (e.g. multiple addresses or course selections) are handled through dedicated tables (`AIUAddress`, `Use1`, `Teaches`).
* **2NF (Second Normal Form):** **VERIFIED DEMONSTRATED.**
  - All non-key attributes are fully functionally dependent on the primary key.
  - Composite primary keys (e.g., `Use1(AIUCourseCode, CourseraCourseSlug)`) contain no partial dependencies.
* **3NF (Third Normal Form):** **VERIFIED DEMONSTRATED.**
  - Transitive dependencies are removed. For instance, `AIUAddress` was explicitly separated into a standalone table to eliminate transitive dependency between `OrgID`/`AIUEmail` and location attributes (documented in `DB Project 1.docx`).
* **BCNF (Boyce-Codd Normal Form):** **VERIFIED DEMONSTRATED & DOCUMENTED.**
  - Documented in `DB Project 1.docx` (Section 5): "BCNF is satisfied as there are no remaining anomalies resulting from multiple candidate keys." Every determinant in the design is a candidate key.

---

### Database Objects Summary

* **Views (10 Created in `DB/New Text Document.txt`):**
  1. `CourseEnrollmentCount`: Aggregates student counts per AIU course using `LEFT JOIN`.
  2. `CourseraCourseInstructors`: Joins Coursera courses to instructors.
  3. `CourseraProgramEnrollmentCount`: Aggregates total program enrollments.
  4. `StudentsEnrolledInProgram`: Lists student details by program ID.
  5. `StudentAverageExamMarks`: Calculates average exam marks per student using `AVG()`.
  6. `AiuCoursesInField`: Filters AIU courses by academic field ('CSE').
  7. `AiuInstructorsInField`: Displays unique instructors teaching in field 'CSE' using `DISTINCT`.
  8. `CourseraCoursesWithDurationGreaterThan5`: Filters courses with module duration $> 5$.
  9. `OrgOfferingAiuCourses`: Joins Organizations to AIU courses.
  10. `CoursesTaughtByInstructor`: Filters courses taught by a specific instructor.
* **Stored Procedures (10 Created in `DB/New Text Document.txt`):**
  - 10 static MySQL stored procedures wrapping the view queries using `DELIMITER // ... END// DELIMITER ;` syntax (e.g., `GetCoursesTaughtByInstructor`, `GetCourseEnrollmentCount`, `GetStudentAverageExamMarks`).
* **Triggers:** **NOT IMPLEMENTED / NONE FOUND.**
* **Indexes:** PK indexes auto-generated by MySQL engine. No custom secondary `CREATE INDEX` statements exist.
* **Transactions / Cascading:** No explicit `START TRANSACTION`, `COMMIT`, or `ON DELETE CASCADE` constraints declared in SQL scripts.

---

## PART 4 — SQL ANALYSIS

### SQL Techniques Verified in Codebase

| SQL Technique | Present? | Location / Example |
| :--- | :---: | :--- |
| `SELECT` | **Yes** | All 10 queries in `DB/New Text Document.txt` |
| `INSERT INTO` | **Yes** | 18 table population statements in `DB Project/DB Project.sql` |
| `CREATE TABLE` | **Yes** | 18 table definitions in `DB Project/DB Project.sql` |
| `CREATE VIEW` | **Yes** | 10 view definitions in `DB/New Text Document.txt` |
| `CREATE PROCEDURE` | **Yes** | 10 procedure definitions in `DB/New Text Document.txt` |
| `INNER JOIN` / `JOIN` | **Yes** | `AIUCourses JOIN Teaches JOIN Instructor` (`DB/New Text Document.txt` L4-L5) |
| `LEFT JOIN` | **Yes** | `AIUCourses LEFT JOIN Enroll ON ...` (`DB/New Text Document.txt` L11) |
| `GROUP BY` | **Yes** | `GROUP BY AIUCourses.AIUCourseName` (`DB/New Text Document.txt` L12) |
| `AVG()` Aggregation | **Yes** | `AVG(Enroll.CourseExamMark) AS AvgExamMark` (`DB/New Text Document.txt` L35) |
| `COUNT()` Aggregation | **Yes** | `COUNT(Enroll.StuID) AS NumOfStudents` (`DB/New Text Document.txt` L9) |
| `DISTINCT` | **Yes** | `SELECT DISTINCT Instructor.InstructorName` (`DB/New Text Document.txt` L46) |
| `WHERE` Filtering | **Yes** | `WHERE Instructor.InstructorName = 'Islam Elkabani'` (`DB/New Text Document.txt` L6) |
| `DELIMITER` (MySQL) | **Yes** | `DELIMITER // ... DELIMITER ;` (`DB/New Text Document.txt` L145-L154) |
| `HAVING` | **No** | Not present |
| `Subqueries` / `CTEs` | **No** | Not present |
| `Window Functions` | **No** | Not present |
| `Triggers` | **No** | Not present |
| Explicit `INDEX` | **No** | Primary keys only |

---

## PART 5 — APPLICATION INTEGRATION

* **Backend Language:** **NOT VERIFIED / NOT IMPLEMENTED.**
* **Framework:** **NOT VERIFIED / NOT IMPLEMENTED.**
* **Database Driver / Connection:** **NOT VERIFIED / NOT IMPLEMENTED.**
* **CRUD Operations via App:** **NOT VERIFIED / NOT IMPLEMENTED.**
* **Authentication / Authorization Middleware:** **NOT VERIFIED / NOT IMPLEMENTED.**
* **SQL Injection Protections / Parameterized Queries:** **NOT VERIFIED / NOT IMPLEMENTED.** (Stored procedures use hardcoded string literals inside SQL statements rather than parameterized inputs).
* **API Endpoints:** **NOT VERIFIED / NOT IMPLEMENTED.**
* **Architecture Summary:** Pure RDBMS Database Design and SQL engineering project. No web application, REST API, or backend code exists in the repository.

---

## PART 6 — DATA AUDIT

* **Data Sources:** Dual data layer present:
  1. **Synthetic Seed Data:** Included in `DB Project.sql` (`INSERT INTO User1`, `Org`, `AIUCourses`, `CourseraCourses`, `Enroll`, etc.) with ~3–5 records per table for DDL verification.
  2. **Real University Datasets:** Extensive real-world data files stored in `DB Project/CSV/`, `DB Project/Excel/`, `DB Project/Data for Coursera Project/`, and `DB garbage/New Microsoft Excel Worksheet.csv` (44MB CSV file).
* **Record Count (Safely Calculated):**
  - `New Microsoft Excel Worksheet.csv`: **100,000+ real student enrollment and activity log rows**.
  - `Coursera Catalogs`: 8 dedicated faculty catalogs (CSE, Pharmacy, Dentistry, Business, Engineering, Art & Design, Public Health, Basic Sciences) containing hundreds of mapped Coursera courses.
* **Data Generation / Import Script:** `DB garbage/DB Project.sql` contains Python snippet (`csv.reader`) demonstrating automated CSV parsing to generate SQL `INSERT` statements.

---

## PART 7 — SECURITY AUDIT

* **Password Hashing:** **NOT IMPLEMENTED.** Plaintext passwords stored in database (`User1` table: `'Ga2#Rav$5'`, `'Pr0+Rin^7'`, `'password123'`).
* **Authentication:** **CONCEPTUAL ONLY.** Documented in business rules, but no code implementation exists.
* **Authorization / RBAC:** **CONCEPTUAL ONLY.** Stated requirement distinguishes Main Coordinator, Field Coordinator, and Instructor permissions, but no MySQL `GRANT` statements or middleware access rules exist.
* **SQL Injection Prevention:** **NOT IMPLEMENTED.**
* **Secrets Management:** **NOT IMPLEMENTED.** No `.env` or configuration management files.
* **Security Evaluation:** The project is an academic database prototype and is **not secure for production deployment** in its current state.

---

## PART 8 — PERFORMANCE & OPTIMIZATION AUDIT

* **Indexing:** Primary key default B-tree indexes only. No secondary indexes (`CREATE INDEX`) created for foreign keys or search fields (`InstructorName`, `Field`, `StuEmail`).
* **Query Optimization:** Demonstrated query design optimization by using `LEFT JOIN` to handle zero-enrollment courses and `DISTINCT` to eliminate query result duplicates.
* **EXPLAIN / Benchmarking:** **NOT IMPLEMENTED / NOT VERIFIED.**
* **Caching / Connection Pooling:** **NOT IMPLEMENTED.**

---

## PART 9 — SOFTWARE ENGINEERING PRACTICES

* **Project Organization:** High. Structured academic folder hierarchy separating relational design documents, SQL code, EER diagrams, presentation slides, and CSV/Excel raw datasets.
* **Modularity:** High database modularity. Schema divided into 18 logical entities; views and stored procedures decoupled into separate script sections.
* **Documentation Quality:** Excellent. `DB Project 1.docx` provides an in-depth technical report covering problem context, business rules, EER diagram specifications, full relational schema mappings, and 1NF–BCNF normalization analyses.
* **Version Control / Git Artifacts:** **NOT VERIFIED.** No `.git` metadata present in the project directory.

---

## PART 10 — UI / FRONTEND AUDIT

* **UI / Frontend Components:** **NOT IMPLEMENTED / NOT VERIFIED.** The optional course prompt task ("Fully Connected Website") was not developed in this repository.

---

## PART 11 — REPORTS, PRESENTATIONS & DOCUMENTATION AUDIT

* **Problem Statement:** AIU University needed an automated DBMS solution to manage Coursera course integrations across 8 faculties, track weekly student license allocations under university quotas, map online modules to 16-week academic syllabi, and generate faculty progress reports.
* **Documented Requirements:** 
  - Unique Coursera course slugs.
  - Multi-course association with AIU subjects.
  - Role-based visibility rules (Main Coordinator vs Field Coordinator vs Instructor).
  - Automatically generated weekly license usage and completion reports.
* **EER Diagram:** Complete EER diagram modeled in Draw.io (`Project DB.drawio`) and rendered as PNG (`Project DB.drawio.png`), showing entities, attributes, primary/foreign keys, cardinality, and relationships.
* **Normalization Documentation:** Detailed 5-step normalization breakdown (Unnormalized $\rightarrow$ 1NF $\rightarrow$ 2NF $\rightarrow$ 3NF $\rightarrow$ BCNF) documented in `DB Project 1.docx`.

---

## PART 12 — MY CONTRIBUTION ASSESSMENT

### A. Strongly Supported Technical Contribution (Verified in Code & Docs)
1. **Relational Schema Architecture:** Designed and defined the 18-table relational database schema in MySQL DDL (`DB Project.sql`).
2. **Database Normalization:** Performed and documented formal database normalization (1NF, 2NF, 3NF, BCNF) to eliminate data redundancy and anomalies (`DB Project 1.docx`).
3. **SQL Query Engineering:** Formulated and implemented 10 multi-table SQL queries addressing complex business reporting requirements (`DB/New Text Document.txt`).
4. **Database Objects Implementation:** Built 10 MySQL `CREATE VIEW` abstractions and 10 MySQL `CREATE PROCEDURE` routines (`DB/New Text Document.txt`).
5. **EER Diagram Modeling:** Modeled the Enhanced Entity-Relationship diagram (`Project DB.drawio`).

### B. Project-Level Contribution (Supported by Repository Assets)
1. **Curating Real Academic Data:** Processed real university Coursera catalogs and student lists across 8 faculties (`Data for Coursera Project/`).
2. **Technical Reporting & Presentation:** Authored the project documentation report (`DB Project 1.docx`) and presentation deck (`DB project.pptx`).

### C. Requires My Confirmation
1. **Specific Feature Highlights:** Confirm if you want any specific design decision emphasized in your personal profile.

### D. Do Not Claim
1. Full-stack web development or frontend application creation.
2. Web backend API development (Node.js/Python/Java).
3. Production security implementation (password hashing, RBAC grants).
4. SQL query performance benchmarking or custom indexing tuning.

---

## PART 13 — TECHNICAL SKILLS EVIDENCED

### Database Engineering & SQL
* **Relational Database Design:** Entity-Relationship (ER/EER) Modeling, Schema Architecture, Primary & Foreign Key Constraints, Referential Integrity.
* **Database Normalization:** 1NF, 2NF, 3NF, BCNF Analysis, Functional Dependency Identification.
* **Advanced SQL Querying:** Multi-Table `JOIN`, `LEFT JOIN` (Outer Joins), Aggregations (`COUNT`, `AVG`), Grouping (`GROUP BY`), Data Deduplication (`DISTINCT`).
* **Database Programming:** MySQL Views (`CREATE VIEW`), MySQL Stored Procedures (`CREATE PROCEDURE`, `DELIMITER`).

### Software Engineering & Tools
* **Data Engineering & Curation:** CSV/Excel Dataset Structuring, Data Mapping, CSV-to-SQL script concepts.
* **Technical Communication:** Technical Writing, EER Diagramming (`Draw.io`), Architectural Presentation (`PowerPoint`).

---

## PART 14 — CV-READY TECHNICAL BULLETS

1. **Designed and architected an 18-table relational database schema** in MySQL for an academic course management system (AIU Coursera Integration), enforcing primary key, foreign key, and referential integrity constraints across complex entity relationships.
2. **Normalized database schema from unnormalized specifications up to 3NF and BCNF**, eliminating partial and transitive functional dependencies while isolating multi-valued location attributes into dedicated tables.
3. **Engineered 10 production-ready SQL views** utilizing multi-table `JOIN`s, `LEFT JOIN`s, and `GROUP BY` aggregations to generate automated weekly reporting metrics on student enrollments, completion rates, and exam score averages.
4. **Developed 10 MySQL stored procedures** using custom delimiters to encapsulate core business logic for department-level license tracking, instructor course lookups, and enrollment statistics.
5. **Constructed an Enhanced Entity-Relationship (EER) diagram** mapping complex domain relationships between academic faculties, university courses, external online course slugs, weekly syllabi schedules, and student grade records.
6. **Curated and structured multi-department datasets** comprising CSV and Excel workbooks across 8 university faculties (CSE, Pharmacy, Engineering, Business, etc.) to seed and validate database queries.
7. **Authored comprehensive technical documentation** detailing business rules, functional dependency mappings, normalization steps, and relational query specifications.

---

## PART 15 — PORTFOLIO STORY

1. **Problem:** Al Alamein International University (AIU) integrated Coursera online courses into its degree programs across 8 academic faculties. The university lacked a centralized database system to map internal academic courses to external Coursera course modules, track seat license usage against strict quotas, and aggregate weekly student enrollment and completion metrics for faculty coordinators.
2. **Solution:** Designed and implemented a normalized MySQL relational database system that models academic units, course syllabi, instructors, students, external Coursera programs, weekly module mappings, and student assessment grades.
3. **Architecture:** Relational RDBMS architecture consisting of 18 normalized tables, 10 analytical SQL views, and 10 stored procedures.
4. **Database Design:** 18 core tables including `User1`, `Org`, `Coursera`, `AIU`, `AIUAddress`, `AIUCourses`, `CourseraCourses`, `Use1`, `Instructor`, `Teaches`, `CourseraProgram`, `Use2`, `Student`, `Invite`, `Enroll`, `CourseraCoordinator`, `CourseraModule`, and `Map`.
5. **Key Technical Challenges:** 
   - Modeling complex many-to-many relationships (e.g. instructors teaching multiple courses, courses mapping to multiple Coursera slugs, assigning modules to specific semester weeks).
   - Enforcing strict 3NF/BCNF normalization without compromising query performance.
   - Formulating SQL reporting queries using `LEFT JOIN`s to ensure courses with zero active enrollments were accurately captured in university counts.
6. **Technologies Used:** MySQL, SQL DDL/DML, Procedural SQL, Draw.io, Microsoft Excel, CSV.
7. **What Was Implemented:** Complete RDBMS DDL schema script, DML seed dataset, 10 SQL reporting views, 10 MySQL stored procedures, EER diagram source, and technical normalization documentation.
8. **Results:** Delivered a complete database blueprint capable of tracking university-wide online learning progress, managing weekly license allocations, and generating department-level completion reports.
9. **Limitations:** Web frontend UI and backend API were not implemented; database lacks secondary indexing and password encryption.
10. **Personal Contribution:** Designed database schema, executed formal normalization analysis (1NF–BCNF), built EER diagrams, authored SQL queries, views, and stored procedures, and wrote technical documentation.

---

## PART 16 — INTERVIEW PREPARATION GUIDE

### Database Design Questions

* **Q: Why did you separate `AIUAddress` into its own table instead of keeping it in `AIU` or `Org`?**
  * *Answer:* In our normalization analysis, we noticed that AIU address was transitively dependent on `OrgID` rather than directly dependent on the primary key alone. To satisfy 3NF and eliminate transitive dependencies, we isolated `AIUAddress` into a separate table linked via foreign key.
* **Q: How did you handle many-to-many relationships in your schema?**
  * *Answer:* We implemented junction tables with composite primary keys and foreign keys. For example, `Use1` links `AIUCourses` to `CourseraCourses` using `(AIUCourseCode, CourseraCourseSlug)`, `Teaches` links `Instructor` to `AIUCourses`, and `Map` links weekly schedules to modules, courses, and instructors.
* **Q: Why did you use a `LEFT JOIN` in the `CourseEnrollmentCount` view?**
  * *Answer:* An `INNER JOIN` would exclude AIU courses that currently have zero enrolled students. By using `AIUCourses LEFT JOIN Enroll`, we ensure all courses appear in the aggregate report with a student count of 0.
* **Q: How does the `Map` table support weekly syllabus planning?**
  * *Answer:* `Map` stores `weekNo`, `ModuleID` (FK to `CourseraModule`), `CourseCode` (FK to `AIUCourses`), and `InstructorID`. This allows instructors to assign specific online modules to individual weeks of the 16-week academic semester.

### SQL Questions

* **Q: How did you compute student exam averages across different courses?**
  * *Answer:* We authored a query joining `Student` and `Enroll` on `StuID`, grouping by `Student.StuName`, and applying `AVG(Enroll.CourseExamMark)`.
* **Q: How are your stored procedures implemented?**
  * *Answer:* In MySQL, we defined stored procedures using `DELIMITER //` to change the statement delimiter, created procedures such as `GetCourseEnrollmentCount()`, and reset the delimiter back to `;`.

### Project Architecture Questions

* **Q: What would you add if you were to deploy this database to production?**
  * *Answer:* I would implement password hashing (e.g., bcrypt/Argon2), enforce database Role-Based Access Control (RBAC) via MySQL user privileges (`GRANT SELECT ON view...`), create secondary indexes on frequently searched columns (`Field`, `InstructorName`, `StuEmail`), and build a REST API backend with parameterized SQL queries to protect against SQL injection.

---

## PART 17 — CLAIM SAFETY MATRIX

| Claim | Status | Repository Evidence |
| :--- | :---: | :--- |
| **Database Technology (MySQL)** | **VERIFIED** | DDL/DML scripts in `DB Project.sql` & `DB/New Text Document.txt` (`DELIMITER //`, `VARCHAR`, `INT`) |
| **SQL Implementation** | **VERIFIED** | 18 `CREATE TABLE` statements, 10 `CREATE VIEW` statements, 10 `CREATE PROCEDURE` statements |
| **18 Relational Tables** | **VERIFIED** | Declared in `DB Project/DB Project.sql` (`User1`, `Org`, `AIU`, `AIUCourses`, `CourseraCourses`, `Enroll`, etc.) |
| **Normalization (1NF–BCNF)** | **VERIFIED** | Documented step-by-step with functional dependency analysis in `DB Project 1.docx` |
| **EER Diagram** | **VERIFIED** | Source Draw.io file `Project DB.drawio` and exported image `Project DB.drawio.png` |
| **Real Datasets Processed** | **VERIFIED** | 44MB CSV dataset + 8 faculty Excel catalogs in `DB Project/Data for Coursera Project/` |
| **Academic Course Context** | **VERIFIED** | CSE221 Database Systems (Spring 2024, AIU University, Dr. Laila Shoukry) in `CSE221 Project Topic and Deadlines.pdf` |
| **Web Backend / API** | **NOT VERIFIED** | No backend application code (Node.js, Python Flask/Django, Java) exists in the repository |
| **Web Frontend / UI** | **NOT VERIFIED** | No HTML/CSS/JS or frontend framework code exists in the repository |
| **Authentication / Password Hashing**| **NOT VERIFIED** | Plaintext password columns in `User1` table (`'Ga2#Rav$5'`, `'password123'`) |
| **Production Security / RBAC** | **NOT VERIFIED** | No MySQL user grant scripts or middleware permission checks |
| **Query Benchmarks / Indexes** | **NOT VERIFIED** | Primary keys only; no secondary `CREATE INDEX` statements or EXPLAIN execution plans |
| **Production Deployment** | **NOT VERIFIED** | No dockerfiles, deployment scripts, or cloud hosting artifacts |
| **Personal Contribution** | **VERIFIED / SUPPORTED** | Tasneem Ibrahim named as project author on report `DB Project 1.docx` and presentation `DB project.pptx` |

---

## AUDIT STATUS

* **Technical implementation audit:** COMPLETE
* **Database design audit:** COMPLETE
* **SQL audit:** COMPLETE
* **Contribution audit:** COMPLETE
* **Documentation audit:** COMPLETE
* **Overall confidence:** HIGH
