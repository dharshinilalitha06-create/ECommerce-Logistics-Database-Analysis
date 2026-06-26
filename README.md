# E-Commerce Logistics Database Optimization & Financial Analytics

## 📌 Project Overview
This project simulates real-world supply chain and logistics analytics for an e-commerce retail store. The core objective is to audit fragmented relational databases, calculate core shipping distribution workloads, and evaluate financial revenue moving through different logistics channels.

## 🛠️ Tech Stack & Skills Used
- **Language:** SQL (Structured Query Language)
- **Database Architecture:** Relational Database Management Systems (RDBMS)
- **Advanced Techniques:** Multi-Table Table Joins (4-Table Chains), Grouped Aggregations (`GROUP BY`), Multi-Condition Math Calculations (`SUM(Quantity * Price)`), Column Aliasing (`AS`).

## 📊 Core Queries Developed & Documented

### 1. Multi-Table Supply Chain Verification Query
Chained three separate production sheets (`Orders`, `Customers`, and `Shippers`) together simultaneously using matching relational IDs to audit tracking workflows.
```sql
SELECT Orders.OrderID, Customers.CustomerName, Shippers.ShipperName
FROM Orders
INNER JOIN Customers ON Orders.CustomerID = Customers.CustomerID
INNER JOIN Shippers ON Orders.ShipperID = Shippers.ShipperID;
```

### 2. Logistics Workload Volume Analysis
Aggregated 196 transactional history rows to isolate total order distributions across active shipping channels, identifying relative vendor utilization rates.
```sql
SELECT Shippers.ShipperName, COUNT(Orders.OrderID) AS TotalOrdersProcessed
FROM Orders
INNER JOIN Shippers ON Orders.ShipperID = Shippers.ShipperID
GROUP BY Shippers.ShipperName;
```

### 3. Supply Chain Revenue Channel Mapping
Formulated a comprehensive 4-table join mapping financial lines from individual product inventory costs up to high-level logistics operators. 
```sql
SELECT Shippers.ShipperName, SUM(OrderDetails.Quantity * Products.Price) AS TotalRevenueUSD
FROM Orders
INNER JOIN Shippers ON Orders.ShipperID = Shippers.ShipperID
INNER JOIN OrderDetails ON Orders.OrderID = OrderDetails.OrderID
INNER JOIN Products ON OrderDetails.ProductID = Products.ProductID
GROUP BY Shippers.ShipperName;
```

## 📈 Key Business Insights Extracted
- **Volume Metrics:** Identified that shipping operations are distributed across a three-vendor tier. **Speedy Express** handles the minimum delivery load (54 orders), **Federal Shipping** commands a standard mid-tier steady-state volume (68 orders), and **United Package** leads overall operational capacity (74 orders).
- **Revenue Operations:** Verified that financial pipelines scale proportionally with order distribution, mapping **Federal Shipping** as the baseline median revenue channel for the company, capturing exactly **$135,587.52** in asset distributions.

---
*Developed as part of my B.Tech CSE (AI & Data Science) Portfolio at SASTRA Deemed University.*
