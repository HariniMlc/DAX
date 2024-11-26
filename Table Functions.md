# Table Functions

## Basic functions that work on full tables

### FILTER
- **Description**: Returns a table that represents a subset of another table or expression.
- **Example**: 
  ```DAX
  FILTER(Sales, Sales[Quantity] > 10)
  ```
  This example filters the `Sales` table to include only rows where the `Quantity` is greater than 10.

### ALL
- **Description**: Returns all the rows in a table or all the values in a column, ignoring any filters that might have been applied.
- **Example**: 
  ```DAX
  ALL(Products)
  ```
  This example returns all rows from the `Products` table, ignoring any filters.

### VALUES
- **Description**: Returns a one-column table that contains the distinct values from the specified column.
- **Example**: 
  ```DAX
  VALUES(Products[Category])
  ```
  This example returns a table with distinct categories from the `Products` table.

### DISTINCT
- **Description**: Returns a one-column table that contains the distinct values from the specified column or table.
- **Example**: 
  ```DAX
  DISTINCT(Sales[ProductID])
  ```
  This example returns a table with distinct product IDs from the `Sales` table.

### RELATEDTABLE
- **Description**: Returns a table that is related to the current row.
- **Example**: 
  ```DAX
  RELATEDTABLE(Sales)
  ```
  This example returns the rows from the `Sales` table that are related to the current row in another table.

Their result is often used in other functions
They can be combined together to form complex expressions

We will discover many other table functions later in the course

# Calculated Tables
Virtual tables created using DAX formulas in Power BI.

### Steps to Create a Calculated Table:

1. **Open Power BI Desktop**.
2. **Navigate to the Data View**.
3. **Select New Table** from the Calculations group.
4. **Enter your DAX formula** in the formula bar.

### Example DAX Formula:

```DAX
Western Region Employees = UNION('Northwest Employees', 'Southwest Employees')
```

This will create a new table named `Western Region Employees` that combines the data from both `Northwest Employees` and `Southwest Employees`.

You can now use this new table just like any other table in Power BI. You can create relationships with other tables, add measures and calculated columns, and use it in your reports and visualizations



# The FILTER Function
### FILTER
- **Description**: Adds a new condition, restricts the number of rows of a table, returns a table, and can be iterated by an «X» function.
- **Requirements**: Needs a table as input. The input can be another FILTER.
- **Example**: 
  ```DAX
  FILTER(Sales, Sales[Quantity] > 10)
  ```

# The ALL Function
### ALL
- **Description**: Returns all the rows of a table, ignores the filter context, returns a table, and can be iterated by an «X» function.
- **Requirements**: Needs a table as input. Can be used with a single column.
- **Example**: 
  ```DAX
  ALL(Customers[CustomerName])
  ```
  The result contains a table with one column.

# Mixing Filters
- Table functions can be mixed.
- Each one requires a table.
- Each one returns a table.
- **Example**: 
  ```DAX
  FILTER(ALL(Table), Condition)
  ```
  Puts a filter over the entire table, ignoring the current filter context.

# DISTINCT
- **Description**: Returns the distinct values of a column, only the ones visible in the current context.
- **Example**: 
  ```DAX
  NumOfProducts := COUNTROWS(DISTINCT(Product[ProductCode]))
  ```

# RELATEDTABLE
- **Description**: Returns a table with all the rows related to the current one.
- **Example**: Compute the number of red products for a category. Build a calculated column in the Categories table:
  ```DAX
  NumOfRedProducts := COUNTROWS(
    FILTER(
      RELATEDTABLE(Product),
      Product[Color] = "Red"
    )
  )
  ```
