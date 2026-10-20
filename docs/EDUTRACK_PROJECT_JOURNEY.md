# EduTrack Power BI Project Journey

**Project owner:** Samson Oguntade  
**Programme:** ITF–NECA TSDP  
**Tool:** Microsoft Power BI Desktop

## 1. Project purpose

The EduTrack Campus Analytics Dashboard is an end-of-module project in which I take the role of a data analyst supporting a college registrar. The task is to transform related Excel tables into an interactive Power BI report that can help management understand enrolment, student performance, staffing, and course activity.

The official brief asks for answers to seven of ten business questions, presented in a single report. Required deliverables are a Power BI file, a PDF export, and a short written explanation with a screenshot for each selected question.

## 2. Understanding the source data

The workbook contains five main tables:

| Table | Rows in the brief | Main content |
|---|---:|---|
| departments | 30 | Department names, buildings, budgets |
| instructors | 60 | Instructor IDs, departments, hire dates, salaries |
| students | 100 | Student IDs, departments, enrollment years, cumulative GPA, gender |
| courses | 48 | Course IDs, departments, instructors, credits |
| enrollments | 100 | Student-course records, semester, grade point, enrollment date |

The workbook's README sheet is only descriptive and should not be loaded as a data table.

## 3. Importing the workbook

I used **Get Data → Excel workbook** in Power BI Desktop to locate the source workbook. I selected **Transform Data** so that I could inspect and prepare the data before building report visuals.

**Screenshot placeholder:** Get Data and the Transform Data choice.

## 4. Inspecting and preparing data in Power Query

In Power Query Editor, I inspected the available tables and columns, reviewed values and data types, and performed data preparation where necessary. The project notes record that each column was inspected and appropriate data types were assigned.

The project brief specifically warns that date columns such as `hire_date`, `date_of_birth`, and `enrollment_date` may import as text. They should be converted to Date where appropriate before date-based analysis.

After preparation, I used **Close & Apply** to load the tables into Power BI.

**Screenshot placeholders:**
- Power Query Editor showing the tables.
- Data profiling/column quality.
- Example of data type review or cleaning.
- Close & Apply or the loaded tables.

The final write-up should describe the exact cleaning operations that were actually performed. It should not claim that every possible data-quality issue was found or fixed unless that was verified.

## 5. Building the model

The source workbook has multiple related tables. The project brief lists the following one-to-many relationships:

| One side | Many side | Key |
|---|---|---|
| departments | instructors | `department_id` |
| departments | students | `department_id` |
| departments | courses | `department_id` |
| instructors | courses | `instructor_id` |
| students | enrollments | `student_id` |
| courses | enrollments | `course_id` |

I connected the tables in Model view and described the result in my notes as a star-like flow, rather than claiming the model was a perfect star schema.

My notes mention that the students–enrollments relationship and courses–instructors relationship appeared inactive in the model at one point. This should be checked against the current PBIX and the project brief. The brief specifies the relationships above; a dashed line indicates an inactive relationship, which does not filter by default. It may be intentional in some models, but its impact on measures must be understood before explaining or using it.

**Screenshot placeholders:**
- Overall Model view.
- Manage Relationships.
- Edit Relationship dialog.
- Example of the courses-to-departments relationship.
- Dashed/inactive relationship if it is still present.

## 6. Writing DAX and answering business questions

After preparing the data and building relationships, I began writing DAX measures and calculated columns for the selected questions. The formulas should be validated against the final model, particularly where a calculation depends on relationships or filter context.

An important distinction in this project is that `students[gpa]` represents student cumulative GPA, while `enrollments[grade_point]` represents grade points on enrolment records. These fields answer different questions and should not be treated as interchangeable.

## 7. Selecting report questions

The latest working status lists these six questions as worked on:

- **Q1:** Institutional totals, average student GPA, and largest intake year.
- **Q2:** Student counts by department and gender, including the top five departments.
- **Q3:** Average student GPA by department.
- **Q4:** Departments with more than four instructors and average salary comparisons.
- **Q8:** Courses with average enrolment grade point above 3.0.
- **Q9:** Distribution of students across GPA bands, including the At Risk category.

The six report pages and their charts have been reported as created. The next priority is to write the key insight for each page.

The course requires seven questions. **Q5**, which asks about Fall 2024 enrolments and the students enrolled in courses during that semester, was recommended as the next question. This is a recommendation, not a claim that Q5 has already been completed.

An earlier uploaded article covers Q1, Q2, Q3, Q7, Q8 and Q9. The difference between that article's question selection and the latest working status is preserved in the project notes.

## 8. Report design

The recorded design choices are:
- Twilight colour palette.
- Semibold titles.
- Visual borders turned off.
- Chart titles written to match the business question.
- A clean, consistent multi-page report.

The aim is to make the report useful to a non-technical college audience. Each page should state what the visual shows, the finding supported by the data, why it matters, and a possible action.

## 9. Findings and validation

The uploaded article records several numerical findings. They are reproduced in [Article and Reported Findings](ARTICLE_AND_FINDINGS.md), clearly labelled as figures reported by that draft.

The article also records two quality-control issues:
1. A Q7 measure counting courses above average enrolment disagreed with the chart, which showed nine courses.
2. The intake chart and year slicer displayed different year ranges, suggesting they may have been built from different fields.

These should be resolved before presenting the relevant figures as validated results. Small department populations also make GPA rankings sensitive to individual students; this caveat is especially important where a department has only one student.

## 10. Challenges and lessons

The project notes and article identify or suggest these areas to document:
- Understanding how multiple tables connect.
- Reviewing inactive relationships and their impact.
- Testing DAX results instead of assuming a formula is correct because it runs.
- Keeping year fields consistent between charts and slicers.
- Explaining results to non-technical readers.
- Avoiding overconfident conclusions from very small groups.

The final presentation should describe challenges that genuinely occurred and distinguish them from general limitations of the dataset.

## 11. Presentation direction

An earlier 20-slide presentation was created, but feedback was that it was too technical. The revised version should tell the story of the project in natural, presentation-friendly language: what I did, why I did it, what I noticed, and what I learned.

The presentation should include spaces for my own screenshots, selected questions, verified findings, challenges, limitations, and recommendations. I plan to provide a Canva template to guide the revision.

## 12. Current status and next actions

| Item | Status |
|---|---|
| Dataset import and Power Query work | Worked on |
| Data model and relationships | Created; verify current relationship settings |
| DAX | Written for selected questions; validate |
| Q1, Q2, Q3, Q4, Q8, Q9 | Worked on |
| Six report pages and charts | Reported complete |
| Key insights per page | Next priority |
| Seventh question | Q5 recommended |
| Article-reported discrepancies | Need verification |
| Screenshots and final deliverables | Organise/add |
| Presentation | Simplify and adapt to Canva template |

## 13. Screenshot checklist

- [ ] Get Data / Excel workbook selection.
- [ ] Transform Data selection.
- [ ] Power Query Editor.
- [ ] Data profiling and cleaning.
- [ ] Data type changes.
- [ ] Close & Apply.
- [ ] Overall Model view.
- [ ] Manage Relationships.
- [ ] Edit Relationship dialog.
- [ ] Courses-to-departments relationship.
- [ ] Inactive relationships, if present.
- [ ] Each report page.
- [ ] Final dashboard overview.
- [ ] Evidence supporting the key findings.

## 14. Submission checklist

- [ ] Final `.pbix` file using the required naming convention.
- [ ] PDF export with all report pages.
- [ ] Written explanation and screenshot for each of seven questions.
- [ ] Final model and measures verified.
- [ ] Screenshots and files checked for permission to share before publishing to a public repository.
