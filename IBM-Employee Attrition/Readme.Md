A professional Power BI dashboard analyzing employee attrition across demographics, tenure, role, and compensation, built on the IBM HR Analytics dataset. This project focuses on transforming raw transactional HR data into interactive, executive-ready insights.

![Alt](https://github.com/utkaarsh18/Power-BI/blob/a244383f90e62a5e46d4f867620ef6e27a2168bb/IBM-Employee%20Attrition/dashboard.png)

**Overview**
The goal of this project is to answer a critical business question: **Where is employee attrition concentrated, and which cohorts present the highest risk to the organization?**
By tracking key HR metrics alongside granular employee segments, this dashboard empowers HR leaders to transition from reactive exit-interview tracking to proactive, data-driven retention planning.

**Dataset**
The analysis is based on the IBM HR Analytics Employee Attrition and Performance dataset (available on Kaggle)
**Scope**: 1,470 employees (historical records)
**Attributes**: 35 features covering demographics (Age, Gender, Education), role specifics (JobRole, Department, JobLevel), tenure, compensation (MonthlyIncome, PercentSalaryHike), and historical attrition status ("Yes"/"No").

**Tools Used**
**Power BI Desktop**: Core dashboard development, visualization design, and canvas layout
**Power** Query: Data extraction, column profiling, data type formatting, and initial transformation
**DAX** (Data Analysis Expressions): Custom statistical calculations and key performance indicator (KPI) metric definitions.

**Data Transformations & Grouping**
To avoid cluttered visuals and reveal actionable generational trends, raw values were structured using specialized grouping models:
Tenure Segmentation: Raw years at the company were grouped into clean operational bands using a logical conditional model:
1) 0-1 yr (Onboarding & critical transition phase)
2) 1-3 yr (Early career integration)
3) 3-5 yr (Mid-tenure)
4) 5+ yr (Established tenure)
Equal Age Binning: To ensure a mathematically balanced, unbiased view across age groups, the numeric Age column was compiled into uniform **10-year equal brackets** using Power BI's automatic binning tools:
1) 10-19
2) 20-29
3) 30-39
4) 40-49
5) 50-59

**DAX Measure**:
**Total Employees**    = COUNTROWS('HR')
**Attrition Count**   = CALCULATE([Total Employees], 'HR'[Attrition] = "Yes")
**Attrition Rate**     = DIVIDE([Attrition Count], [Total Employees])
**Avg Monthly Income** = AVERAGE('HR'[MonthlyIncome])

**Key Findings & Data Insights**
**Attrition is Heavily Front-Loaded:** Early tenure is the primary driver of turnover. Employees in their first year (0-1 yr) exhibit a massive **34.88% attrition rate**, which is more than triple the **10.81%** rate seen in mature employees (5+ yr). Turnover drops steeply with every year of experience (18.43% at 1-3 years and 13.07% at 3-5 years) against the company baseline of 16.12%.
**The Compensation Inverse Relationship**: A clear financial trend is revealed when plotting job roles. Roles clustered at the lower end of the income scale (such as Sales Representatives averaging **$2.6K monthly**) experience the highest peak attrition at **39.76%**. Conversely, high-earning leadership roles (Managers and Research Directors averaging **$16K–$17.2K**) see attrition drop safely near zero (**4.90% and 2.50%** respectively)
**Departmental Risk Variation**: Attrition is not uniform across business units. The Sales department experiences the highest turnover at 38.55%, closely followed by Human Resources at 35.59%, while Research & Development remains the most stable quadrant at 25.86%
**Generational Decline** (The Age Trend): Plotting attrition over the newly formed, equal age bins highlights a striking downward linear trend. Turnover peaks sharply among the youngest segment of the workforce (hitting 58.82% in the youngest bracket) and declines predictably as employees age, bottoming out at just 9.74% in the 40s bracket before experiencing a minor, expected pre-retirement fluctuation (13.69%) in the 50s.

