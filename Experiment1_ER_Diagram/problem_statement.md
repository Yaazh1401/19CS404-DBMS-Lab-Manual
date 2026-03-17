# ER Diagram Workshop – Submission Template

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

![ER Diagram](https://github.com/Yaazh1401/19CS404-DBMS-Lab-Manual/blob/main/Experiment1_ER_Diagram/tr.jpeg?raw=true)

### Entities and Attributes

| Entity | Attributes (PK, FK) | Notes |
|--------|--------------------|-------|
|  Member      |  ID(pk),name,membership type                  |       |
|Program        |  Program id(pk),program name                        |       |
|  trainer      |     name,contact no,experience               |       |
| session       |    date,day,trainer name                |       |
|payment         |   name,date,amount                 |       |
|  attendance      |   date,status                 |       |

### Relationships and Constraints

| Relationship | Cardinality | Participation | Notes |
|--------------|------------|---------------|-------|
| member - payment             |  one-to-many          |   makes            |       |
| member-program             |  many-to-many          |   register            |       |
|  program-trainer            |  many-to-many          |  assigns             |       |
|  trainer-session            |  one-to-many          |  conducts             |       |
|   session-attendance           |  one-to-many          | records              |       |

### Assumptions
Each entity (Member, Program, Trainer) has a unique identifier, even if not explicitly shown.

A member can register for multiple programs and make multiple payments.

A trainer can handle multiple programs and sessions, but each session has only one trainer.

Attendance is recorded for each member in each session with status (Present/Absent).

Many-to-many relationships (Member–Program, Program–Trainer) are handled using junction tables.

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
![ER Diagram](https://github.com/Yaazh1401/19CS404-DBMS-Lab-Manual/blob/main/Experiment1_ER_Diagram/lb.jpeg?raw=true)

### Entities and Attributes

| Entity | Attributes (PK, FK) | Notes |
|--------|--------------------|-------|
| members       |     Id (Primary Key), Name, Email, Phone               |       |
| book       |  Title, Author, Category                    |       |
|   Event      | Id (Primary Key), Name, Type, Date                   |       |
|  speaker      |   Id (Primary Key), Name, Bio                   |       |
| room       |  Name, Capacity, Type                  |       |

### Relationships and Constraints

| Relationship | Cardinality | Participation | Notes |
|--------------|------------|---------------|-------|
| Members— Book             |  many-to-many          |   Borrow               |       |
| members-event             |  many-to-many          | registration              |       |
|event-speaker              |  many-to-many          |  has             |       |
| event-room             |  one-to-many          |  booked for             |       |

### Assumptions
Each main entity (Members, Event, Speaker) has a unique ID, and Room Name is treated as unique.

A member can borrow multiple books, and a book can be borrowed by multiple members over time.

A member can register for multiple events, and each event can have many members.

An event can have multiple speakers, and a speaker can participate in multiple events.

Each event is assigned to one room, but a room can host multiple events at different times.

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
![ER Diagram](https://github.com/Yaazh1401/19CS404-DBMS-Lab-Manual/blob/main/Experiment1_ER_Diagram/res.jpeg?raw=true)

### Entities and Attributes

| Entity | Attributes (PK, FK) | Notes |
|--------|--------------------|-------|
| customer       |   customer_id (Primary Key), name                  |       |
|reservation        |   reservation_id (Primary Key), customer_id (Foreign Key), waiter_id (Foreign Key), date, time, num_of_customers                   |       |
|waiter        |  waiter_id (Primary Key), name                  |       |
| order       |ord_id (Primary Key), reservation_id (Foreign Key), dish_id (Foreign Key), quantity                     |       |
|  dish      |dish_id (Primary Key), ord_id, category_id (Foreign Key), name, price                     |       |
| dish category       |  category_id (Primary Key), name, category                    |       |
| bill       |   bill_id (Primary Key), reservation_id (Foreign Key), ord_id (Foreign Key), total_amount, food_and_service_charge                   |       |

### Relationships and Constraints

| Relationship | Cardinality | Participation | Notes |
|--------------|------------|---------------|-------|
| customer-reservation             |   one-to-many           |  Makes             |       |
| waiter-reservation             |   one-to-many           |  Serves             |       |
| reservation-order             | one-to-many           |   Has             |       |
|  order-dish            |  many-to-many          | Include              |       |
| dish-dish category             |  one-to-many          | Classify               |       |
| reservation-bill             |one-to-one            |  Generates             |       |
|order-bill              |  one-to-one          |  Calculates             |       |


### Assumptions
Each entity has a unique primary key, and all foreign keys correctly reference related entities.

A customer can make multiple reservations, but each reservation is linked to one customer and one waiter.

A reservation can have multiple orders, and each order can include multiple dishes (handled using a junction table).

Each dish belongs to one category, and a category can contain many dishes.

Each reservation generates one bill, calculated based on its orders, maintaining a 1:1 relationship.

## Instructions for Students

1. Complete **all three scenarios** (A, B, C).  
2. Identify entities, relationships, and attributes for each.  
3. Draw ER diagrams using **draw.io / diagrams.net** or hand-drawn & scanned.  
4. Fill in all tables and assumptions for each scenario.  
5. Export the completed Markdown (with diagrams) as **a single PDF**
