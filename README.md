# E-Commerce Order Management System (DBMS Tasks)

**Project Title:** E-Commerce Order Management Database System  
**Author:** Thirupathi M  
**Register Number:** C4S38023  
**Department:** B.Sc Artificial Intelligence (AI)  
**Academic Year:** 2024–2027  

---

## 📌 Project Overview
The **E-Commerce Order Management Database System** is a centralized relational database project designed to model, automate, and manage the complete lifecycle of customer orders in an e-commerce platform. It handles catalog organization, seller inventory tracking, order processing, payment transactions, customer reviews/ratings, and analytical SQL querying.

---

## 📁 Repository Structure & Completed Tasks

### 📄 Task 1: Software Requirement Specification (SRS)
* **File:** `Task 1 - Requirement specification document..docx`
* **Description:** Details the functional and non-functional requirements of the centralized E-Commerce Order Management System, covering order processing workflows, customer management, inventory control, and payment/shipment integrations.

### 📄 Task 2: Product & Category Module
* **File:** `Task 2 - Table Design.docx`
* **Description:** Focuses on the core catalog entities.
* **Key Schemas:**
  * `Category` (`CategoryID`, `CategoryName`)
  * `Product` (`ProductID`, `ProductName`, `CategoryID`, `Price`, `Stock`)

### 📄 Task 3: Seller & Inventory Management System
* **File:** `Task 3 - Seller and Inventory Management System.docx`
* **Description:** Manages multi-seller stock allocations and merchant contacts.
* **Key Schemas:**
  * `Seller` (`SellerID`, `SellerName`, `Phone`)
  * `Inventory` (`InventoryID`, `SellerID`, `ProductID`, `Stock`)

### 📄 Task 4: Order Management System
* **File:** `Task 4 - Order Management System.docx`
* **Description:** Handles customer purchases, line-item order details, and sales calculations.
* **Key Schemas:**
  * `Orders` (`OrderID`, `CustomerName`, `OrderDate`, `TotalAmount`)
  * `Order_Details` (`OrderDetailID`, `OrderID`, `ProductID`, `Quantity`)

### 📄 Task 5: Payment Transaction Management System
* **File:** `Task 5 - Payment Transaction Management System.docx`
* **Description:** Manages order payment transactions, payment modes (UPI, Card, Cash), and payment statuses (Success, Failed).
* **Key Schemas:**
  * `Payment` (`PaymentID`, `OrderID`, `PaymentMode`, `PaymentDate`, `PaymentStatus`, `Amount`)

### 📄 Task 6: Product Review & Rating Management System
* **File:** `Task 6 - Product Review and Rating Management System.docx`
* **Description:** Manages customer feedback, product review comments, and numerical ratings.
* **Key Schemas:**
  * `Review` (`ReviewID`, `ProductID`, `CustomerName`, `ReviewText`, `ReviewDate`)
  * `Rating` (`RatingID`, `ProductID`, `CustomerName`, `Rating`)

### 📄 Task 7: SQL Query Implementation for E-Commerce Database
* **File:** `Task 7 - SQL Query Implementation for E-Commerce Database.docx`
* **Description:** Implementation of essential SQL data retrieval queries using `SELECT`, `WHERE`, `ORDER BY`, `DISTINCT`, and `BETWEEN` operations across product catalog and transaction data.

---

## 🛠️ Complete Database Schema

```sql
-- Database Initialization
CREATE DATABASE Ecommerce;
USE Ecommerce;

-- 1. Category Table
CREATE TABLE Category (
    CategoryID INT PRIMARY KEY,
    CategoryName VARCHAR(50)
);

-- 2. Product Table
CREATE TABLE Product (
    ProductID INT PRIMARY KEY,
    ProductName VARCHAR(50),
    CategoryID INT,
    Price INT,
    Stock INT,
    FOREIGN KEY (CategoryID) REFERENCES Category(CategoryID)
);

-- 3. Seller Table
CREATE TABLE Seller (
    SellerID INT PRIMARY KEY,
    SellerName VARCHAR(50),
    Phone VARCHAR(15)
);

-- 4. Inventory Table
CREATE TABLE Inventory (
    InventoryID INT PRIMARY KEY,
    SellerID INT,
    ProductID INT,
    Stock INT,
    FOREIGN KEY (SellerID) REFERENCES Seller(SellerID),
    FOREIGN KEY (ProductID) REFERENCES Product(ProductID)
);

-- 5. Orders Table
CREATE TABLE Orders (
    OrderID INT PRIMARY KEY,
    CustomerName VARCHAR(50),
    OrderDate DATE,
    TotalAmount INT
);

-- 6. Order Details Table
CREATE TABLE Order_Details (
    OrderDetailID INT PRIMARY KEY,
    OrderID INT,
    ProductID INT,
    Quantity INT,
    FOREIGN KEY (OrderID) REFERENCES Orders(OrderID),
    FOREIGN KEY (ProductID) REFERENCES Product(ProductID)
);

-- 7. Payment Table
CREATE TABLE Payment (
    PaymentID INT PRIMARY KEY,
    OrderID INT,
    PaymentMode VARCHAR(20),
    PaymentDate DATE,
    PaymentStatus VARCHAR(20),
    Amount INT,
    FOREIGN KEY (OrderID) REFERENCES Orders(OrderID)
);

-- 8. Review Table
CREATE TABLE Review (
    ReviewID INT PRIMARY KEY,
    ProductID INT,
    CustomerName VARCHAR(50),
    ReviewText VARCHAR(200),
    ReviewDate DATE,
    FOREIGN KEY (ProductID) REFERENCES Product(ProductID)
);

-- 9. Rating Table
CREATE TABLE Rating (
    RatingID INT PRIMARY KEY,
    ProductID INT,
    CustomerName VARCHAR(50),
    Rating INT,
    FOREIGN KEY (ProductID) REFERENCES Product(ProductID)
);
```

---

## 📊 Useful SQL Queries (Task 7 Examples)

```sql
-- Display all products and specific columns
SELECT * FROM Product;
SELECT ProductName, Price FROM Product;

-- Filter products by price thresholds
SELECT * FROM Product WHERE Price > 10000;
SELECT * FROM Product WHERE Price < 5000;

-- Sort products by price ascending & descending
SELECT * FROM Product ORDER BY Price ASC;
SELECT * FROM Product ORDER BY Price DESC;

-- Get unique payment modes & categories
SELECT DISTINCT CategoryID FROM Product;
SELECT DISTINCT PaymentMode FROM Payment;

-- Search products in a specific price range
SELECT * FROM Product WHERE Price BETWEEN 1000 AND 30000;

-- Filter products by category
SELECT * FROM Product WHERE CategoryID = 1;
```

---

## 🚀 Future Scope & Roadmap for Upcoming Work

As the project evolves, the following modules and tasks are planned for future implementation:

* [ ] **Customer & User Account Management:** Dedicated `Customer` entity with authentication, password hashing, address book, and profile settings.
* [ ] **Shipment & Delivery Logistics Module:** Order tracking, courier assigning, dispatch status, and delivery schedules (`ShipmentID`, `TrackingNumber`, `DeliveryDate`).
* [ ] **Returns, Refunds & Customer Claims:** Workflow handling for order cancellations, return requests, and refund tracking.
* [ ] **Advanced SQL Analytics & Procedures:**
  * Complex relational `JOIN` queries for business intelligence and sales dashboards.
  * SQL Views for real-time inventory and top-selling product summaries.
  * Stored Procedures & Triggers for automated stock deduction upon payment confirmation (`PaymentStatus = 'Success'`).
  * Database Indexing on primary & foreign keys for high-concurrency query optimization.
* [ ] **Web Application & REST API Integration:** Building an interactive frontend UI (React/Next.js) connected to a backend REST API (Node.js/Express or Python/FastAPI) backed by this DBMS database.

---

## 📜 License & Usage
This repository is maintained for DBMS coursework and practical tasks under the B.Sc Artificial Intelligence program.
