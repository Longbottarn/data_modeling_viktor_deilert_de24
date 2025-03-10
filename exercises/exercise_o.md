# Exercise 0

## 1. Hospital task

You have this json data, convert it into three tables: Hospital, Department and Doctor. Fill these tables with data. Do this manually and not programmatically.

```json
{
  "hospital": "Sjukhusstock",
  "address": "Drottninggatan 3, Stockholm",
  "departments": [
    {
      "name": "Kardiologi",
      "doctors": [
        { "id": 1, "name": "Dr. Abra Abrahamson" },
        { "id": 2, "name": "Dr. Erika Eriksson" }
      ]
    },
    {
      "name": "Neurologi",
      "doctors": [{ "id": 3, "name": "Dr. Sven Svensson" }]
    }
  ]
}
```

### Solution

Approach

- identify entities
- identify relationships and cardinalities
- create conceptual ERD
- create tables

**Initial naive coneptual ERD**

<img src = "../assets\initial_conceptual_model_ex1.png" width=400>

**Initial tables**

Hospital

| hospital_id | name         | adress          |
| ----------- | ------------ | --------------- |
| 1           | Sjukhusstock | Drottinggatan 3 |

Department

| department_id | name       |
| ------------- | ---------- |
| 1             | Kardiologi |
| 2             | Neurologi  |

Doctor

| doctor_id | name                |
| --------- | ------------------- |
| 1         | Dr. Abra Abrahamson |
| 2         | Dr. Erika Eriksson  |
| 3         | Dr. Sven Svensson   |

Refined with bridge tables to reflect many-to-many relationships

<img src ="../assets\conceptual_hospital_ex0_1.png" width=500>

HospitalDepartment

| hospital_department_id | hosptial_id | department_id |
| ---------------------- | ----------- | ------------- |
| 1                      | 1           | 1             |
| 2                      | 1           | 2             |

HospitalDoctor



DepartmentDoctor



Test a join

Want informattion on Sjukhussstock and its departments
- hospital_department can join with department_id on department table and hosptital_id on hospital_table
- query name from hopsital table and name from department table

---
## 2. Library Bookly

A library called Bookly keeps track of books and members who borrow them. Each book has a title, author, and ISBN number. Each member has a membership ID, name, and contact information. A member can borrow multiple books, but each book can be borrowed by only one member at a time.

a) Identify the entities and attributes for each entity.

b) Determine the relationship between member and books.

c) Draw a conceptual ERD using crow foots notation.

### Solution

a) Entities: 

**Book**
- ISBN
- title
- author

> [!NOTE]
> ISBN is a unique number for book, which could be used as a primary key, this will make it into a `natural key`

**Member**
- membership_id
- first_name
- last_name
- phone
- adress
- email

**Borrowing**
- borrowing_id
- ISBN
- membership_id
- return_date
- borrow_date


b)
- A Member can have zero or several Borrowings 
- A Borrowing can be made by one and only one Member
- A Borrowing is linked to one and only one Book
- A Book is linked to zero, one or more Borrowings

c)

Initial conceptual ERD

<img src = "../assets\Bookly_ex0_2_1.png" width=500>

<br>

Replaced many-to-many with a bridge table (composite enitity)

<img src = "../assets\Bookly_ex0_2_2.png" width=500>

## 3. Conceptual ERD to words

<img src="https://github.com/kokchun/assets/raw/main/data_modeling/car_rental.png?raw=true" alt="course structure" width="500" style="max-width: 100%;">

This is an ERD conceptual diagram that a database designer and the business stakeholders agreed upon in a car rental company called Carent.

course structure

a) Describe the entities in this conceptual ERD.

b) Write out the relationship labels.

c) Describe the relationships between the entities (one-to-many, one-to-one and many-to-many).

d) Define the relationship statement for example: "A Customer can have one or more Rentals".

### Solutions

a) 

- Customer is a person that can make a rental for cars.

- Car is the cars that can be rented by a person.

- Rental (Composite entity) is the transaction between customers and cars.

b) 

c) 

- Customer to Rental (one-to-many)
- Rental to Customer (many-to-one)
- Rental to Car (many-to-one)
- Car to Rental (one-to-many)

d)

- Customer makes one or more Rentals over time
- Each Rental is connected to one Customer
- Each Rental is for one Car
- Each Car can be in several Rentals


## 5. University management system

A university needs a system to manage students, courses, and professors.

each student can enroll in multiple courses.
each course is taught by one professor.
a teacher can teach multiple courses.
a) Identify entities and their relationships

b) Come up with possible attributes for the entities

c) Draw conceptual ERD with cardinalities

d) Define business rules (e.g. a student can enroll in max 4 courses)

