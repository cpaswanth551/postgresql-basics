
---

# SQL Basics - README  

This guide contains essential SQL queries to help you manage and interact with tables in a relational database. Below are examples of creating tables, inserting data, filtering, updating, and deleting records.

---

## 1. **Creating a Table**  
Create a table named `studentTB` with three columns: `id`, `name`, and `address`.  
```sql
CREATE TABLE studentTB (
    id SERIAL PRIMARY KEY,  
    name VARCHAR(50) NOT NULL,  
    address VARCHAR(350)
);
```
- **`SERIAL`**: Automatically increments the value for the `id` column.  
- **`PRIMARY KEY`**: Ensures each `id` value is unique.  
- **`NOT NULL`**: The `name` column must have a value.

---

## 2. **Inserting Data into the Table**  
Add records to the `studentTB` table.  
```sql
INSERT INTO studentTB (name, address) VALUES ('Aswanth', 'Address here');
```

---

## 3. **Retrieving Data (SELECT Queries)**  

### 3.1. Select All Records in Ascending Order  
```sql
SELECT * FROM studentTB ORDER BY name;
```

### 3.2. Select All Records in Descending Order  
```sql
SELECT * FROM studentTB ORDER BY name DESC;
```

### 3.3. Select Specific Columns with a Limit  
Retrieve only `name` values, limited to the first 2 results.  
```sql
SELECT name FROM studentTB LIMIT 2;
```

### 3.4. Skip Rows Using OFFSET  
Skip the first 2 rows and retrieve the rest.  
```sql
SELECT * FROM studentTB OFFSET 2;
```

### 3.5. Filter Records by ID  
Get the student with `id = 2`.  
```sql
SELECT * FROM studentTB WHERE id = 2;
```

### 3.6. Use OR Condition in Filtering  
Retrieve students with `id = 2` or `name = 'Sanjay'`.  
```sql
SELECT * FROM studentTB WHERE id = 2 OR name = 'Sanjay';
```

### 3.7. Use AND Condition in Filtering  
Retrieve students where both `id = 2` and `name = 'Sanjay'`.  
```sql
SELECT * FROM studentTB WHERE id = 2 AND name = 'Sanjay';
```

---

## 4. **Modifying the Table**  

### 4.1. Add a New Column  
```sql
ALTER TABLE studentTB ADD std INTEGER;
```

### 4.2. Update Column Values  
Set the value of the `std` column to `5` for all records.  
```sql
UPDATE studentTB SET std = 5;
```

Update the `std` value to `12` only for the student with `id = 2`.  
```sql
UPDATE studentTB SET std = 12 WHERE id = 2;
```

---

## 5. **Deleting Data and Dropping Tables**  

### 5.1. Truncate the Table  
Removes all records but keeps the table structure intact.  
```sql
TRUNCATE TABLE studentTB;
```

### 5.2. Delete All Records  
Similar to `TRUNCATE`, but this query logs each deletion.  
```sql
DELETE FROM studentTB;
```

### 5.3. Drop the Table  
Completely removes the table from the database.  
```sql
DROP TABLE studentTB;
```

---

## Summary  

| **Operation**         | **Query Example**                                 | **Description**                                          |
|-----------------------|---------------------------------------------------|----------------------------------------------------------|
| Create Table          | `CREATE TABLE studentTB(...)`                     | Creates a new table with columns.                        |
| Insert Data           | `INSERT INTO studentTB VALUES(...)`               | Inserts new data into the table.                         |
| Select with Filter    | `SELECT * FROM studentTB WHERE id = 2`            | Retrieves specific records based on conditions.          |
| Update Data           | `UPDATE studentTB SET std = 12 WHERE id = 2`      | Modifies data in specific rows.                          |
| Delete Records        | `DELETE FROM studentTB`                           | Removes all records from the table.                      |
| Truncate Table        | `TRUNCATE TABLE studentTB`                        | Empties the table while keeping the structure.           |
| Drop Table            | `DROP TABLE studentTB`                            | Deletes the table permanently from the database.         |

---

