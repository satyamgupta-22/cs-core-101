# GROUP BY vs HAVING (and SQL Execution Order)

## Diagram
```mermaid
flowchart LR
    F["FROM / JOIN"] --> W["WHERE: filter rows"]
    W --> G["GROUP BY: make groups"]
    G --> H["HAVING: filter groups"]
    H --> S["SELECT: pick columns"]
    S --> O["ORDER BY"]
    O --> L["LIMIT"]
```

## Explained in 5 lines
1. **GROUP BY** collects rows with the same value into groups so you can use aggregate functions like `COUNT`, `SUM`, `AVG`, `MIN` and `MAX`.
2. **WHERE** filters **individual rows** *before* grouping, and it can't use aggregate functions.
3. **HAVING** filters **groups** *after* grouping, so it can use aggregates.
4. Example: departments with more than 5 employees, counting only employees earning over 30000:

```sql
SELECT dept_id, COUNT(*) AS total
FROM employees
WHERE salary > 30000
GROUP BY dept_id
HAVING COUNT(*) > 5;
```

5. The logical order is the diagram above. That is why you can't use a `SELECT` alias inside `WHERE` in standard SQL.

## Common interview questions
- Difference between WHERE and HAVING?
- Can we use HAVING without GROUP BY?
- Order of execution of a SQL query?
- Why can't aggregate functions be used in WHERE?
- What does COUNT(*) vs COUNT(column) do with NULLs?

## Revision cheat-line
> WHERE filters rows before grouping. HAVING filters groups after grouping.
