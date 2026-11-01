# Primary Key vs Foreign Key vs Candidate Key

## Example table
**students** (`student_id`, `email`, `phone`, `name`, `dept_id`)

## Diagram
```mermaid
flowchart TB
    SK["Super key: any set of columns that uniquely identifies a row"] --> CK["Candidate key: a minimal super key, with no extra column"]
    CK --> PK["Primary key: the one candidate key you choose"]
    CK --> AK["Alternate key: the candidate keys you did not choose"]
    FK["Foreign key: a column that points to the primary key of another table"] -.-> PK
```

## Explained in 5 lines
1. A **super key** is any column set that uniquely identifies rows (for example `student_id`, or `student_id + name`).
2. A **candidate key** is a *minimal* super key. In the example, `student_id` and `email` could both be candidate keys.
3. The **primary key** is the one candidate key you pick. It must be unique and **never NULL**, and a table has only one. The rest are **alternate keys**.
4. A **foreign key** is a column in one table that refers to the primary key of another (`students.dept_id` points to `departments.dept_id`), which enforces **referential integrity**.
5. A **composite key** uses more than one column together, and a **unique key** enforces uniqueness but, unlike the primary key, can allow a NULL.

## Common interview questions
- Difference between primary key and unique key?
- What is a candidate key? How is it different from a super key?
- What is a foreign key and what is referential integrity?
- Can a table have more than one primary key? Can a primary key be NULL?
- What are ON DELETE CASCADE and SET NULL?

## Revision cheat-line
> Candidate keys are the contestants, the primary key is the winner, and a foreign key is a pointer to another table's winner.
