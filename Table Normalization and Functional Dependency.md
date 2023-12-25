[[MySQL Day Two]]
[[MySQL Day One]]
---
# Table Normalization
## Unnormalized Table
Known as flat or *denormalized* table. Contains redundant data, and has not been normalized according to the principles of normalization.

## Normalization
### 1NF
- eliminates data redundancy
- records must be atomic
- Records must contain exactly *ONE* value
### 2NF
- Table must be in 1st Normal Form
- Table should only have *ONE* primary key
### 3NF
- Table should be in 2NF
- Table should not have any functional dependencies
#### Functional Dependency
- When you change one column value, you must also change another column value
- To achieve 3NF, you must eliminate functional dependency by use of another table or any other means.