# Use Case: Data Wrangling

## Objective

Give the AI tool a messy, real-world-like data challenge and ask it to clean, transform, and merge datasets. Tests pandas proficiency, handling of edge cases, and ability to produce analysis-ready data.

## The Task

You have three messy CSV files that need to be combined and cleaned. Create these files or use the specifications below to generate them:

### File 1: `sales.csv`
```
order_id,customer_name,product,amount,date,region
1001,John Smith,Widget A,49.99,01/15/2024,Northeast
1002,jane doe,Widget B,$75.50,2024-01-16,northeast
1003,JOHN SMITH,Widget A,49.99,Jan 17 2024,NE
1004,Sarah Connor,Widget C,120.00,2024/01/18,West
1005,,Widget B,75.50,2024-01-19,Southeast
1006,Bob Wilson,Widget A,-49.99,2024-01-20,Northeast
1007,Jane Doe,Widget D,0,01-21-2024,
```

### File 2: `customers.csv`
```
name,email,signup_date,tier
John Smith,john@email.com,2023-06-15,Gold
Jane Doe,jane@email.com,2023-07-20,Silver
Sarah Connor,sarah@email.com,2023-08-01,Gold
Bob Wilson,bob@email.com,N/A,Bronze
Tom Jones,tom@email.com,2023-09-10,Silver
```

### File 3: `products.csv`
```
product_name,category,cost,margin
Widget A,Electronics,25.00,0.50
Widget B,Electronics,40.00,0.47
Widget C,Home,60.00,0.50
Widget D,Home,NULL,NULL
```

### Cleaning Requirements

1. **Standardize names**: Consistent casing, handle duplicates (John Smith = JOHN SMITH)
2. **Fix dates**: Parse all date formats into a standard format
3. **Clean amounts**: Remove $ signs, handle negatives and zeros
4. **Standardize regions**: NE = Northeast, etc.
5. **Handle missing values**: Fill or flag appropriately
6. **Merge all three tables** into one analysis-ready dataset
7. **Add computed columns**: profit per order, customer lifetime value

## Acceptance Criteria

- [ ] All three files are merged correctly
- [ ] Name matching works across different casings
- [ ] All date formats are parsed into consistent datetime
- [ ] Dollar signs and invalid amounts are handled
- [ ] Region names are standardized
- [ ] Missing values are handled with a documented strategy
- [ ] Output is a clean, analysis-ready DataFrame

## Suggested Prompt

> "I have three messy CSV files that need to be cleaned and merged into one analysis-ready dataset. Sales data has inconsistent dates, names, and amounts. Customer data has missing values. Product data has NULLs. Clean everything up, merge them, and add profit calculations."

## What to Observe

- Does it handle all the data quality issues or miss some?
- How does it approach name matching (exact after normalization, fuzzy)?
- Does it parse all date formats correctly?
- How does it handle the negative amount and zero amount?
- Does it document its cleaning decisions?
- Does it validate the output (row counts, null checks after merge)?
- Is the pandas code idiomatic or clunky?
