# Employee-Attrition-Dashboard-
This Interactive PowerBI Dashboard project showcases an analysis of Employee Attrition from a synthetic data made with AI. 
The data consists of a replicate employee data that is commonly used for analysis. 

<img width="727" height="404" alt="image" src="https://github.com/user-attachments/assets/5339cb0b-a07e-4e7a-8b62-3cd74213baf6" />

_*Screenshot of dashboard_

## Dataset 
- EmployeeID: Unique identifier for each employee
- Age: Employee's age
- Department: States under what department an employee is
- JobRole: The employee's job position
- YearsAtCompany: How long the employee has stayed in the company
- MonthlyIncome: The monthly salary an employee earns
- JobSatisfaction: Rating of 1 (lowest) and 5 (highest) of an employee's satisfaction
- WorkLifeBalance:  Rating of 1 (lowest) and 5 (highest) of an employee's work life balance
- OverTime: If an employee works on overtime on a daily basis
- PromotionLastYear: If an employee was promoted last year.
- PercentSalaryHike: Percentage of the increase of their salary
- PerformanceRating: Employee's performance rating in their job
- EducationaLevel: Employee's education level (1-4)
- MaritalStatus: Employee's Marital Status
- DistanceFromHome: Employee's distance from their workplace (measured in kilometers)
- NumCompaniesWorked: Number of companies an employee has worked before working here
- StockOptionLevel: Employee's stock option capacity
- ExitFlag - States if a candidate has left the company
- ExitYear - States the year a candidate has left

  ## DAX Formula Measures used
  - **Total Employees** = CALCULATE( COUNTROWS('employee_attrition_1500'), ALLSELECTED('employee_attrition_1500'[JobSatisfaction])
  - **Total Exits** = CALCULATE(COUNTROWS(employee_attrition_1500), employee_attrition_1500[ExitFlag] = 1)
  - **Total Headcount** = CALCULATE(COUNTROWS('employee_attrition_1500'),ALLSELECTED('employee_attrition_1500'[JobSatisfaction]), REMOVEFILTERS('employee_attrition_1500'[ExitYear])
  - **Attrition Rate** = DIVIDE([Total Exits], [Total Headcount], 0)
  - **Attrition Count** = SUM(employee_attrition_1500[ExitFlag])
  - **Age Group Bucket** = SWITCH(
    TRUE(),
    employee_attrition_1500[Age] < 25, "Under 25",
    employee_attrition_1500[Age] <= 34, "25 - 34",
    employee_attrition_1500[Age] <= 44, "35 - 44",
    employee_attrition_1500[Age] <= 54, "45 - 54",
    "55 and Over"
