# HR-Analytics

# Performed the following challenges:
- Data modeling
- Exploratory Data Analysis
- DAX functions
- Report Design

# Performed DAX calculations:
- % Attrition Rate
  - % Attrition Rate = DIVIDE([InactiveEmployees], [TotalEmployees])
- % Attrition Rate Date
  - % Attrition Rate Date = DIVIDE([InactiveEmployeesDate], [TotalEmployeesDate])
- Active Employees
  - ActiveEmployees = CALCULATE([TotalEmployees], FILTER(DimEmployee, DimEmployee[Attrition] = "No"))
- Average Salary
  - AverageSalary = AVERAGE(DimEmployee[Salary])
- Environment Satisfaction
  - EnvironmentSatisfaction = 
CALCULATE(
    MAX(FactPerformanceRating[EnvironmentSatisfaction]), 
    USERELATIONSHIP(FactPerformanceRating[EnvironmentSatisfaction], DimSatisfiedLevel[SatisfactionLevel]))
- Inactive Employees
  - InactiveEmployees = CALCULATE([TotalEmployees], filter(DimEmployee, DimEmployee[Attrition] = "Yes"))
- Inactive Employees Date
  - InactiveEmployeesDate = CALCULATE([InactiveEmployees], USERELATIONSHIP(DimEmployee[HireDate], DimDate[Date]))
- Job Satisfaction
  - JobSatisfaction = MAX(FactPerformanceRating[JobSatisfaction])
- Last Review Date
  - LastReviewDate = 
IF (
    MAX ( FactPerformanceRating[ReviewDate] ) = BLANK (),
    "No Review Yet",
    MAX ( FactPerformanceRating[ReviewDate] )
)
- Manager Rating
  - ManagerRating = 
CALCULATE(
    MAX(FactPerformanceRating[ManagerRating]), 
    USERELATIONSHIP(FactPerformanceRating[ManagerRating], DimRatingLevel[RatingLevel]))
- Next Review Date
  - NextReviewDate = 
VAR reviewOrHire =
    IF (
        MAX ( FactPerformanceRating[ReviewDate] ) = BLANK (),
        MAX ( DimEmployee[HireDate] ),
        MAX ( FactPerformanceRating[ReviewDate] )
    )
RETURN
    reviewOrHire + 365
- Relationship Satisfaction
  - RelationshipSatisfaction = 
CALCULATE(
    MAX(FactPerformanceRating[RelationshipSatisfaction]), 
    USERELATIONSHIP(FactPerformanceRating[RelationshipSatisfaction], DimSatisfiedLevel[SatisfactionLevel]))
- Self Rating
  - SelfRating = 
CALCULATE(
    MAX(FactPerformanceRating[SelfRating]), 
    USERELATIONSHIP(FactPerformanceRating[SelfRating], DimRatingLevel[RatingLevel]))
- Total Employees
  - TotalEmployees = DISTINCTCOUNT(DimEmployee[EmployeeID])
- Total Employees Date
  - TotalEmployeesDate = 
CALCULATE (
    [TotalEmployees],
    USERELATIONSHIP ( DimEmployee[HireDate], DimDate[Date] )
)
- Worklife Balance
  - WorkLifeBalance = 
CALCULATE(
    MAX(FactPerformanceRating[WorkLifeBalance]), 
    USERELATIONSHIP(FactPerformanceRating[WorkLifeBalance], DimSatisfiedLevel[SatisfactionLevel]))

# Dashboards
- Overview
![i5tkhu32 sq3](https://github.com/MarcvWaes/HR-Analytics/assets/120553175/24abd0d4-1be3-4686-abd6-6e66a6df8678)

- Demographics
![dmnlwhhh f2y](https://github.com/MarcvWaes/HR-Analytics/assets/120553175/6657fe87-f57d-4ccf-aa58-910a98b3812e)

- Performance Tracker
![awady2q5 v20](https://github.com/MarcvWaes/HR-Analytics/assets/120553175/37de4aa2-755e-4b02-943a-fa19b6fc8625)

- Attrition
![b0dlm1sa 0is](https://github.com/MarcvWaes/HR-Analytics/assets/120553175/593ae1b6-b3bb-4f97-881d-1ea09a85e633)
