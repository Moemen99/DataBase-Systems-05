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

[Content remains the same as in the previous version]

### Case 2: Partial Participation from One Side

In this case, one entity has total participation while the other has partial (optional) participation.

#### Example: Employee and Computer (Employee is optional)

Scenario: Every computer must be assigned to an employee, but not every employee needs to have a computer.

##### Approach: Separate Tables

We use two separate tables to avoid null values in the mandatory side.

**Employee Table:**

| Employee_ID (PK) | Employee_Name |
|------------------|---------------|
| E001             | John Doe      |
| E002             | Jane Smith    |
| E003             | Bob Johnson   |

**Computer Table:**

| Computer_ID (PK) | Computer_Name | Employee_ID (FK) |
|------------------|---------------|-------------------|
| C001             | Dell XPS      | E001              |
| C002             | MacBook Pro   | E002              |

**Note:** 
- The foreign key is in the "total" participation table (Computer).
- Some employees may not have a computer (e.g., E003).
- Every computer must be assigned to an employee.

### Case 3: Optional Participation from Both Sides

In this case, participation is optional for both entities. This typically requires a third table to represent the relationship.

#### Example: Employee and Car

Scenario: An employee may or may not own a car, and a car may or may not be owned by an employee.

##### Approach: Three Tables

**Employee Table:**

| Employee_ID (PK) | Employee_Name |
|------------------|---------------|
| E001             | John Doe      |
| E002             | Jane Smith    |

**Car Table:**

| Car_ID (PK) | Car_Type    |
|-------------|-------------|
| C001        | Sedan       |
| C002        | SUV         |

**Employee_Car Table:**

| Employee_ID (FK, PK) | Car_ID (FK) |
|----------------------|-------------|
| E001                 | C002        |

**Notes:**
- The Employee_Car table represents the relationship.
- Either Employee_ID or Car_ID can be the primary key of the Employee_Car table.
- An employee will appear at most once in the Employee_Car table.
- A car will appear at most once in the Employee_Car table.

## Summary of One-to-One Relationships

1. **Total from both sides:** Can use a single table or two tables with a foreign key in either.
2. **Partial from one side:** Use two tables, with the foreign key in the "total" participation table.
3. **Optional from both sides:** Use three tables, with a separate table for the relationship.

As the degree of optionality increases, the number of tables typically increases to maintain data integrity and avoid null values.

---

## Next Steps

In the following sections, we'll explore:
- One-to-Many relationships
- Many-to-Many relationships
- Ternary relationships
- Unary relationships

We'll discuss their characteristics, mapping strategies, and provide examples for each case.
