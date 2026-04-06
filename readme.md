# 📦 Instagram Thrift & Handmade Store – ER Diagram Documentation

## 📌 Overview

This project presents the Entity-Relationship (ER) diagram for a small-scale Instagram-based business that sells **thrifted fashion items** and **handmade products**. Initially, orders are managed through Instagram DMs and WhatsApp, but as the business grows, a structured database system becomes necessary.

The goal of this design is to create a **scalable and normalized database model** that efficiently manages products, inventory, customers, orders, payments, and shipping details.

---

## 🎯 Objectives

The ER diagram is designed to support the following:

* Maintain product catalog (thrift & handmade)
* Track available inventory
* Manage customer information
* Handle multiple orders per customer
* Support multiple items per order
* Store payment and shipping details
* Distinguish between unique and bulk products

---

## 🧩 Key Design Considerations

### 1. Thrift vs Handmade Products

* **Thrift Items**: Unique, single-piece items with individual conditions
* **Handmade Items**: Produced in multiple quantities

To handle this difference, the design separates:

* **Product (general info)**
* **Inventory (actual sellable units)**

---

### 2. Inventory Management

The **Inventory** entity allows:

* Multiple variations (size, color)
* Condition tracking (for thrift items)
* Quantity handling (bulk for handmade)

---

### 3. Order Handling

* A customer can place multiple orders
* Each order can contain multiple products
* This is implemented using a **junction table (Order_Item)**

---

## 🗂️ Entities and Attributes

### 🟦 Product

Stores general product details.

* product_id (PK)
* name
* description
* category
* type (thrift / handmade)
* base_price

---

### 🟦 Inventory

Represents actual stock units.

* inventory_id (PK)
* product_id (FK)
* quantity
* size
* color
* condition
* is_available

---

### 🟦 Customer

Stores customer details.

* customer_id (PK)
* name
* phone
* email
* address

---

### 🟦 Order

Represents a purchase transaction.

* order_id (PK)
* customer_id (FK)
* order_date
* total_amount
* payment_status
* shipping_status

---

### 🟦 Order_Item

Resolves many-to-many relationship between orders and products.

* order_item_id (PK)
* order_id (FK)
* inventory_id (FK)
* quantity
* price_at_purchase

---

### 🟦 Payment

Tracks payment information.

* payment_id (PK)
* order_id (FK)
* amount
* payment_method
* payment_status
* payment_date

---

### 🟦 Shipping

Stores delivery details.

* shipping_id (PK)
* order_id (FK)
* address
* shipped_date
* delivered_date
* status

---

## 🔗 Relationships

* One **Customer** can place many **Orders** (1:N)
* One **Order** can contain many **Order_Items** (1:N)
* One **Product** can have many **Inventory** entries (1:N)
* One **Inventory** item can appear in multiple **Order_Items** (1:N)
* One **Order** has one **Payment** (1:1)
* One **Order** has one **Shipping** record (1:1)

---

## 🧠 Normalization & Design Quality

* The database follows **normalization principles**
* Avoids data redundancy
* Separates concerns (product vs inventory vs orders)
* Supports scalability as business grows
* Handles both unique and bulk inventory efficiently

---

## 🚀 Future Enhancements

* Product image storage
* Discount and coupon system
* Return/refund management
* Order tracking via logistics integration
* Admin dashboard for analytics

---

## ✅ Conclusion

This ER diagram provides a **robust and flexible foundation** for managing an Instagram-based thrift and handmade store. It accurately models real-world business scenarios while maintaining clarity, scalability, and efficiency.

---
