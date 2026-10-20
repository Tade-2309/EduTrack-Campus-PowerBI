# EduTrack Campus Analytics Dashboard — Power BI

**Project owner:** Samson Oguntade  
**Programme:** ITF–NECA TSDP  
**Tool:** Microsoft Power BI Desktop  
**Project type:** Academic end-of-module data analytics project  
**Status:** Dashboard pages and charts reported complete for six selected questions; insight validation and final documentation are in progress.

## Overview

EduTrack is a college analytics project built around a registrar's everyday questions: student numbers, staffing, courses, department-level performance, enrolment patterns, and student GPA categories. The aim is to turn a workbook of related tables into a clear, interactive report that can support informed discussions.

This repository documents the project brief, the workflow, the article describing the build, decisions made during development, DAX examples, and the next steps. It distinguishes reported dashboard findings from items that still need checking in the final Power BI model.

## Dataset

The supplied Excel workbook contains five data tables. The README sheet in the workbook is descriptive and should not be loaded as a data table.

| Table | Rows in project brief | Purpose |
|---|---:|---|
| `departments` | 30 | Departments, buildings, budgets |
| `instructors` | 60 | Instructors, departments, hire dates, salaries |
| `students` | 100 | Students, departments, enrollment year, GPA, gender |
| `courses` | 48 | Courses, departments, assigned instructors, credits |
| `enrollments` | 100 | Student-course enrolment records, semester, grade point, date |

Do not upload private, restricted, or instructor-provided source data to a public repository unless you have permission. Use the documentation and screenshots here to explain the project; add only files you are allowed to share.

## Workflow

1. Import the Excel workbook with **Get Data → Excel workbook**.
2. Choose **Transform Data** and inspect the tables in Power Query.
3. Review column values, profiling, and data types; clean only where needed.
4. Use **Close & Apply** to load the prepared tables.
5. Build and verify relationships in Model view.
6. Create and validate DAX measures/calculated columns.
7. Build report pages for selected business questions.
8. Write a plain-language insight for each page and explain what action it may support.
9. Export the finished report to PDF and submit the required Power BI file and write-up through the course portal.

## Selected business questions and current progress

The latest project status shared in the working conversation lists **Q1, Q2, Q3, Q4, Q8 and Q9** as the six questions worked on so far. Their report pages and charts have been reported as created. The project brief requires seven of the ten questions, so **Q5 (Fall 2024 enrolments)** was recommended as a practical next question.

| Question | Focus | Current note |
|---|---|---|
| Q1 | Institutional totals, average GPA, largest intake year | Worked on |
| Q2 | Students by department and gender; top five departments | Worked on |
| Q3 | Average GPA by department | Worked on |
| Q4 | Departments with more than four instructors and average salaries | Worked on |
| Q8 | Courses with average grade point above 3.0 | Worked on |
| Q9 | GPA bands and At Risk students | Worked on |
| Q5 | Fall 2024 enrolments and students/courses enrolled | Recommended next |

An earlier article draft documents **Q1, Q2, Q3, Q7, Q8 and Q9**. That article version and the latest working status are both preserved in this repository; they should not be silently treated as the same selection.

## Reported findings from the uploaded article

The article draft reports the following figures from the dashboard. They are preserved as **article-reported results**, not independently revalidated values:

- 100 students, 60 instructors, 48 courses, 100 enrolment records, and average GPA of 3.08.
- 2024 was reported as the largest intake year, with 50 students.
- Computer Science and Economics were reported as the largest departments, with 14 students each.
- Mathematics was reported as the highest department average GPA (3.29); Statistics was lowest (2.40), but with only one student.
- For Q7, the article reports an average of 3.03 enrolments per course and nine courses above that average.
- For Q8, the article reports 22 courses with average grade point above 3.0 and an overall course average of 3.06.
- For Q9, the article reports 21 Excellent, 36 Good, 40 Fair, and 3 At Risk students.

**Quality note:** The article itself describes a measure/chart disagreement for Q7 and a mismatch between the intake chart and year slicer. Those items need to be resolved and the relevant measures rechecked before the figures are presented as final verified results. Student cumulative GPA and course enrolment grade points are different fields and must not be conflated.

## Design direction

- Power BI Twilight theme
- Semibold chart titles
- Visual borders turned off to reduce clutter
- Appropriate visuals for each question
- Clear plain-language page insights
- Presentation style should be professional but not overly technical

## Documentation

- [Project journey](docs/EDUTRACK_PROJECT_JOURNEY.md)
- [Article and reported findings](docs/ARTICLE_AND_FINDINGS.md)
- [Conversation and decisions log](docs/PROJECT_CONVERSATION_NOTES.md)
- [DAX examples and validation notes](docs/DAX_DOCUMENTATION.md)
- [Data and screenshot guidance](data/README.md) and [screenshots guidance](screenshots/README.md)
- [Presentation guidance](presentation/README.md)

## Deliverables

The course brief calls for:
- A Power BI `.pbix` file named `lastname_firstname_edutrack.pbix`
- A PDF export containing every report page
- A short write-up for each of the seven questions, including a visual screenshot and one or two sentences explaining the insight

## Next steps

1. Add and complete Q5 or another seventh question.
2. Verify the data model and any inactive relationships.
3. Reconcile the article's Q7 measure/chart discrepancy and intake-year field mismatch.
4. Validate all DAX results against the data.
5. Write concise, evidence-based insights for each report page.
6. Add approved screenshots and final deliverables when ready.
7. Revise the presentation using the Canva template when supplied.

---
*This repository is a living project record. Update the status as the model, visuals, and results are verified.*
