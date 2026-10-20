# Uploaded Article: From Excel to Insight

**Source article:** *From Excel to Insight: Building the EduTrack Campus Dashboard in Power BI*  
**Date shown in the article:** October 20, 2026  
**Author label in source:** @Samson

This file preserves the article's main structure, workflow, DAX examples, findings, limitations, and recommendations. It is a documented version of the uploaded source article, not an independent audit of the PBIX.

## Article purpose

The article describes a beginner-friendly walkthrough of the ITF–NECA TSDP end-of-module project. The stated aim is to show how five Excel tables are imported, inspected, connected in a Power BI model, analysed with DAX, and turned into a report that a college registrar can use.

The article says the brief requires seven of ten questions, a PBIX file, a PDF export, and a short write-up. Its own walkthrough covers six questions: Q1, Q2, Q3, Q7, Q8, and Q9.

## Workflow described in the article

1. Use **Get Data → Excel workbook**.
2. Select the five data sheets and leave the descriptive README sheet out of the model.
3. Select **Transform Data** to open Power Query.
4. Inspect column names, values, and data types.
5. Fix data types where necessary; the article calls out date fields that may import as text.
6. Use **Close & Apply** to load the prepared tables.
7. Build relationships in Model view and check cardinality and filter direction.
8. Write DAX measures and calculated columns.
9. Choose appropriate visuals and slicers.
10. Write a finding, explain why it matters, and identify an action.

## Relationships listed in the article

| One side | Many side | Key |
|---|---|---|
| departments | instructors | `department_id` |
| departments | students | `department_id` |
| departments | courses | `department_id` |
| instructors | courses | `instructor_id` |
| students | enrollments | `student_id` |
| courses | enrollments | `course_id` |

The article says the instructors-to-courses relationship appeared as a dashed/inactive line in its model. It explains that an inactive relationship does not filter by default and can be activated for a specific measure with `USERELATIONSHIP`. Check the current PBIX before assuming that this is still the model state.

## DAX examples included in the article

These are simplified examples from the article, not a guarantee that they match every final report measure.

Count students:

```dax
Total Students = DISTINCTCOUNT ( students[student_id] )
```

Average student GPA:

```dax
Average GPA = AVERAGE ( students[gpa] )
```

Average enrolments per course (article's Q7 example):

```dax
Avg Enrollment per Course =
DIVIDE (
    COUNTROWS ( enrollments ),
    DISTINCTCOUNT ( enrollments[course_id] )
)
```

Courses with average grade point above 3.0:

```dax
Courses Above 3 GPA =
COUNTROWS (
    FILTER (
        VALUES ( courses[course_id] ),
        CALCULATE ( AVERAGE ( enrollments[grade_point] ) ) > 3
    )
)
```

GPA bands based on the students table:

```dax
GPA Band =
SWITCH (
    TRUE (),
    students[gpa] >= 3.5, "Excellent",
    students[gpa] >= 3.0, "Good",
    students[gpa] >= 2.0, "Fair",
    "At Risk"
)
```

The article advises checking measures against a visual or table whose results can be checked directly. It explicitly notes that a formula can run without an error and still return the wrong result.

## Design choices reported

- Twilight theme.
- Semibold chart titles.
- Visual borders turned off.
- Cards for headline numbers and bars for rankings.
- Doughnut and treemap visuals for parts of a whole.
- Slicers for gender, enrollment year, credits, building, and semester.
- Six pages, one for each question covered by that article.

## Findings reported by the article

**Important:** These are figures reported in the uploaded article. They have not been independently recalculated from the original workbook or PBIX during this documentation step.

### Q1 — Campus at a glance

The article reports:
- 100 students.
- 60 instructors.
- 48 courses.
- 100 enrolment records.
- Average student GPA of 3.08.
- 2024 as the largest intake year with 50 students; 2022 with 12, 2023 with 20, and 2025 with 18.

The article says that a large intake in one year has implications for class sizes, staffing, and student support.

### Q2 — Students by department

The article reports Computer Science and Economics as the largest departments with 14 students each, followed by Accounting (13), Business Administration (11), and Electrical Engineering (10). It reports five departments with one student each.

The article recommends reviewing resource allocation and the viability of very small programmes, while avoiding unsupported conclusions from the small counts alone.

### Q3 — GPA by department

The article reports Mathematics with the highest average GPA at 3.29 and Statistics lowest at 2.40. It notes that Statistics has only one student, so the department ranking should be treated as a prompt for review rather than a definitive judgement.

### Q7 — Courses above average enrolment

The article reports:
- Average enrolments per course: 3.03.
- Nine courses above the average.
- Linear Algebra and Thermodynamics with 10 enrolments each.
- Management Accounting and Real Estate Valuation with eight each.

**Validation issue explicitly recorded in the article:** a measure counting courses above average disagreed with the chart, which showed nine. Reconcile the measure, the chart, and the definition of average before using the count as final.

### Q8 — Courses with average grade point above 3.0

The article reports:
- 22 courses above 3.0 average grade point.
- Overall course average of 3.06.
- Entrepreneurship, Introduction to Programming, and Local Government Administration among the leading courses.
- Discrete Mathematics and Public Policy Analysis near the bottom at about 2.0.

The course grade point is based on enrolment records and is not the same field as each student's cumulative GPA.

### Q9 — Student GPA bands

The article reports the following distribution:

| GPA band | Reported student count |
|---|---:|
| Excellent (3.50–4.00) | 21 |
| Good (3.00–3.49) | 36 |
| Fair (2.00–2.99) | 40 |
| At Risk (below 2.00) | 3 |

The article says the three At Risk students represent 3% of the 100-student cohort, with GPAs from 1.59 to 1.92.

## Challenges and limitations recorded in the article

The article lists four main challenges:
- Understanding the five-table model and an inactive relationship.
- A disagreement between the Q7 measure and chart.
- Different year ranges in the intake chart and year slicer, suggesting different fields were used.
- Translating charts into plain-language insights.

The article lists these limitations:
- Small dataset: 100 students and 100 enrolment records.
- Small departments make average GPA unstable.
- A snapshot describes what happened but does not establish why.
- The article covers six questions rather than all possible questions.

## Recommendations reported in the article

| Recommendation | Article's supporting observation | Suggested action |
|---|---|---|
| Support At Risk students early | Three students reported below 2.0 GPA | Offer advising and tutoring before the next semester |
| Plan for peak demand | 2024 reported with 50 students; two courses reported with 10 enrolments each | Plan seats and staffing ahead of peak periods |
| Review very small departments carefully | Five departments reportedly have one student; Statistics has one student in the reported GPA comparison | Review before making performance or funding judgements |
| Learn from stronger courses | 22 courses reportedly average above 3.0 | Investigate practices that may help lower-scoring courses |

These recommendations should be retained only to the extent that their supporting figures survive validation.

## Skills described by the article

- Power Query data inspection and preparation.
- Data modelling and relationships.
- DAX measures and calculated columns.
- Multi-page visualisation with cards, bars, treemap, doughnut, and slicers.
- Quality checking of measures and small-sample interpretation.
- Plain-language communication of findings and actions.

## Difference from the latest working status

The article covers **Q1, Q2, Q3, Q7, Q8, Q9**. The latest project update in the working conversation says the six pages worked on are **Q1, Q2, Q3, Q4, Q8, Q9**. Preserve both versions until the actual PBIX and final report determine which questions are in the submission.

## Source and verification note

This documentation is based on the uploaded Markdown article and the project brief. Numerical findings above are attributed to the article. The actual workbook, report visuals, DAX measures, and relationship settings should be checked before these values are described as independently verified.
