# E-Commerce Order Management System (DBMS Tasks)

**Project Title:** E-Commerce Order Management Database System  
**Author:** Thirupathi M  
**Register Number:** C4S38023  
**Department:** B.Sc Artificial Intelligence (AI)  
**Academic Year:** 2024–2027  

---

## 📌 Project Overview
The **E-Commerce Order Management Database System** is a centralized relational database project designed to model, automate, and manage the complete lifecycle of customer orders in an e-commerce platform. It handles everything from catalog organization, seller inventory tracking, to order placement and detail management.

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

---

## 🛠️ Database Schema Overview

```sql
-- Database Initialization
CREATE DATABASE Ecommerce;
USE Ecommerce;

-- Category Table
CREATE TABLE Category (
    CategoryID INT PRIMARY KEY,
    CategoryName VARCHAR(50)
);

-- Product Table
CREATE TABLE Product (
    ProductID INT PRIMARY KEY,
    ProductName VARCHAR(50),
    CategoryID INT,
    Price INT,
    Stock INT,
    FOREIGN KEY (CategoryID) REFERENCES Category(CategoryID)
);

-- Seller Table
CREATE TABLE Seller (
    SellerID INT PRIMARY KEY,
    SellerName VARCHAR(50),
    Phone VARCHAR(15)
);

-- Inventory Table
CREATE TABLE Inventory (
    InventoryID INT PRIMARY KEY,
    SellerID INT,
    ProductID INT,
    Stock INT,
    FOREIGN KEY (SellerID) REFERENCES Seller(SellerID),
    FOREIGN KEY (ProductID) REFERENCES Product(ProductID)
);

-- Orders Table
CREATE TABLE Orders (
    OrderID INT PRIMARY KEY,
    CustomerName VARCHAR(50),
    OrderDate DATE,
    TotalAmount INT
);

-- Order Details Table
CREATE TABLE Order_Details (
    OrderDetailID INT PRIMARY KEY,
    OrderID INT,
    ProductID INT,
    Quantity INT,
    FOREIGN KEY (OrderID) REFERENCES Orders(OrderID),
    FOREIGN KEY (ProductID) REFERENCES Product(ProductID)
);
```

---

## 🚀 Future Scope & Upcoming Tasks

As the project evolves, the following modules and tasks are planned for future implementation:

* [ ] **Customer & User Account Management:** Dedicated `Customer` entity with authentication, address book, and profile settings.
* [ ] **Payment & Transaction Module:** Payment gateway integration schemas (`PaymentID`, `PaymentMethod`, `TransactionStatus`).
* [ ] **Shipment & Delivery Logistics:** Order tracking, courier assigning, and dispatch status (`ShipmentID`, `TrackingNumber`, `DeliveryDate`).
* [ ] **Returns, Refunds & Claims:** Workflow handling for order cancellations, returns, and refund tracking.
* [ ] **Advanced SQL Operations:**
  * Complex relational `JOIN` queries for analytics and reporting.
  * SQL Views for order summary dashboards.
  * Stored Procedures & Triggers for automated stock deduction upon order confirmation.
  * Database Indexing for high-concurrency query optimization.
* [ ] **Web Application / API Integration:** Building a frontend UI (React/Next.js or HTML/JS) connected to a backend REST API backed by this MySQL/DBMS database.

---

## 📜 License & Usage
This repository is maintained for DBMS coursework and practical tasks under B.Sc Artificial Intelligence program.
