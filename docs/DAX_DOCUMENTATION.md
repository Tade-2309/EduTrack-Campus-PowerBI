# EduTrack DAX Documentation

This file documents DAX examples used or discussed during the EduTrack project. **Treat these as patterns to test, not certified final measures.** Confirm table/column names, filter context, relationships, and results in the current PBIX.

## Important field distinction

- `students[gpa]`: student cumulative GPA, used for student-level GPA analysis.
- `enrollments[grade_point]`: grade point attached to an enrolment/course record, used for course grade-point analysis.

Do not use enrolment grade points as a substitute for students' cumulative GPA.

## Core count measures

```dax
Total Students =
DISTINCTCOUNT ( students[student_id] )

Total Instructors =
DISTINCTCOUNT ( instructors[instructor_id] )

Total Courses =
DISTINCTCOUNT ( courses[course_id] )

Total Enrolments =
COUNTROWS ( enrollments )
```

## Average student GPA

```dax
Average GPA =
AVERAGE ( students[gpa] )
```

This measure can be displayed by department if the department-to-students relationship filters correctly.

## Department student count

```dax
Department Students =
DISTINCTCOUNT ( students[student_id] )
```

Use department and gender fields in the visual only after confirming the field names and that filters behave as expected.

## Instructor count and salary

```dax
Instructor Count =
DISTINCTCOUNT ( instructors[instructor_id] )

Average Salary =
AVERAGE ( instructors[salary] )
```

For Q4, filter departments to those with more than four instructors and compare average salaries within that filtered group. Verify that department context propagates to the instructors table.

## Fall 2024 enrolments (Q5)

A simple starting measure, if the semester column contains the exact text value `Fall 2024`:

```dax
Fall Enrolments =
CALCULATE (
    COUNTROWS ( enrollments ),
    enrollments[semester] = "Fall 2024"
)
```

Check the actual distinct semester values first. If the dataset uses a different format, adjust the filter to match the data. For the list of students and courses, use the relevant fields from students, courses, and enrollments and confirm the relationships filter correctly.

## Enrolments per course (Q7 article example)

```dax
Course Enrolments =
COUNTROWS ( enrollments )

Avg Enrollment per Course =
DIVIDE (
    COUNTROWS ( enrollments ),
    DISTINCTCOUNT ( enrollments[course_id] )
)
```

This ratio is a simple overall average over courses represented in the enrolments table. If the business definition includes courses with zero enrolments, use a measure that iterates over the full courses table instead. Choose and document the intended definition.

The uploaded article reports a disagreement between a Q7 measure and the chart, so the count of courses above average must be reconciled with the actual chart and data before reporting it as final.

## Courses above grade point 3.0 (Q8)

```dax
Course GPA =
AVERAGE ( enrollments[grade_point] )

High GPA Courses =
COUNTROWS (
    FILTER (
        VALUES ( courses[course_id] ),
        CALCULATE ( [Course GPA] ) > 3.0
    )
)
```

Check that the courses-to-enrolments relationship is active or otherwise handled correctly for this measure. Confirm whether courses with no enrolments should be excluded.

## GPA category calculated column (Q9)

```dax
GPA Category =
SWITCH (
    TRUE (),
    ISBLANK ( students[gpa] ), "Not Recorded",
    students[gpa] > 4.0 || students[gpa] < 0, "Check GPA",
    students[gpa] >= 3.5, "Excellent",
    students[gpa] >= 3.0, "Good",
    students[gpa] >= 2.0, "Fair",
    "At Risk"
)
```

This column adds a category for each student row. Confirm the GPA scale and decide how blanks or out-of-range values should be handled. The course brief defines the bands as Excellent (3.50–4.00), Good (3.00–3.49), Fair (2.00–2.99), and At Risk (below 2.00).

A simple category count measure is:

```dax
Students per Category =
DISTINCTCOUNT ( students[student_id] )
```

Place the category column on the visual axis/legend so that the measure is evaluated by category.

## Intake year (Q1)

A basic count of students can be used by enrollment year:

```dax
Student Intake =
DISTINCTCOUNT ( students[student_id] )
```

Use the student's enrollment-year field for the intake analysis. The uploaded article notes that its intake chart and year slicer displayed different year ranges, so confirm both visuals use the same field.

## Validation checklist

- [ ] Confirm the actual table and column names in the model.
- [ ] Check data types, especially date columns and numeric salary/GPA fields.
- [ ] Confirm the expected relationships and cardinality.
- [ ] Review dashed/inactive relationships and their effect on filter context.
- [ ] Compare headline measures against a table or source-data count.
- [ ] Check course averages against a detail table of course-level counts/averages.
- [ ] Ensure student GPA and enrolment grade point are not confused.
- [ ] Confirm GPA band boundaries, blanks, and invalid values.
- [ ] Check that the Q7 count matches the chart.
- [ ] Check that the Q1 intake chart and year slicer use the same enrollment-year field.
- [ ] Record any assumptions in the final report.
