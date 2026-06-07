# Employee Attrition Analysis

## 1. Problem Statement
Atlas Lab, a software company, has recorded significant employee attrition over the past 24 months. Management is concerned about talent loss and wants insight into the factors driving employee exits.

### Key Business Questions
- What is the average remuneration of employees compared to the industry average?.
- What is the hiring trend over the past 12 months?.
- Which department recorded the highest attrition rate historically?.
- When is an employee most likely to leave the company?. What is the average employment duration for attritted employees
- What is the impact of overtime and work travel requirements on employee attrition?
- What welfare and training programs should be implemented?

## 2. Dataset Description
The dataset for this analysis includes the following fact and dimension tables.
#### 📁 Fact table
##### FactPerformance
- PerformanceID
- EmployeeID
- ReviewDate
- EnvironmentSatisfaction
- JobSatisfaction
- RelationshipSatisfaction
- WorkLifeBalance
- SelfRating
- ManagerRating
- TrainingOpportunitiesWithinYear
- TrainingOpportunitiesTaken

### 📁 Dimension Tables
##### DimEmployee
- EmployeeID
- FirstName
- LastName
- Gender
- Age
- BusinessTravel
- Department
- DistanceFromHome
- State
- Ethnicity
- Education
- JobRole
- Salary
- StockOptionLevel
- OverTime
- HireDate
- Attrition
- YearsAtCompany
- YearsInMostRecentRole
- YearsSinceLastPromotion
- YearsWithCurrentManager

##### DimSatisfiedLevel
- SatisfactionID
- SatisfactionLevel

##### DimRatingLevel
- RatingID
- RatingLevel
- 
##### DimEducationLevel
- EducationLevelID
- EducationLevel

## 3. Data Model Diagram
![data model](https://github.com/Gab001-data/HR-Attrition-Analysis/blob/main/img/data_model.png)

## 4. Key DAX Measures
##### 🚶 % Attrition Rate
```
</> DAX
% Attrition Rate = DIVIDE([InactiveEmployees], [TotalEmployees])

```
##### 🧑 InactiveEmployees
```
</> DAX
ActiveEmployees = CALCULATE([TotalEmployees], FILTER(DimEmployee, DimEmployee[Attrition] = "Yes"))

```
##### 👥 TotalEmployees
```
</> DAX
TotalEmployees = DISTINCTCOUNT(DimEmployee[EmployeeID])

```
##### 💰 AverageSalary
```
</> DAX
AverageSalary = AVERAGE(DimEmployee[Salary])

```

##### ✅ ManagerRating
```
</> DAX
ManagerRating = 
CALCULATE (
    MAX ( FactPerformanceRating[ManagerRating] ),
    USERELATIONSHIP ( FactPerformanceRating[ManagerRating], DimRatingLevel[RatingID] )
)

```

##### ⚖️ WorkLifeBalance
```
</> DAX
WorkLifeBalance = 
CALCULATE (
    MAX ( FactPerformanceRating[WorkLifeBalance] ),
    USERELATIONSHIP ( FactPerformanceRating[WorkLifeBalance], DimSatisfiedLevel[SatisfactionID] )
)

```
## 5. Dashboard Screenshots
##### 📌 Executive Overview Dashboard
- KPI Cards: Total Employees, Active Employees, Inactive Employees, % Attrition Rate
- Trend: Yearly Employee Hiring trend
- Bar Chart: Count of Active employees by Dept
- Active employees by Department and Job Role hierarchy map.

![overview dashboard](https://github.com/Gab001-data/HR-Attrition-Analysis/blob/main/img/Overview.png)

##### 📌Employee Demography
- KPI Cards: Youngest, Oldest Employee
- Proportion of Employees by Marital Status
- Column Chart: Distribution of Employees by Age and Gender, Count of Employees, and Average Salary by Ethnicity

![demograph](https://github.com/Gab001-data/HR-Attrition-Analysis/blob/main/img/Demography.png)

##### 📌 Employee Performance Tracker
- Cards: Start Date, Last Review Date, Next Review Date
- TrendLine: Job Satisfaction, Relationship Satisfaction, Environment Satisfaction, Manager Rating, Self Rating, Work Life Balance

![performance tracker](https://github.com/Gab001-data/HR-Attrition-Analysis/blob/main/img/Performance_Tracker.png)

##### 📌Attrition
- KPI Card: % Attrition Rate
- TrendLine: % Attrition Rate by Hire Date
- Column Charts: Attrition Rate by Department & Job Role, Attrition by Travel Frequency, Overtime, and Tenure

![Attrition](https://github.com/Gab001-data/HR-Attrition-Analysis/blob/main/img/Attrition.png)

## 6. Insight & Recommendation
##### 🔍 Key Insights
##### 1. Longer Employee Tenure = Less Attrition
- Employees with less than 5 years at the company are more likely to leave
- Employees with Tenure above 9 years account for only 0.8% of total attrition.

##### 2. Frequent work travels drive attrition
- 24% of Employees with frequent travel requirements leave the company compared to 15.0% for employees with some travel requirements, and 8.0% for no travel employees

##### 3. Impact of Overtime work
- Over 30.5% of employees with overtime requirements exit the company.
- Overtime work has a tremendous impact on attrition. only 10.4% of Employees with no overtime work requirement exited.

##### 4. Historically, attrition rate has been fairly constant
- Attrition by hire data has changed from 15% in 2012 to 16.1% in 2022

#### 💡Recommendations
##### 1. Employee Onboarding and Training
- Ensure proper onboarding for new employees
- Implement comprehensive training & welfare programs for employees to ensure job and environment satisfaction, and work-life balance.
- frequent review of training to ensure contents are upto date and relevant employee's job role

