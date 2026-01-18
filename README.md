
# Food Pickup Mobile App - Database Architecture 🍔

**Role:** Database Architect
**Project Type:** Team-Based Mobile Application (Flutter & MySQL)
**Focus:** Relational Design, Data Integrity, Business Logic

### 📄 Project Overview
A multi-user food ordering platform designed to connect university vendors with students and staff. My primary role was **Database Architect**, responsible for designing the structural blueprint that handles high-volume orders, inventory management, and complex user permissions.

This repository showcases the **architectural designs** and **logic definitions** behind the system.

### 📊 System Architecture (See Diagrams)

#### 1. Entity Relationship Diagram (ERD)
*(Please view `ERD_Diagram.png` in the file list)*
I designed a **Normalized (3NF)** schema to ensure data consistency. Key relationships include:
* **One-to-Many:** One Restaurant $\rightarrow$ Many Menu Categories $\rightarrow$ Many Items.
* **Many-to-Many:** Orders utilize a flexible association between Users and Menu Items to allow for customized baskets.

#### 2. Relational Model
*(Please view `Relational_Model.png` in the file list)*
Detailed schema definition including Primary Keys (PK), Foreign Keys (FK), and strict data typing to prevent storage errors.

### 🧠 Core Business Logic Designed
*Instead of simple CRUD operations, I architected the database to enforce specific business rules:*

* **User Segmentation (Dynamic Pricing):**
    * The schema distinguishes between `Student` and `Staff` roles.
    * Logic was defined to automatically trigger a **15% discount** calculation when a `Staff` ID is associated with a new order.
* **Temporal Constraints (Operating Hours):**
    * Restaurants have defined `opening_time` and `closing_time` fields.
    * The system logic prevents `Order_Creation` transactions if the timestamp falls outside these bounds.
* **Order State Machine:**
    * Orders are restricted to specific status transitions to ensure integrity (e.g., an order cannot move from `Pending` directly to `Completed` without passing through `Accepted` and `Ready`).
    * Vendor actions (Accept/Cancel) trigger real-time status updates in the `Orders` table.

---
*Note: This repository serves as a design portfolio showcasing the backend architecture. The implementation was part of a larger team codebase.*
