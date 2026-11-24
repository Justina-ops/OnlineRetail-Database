# Online Retail Order Fulfilment Database

An Oracle SQL and PL/SQL database project developed for UCCD2303 Database Technology at UTAR.

The project models an online retailer's order fulfilment process, covering customers, products, inventory, orders, payments and shipments.

## Technologies

- Oracle Database
- SQL
- PL/SQL
- SQL*Plus

## Database Design

The database contains 13 related tables and 131 sample records.

It includes:

- Primary and foreign keys
- Unique and check constraints
- A composite key for order items
- Separate tables for card, e-wallet and banking payments
- Separate tables for standard delivery and self-pickup

## Files and Contributions

| File | Purpose | Contributor |
| --- | --- | --- |
| `Database_setup.sql` | Creates tables, constraints and sample data | Group work |
| `payments.sql` | Payment queries, procedures and functions | Liew Jia Min |
| `order_customers.sql` | Customer order history, order updates and spending calculations | Leong Di Hao |
| `products_inventory.sql` | Product sales, stock reports and restocking operations | Ngu Jing Rong |
| `shipments.sql` | Shipment queries, employee assignment and delivery calculations | Yew Kai Qian |

## My Contributions

My individual module is `payments.sql`. It contains:

- A query showing completed payments with order and customer details.
- A query showing card payments and their card details.
- A procedure for adding an e-wallet payment.
- A procedure for displaying a customer's payment history.
- A function for counting completed payments by payment method.
- A function for retrieving the bank associated with an FPX payment.

## How to Run

Download the repository and open SQL*Plus from the project folder. Connect to a dedicated coursework database schema.

First, create the tables and load the sample data:

```sql
@Database_setup.sql
```

Then run the module scripts:

```sql
SET SERVEROUTPUT ON

@payments.sql
@order_customers.sql
@shipments.sql
@products_inventory.sql
```

`Database_setup.sql` drops and recreates the project's tables. Running it again resets the sample data.

`products_inventory.sql` includes demonstration calls with expected validation errors and a successful restocking example that updates stock.

## Payment Module Examples

Display the payment history of customer 1:

```sql
EXEC Print_Customer_Payment_History(1);
```

Count completed card payments:

```sql
SELECT Count_Completed_Payments('CARD') AS Completed_Card_Payments
FROM dual;
```

Retrieve the bank for payment 11:

```sql
SELECT Get_Payment_Bank(11) AS Bank_Name
FROM dual;
```

## Project Context

This is a university group project. The file table identifies each member's individual module.
