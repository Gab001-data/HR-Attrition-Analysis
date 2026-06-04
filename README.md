# Employee Attrition Analysis

## 1. Problem Statement
Genomy, a software company, has recorded increased employee attrition over the past 24 months. Management is concerned about talent loss and wants insight into the factors driving employee exits.

### Key Business Questions
- What is the average remuneration of exited employees compared to the industry average?.
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
