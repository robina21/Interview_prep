# Dimension and Fact Tables

## 1️⃣ Fact Tables

Contain **measurable, quantitative data**.

| Attribute | Description |
|------------|-------------|
| **Grain** | Level of detail (e.g., one row per sale) |
| **Foreign Keys** | Links to dimension tables |
| **Measures** | Numeric values (e.g., sales_amount, units_sold) |

**Example:**
| sale_id | date_key | product_key | customer_key | sales_amount |
|----------|-----------|-------------|---------------|---------------|
| 1 | 20231001 | 11 | 501 | 250.00 |

---

## 2️⃣ Dimension Tables

Contain **descriptive attributes** related to facts.

| Attribute | Description |
|------------|-------------|
| **Primary Key** | Unique identifier (used in fact tables) |
| **Attributes** | Non-measurable, descriptive info |

**Example:**
| customer_key | customer_name | region |
|---------------|---------------|---------|
| 501 | Alice | West Coast |

---

## 3️⃣ Relationship

Fact tables reference multiple dimension tables via foreign keys.  
Dimensions provide *context*, facts provide *metrics*.

---

## 4️⃣ Summary

| Type | Data Type | Example | Size |
|------|------------|----------|------|
| **Fact Table** | Quantitative | Sales, Revenue | Large |
| **Dimension Table** | Qualitative | Customer, Product | Small |
