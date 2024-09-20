# Database Mapping: One-to-One Relationships

## Degrees of Relations in ERD

In Entity-Relationship Diagrams (ERD), we have three degrees of relations:

1. **Binary** (3 cases)
   - One-to-One (3 cases)
   - One-to-Many (2 cases)
   - Many-to-Many (1 case)
2. **Ternary** (1 case)
3. **Unary** (1 case)

## Binary One-to-One Relationships

### Case 1: Total Participation from Both Sides

In this case, each entity in both related entity sets must participate in the relationship.

#### Example: Employee and Computer

Scenario: Each employee has exactly one computer, and each computer is assigned to exactly one employee.

##### Approach 1: Single Table

We can combine both entities into a single table:

| Employee_ID (PK) | Employee_Name | Computer_ID | Computer_Name |
|------------------|---------------|-------------|---------------|
| E001             | John Doe      | C001        | Dell XPS      |
| E002             | Jane Smith    | C002        | MacBook Pro   |

**Advantages:**
- Good performance for queries involving both entities
- Ensures total participation

**Considerations:**
- Choose the primary key based on the more dominant entity (e.g., Employee_ID)

##### Approach 2: Separate Tables

We might use two tables in cases where:
- We want to avoid null values
- We need to prevent data duplication

**Employee Table:**

| Employee_ID (PK) | Employee_Name |
|------------------|---------------|
| E001             | John Doe      |
| E002             | Jane Smith    |

**Computer Table:**

| Computer_ID (PK) | Computer_Name | Employee_ID (FK) |
|------------------|---------------|-------------------|
| C001             | Dell XPS      | E001              |
| C002             | MacBook Pro   | E002              |

**Note:** The foreign key in the Computer table ensures the one-to-one relationship.

### Other Cases of One-to-One Relationships

1. Partial participation from one side
2. Optional participation from both sides

These cases introduce the possibility of null values and require careful consideration in the database design.

---

## Next Steps

In the following sections, we'll explore:
- One-to-Many relationships
- Many-to-Many relationships
- Ternary relationships
- Unary relationships

We'll discuss their characteristics, mapping strategies, and provide examples for each case.
