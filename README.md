# Comprehensive Data Analysis of a Film Rental Database Using Advanced SQL

## Project Overview

This project focuses on an in-depth analysis of a film rental database using advanced SQL techniques. The goal was to extract meaningful insights and address various business-related queries that can aid in strategic decision-making and operational efficiency. The database represents a hypothetical film rental company, and the analysis covers aspects such as staff details, inventory management, customer activity, data breach liability, film diversity, replacement costs, payment processing, and customer rental behavior.

## Table of Contents
- [Project Overview](#project-overview)
- [Database Schema](#database-schema)
- [Analysis and Queries](#analysis-and-queries)
  - [1. Staff Details and Store Assignment](#1-staff-details-and-store-assignment)
  - [2. Inventory Management](#2-inventory-management)
  - [3. Customer Activity Analysis](#3-customer-activity-analysis)
  - [4. Data Breach Liability Assessment](#4-data-breach-liability-assessment)
  - [5. Film Diversity and Inventory](#5-film-diversity-and-inventory)
  - [6. Replacement Cost Analysis](#6-replacement-cost-analysis)
  - [7. Payment Processing and Fraud Prevention](#7-payment-processing-and-fraud-prevention)
  - [8. Customer Base Understanding](#8-customer-base-understanding)
- [Technologies Used](#technologies-used)
- [Conclusion](#conclusion)

## Database Schema

The database schema includes several tables representing different entities in the film rental business, such as staff, stores, inventory, customers, films, payments, and rentals. The primary tables used in the analysis are:

- **Staff**: Contains information about staff members, including their names, email addresses, and store assignments.
- **Store**: Contains details about the stores.
- **Inventory**: Holds information about the film inventory at each store.
- **Customer**: Includes customer information such as email addresses.
- **Film**: Contains details about the films available for rental.
- **Category**: Represents different film categories.
- **Payment**: Records payment transactions.
- **Rental**: Tracks film rentals by customers.

## Analysis and Queries

### 1. Staff Details and Store Assignment

To compile a list of all staff members, including their first and last names, email addresses, and the store identification number where they work, we used the following SQL query:

```sql
SELECT CONCAT(first_name,' ', last_name), store_id, email
FROM staff;

```

### 2. Inventory Management

To provide separate counts of inventory items held at the two stores, we used the following SQL queries:

```sql
SELECT store_id,COUNT(*)
FROM inventory 
GROUP BY store_id;
```

### 3. Customer Activity Analysis

To count the active customers for each store separately, we defined active customers as those who have made at least one rental. The queries used are:

```sql
SELECT store_id, COUNT(active) Active_Customers
FROM customer
GROUP BY store_id;
```

### 4. Data Breach Liability Assessment

To assess the liability of a data breach by counting all customer email addresses stored in the database, we used:

```sql
SELECT COUNT(email)
FROM customer;
```

### 5. Film Diversity and Inventory

To analyze film diversity and inventory, we provided the count of unique film titles in inventory at each store and the count of unique categories of films available.

```sql
SELECT store_id, COUNT(DISTINCT film_id) AS unique_films
FROM inventory
GROUP BY store_id; 

SELECT COUNT(DISTINCT name) AS unique_categories
FROM category;
```

### 6. Replacement Cost Analysis

To evaluate the replacement costs of films, identifying the least expensive, most expensive, and average replacement costs, we used:

Least expensive film to replace:
```sql
SELECT MIN(replacement_cost) AS min_replacement_cost
FROM film;
```

Most expensive film to replace:
```sql
SELECT MAX(replacement_cost) AS max_replacement_cost
FROM film;
```

Average replacement cost:
```sql
SELECT AVG(replacement_cost) AS avg_replacement_cost
FROM film;
```

### 7. Payment Processing and Fraud Prevention

To implement payment monitoring systems and minimize fraud risk, we calculated the average and maximum payments processed:

Average payment processed:
```sql
SELECT AVG(amount) AS avg_payment
FROM payment;
```

Maximum payment processed:
```sql
SELECT MAX(amount) AS max_payment
FROM payment;
```

### 8. Customer Base Understanding

To understand the customer base, we provided a list of all customer IDs with a count of rentals they have made, ordered by highest volume:

```sql
SELECT customer_id, COUNT(rental_id) AS rental_count
FROM rental
GROUP BY customer_id
ORDER BY rental_count DESC;
```

## Technologies Used

- **SQL**: For querying and analyzing the database.
- **Database Management System**: Assumed to be MySQL or PostgreSQL for running the queries.
- **Data Visualization Tools**: Optional, for visualizing the results (e.g., Tableau, Power BI).

## Conclusion

This project demonstrated the application of advanced SQL techniques to extract valuable insights from a film rental database. The analysis provided actionable information for staff management, inventory control, customer engagement, data breach risk assessment, film diversity evaluation, cost analysis, payment monitoring, and customer behavior understanding. The skills and insights gained from this project are crucial for making informed business decisions and improving operational efficiency in a film rental business.

Feel free to explore the SQL queries and modify them as needed for your own analysis or to gain deeper insights into the film rental database.
