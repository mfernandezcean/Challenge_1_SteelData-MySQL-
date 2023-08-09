#  Car shop Challenge

![steveshowroom](https://github.com/mfernandezcean/Challenge_1_SteelData/assets/105746149/3178b4d0-c74b-4f7c-aa47-ca4518fa1c9c)


[Link to Steel Data Challenge](https://steeldata.org.uk/sql1.html)



**QUESTIONS:**
 1. What are the details of all cars purchased in the year 2022?
 2. What is the total number of cars sold by each salesperson?
 3. What is the total revenue generated by each salesperson?
 4. What are the details of the cars sold by each salesperson?
 5. What is the total revenue generated by each car type?
 6.  What are the details of the cars sold in the year 2021 by salesperson ‘Emily Wong’?
 7. What is the total revenue generated by the sales of hatchback cars?
 8. What is the total revenue generated by the sales of SUV cars in the year 2022?
 9. What is the name and city of the salesperson who sold the most number of cars in the year 2023?
 10. What is the name and age of the salesperson who generated the highest revenue in the year 2022? 

### Answers:

1-What are the details of all cars purchased in the year 2022?

SELECT *
FROM cars;

![vsdvds](https://github.com/mfernandezcean/Challenge_1_SteelData/assets/105746149/55a6ad29-004e-46a4-91e1-7ec8cec0f7fa)
--

2-What is the total number of cars sold by each salesperson?

SELECT s.salesman_id,
p.name,
COUNT(sale_id) AS Sales
FROM sales s 
LEFT JOIN salespersons p
ON p.salesman_id =s.salesman_id
GROUP BY 1,2;

![ascasca](https://github.com/mfernandezcean/Challenge_1_SteelData-MySQL-/assets/105746149/deac8fdc-854a-4dca-9b6c-f47ae200f212)
--
3-What is the total revenue generated by each salesperson?

        SELECT  s.salesman_id,
	       p.name,
          SUM(c.cost_$) as Profit_salesperson
        
        FROM sales s 
        LEFT JOIN salespersons p
        ON  p.salesman_id =s.salesman_id
        LEFT JOIN cars c
        ON s.car_id = c.car_id
        
        GROUP BY 1,2;

![qwwfqffwq](https://github.com/mfernandezcean/Challenge_1_SteelData-MySQL-/assets/105746149/360ac4ed-ed83-4de9-8b44-fc0183d434fd)
--
4-What are the details of the cars sold by each salesperson?

SELECT s.salesman_id,
p.name, 
c.car_id,
c.make,
c.type,
c.style,
c.cost_$
FROM sales s
LEFT JOIN cars c
ON s.car_id = c.car_id
LEFT JOIN salespersons p
ON s.salesman_id = p.salesman_id
ORDER BY s.salesman_id, c.car_id;

![wqfwqfwwqf](https://github.com/mfernandezcean/Challenge_1_SteelData-MySQL-/assets/105746149/cb4a17f6-7d27-4b46-b1f1-b4cf7466cd00)
