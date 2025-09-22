1. select * from users;
2. SELECT * FROM `users` WHERE created_at like '%2024%';
3. select * from users where gender ='female'and age < 30;
4. select * from products;
5. select users.name as '氏名', orders.order_date as '注文日' from users join orders on users.id = orders.id;
6.select products.product_name, order_items.quantity, products.price, products.price* order_items.quantity from order_items join products on products.id = order_items.id group by products.product_name;
7.select users.name, order_items.quantity from order_items join users on users.id = order_items.id group by users.name;
8. select users.name as '氏名', products.price*order_items.quantity as '総購入金額' from products join order_items on products.id=order_items.product_id join users on users.id = order_items.order_id;
9. SELECT users.name AS '氏名', SUM(products.price * order_items.quantity) AS '総購入金額' FROM products JOIN order_items ON products.id = order_items.product_id JOIN orders ON orders.id=order_items.order_id JOIN users ON users.id= orders.user_id WHERE '総合購入金額' =( SELECT MIN('総合購入金額') FROM users );
10. select products.product_name as '製品名', SUM(order_items.quantity) from order_items join products on order_items.product_id=products.id GROUP BY products.product_name;
11. select users.name as ‘氏名’, 
12. SELECT order_id FROM order_items GROUP BY order_id HAVING COUNT(product_id) >= 2;
13. select users.name as 'TVを購入した人'from users join order_items on users.id=order_items.order_id WHERE order_items.product_id=1;
14. SELECT orders.order_date as '注文日', users.name as '氏名', products.product_name as'商品名', order_items.quantity as '数量', products.price * order_items.quantity as '合計金額' FROM users JOIN order_items ON users.id = order_items.order_id JOIN products ON order_items.product_id = products.id JOIN orders ON users.id = orders.user_id GROUP BY orders.id;
15. select products.product_name as '最も多く購入された商品' from products join order_items on order_items.product_id=products.id HAVING SUM(quantity) order by order_items.product_id desc limit 1;
16. SELECT DATE_FORMAT(orders.order_date, '%Y-%m') as Month, COUNT(*) FROM orders GROUP BY Month;
17.SELECT * FROM `products` WHERE NOT EXISTS(select 1 from order_items where order_items.product_id=products.id);
18.create INDEX new_idx on order_items(product_id);→構造のインデックスから確認可
19. select users.name as ‘氏名’, AVG(→何に対しての平均？？？？
20.SELECT users.name, MAX(orders.order_date) from users JOIN orders on users.id=orders.user_id GROUP BY users.name;
21. INSERT into users (id, name, age, gender,created_at)values (6,’中村愛’,25,’female’,’2025-06-01’);
22. INSERT into products (id,product_name,price)values(6,’エアコン’,60000);
23. Insert into orders (id,user_id,order_date)values(7,1,'2025-06-10');
24. insert into order_items (id,order_id,product_id,quantity)values(10,10,6,1);
25. update users set age=24 where id=4;
26. update products set price=price*1.1;
27. update orders set order_date='2024-05-01' where order_date like '2024-05-__';
28. delete from users where name=‘高橋健一’;
29. delete from order_items where order_id=5;
30.DELETE FROM products WHERE NOT EXISTS(SELECT 1 from order_items WHERE products.id=order_items.product_id);