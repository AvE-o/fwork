#检索数据
SELECT

SELECT cust_id
FROM Customers;

SELECT DISTINCT prod_id
FROM OrderItems;

SELECT cust_id, cust_name 
FROM Customers;

SELECT cust_name
FROM Customers
ORDER BY cust_name DESC

SELECT cust_id, order_num
FROM Orders
ORDER BY cust_id, order_date DESC

SELECT quantity, item_price
FROM OrderItems
ORDER BY quantity DESC, item_price DESC

SELECT vend_name
FROM Vendors
ORDER BY vend_name DESC

#过滤数据
WHERE

SELECT prod_id, prod_name
FROM Products
WHERE prod_price = 9.49

SELECT prod_id, prod_name
FROM Products
WHERE prod_price >= 9


SELECT prod_name, prod_price
FROM Products
WHERE prod_price BETWEEN 3 AND 6
ORDER BY prod_price

SELECT order_num
FROM OrderItems
GROUP BY order_num
HAVING SUM(quantity) >= 100

#高级数据过滤
AND / OR

SELECT vend_name
FROM Vendors
WHERE vend_country = 'USA' AND vend_state = 'CA'


SELECT order_num, prod_id, quantity
FROM OrderItems
//WHERE prod_id IN ('BR01', 'BR02', 'BR03') AND quantity >= 100
WHERE prod_id = 'BR01' OR 'BR02' OR 'BR03' AND quantity >= 100

SELECT prod_name, prod_price
FROM Products
WHERE prod_price BETWEEN 3 AND 6
ORDER BY prod_price ASC

SELECT vend_name
FROM Vendors
WHERE vend_country = 'USA' AND vend_state = 'CA'
ORDER BY vend_name

#通配符
和LIKE 共用
'%'
'_'






