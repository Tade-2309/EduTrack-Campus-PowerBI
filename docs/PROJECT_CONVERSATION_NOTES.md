# EduTrack Project Conversation Notes

This file records the project-related decisions and status updates from the working conversation. It is not intended to reproduce unrelated personal conversations.

## Latest progress update

The user reported having worked on questions **8, 9, 1, 2, 3, and 4**. The latest organised status is therefore:

- Q1: institutional totals, average GPA, largest intake year.
- Q2: students by department and gender, top five departments.
- Q3: average GPA by department.
- Q4: departments with more than four instructors and average salary.
- Q8: courses with average grade point above 3.0.
- Q9: GPA bands and At Risk students.

The user previously stated that all six report pages had been created and all charts completed. The next priority was writing key insights for each page.

## Seventh question

The course brief requires seven of ten questions. Q5 was recommended as the next question:

> How many enrolments were recorded in Fall 2024, and which students were enrolled in which courses during that semester?

Q5 is a recommendation for the next step, not a claim that it is already completed.

## Project journey documented

The recorded journey includes:
1. Downloading the Excel dataset.
2. Using Get Data in Power BI Desktop.
3. Selecting Transform Data.
4. Inspecting and cleaning in Power Query.
5. Reviewing column values and data types.
6. Applying changes with Close & Apply.
7. Creating relationships in Model view.
8. Writing DAX.
9. Selecting business questions and matching calculations/visuals to them.
10. Designing the report using the Twilight palette, semibold titles, and borders turned off.
11. Creating report pages and charts.
12. Preparing key insights, limitations, recommendations, and a final presentation.

## Model details to verify

The user described the model as a star-like flow rather than a perfect star schema. Notes mention inactive relationships involving students/enrolments and courses/instructors at one point. The uploaded article specifically describes the instructors–courses relationship as inactive.

The official project brief lists six one-to-many relationships. The current PBIX should be checked to confirm which relationships are active and why any inactive relationship is needed. Do not treat an inactive relationship as necessarily wrong or assume it is correct without inspecting the model.

## Presentation preferences and feedback

An earlier 20-slide PowerPoint was created for the project journey. The user said the presentation was too technical. The revised presentation should be more natural and accessible, focusing on:
- What I did.
- Why I did it.
- What I noticed.
- What I learned.
- What the findings mean for the college.

It should preserve room for the user's screenshots, findings, challenges, limitations, and recommendations. The user plans to provide a Canva template for the revision.

## Documentation request

The user asked for the whole project-related conversation to be documented in Markdown in a new dedicated GitHub repository. The chosen repository is:

**Repository:** [Tade-2309/EduTrack-Campus-PowerBI](https://github.com/Tade-2309/EduTrack-Campus-PowerBI)

The repository is public, so only files and screenshots the user is allowed to share should be added. Do not publish the source workbook or other restricted course materials without permission.

## Immediate next steps

1. Complete Q5 or another seventh question.
2. Write evidence-based insights for each report page.
3. Reconcile the Q7 measure/chart disagreement in the uploaded article.
4. Reconcile the intake chart and year slicer fields.
5. Validate relationships and DAX against the actual PBIX.
6. Organise the screenshot evidence.
7. Prepare challenges, limitations, and recommendations based on verified work.
8. Simplify the presentation and adapt it to the Canva template when supplied.
9. Ensure the PBIX, PDF export, and seven question write-ups meet the brief.
