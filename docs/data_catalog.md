# 📘 Data Dictionary for Gold Layer  

## Overview  
The **Gold Layer** is the business-level data representation, structured to support analytical and reporting use cases.  
It consists of **dimension tables** and **fact tables** for specific business metrics.  

---

## 1. 🧑‍🤝‍🧑 gold.dim_customers  

**Purpose:** Stores customer details enriched with demographic and geographic data.  

**Columns:**  

| **Column Name**   | **Data Type**   | **Description**                                                                 |
|-------------------|----------------|---------------------------------------------------------------------------------|
| **customer_key**  | INT            | Surrogate key uniquely identifying each customer record in the dimension table. |
| **customer_id**   | INT            | Unique numerical identifier assigned to each customer.                          |
| **customer_number** | NVARCHAR(50) | Alphanumeric identifier representing the customer, used for tracking and referencing. |
| **first_name**    | NVARCHAR(50)   | The customer’s first name, as recorded in the system.                           |
| **last_name**     | NVARCHAR(50)   | The customer’s last name or family name.                                        |
| **country**       | NVARCHAR(50)   | The country where the customer resides.                                         |
| **marital_status**| NVARCHAR(20)   | The marital status of the customer (e.g., Single, Married).                     |
| **gender**        | NVARCHAR(10)   | The gender of the customer (Male/Female).                                       |
| **birth_date**    | DATE           | The date of birth of the customer.                                              |
| **create_date**   | DATE           | The date the record was created in the system.                                  |

---

## 2. 📦 gold.dim_product  

**Purpose:** Stores product-related information, including hierarchy, category, and lifecycle details.  

**Columns:**  

| **Column Name**   | **Data Type**   | **Description**                                                                 |
|-------------------|----------------|---------------------------------------------------------------------------------|
| **product_key**   | INT            | Surrogate key uniquely identifying each product record in the dimension table.  |
| **product_id**    | INT            | Unique identifier for the product.                                              |
| **product_number**| NVARCHAR(50)   | Alphanumeric identifier representing the product.                               |
| **product_name**  | NVARCHAR(100)  | The descriptive name of the product.                                            |
| **category_id**   | NVARCHAR(20)   | Identifier for the product category.                                            |
| **category**      | NVARCHAR(50)   | Product category name (e.g., Components, Bikes).                                |
| **subcategory**   | NVARCHAR(50)   | Subdivision of the product category (e.g., Road Frames, Mountain Bikes).        |
| **maintenance**   | NVARCHAR(5)    | Indicates whether the product requires maintenance (Yes/No).                    |
| **cost**          | DECIMAL(18,2)  | Standard cost of the product.                                                   |
| **product_line**  | NVARCHAR(50)   | Product line to which the product belongs (e.g., Road, Mountain).               |
| **start_date**    | DATE           | The date the product became available.                                          |

---

## 3. 📊 gold.fact_sales  

**Purpose:** Stores sales transaction details, linking customers and products with order and financial information.  

**Columns:**  

| **Column Name**   | **Data Type**   | **Description**                                                                 |
|-------------------|----------------|---------------------------------------------------------------------------------|
| **order_number**  | NVARCHAR(20)   | Unique identifier for the sales order.                                          |
| **product_key**   | INT            | Foreign key linking to the `gold.dim_product` table.                            |
| **customer_key**  | INT            | Foreign key linking to the `gold.dim_customers` table.                          |
| **order_date**    | DATE           | The date when the sales order was created.                                      |
| **shipping_date** | DATE           | The date when the product was shipped to the customer.                          |
| **due_date**      | DATE           | The expected delivery due date for the order.                                   |
| **sales_amount**  | DECIMAL(18,2)  | Total monetary amount of the sales order.                                       |
| **quanity**       | INT            | Number of units sold in the order.                                              |
| **price**         | DECIMAL(18,2)  | Price of a single unit of the product.                                          |

---
