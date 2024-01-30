# Common Table Expression in SQL 


**Author**: Prashant Tripathi <br />
**Email**: Prashanttripathi2k24@gmail.com <br />
**LinkedIn**: https://www.linkedin.com/in/prashanttripathi786/  <br />


Common Table Expression is among the Most Asked Questions in the SQL Interview!

## What Exactly is a CTE?

CTE is a powerful feature in SQL that allows us to create temporary result sets, enhancing the readability and manageability of our queries.

## Why CTE?

**Readability** : CTEs make complex queries easier to understand by breaking them into smaller, logical components. And the Best way to get rid of Nested subqueries.

**Reuse**: We can reference the CTE multiple times in a query, promoting code reusability.

**Recursive Queries**: Perfect for scenarios involving hierarchical data structures.

## How to Learn and Practise?

Total we will watch two videos , Below is the First Video.

a) [CTE by Sumit Mittal](https://www.youtube.com/watch?v=zg9GNdX-Q9g&t=6s).

First watch the Above Video and Simulataneously copy the below script in Mysql or Sql Server to create Tables  to Practise the Question.

``` sql
CREATE TABLE Orders (
    order_id INT PRIMARY KEY,
    order_date DATE,
    order_customer_id INT,
    order_status VARCHAR(50)
);

INSERT INTO Orders (order_id, order_date, order_customer_id, order_status)
VALUES
    (1, '2024-01-30', 101, 'Shipped'),
    (2, '2024-02-15', 102, 'Processing'),
    (3, '2024-03-01', 103, 'Delivered'),
    (4, '2024-03-15', 101, 'Pending'),
    (5, '2024-04-01', 102, 'Shipped'),
    (6, '2024-04-15', 101, 'Processing'),
    (7, '2024-05-01', 102, 'Delivered'), 
    (8, '2024-05-15', 101, 'Pending'),
    (9, '2024-06-01', 109, 'Shipped'),
    (10, '2024-06-15', 102, 'Processing'),
    (11, '2024-07-01', 103, 'Delivered'), 
    (12, '2024-07-15', 102, 'Pending'),
    (13, '2024-08-01', 120, 'Shipped'),
    (14, '2024-08-15', 114, 'Processing'),
    (15, '2024-09-01', 115, 'Delivered'),
    (16, '2024-09-15', 109, 'Pending'),
    (17, '2024-10-01', 102, 'Shipped'),
    (18, '2024-10-15', 109, 'Processing'),
    (19, '2024-11-01', 101, 'Delivered'),
    (20, '2024-11-15', 120, 'Pending');

```
## Question - 1
1) Find out the total Number of Orders each customers has Placed.
2) Find out the Average number of Order Placed by each customer. (Average order Per Customer)
3) Find out the Premium Customers. (Customers who have Placed more number of orders than the Average order).

**Note** Try to Solve the above Questions firstly by using Subquery and then Using CTE.You will find that Using Cte is much easier and Helpful.

## Answers

<details>
  <summary>Click to See the Output of Question -1 </summary>

  ##### Expected Results:
order_customer_id| Total_orders |
------------     |--------------|
101              | 5            |
102	             | 6            |
103	             | 2            |
109	             | 3            |
114	             | 1            |
115	             | 1            |
120	             | 2            |


</details>
</p>

<details>
  <summary>Click to See the  Query for Question - 1 </summary>

``` sql
SELECT ORDER_CUSTOMER_ID, 
COUNT(*) AS Total_orders
FROM ORDERS
GROUP BY order_customer_id;

``` 

  </details>
</p>


<details>
    
  <summary>Click to See the Output of Question -2 </summary>

  Average_order_per_customer|
  --------------------------|
   2                        | 
                  
</details>
</p>


<details>
  <summary>Click to See the  Query for Question - 2 </summary>

  ``` sql
with Total_order (order_customer_id , total_orders) as 
(
SELECT ORDER_CUSTOMER_ID, 
COUNT(*) AS Total_orders
FROM ORDERS
GROUP BY order_customer_id)

select Avg(Total_orders) As Average_order_per_customer
from Total_order;
```

  </details>
</p>


<details>
    
  <summary>Click to See the Output of Question -3 </summary>

order_customer_id |	total_orders |	Average_order_per_customer |
  ----------------|  ------------|  -------------------------- |
101	              |5	         | 2                           |
102               |6	         | 2                           |
109	              |3	         | 2                           |

  </details>
</p>





