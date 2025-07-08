# Data Catalog for Gold Layer

## Overview
The Gold Layer is the business-level data representation, structured to support analytical and reporting use cases. It consists of **dimension tables** and **fact tables** for specific business metrics.

---

### 1. **gold.dim_customers**
- **Purpose:** Stores customer details enriched with demographic and geographic data.
- **Columns:**

| Column Name      | Data Type     | Description                                                                                   | Example               |
|------------------|---------------|-----------------------------------------------------------------------------------------------|-----------------------|
| customer_key     | INT           | Surrogate key uniquely identifying each customer record in the dimension table.               | 1                     |
| customer_id      | INT           | Unique numerical identifier assigned to each customer.                                        | 11000                 |
| customer_number  | NVARCHAR(50)  | Alphanumeric identifier representing the customer, used for tracking and referencing.         | AW00011000            |
| first_name       | NVARCHAR(50)  | The customer's first name, as recorded in the system.                                         | Jon                   |
| last_name        | NVARCHAR(50)  | The customer's last name or family name.                                                      | Yang                  |
| country          | NVARCHAR(50)  | The country of residence for the customer.                                                    | Australia             |
| marital_status   | NVARCHAR(50)  | The marital status of the customer.                                                           | 'Married', 'Single', 'n/a'  |
| gender           | NVARCHAR(50)  | The gender of the customer.                                                                   | 'Male', 'Female', 'n/a'     |
| birthdate        | DATE          | The date of birth of the customer, formatted as YYYY-MM-DD.                                   | 1971-10-06            |
| create_date      | DATE          | The date and time when the customer record was created in the system.                         | 2025-07-08            |

---

### 2. **gold.dim_products**
- **Purpose:** Provides information about the products and their attributes.
- **Columns:**

| Column Name         | Data Type     | Description                                                                                   | Example                    |
|---------------------|---------------|-----------------------------------------------------------------------------------------------|----------------------------|
| product_key         | INT           | Surrogate key uniquely identifying each product record in the product dimension table.        | 1                          |
| product_id          | INT           | A unique identifier assigned to the product for internal tracking and referencing.            | 210                        |
| product_number      | NVARCHAR(50)  | A structured alphanumeric code representing the product, often used for categorization or inventory. | FR-R92B-58          |
| product_name        | NVARCHAR(50)  | Descriptive name of the product, including key details such as type, color, and size.         | HL Road Frame - Black - 58 |
| category_id         | NVARCHAR(50)  | A unique identifier for the product's category, linking to its high-level classification.     | CO_RF                      |
| category            | NVARCHAR(50)  | The broader classification of the product to group related items.                             | Compnents                  |
| subcategory         | NVARCHAR(50)  | A more detailed classification of the product within the category, such as product type.      | Road Frames                |
| maintenance_required| NVARCHAR(50)  | Indicates whether the product requires maintenance.                                           | Yes                        |
| cost                | INT           | The cost or base price of the product, measured in monetary units.                            | 885                        |
| product_line        | NVARCHAR(50)  | The specific product line or series to which the product belongs.                             | Road                       |
| start_date          | DATE          | The date when the product became available for sale or use, stored in.                        | 2003-07-01                 |    

---

### 3. **gold.fact_sales**
- **Purpose:** Stores transactional sales data for analytical purposes.
- **Columns:**

| Column Name     | Data Type     | Description                                                                                   | Example                    |
|-----------------|---------------|-----------------------------------------------------------------------------------------------|----------------------------|
| order_number    | NVARCHAR(50)  | A unique alphanumeric identifier for each sales order.                                        | SO54496                    |
| product_key     | INT           | Surrogate key linking the order to the product dimension table.                               | 20                         |
| customer_key    | INT           | Surrogate key linking the order to the customer dimension table.                              | 10769                      |
| order_date      | DATE          | The date when the order was placed.                                                           | 2010-12-29                 |
| shipping_date   | DATE          | The date when the order was shipped to the customer.                                          | 2011-01-05                 |
| due_date        | DATE          | The date when the order payment was due.                                                      | 2011-01-10                 |
| sales_amount    | INT           | The total monetary value of the sale for the line item, in whole currency units.              | 50                         |
| quantity        | INT           | The number of units of the product ordered for the line item.                                 | 2                          |
| price           | INT           | The price per unit of the product for the line item, in whole currency units.                 | 25                         |
