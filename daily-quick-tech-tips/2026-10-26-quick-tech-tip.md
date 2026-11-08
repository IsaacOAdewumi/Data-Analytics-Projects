# Quick Tech Tip | Data Analytics & Statistical Insights

**QUICK TECH TIP #1**

**Today's Topic:** Preserve unmatched rows when filtering a `LEFT JOIN`

**The Tip:** If your report must include every customer—including those without a completed order—put the order-status condition in the `ON` clause. A condition on the right-hand table in `WHERE` can remove the `NULL` rows created for customers without a match.

**Practical Example:** Illustrative SQL; assume `orders.status` identifies completed orders.

```sql
SELECT c.customer_id, c.customer_name, o.order_id
FROM customers AS c
LEFT JOIN orders AS o
  ON o.customer_id = c.customer_id
 AND o.status = 'completed';
```

Customers with no completed order remain in the result with a `NULL` `order_id`. Customers with multiple completed orders can still appear on multiple rows.

**Why It Matters:** This prevents undercounting in customer coverage, retention, and research cohort analyses.

**Common Mistake to Avoid:** Adding `WHERE o.status = 'completed'` and expecting customers without a match to remain.

**Try It Yourself:** Compare the customer count here with a version that puts the status filter in `WHERE`.

**Engagement Question:** Where have you used a `LEFT JOIN` to preserve records with no match?

*Practical data skills. Better analysis. Smarter decisions.*

**Hashtags:** #SQL #DataAnalytics #ResearchMethods
