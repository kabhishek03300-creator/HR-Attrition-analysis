HR Analytics Dashboard | Tableau Project
An interactive Human Resources (HR) Analytics Dashboard developed in Tableau to explore employee attrition, workforce composition, departmental patterns, age-group distribution, and job satisfaction.

The project combines multiple HR visualizations into one dashboard so that users can review workforce indicators and explore how attrition is distributed across employee groups. The workbook includes calculated fields for attrition count, attrition rate, and active employees, along with an adjustable age-bin parameter.
Project type: Data Analytics / Business Intelligence
Primary tool: Tableau
Workbook: HR DASHBOARD.twb
Dashboard title stored in workbook: HR ANALYSTICS DASHBOARD

Table of Contents
- Project Overview
- Project Objectives
- Dashboard at a Glance
- Dashboard Worksheets
- Key Performance Indicators
- Calculated Fields
- Dataset Overview
- Data Fields
- Filters and Parameters
- How to Open the Project
- Repository Structure
- How to Use the Dashboard
- Insights This Dashboard Can Help Explore
- Technical Details
- Data Connection Notes
- Limitations and Assumptions
- Possible Future Improvements
- Author
Project Overview
Employee attrition is an important HR metric because employee departures can affect workforce stability, recruitment requirements, team experience, and organizational costs. HR teams often need to understand not only how many employees have left, but also how attrition is distributed across departments, age groups, gender, education fields, and job roles.

This Tableau project provides a consolidated view of selected HR indicators. It includes KPI calculations and supporting visualizations that allow users to examine employee attrition and workforce composition from different perspectives.

The dashboard is designed for exploratory analysis. Users can review the overall indicators and then examine the breakdowns shown in the individual charts. The workbook does not itself establish the reasons employees leave; it provides descriptive views of the fields available in the underlying dataset.
Project Objectives
The main objectives of this project are to:
1. Monitor workforce indicators — display total attrition count, attrition rate, and active employee count.
2. Explore attrition by gender — compare the recorded attrition counts for different gender categories.
3. Compare departments — review how attrition is distributed across departments.
4. Understand workforce age distribution — group employees into age bands and review the number of employees in each band.
5. Explore job satisfaction — view job satisfaction ratings across job roles and education categories.
6. Review education-field patterns — compare attrition counts across education fields.
7. Compare age and gender patterns — examine attrition rates by gender across age groups.
8. Support HR exploration — provide a single place to inspect the selected workforce metrics and visual breakdowns.
Dashboard at a Glance
The Tableau workbook contains one dashboard and seven worksheets.
Component	Purpose
KPI	Displays the main workforce indicators
Attrition by Gender	Compares attrition counts by gender
Department wise Attrition	Shows attrition by department
Education Field wise Attrition	Shows attrition by education field
Job Satisfaction Rating	Displays job satisfaction by job role and education category
No of Employee by Age Group	Shows employee counts across age bands
Attrition Rate by Gender for Different Age Group	Compares attrition rates by gender and age group


The dashboard is built from the HR dataset connected to the Tableau workbook. The views are intended to complement one another: the KPI view provides a high-level summary, while the remaining views provide category-level breakdowns.
Dashboard Worksheets
1. KPI
The KPI worksheet contains three calculated workforce indicators:
- Attrition Count — the count of records identified as attrition cases by the workbook's calculation.
- Attrition Rate — attrition count divided by employee count.
- Active Employee — employee count minus attrition count.
These indicators provide a high-level summary before the user explores the detailed charts.
2. Attrition by Gender
This worksheet presents attrition count split by the Gender field. It can be used to compare the number of recorded attrition cases between the gender categories present in the dataset.

This is a count comparison, not a conclusion about the causes of attrition or the likelihood of an individual employee leaving.
3. Department wise Attrition
This worksheet groups attrition by Department. The workbook includes an Education filter associated with this view, allowing the department breakdown to be explored for selected education categories.
4. Education Field wise Attrition
This worksheet groups attrition by Education Field. It helps users examine how attrition cases are distributed across the education-field categories contained in the source data.
5. Job Satisfaction Rating
This worksheet presents Job Satisfaction across Job Role and education categories. It provides a way to compare the satisfaction-rating distribution represented in the workbook.

The source field is a rating value; the chart should be interpreted as a descriptive view of the available ratings rather than proof of why employees stay or leave.
6. No of Employee by Age Group
This worksheet displays employee counts by age group. The workbook creates an age bin from the Age field and uses a parameter called Bine Size to control the bin size.

The parameter's saved default is 4. Its allowed range in the workbook is 2 to 10, with increments of 1.
7. Attrition Rate by Gender for Different Age Group
This worksheet compares attrition rates across gender and age-group categories. It brings together the Gender, age-group, and attrition calculations to support a more detailed comparison than the overall KPI.
Key Performance Indicators
The workbook defines three primary KPIs.
KPI	Meaning	Workbook calculation
Attrition Count	Counts records where Attrition is Yes	SUM([Attrition Count])
Attrition Rate	Attrition count divided by employee count	SUM([Attrition Count]) / SUM([Employee Count])
Active Employee	Employee count less attrition count	SUM([Employee Count]) - SUM([Attrition Count])


1. Attrition Count
This calculated field converts the attrition status into a numeric indicator:
- If Attrition is Yes, the calculation returns 1.
- Otherwise, it returns 0.
The values can then be summed to obtain the attrition count.
2. Attrition Rate
The attrition rate is calculated by dividing the summed attrition count by the summed employee count:
\[
\text{Attrition Rate} =
\frac{\text{Total Attrition Count}}{\text{Total Employee Count}}
\]
The workbook formula returns a ratio. Format the result as a percentage in Tableau if a percentage display is desired.
3. Active Employee
The active employee calculation subtracts attrition count from employee count:
\[
\text{Active Employees} =
\text{Employee Count} - \text{Attrition Count}
\]
This is the workbook's defined calculation. Its accuracy depends on the meaning and granularity of the Employee Count field in the supplied dataset.
Calculated Fields
The following are the principal calculated fields identified in the Tableau workbook.
Attrition Count
IF [Attrition] = "Yes" THEN 1
ELSE 0
END
Explanation: Converts the text-based attrition status into a numeric flag. Records marked Yes return 1; all other values return 0.
Attrition Rate
SUM([Calculation_1743336821469184]) / SUM([Employee Count])
Explanation: Divides the sum of the attrition-count calculation by the sum of employee count.
Active Employee
SUM([Employee Count]) - SUM([Calculation_1743336821469184])
Explanation: Subtracts the summed attrition-count calculation from the summed employee count.
Age Bin
The workbook creates an age bin from the Age field:
[Age]
The bin size is controlled by the Bine Size parameter rather than being hard-coded in this calculated field.
Bine Size Parameter
Parameter setting	Value
Default value	4
Minimum	2
Maximum	10
Step / granularity	1


Changing this parameter changes the grouping interval used in the age distribution view.
Dataset Overview
The workbook references a CSV data source with the following name:

HR Data.xlsx - HR data (1).csv

Although the source name contains HR Data.xlsx, the Tableau connection identifies the file as a CSV.

The workbook metadata includes an extract with an approximate record count of 1,470. This is metadata from the workbook extract; verify the current source file if an exact, up-to-date row count is required.

The dataset contains employee-related demographic, employment, satisfaction, and compensation fields. The workbook uses these fields to build the dashboard views and calculations.
Main Data Categories
Category	Example fields
Employee identification	Employee Number, emp no, Employee Count
Demographics	Age, Gender, Marital Status
Organization	Department, Job Role, Business Travel
Education	Education, Education Field
Attrition and work pattern	Attrition, Over Time, CF_attrition label, CF_current Employee
Satisfaction and engagement	Job Satisfaction, Environment Satisfaction, Job Involvement, Relationship Satisfaction, Work Life Balance
Experience and tenure	Total Working Years, Years At Company, Years In Current Role, Years With Curr Manager
Compensation and performance	Monthly Income, Daily Rate, Hourly Rate, Monthly Rate, Percent Salary Hike, Performance Rating
Training and career progression	Training Times Last Year, Years Since Last Promotion, Num Companies Worked, Job Level


Data Fields
The workbook's source connection defines the following fields.
Employee and Demographic Fields
Field	Description
Employee Number	Employee number identifier
emp no	Employee-number field stored as text
Employee Count	Employee-count measure used in the KPI calculations
Age	Employee age
Gender	Gender category
Marital Status	Marital-status category


Organization and Education Fields
Field	Description
Department	Department category
Job Role	Job-role category
Business Travel	Business-travel category
Education	Education category
Education Field	Education-field category


Attrition and Employment Fields
Field	Description
Attrition	Attrition status used by the attrition calculation
Over Time	Overtime category
Over18	Field indicating the source's over-18 category
CF_age band	Age-band field present in the source
CF_attrition label	Attrition-label field present in the source
CF_current Employee	Current-employee indicator field present in the source


Satisfaction and Engagement Fields
Field	Description
Job Satisfaction	Job satisfaction rating
Environment Satisfaction	Environment satisfaction rating
Job Involvement	Job involvement rating
Relationship Satisfaction	Relationship satisfaction rating
Work Life Balance	Work-life-balance rating


Experience, Training, and Career Fields
Field	Description
Total Working Years	Total years of work experience
Years At Company	Years spent at the company
Years In Current Role	Years in the current role
Years With Curr Manager	Years with the current manager
Training Times Last Year	Training count during the previous year
Years Since Last Promotion	Years since the last promotion
Num Companies Worked	Number of companies worked at
Job Level	Job-level value
Stock Option Level	Stock-option-level value


Compensation and Performance Fields
Field	Description
Daily Rate	Daily-rate value
Hourly Rate	Hourly-rate value
Monthly Income	Monthly income value
Monthly Rate	Monthly-rate value
Percent Salary Hike	Salary-hike percentage
Performance Rating	Performance rating
Distance From Home	Distance-from-home value
Standard Hours	Standard-hours value


Filters and Parameters
Education Filter
The Department wise Attrition worksheet includes an Education filter. This filter can be used to narrow the department-level attrition view to selected education categories.
Bine Size Parameter
The age distribution worksheet uses the Bine Size parameter.
- Default: 4
- Minimum: 2
- Maximum: 10
- Increment: 1
A smaller bin size creates narrower age intervals; a larger bin size creates wider intervals. This changes the grouping of ages in the chart, not the underlying employee ages.
How to Open the Project
Requirements
- Tableau Desktop or another Tableau application capable of opening .twb workbooks.
- The source CSV file referenced by the workbook.
- Access to the project files.
Steps
1. Download or clone this GitHub repository.
2. Make sure the HR CSV source file is available on your computer.
3. Open Tableau.
4. Select File → Open.
5. Choose HR DASHBOARD.twb.
6. If Tableau reports that the data source cannot be found, reconnect it to the correct CSV file.
7. Confirm that the data fields are recognized and that the worksheets load.
8. Open the HR ANALYSTICS DASHBOARD dashboard.
9. Use the available Education filter and age-bin parameter to explore the views.
Repository Structure
A suggested GitHub repository layout is:
HR-Analytics-Dashboard/
│
├── README.md
│
├── HR DASHBOARD.twb
│
├── data/
│   └── HR Data.xlsx - HR data (1).csv
│
├── screenshots/
│   └── dashboard-preview.png
│
└── docs/
    └── project-notes.md
Important: The structure above is a suggested way to organize the GitHub repository. Only add the data/, screenshots/, or docs/ files if you have those files and are permitted to share them. The supplied workbook is a .twb file and does not package the source CSV inside it.

If you prefer not to publish the source dataset, keep it outside the public repository and add instructions explaining how an authorized user can connect their own copy.
How to Use the Dashboard
1. Open the workbook in Tableau after connecting the source CSV.
2. Start with the KPI section to review the three calculated indicators.
3. Use Attrition by Gender to compare attrition counts by gender.
4. Review Department wise Attrition and use its Education filter to narrow the view.
5. Explore Education Field wise Attrition to compare education-field categories.
6. Review Job Satisfaction Rating to compare satisfaction ratings across job roles and education categories.
7. Use the Bine Size parameter in No of Employee by Age Group to change the age intervals.
8. Review Attrition Rate by Gender for Different Age Group to compare the age-group and gender breakdown.
9. Reset filters or parameters when you want to return to the default view.
The exact interaction behavior depends on the dashboard controls and actions configured in the workbook.
Insights This Dashboard Can Help Explore
The dashboard can be used to investigate questions such as:
- How many attrition cases are recorded in the dataset?
- What attrition rate is produced by the workbook's calculation?
- How many active employees are indicated by the KPI calculation?
- How is attrition distributed across gender categories?
- Which departments have higher or lower attrition counts?
- How does the department-level view change when the Education filter is applied?
- How are attrition cases distributed across education fields?
- How does the employee count vary across age groups?
- How does the age distribution change when the bin size is adjusted?
- How are job satisfaction ratings distributed across job roles and education categories?
- How do attrition rates compare across gender and age groups?
These are analysis questions the workbook can help examine. The README does not state findings or causal explanations because those require analysis of the actual chart values and source records.
Technical Details
Item	Details
Project	HR Analytics Dashboard
Visualization tool	Tableau
Workbook format	Tableau Workbook (.twb)
Data source format	CSV
Dashboard count	1
Worksheet count	7
Main KPI calculations	Attrition Count, Attrition Rate, Active Employee
Parameter	Bine Size
Parameter default	4
Parameter range	2–10
Parameter increment	1


Why Tableau?
Tableau is used in this project to organize HR data into visual views, define calculated fields, and provide interactive controls. It makes it possible to review summary indicators and category-level breakdowns within one workbook.
Data Connection Notes
The supplied .twb file stores the workbook definition and refers to a CSV source. The original connection path recorded in the workbook is:
C:/Users/kabhi/Downloads/HR Data.xlsx - HR data (1).csv
This is a path from the computer on which the workbook was created. It will not normally exist on another user's computer.

The workbook also contains a reference to a temporary Tableau extract under a local AppData/Local/Temp directory. Temporary extract paths are machine-specific and may not be available when the workbook is opened elsewhere.
If the data source is missing
1. Open the workbook in Tableau.
2. Use the data-source warning or connection options to locate the missing source.
3. Browse to your local copy of the HR CSV file.
4. Confirm that the field names and data types match the expected source.
5. Refresh the data if required.
6. Recheck the KPI values and worksheet visualizations.
TWB vs. TWBX
- .twb is a Tableau workbook definition. It stores workbook structure, worksheets, dashboard layout, calculations, and connection information, but does not bundle the external CSV source file.
- .twbx is a packaged Tableau workbook format that can include supporting data and other assets.
If you want to make the project easier to share, consider saving a packaged workbook from Tableau using File → Save As → Tableau Packaged Workbook (.twbx), subject to the dataset's sharing permissions.
Limitations and Assumptions
- The dashboard is based on the fields and calculations defined in the supplied workbook.
- The attrition calculation treats records with Attrition = "Yes" as attrition cases and all other values as zero.
- The attrition-rate formula uses the sum of Employee Count as its denominator.
- The active-employee formula subtracts attrition count from employee count.
- KPI results depend on the source data, its granularity, and the way Employee Count is populated.
- The workbook's age-bin parameter is saved with a default value of 4 and a range from 2 to 10.
- The workbook references a local CSV path and a temporary extract path, so the data connection may need to be repaired on another computer.
- The README does not include fixed KPI totals or business conclusions. Those should be documented only after validating the live dashboard values.
- The workbook definition alone does not establish causal relationships between satisfaction, demographics, and attrition.
Possible Future Improvements
The project could be extended with additional analysis and documentation, for example:
1. Add a dashboard screenshot to the repository so visitors can preview the dashboard without opening Tableau.
2. Add a data dictionary describing the meaning and coding of each source field.
3. Add a data-quality section covering missing values, duplicate employee identifiers, and field validation.
4. Add department-level attrition-rate comparisons, where the denominator is defined consistently.
5. Add views for tenure, overtime, business travel, and years since last promotion if these questions are relevant to the analysis.
6. Add trend analysis if reliable time-period data becomes available.
7. Add dashboard navigation, clear-filter controls, and explanatory tooltips.
8. Validate KPI calculations against a trusted source or a separate summary.
9. Publish a packaged .twbx workbook when sharing the underlying data is permitted.
10. Document the data source version and refresh date so users know which dataset the dashboard represents.
Author
Project: HR Analytics Dashboard
Created with: Tableau

Add your name, GitHub profile, LinkedIn profile, or contact information here before publishing if you want the repository to identify you as the project author.
Disclaimer
This project is intended for learning, portfolio demonstration, and exploratory HR data analysis. The dashboard summarizes the fields and calculations available in the supplied workbook. It should not be used as the sole basis for employment decisions or individual assessments. Confirm data accuracy, privacy permissions, and calculation definitions before using the analysis for business decisions.
