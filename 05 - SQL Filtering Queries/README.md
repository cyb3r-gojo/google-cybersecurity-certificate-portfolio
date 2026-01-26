# 05 – SQL Filtering Queries
## Project Description
In this activity, I used SQL to filter, analyze, and retrieve specific information from authentication and employee datasets. These queries demonstrate how to extract meaningful insights from tables, identify suspicious login activity, and filter employees based on department or geographic attributes. This task showcases my ability to apply conditional filtering, logical operators, and date-based queries in SQL.
## 1. Retrieve After-Hours Failed Login Attempts
**Objective:**
To identify failed login attempts occurring outside standard business hours (after 18:00 and before 08:00).

There was a potential security incident that occurred after business hours (after 18:00). All after hours login attempts that failed need to be investigated.

The **following code** demonstrates how I created a SQL query to filter for failed login attempts that occurred after business hours.
```
SELECT *
FROM log_in_attempts
WHERE login_time > '18:00' AND success = FALSE;
```
**Output:**
    
  <img width="780" height="403" alt="Screenshot 2026-01-26 at 3 56 02 PM" src="https://github.com/user-attachments/assets/bd07a1dd-e981-4b3a-a2a4-c8733e5dac60" />

This query filters for failed login attempts that occurred after 18:00. 
First, I started by selecting all data from the ```log_in_attempts``` table. Then, I used a ```WHERE``` clause with an ```AND``` operator to filter my results to output only login attempts that occurred after 18:00 and were unsuccessful. The first condition is ```login_time > '18:00'```, which filters for the login attempts that occurred after 18:00. The second condition is ```success = FALSE```, which filters for the failed login attempts.

## 2. Retrieve Login Attempts on Specific Dates
A suspicious event occurred on 2022-05-09. Any login activity that happened on 2022-05-09 or on the day before needs to be investigated.

The **following code** demonstrates how I created a SQL query to filter for login attempts that occurred on specific dates.

```
SELECT * 
FROM log_in_attempts 
WHERE login_date = '2022-05-09' OR login_date = '2022-05-08';
```
**Output:**

<img width="392" height="668" alt="Screenshot 2026-01-26 at 4 08 29 PM" src="https://github.com/user-attachments/assets/ccabb2fa-d848-4ea8-95c7-c6984d21a8fe" />

 This query returns all login attempts that occurred on 2022-05-09 or 2022-05-08. First, I started by selecting all data from the ```log_in_attempts``` table. Then, I used a ```WHERE``` clause with an ```OR``` operator to filter my results to output only login attempts that occurred on either 2022-05-09 or 2022-05-08. The first condition is ```login_date = '2022-05-09'```, which filters for logins on 2022-05-09. The second condition is ``` login_date = '2022-05-08'```, which filters for logins on 2022-05-08.

## 3. Retrieve Login Attempts Outside of Mexico

After investigating the organization’s data on login attempts, I believe there is an issue with the login attempts that occurred outside of Mexico. These login attempts should be investigated.

The **following code** demonstrates how I created a SQL query to filter for login attempts that occurred outside of Mexico. 

```
 SELECT * 
 FROM log_in_attempts
 WHERE NOT country LIKE 'MEX%';
```

**Output:**

<img width="173" height="667" alt="Screenshot 2026-01-26 at 4 15 45 PM" src="https://github.com/user-attachments/assets/020c6823-42b5-48b3-a4e0-e7cf53eef001" />

This query returns all login attempts that occurred in countries other than Mexico. First, I started by selecting all data from the ```log_in_attempts``` table. Then, I used a ```WHERE``` clause with ```NOT``` to filter for countries other than Mexico. I used ```LIKE``` with ```MEX%``` as the pattern to match because the dataset represents Mexico as ```MEX``` and ```MEXICO```. The percentage sign (```%```) represents any number of unspecified characters when used with ```LIKE```. 

## 4. Retrieve Employees in Marketing

My team wants to update the computers for certain employees in the Marketing department. To do this, I have to get information on which employee machines to update.

The **following code** demonstrates how I created a SQL query to filter for employee machines from employees in the Marketing department in the East building

```
SELECT *
FROM employees
WHERE department = 'Marketing' AND office LIKE 'EAST%';
```
**Output:**

<img width="582" height="188" alt="Screenshot 2026-01-26 at 4 20 58 PM" src="https://github.com/user-attachments/assets/bd3a827f-3288-47f1-a411-3096f09298b9" />

This query returns all employees in the Marketing department in the East building. First, I started by selecting all data from the ```employees``` table. Then, I used a ```WHERE``` clause with ```AND``` to filter for employees who work in the ```Marketing``` department and in the ```East``` building. I used ```LIKE``` with ```East%``` as the pattern to match because the data in the ```office``` column represents the East building with the specific office number. The first condition is the ```department = 'Marketing'``` portion, which filters for employees in the Marketing department. The second condition is the ```office LIKE 'East%'``` portion, which filters for employees in the East building.

## 5. Retrieve Employees in Finance or Sales

The machines for employees in the Finance and Sales departments also need to be updated. Since a different security update is needed, I have to get information on employees only from these two departments.

The **following code** demonstrates how I created a SQL query to filter for employee machines from employees in the Finance or Sales departments.

```
SELECT * 
FROM employees 
WHERE department = 'Finance' OR department = 'Sales';
```

**Output:**

<img width="306" height="634" alt="Screenshot 2026-01-26 at 4 25 40 PM" src="https://github.com/user-attachments/assets/b7475caa-5cad-4a2d-a2b2-7b8304d7df51" />

This query returns all employees in the Finance and Sales departments. First, I started by selecting all data from the ```employees``` table. Then, I used a ```WHERE``` clause with ```OR``` to filter for employees who are in the Finance and Sales departments. I used the ```OR``` operator instead of ```AND``` because I want all employees who are in either department. The first condition is ```department = 'Finance'```, which filters for employees from the Finance department. The second condition is ```department = 'Sales'```, which filters for employees from the Sales department.

## 6. Retrieve All Employees Not in IT

My team needs to make one more security update on employees who are not in the Information Technology department. To make the update, I first have to get information on these employees.

The **following code** demonstrates how I created a SQL query to filter for employee machines from employees not in the  Information Technology department.

```
SELECT *
FROM employees
WHERE NOT department = 'Information Technology';
```
**Output:**

<img width="148" height="741" alt="Screenshot 2026-01-26 at 4 35 11 PM" src="https://github.com/user-attachments/assets/221fe614-9c0c-4357-9073-3fa21a357cd7" />

The query returns all employees not in the Information Technology department. First, I started by selecting all data from the ```employees``` table. Then, I used a ```WHERE``` clause with ```NOT``` to filter for employees not in this department.

## Summary

I applied filters to SQL queries to get specific information on login attempts and employee machines. I used two different tables, ```log_in_attempts``` and ```employees```. I used the ```AND```, ```OR```, and ```NOT``` operators to filter for the specific information needed for each task. I also used ```LIKE``` and the percentage sign (```%```) wildcard to filter for patterns.
