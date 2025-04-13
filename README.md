# library-schema
Library Schema Extension – SQL Take-Home Challenge

This project extends a basic library database schema by introducing Categories with a many-to-many relationship between books and categories. The schema is normalized up to **3NF (Third Normal Form)** to ensure minimal redundancy and strong relational structure.

Schema Design

# Tables Added:

categories
  - `id` (SERIAL PRIMARY KEY)
  - `name` (VARCHAR)

- **book_categories** *(Join Table for Many-to-Many)*
  - `book_id` (INTEGER, FOREIGN KEY referencing books(id))
  - `category_id` (INTEGER, FOREIGN KEY referencing categories(id))
  - **PRIMARY KEY** (`book_id`, `category_id`)

#Sample Data Inserted

Example categories added:
- Classic
- Dystopian
- Fiction

Books are associated with one or more categories via the `book_categories` table.
Example Query

sql
SELECT 
  b.title AS book_title,
  c.name AS category
FROM 
  books b
JOIN 
  book_categories bc ON b.id = bc.book_id
JOIN 
  categories c ON bc.category_id = c.id
ORDER BY 
  b.title;
