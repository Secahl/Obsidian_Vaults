## Retrieving Hidden Data


Consider a shopping application that displays products in different categories. When the user clicks on the Gifts category, their browser requests the URL:  
	
https://insecure-website.com/products?category=Gifts  

This causes the application to make an SQL query to retrieve details of the relevant products from the database:  
SELECT * FROM products WHERE category = 'Gifts' AND released = 1