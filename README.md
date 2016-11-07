<!--
Example Answer = How many books are in the books table? 200 SELECT COUNT(*) FROM books;

#1)How many users are there?
Answer = 50
Command = SELECT COUNT(*) FROM users;


#2)What are the 5 most expensive items?
Answer =
9984 Small Cotton Gloves
9859 Small Wooden Comput
9790 Awesome Granite Pan
9390 Sleek Wooden Hat   
9341 Ergonomic Steel Car
Command - select price,title from items order by price desc;


#3)What's the cheapest book? (Does that change for "category is exactly 'book'" versus "category contains 'book'"?)
Answer - 1496 Ergonomic Granite Cha
Command - select price,title,category from items where category like '%books%';
Change? - No.


#4)Who lives at "6439 Zetta Hills, Willmouth, WY"? Do they have another address?
Answer - User_id 40 = Corrine Little (Knew it was Corrine by select * from users and looking for id of 40)
Command - select street, user_id from addresses where street like '%6439%';
                    plus
    select addresses.street, users.first_name, users.last_name from addresses inner join users on addresses.user_id=users.id where user_id=40;
2nd address? - Yes


#5)Correct Virginie Mitchell's address to "New York, NY, 10108".
I looked up Virginie's id by: select users.id,  users.first_name, users.last_name from users where first_name='Virginie';
To correct her address I did:
Command - update addresses set city='New York', zip='10108' where id=41;


#6)How much would it cost to buy one of each tool?
Answer - 46477
Command -  select sum(items.price) from items where category like '%tools%';
sum(items.price)

#7)How many total items did we sell?
Answer - 2125
Command - select sum(orders.quantity) from orders;

#8)How much was spent on books?
Answer - 420566  
I found out the id and price for books by = select orders.id, orders.item_id, orders.quantity, items.category, items.price from orders inner join items on orders.item_id=items.id where category like 'books';
Then I found out the price for each by = select sum (orders.quantity * items.price) as total from orders inner join items on orders.item_id=items.id where category like 'books';

#9)Simulate buying an item by inserting a User for yourself and an Order for that User.
Insert User -
insert into users values (51, 'Brian', 'McMillan', 'brianm_91@hotmail.com');
sqlite> select * from users;

Insert Order -
insert into orders values (400, 1000, 1000, 5, datetime());
sqlite> select * from orders;
 -->
