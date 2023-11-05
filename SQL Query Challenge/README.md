# SQL Query Challenge

## Description

In the given database on MS SQL Server, there are products and categories. A single product can belong to many categories, and a single category can have many products. Write an SQL query to select all pairs of "Product Name – Category Name". If a product doesn't have any categories, its name should still be displayed.


## Solution

To address the database requirement where a single product can belong to many categories, and a single category can have many products, we implement a many-to-many relationship. This is achieved by introducing a junction table that links products and categories.

Here is a diagram representing the relationship between products and categories in a database:
<br><br>
![Database Relationship Diagram](https://kroki.io/graphviz/svg/eNqdjzELwjAQhff-iiOrWnCtxMXBxUFci8iZHE2wJuGsitT-d1tIKVVEcHt8j-8dp23BGAysoU6A0Z20ZbnZLRJwXhPkF4OBJJPyrPct3bLXV1VBXuKRSinqCJ4TsDoD67rk8EwZ3JCVQW5E562wosLzYxB78suMBw6fC-9N64eIhkUVyx6NRmG2_L4_T1MnpoDM_m4ItRSqTeNv_vObF0yFgWA=)
<br><br>
The following SQL query selects all pairs of "Product Name – Category Name". It ensures that even products without categories are included in the results:
<br><br>

```sql
SELECT p.name AS 'Product Name', c.name AS 'Category Name'
FROM Product p
LEFT JOIN Product_Category pc ON p.id = pc.product_id
LEFT JOIN Category c ON pc.category_id = c.id;
```

This query uses LEFT JOIN to include all products, even those without an associated category, by joining the Product table with the Product_Category junction table and then joining the Product_Category table with the Category table.