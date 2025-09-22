
## Objective
To understand and apply ER modeling concepts by creating ER diagrams for real-world applications.

## Purpose
Gain hands-on experience in designing ER diagrams that represent database structure including entities, relationships, attributes, and constraints.

---

# Scenario A: City Fitness Club Management

**Business Context:**  
FlexiFit Gym wants a database to manage its members, trainers, and fitness programs.

**Requirements:**  
- Members register with name, membership type, and start date.  
- Each member can join multiple programs (Yoga, Zumba, Weight Training).  
- Trainers assigned to programs; a program may have multiple trainers.  
- Members may book personal training sessions with trainers.  
- Attendance recorded for each session.  
- Payments tracked for memberships and sessions.

### ER Diagram:
*Paste or attach your diagram here*


### Entities and Attributes

| Entity | Attributes (PK, FK) | Notes |
|--------|--------------------|-------|
|        |                    |       |
|        |                    |       |
|        |                    |       |
|        |                    |       |
|        |                    |       |

### Relationships and Constraints

| Relationship | Cardinality | Participation | Notes |
|--------------|------------|---------------|-------|
|              |            |               |       |
|              |            |               |       |
|              |            |               |       |

### Assumptions
- 
- 
- 

---

# Scenario B: City Library Event & Book Lending System

**Business Context:**  
The Central Library wants to manage book lending and cultural events.

**Requirements:**  
- Members borrow books, with loan and return dates tracked.  
- Each book has title, author, and category.  
- Library organizes events; members can register.  
- Each event has one or more speakers/authors.  
- Rooms are booked for events and study.  
- Overdue fines apply for late returns.

### ER Diagram:
*Paste or attach your diagram here*  
![ER Diagram](er_diagram_library.png)

### Entities and Attributes

| Entity | Attributes (PK, FK) | Notes |
|--------|--------------------|-------|
|        |                    |       |
|        |                    |       |
|        |                    |       |
|        |                    |       |
|        |                    |       |

### Relationships and Constraints

| Relationship | Cardinality | Participation | Notes |
|--------------|------------|---------------|-------|
|              |            |               |       |
|              |            |               |       |
|              |            |               |       |

### Assumptions
- 
- 
- 

---

# Scenario C: Restaurant Table Reservation & Ordering

**Business Context:**  
A popular restaurant wants to manage reservations, orders, and billing.

**Requirements:**  
- Customers can reserve tables or walk in.  
- Each reservation includes date, time, and number of guests.  
- Customers place food orders linked to reservations.  
- Each order contains multiple dishes; dishes belong to categories (starter, main, dessert).  
- Bills generated per reservation, including food and service charges.  
- Waiters assigned to serve reservations.

### ER Diagram:
[DBMS-workshop.pdf](https://github.com/user-attachments/files/22460365/DBMS-workshop.pdf)

### Entities and Attributes

| Entity          | Attributes (PK, FK)                                                               | Notes                                                |
| --------------- | --------------------------------------------------------------------------------- | ---------------------------------------------------- |
| **Customer**    | CustomerID (PK), Name, Contact                                                    | A customer may make multiple reservations            |
| **Reservation** | ReservationID (PK), Date, Time, NumGuests, FK CustomerID, FK TableID, FK WaiterID | Reservation links customer, table, and waiter        |
| **Table**       | TableID (PK), Capacity                                                            | Each reservation is assigned a table                 |
| **Waiter**      | WaiterID (PK), Name                                                               | Waiters serve multiple reservations                  |
| **Order**       | OrderID (PK), DateTime, FK ReservationID                                          | Orders are tied to reservations                      |
| **Dish**        | DishID (PK), Name, Category, Price                                                | Dishes belong to categories (starter, main, dessert) |
| **Order\_Dish** | FK OrderID, FK DishID, Quantity                                                   | Resolves M\:N relationship between orders and dishes |
| **Bill**        | BillID (PK), Amount, ServiceCharge, Date, FK ReservationID                        | One bill generated per reservation                   |


### Relationships and Constraints

| Relationship         | Cardinality | Participation             | Notes                                          |
| -------------------- | ----------- | ------------------------- | ---------------------------------------------- |
| Customer–Reservation | 1\:N        | Total on Reservation side | A customer can make multiple reservations      |
| Reservation–Table    | 1:1         | Total                     | A reservation is assigned to exactly one table |
| Reservation–Waiter   | 1\:N        | Partial                   | A waiter can serve many reservations           |
| Reservation–Order    | 1\:N        | Total                     | Each reservation may have multiple orders      |
| Order–Dish           | M\:N        | Total                     | An order can include many dishes               |
| Reservation–Bill     | 1:1         | Total                     | One bill generated per reservation             |


### Assumptions

Walk-in customers are recorded as reservations with immediate Date/Time.
Each reservation corresponds to exactly one bill.
A table can only be assigned to one reservation per time slot.
Waiters can serve multiple reservations, but each reservation has only one waiter assigned.
---

## Instructions for Students

1. Complete **all three scenarios** (A, B, C).  
2. Identify entities, relationships, and attributes for each.  
3. Draw ER diagrams using **draw.io / diagrams.net** or hand-drawn & scanned.  
4. Fill in all tables and assumptions for each scenario.  
5. Export the completed Markdown (with diagrams) as **a single PDF**
