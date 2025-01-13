# HRAnalysis

Objective: Determine key insights related to employee attrition, satisfaction, and performance.

Primary questions to explore:
- What factors contribute to employee attrition?
- How do job satisfaction and work-life balance impact employee retention?
- What is the relationship between income, job role, and attrition?
- How do years of service affect promotion rates and attrition?

In this hypothetical scenario. The executive leadership wants to understand the root cause of attrition and develop data driven strategies to improve employee retention, engagement and overall satisfaction.
As a HR analyst, your role is to analyze employee data and uncover actionable insights that can support strategic decision making.
**Tasks to perform: **
Data Cleaning:
Add primary key
Deleting redundant columns.
Renaming the columns.
Dropping duplicates.
Cleaning individual columns.
Remove the NaN values from the dataset

SQL codes
use hr_data;

-- rename column

ALTER TABLE hr_employee
RENAME COLUMN ï»¿Age to Age;

SELECT *
FROM hr_employee;

-- Give each row a distinct employeeID

Alter TABLE hr_employee
ADD column id INT AUTO_INCREMENT PRIMARY KEY;

-- Overall attrition rate

SELECT 
SUM(CASE WHEN Attrition = 'Yes' THEN 1 else 0 END) as count_yes,
SUM(CASE WHEN Attrition = 'No' THEN 1 else 0 END) as count_no,
COUNT(*) as total_employees,
(SUM(CASE WHEN Attrition = 'Yes' THEN 1 else 0 END) *100/ COUNT(*)) as attrition_rate_perc
FROM hr_employee;

![image](https://github.com/user-attachments/assets/b453897b-7bcb-4b70-bb48-0333c2d5e9c6)

-- Attrition rate for male and female

SELECT 
gender,
SUM(CASE WHEN Attrition = 'Yes' THEN 1 else 0 END) as count_yes,
SUM(CASE WHEN Attrition = 'No' THEN 1 else 0 END) as count_no,
COUNT(*) as total_employees,
(SUM(CASE WHEN Attrition = 'Yes' THEN 1 else 0 END) *100/ COUNT(*)) as attrition_rate_perc
FROM hr_employee
GROUP BY gender;

![image](https://github.com/user-attachments/assets/475a552c-a633-4a87-aa9d-5ed8c146e792)

-- Attrition rate for department

SELECT 
department,
SUM(CASE WHEN Attrition = 'Yes' THEN 1 else 0 END) as count_yes,
SUM(CASE WHEN Attrition = 'No' THEN 1 else 0 END) as count_no,
COUNT(*) as total_employees,
(SUM(CASE WHEN Attrition = 'Yes' THEN 1 else 0 END) *100/ COUNT(*)) as attrition_rate_perc
FROM hr_employee
GROUP BY department;

![image](https://github.com/user-attachments/assets/c0fe60d1-3cbf-4be6-b35f-4ceb60c5edbf)


