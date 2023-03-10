# SQL-LEETCODE

SQL - BIG COUNTRY


| Column Name | Type    |
|-------------|---------|
| name        | varchar |
| continent   | varchar |
| area        | int     |
| population  | int     |
| gdp         | int     |


name is the primary key column for this table.
Each row of this table gives information about the name of a country, the continent to which it belongs, its area, the population, and its GDP value.

A country is big if:

it has an area of at least three million (i.e., 3000000 km2), or
it has a population of at least twenty-five million (i.e., 25000000).
Write an SQL query to report the name, population, and area of the big countries.

Return the result table in any order.

The query result format is in the following example.

 

Example 1:

Input: 
World table:

| name        | continent | area    | population | gdp          |
|-------------|-----------|---------|------------|--------------|
| Afghanistan | Asia      | 652230  | 25500100   | 20343000000  |
| Albania     | Europe    | 28748   | 2831741    | 12960000000  |
| Algeria     | Africa    | 2381741 | 37100000   | 188681000000 |
| Andorra     | Europe    | 468     | 78115      | 3712000000   |
| Angola      | Africa    | 1246700 | 20609294   | 100990000000 |


Output: 


| name        | population | area    |
|-------------|------------|---------|
| Afghanistan | 25500100   | 652230  |
| Algeria     | 37100000   | 2381741 |

**Solution**
```sql

select name, population ,area from world
where area >='3000000' or population >='25000000';
```

1757. Recyclable and Low Fat Products

Table: Products


| Column Name | Type    |
|-------------|---------|
| product_id  | int     |
| low_fats    | enum    |
| recyclable  | enum    |
|-------------|---------|

product_id is the primary key for this table.
low_fats is an ENUM of type ('Y', 'N') where 'Y' means this product is low fat and 'N' means it is not.
recyclable is an ENUM of types ('Y', 'N') where 'Y' means this product is recyclable and 'N' means it is not.

Write an SQL query to find the ids of products that are both low fat and recyclable.

Return the result table in any order.

The query result format is in the following example.

Example 1:

Input: 
Products table:

| product_id  | low_fats | recyclable |
|-------------|----------|------------|
| 0           | Y        | N          |
| 1           | Y        | Y          |
| 2           | N        | Y          |
| 3           | Y        | Y          |
| 4           | N        | N          |

Output: 

| product_id  |
|-------------|
| 1           |
| 3           |

Explanation: Only products 1 and 3 are both low fat and recyclable.
**Solution**
```sql

SELECT PRODUCT_ID FROM PRODUCTS
WHERE LOW_FATS='Y' AND RECYCLABLE='Y';

```

584. Find Customer Referee

Table: Customer


| Column Name | Type    |
|------------|----------|
| id          | int     |
| name        | varchar |
| referee_id  | int     |

id is the primary key column for this table.
Each row of this table indicates the id of a customer, their name, and the id of the customer who referred them.

Write an SQL query to report the names of the customer that are not referred by the customer with id = 2.

Return the result table in any order.

The query result format is in the following example.

Input: 
Customer table:

| id | name | referee_id |
|---|------|------------|
| 1  | Will | null       |
| 2  | Jane | null       |
| 3  | Alex | 2          |
| 4  | Bill | null       |
| 5  | Zack | 1          |
| 6  | Mark | 2          |

Output: 

| name |
|------|
| Will |
| Jane |
| Bill |
| Zack |

***SQL SOLUTION
```
SELECT NAME FROM CUSTOMER WHERE REFEREE_ID <>2 OR REFEREE_ID IS NULL;

```

BASIC SQL QUERY

183. Customers Who Never Order

Table: Customers


| Column Name | Type    |
|-------------|---------|
| id          | int     |
| name        | varchar |


id is the primary key column for this table.
Each row of this table indicates the ID and name of a customer.
 

Table: Orders

| Column Name | Type |
|-------------|------|
| id          | int  |
| customerId  | int  |

id is the primary key column for this table.
customerId is a foreign key of the ID from the Customers table.
Each row of this table indicates the ID of an order and the ID of the customer who ordered it.
 

Write an SQL query to report all customers who never order anything.

Return the result table in any order.

The query result format is in the following example.

 

Example 1:

Input: 
Customers table:

| id | name  |
|----|-------|
| 1  | Joe   |
| 2  | Henry |
| 3  | Sam   |
| 4  | Max   |

Orders table:

| id | customerId |
|----|------------|
| 1  | 3          |
| 2  | 1          |

Output: 

| Customers |
|-----------|
| Henry     |
| Max       |

***SQL SOLUTION
```
    select name  as customers from customers left join orders on customers.id=orders.customerid
    where customerid is null; 
```
BASIC SQL QUERY

Table: Employees


| Column Name | Type    |
|-------------|---------|
| employee_id | int     |
| name        | varchar |
| salary      | int     |

employee_id is the primary key for this table.
Each row of this table indicates the employee ID, employee name, and salary.
 

Write an SQL query to calculate the bonus of each employee. The bonus of an employee is 100% of their salary if the ID of the employee is an odd number and the employee name does not start with the character 'M'. The bonus of an employee is 0 otherwise.

Return the result table ordered by employee_id.

The query result format is in the following example.

 

Example 1:

Input: 
Employees table:

| employee_id | name    | salary |
|-------------|---------|--------|
| 2           | Meir    | 3000   |
| 3           | Michael | 3800   |
| 7           | Addilyn | 7400   |
| 8           | Juan    | 6100   |
| 9           | Kannon  | 7700   |

Output: 
| employee_id | bonus |
|-------------|--------|
| 2           | 0     |
| 3           | 0     |
| 7           | 7400  |
| 8           | 0     |
| 9           | 7700  |

Explanation: 
The employees with IDs 2 and 8 get 0 bonus because they have an even employee_id.
The employee with ID 3 gets 0 bonus because their name starts with 'M'.
The rest of the employees get a 100% bonus.

***SQL SOLUTION
```
*/SELECT EMPLOYEE_ID ,
CASE
WHEN EMPLOYEE_ID % 2=0 THEN 0
WHEN SUBSTRING(NAME,1,1)='M' THEN 0
ELSE SALARY END AS BONUS
FROM EMPLOYEES
ORDER BY EMPLOYEE_ID ;
```
