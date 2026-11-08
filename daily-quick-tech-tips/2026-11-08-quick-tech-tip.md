Quick Tech Tip | Data Analytics & Statistical Insights

## QUICK TECH TIP #1

### Today's Topic
SQL: `COUNT(*)` vs `COUNT(column)` for spotting missing values.

### The Tip
`COUNT(*)` counts every row in the result. `COUNT(customer_id)` counts only rows where `customer_id` is not `NULL`. Compare them to see how many records lack a customer ID.

### Practical Example
Illustrative data: suppose an orders table has 6 rows, and 2 have no customer ID.

```sql
SELECT COUNT(*) AS total_rows,
       COUNT(customer_id) AS rows_with_customer_id,
       COUNT(*) - COUNT(customer_id) AS rows_missing_customer_id
FROM orders;
```

The result is 6 total rows, 4 with an ID, and 2 missing one. This assumes standard SQL aggregate behavior and no `WHERE` filter.

### Why It Matters
Checking completeness before reporting helps you spot data-quality gaps early and explain the denominator behind your metrics.

### Common Mistake to Avoid
`COUNT(customer_id)` does not count unique customers; duplicate IDs are counted repeatedly. For unique, non-`NULL` IDs, use `COUNT(DISTINCT customer_id)`. Also, `NULL` means unknown or absent—not zero or an empty string.

### Try It Yourself
Run the query on a table you use. Do the missing-ID rows represent genuinely unknown values, or a data-entry issue worth investigating?

### Engagement Question
What field do you check first when auditing a dataset for completeness?

### Hashtags
#SQL #DataAnalytics #DataQuality #BusinessIntelligence

Practical data skills. Better analysis. Smarter decisions.
