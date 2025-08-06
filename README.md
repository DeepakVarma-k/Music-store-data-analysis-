# 🎵 Music Store Database Analysis Project

A comprehensive SQL data analysis project demonstrating advanced database querying techniques on a digital music store database. This project showcases real-world data analyst skills including complex joins, subqueries, CTEs, and window functions to extract actionable business insights.

## 📌 Project Overview

This project simulates professional data analyst workflows in the music industry, using SQL to:

✅ **Customer Analytics** - Identify top customers and analyze purchasing behavior  
✅ **Geographic Analysis** - Examine sales patterns across countries and cities  
✅ **Genre Intelligence** - Investigate music preferences and trends  
✅ **Revenue Optimization** - Find high-value opportunities and market segments  
✅ **Artist Performance** - Analyze top-performing artists and track popularity  

## 🗄️ Database Schema & Structure

The database contains **11 interconnected tables** with the following relationships:

```
📊 MUSIC STORE DATABASE SCHEMA
│
├── 🎤 MUSIC CONTENT
│   ├── Artist (ArtistId, Name)
│   ├── Album (AlbumId, Title, ArtistId)
│   ├── Track (TrackId, Name, AlbumId, MediaTypeId, GenreId, Composer, Milliseconds, Bytes, UnitPrice)
│   ├── Genre (GenreId, Name)
│   └── MediaType (MediaTypeId, Name)
│
├── 👥 CUSTOMER & SALES
│   ├── Customer (CustomerId, FirstName, LastName, Company, Address, City, State, Country, PostalCode, Phone, Fax, Email, SupportRepId)
│   ├── Invoice (InvoiceId, CustomerId, InvoiceDate, BillingAddress, BillingCity, BillingState, BillingCountry, BillingPostalCode, Total)
│   └── InvoiceLine (InvoiceLineId, InvoiceId, TrackId, UnitPrice, Quantity)
│
├── 🏢 EMPLOYEE MANAGEMENT
│   └── Employee (EmployeeId, LastName, FirstName, Title, ReportsTo, BirthDate, HireDate, Address, City, State, Country, PostalCode, Phone, Fax, Email)
│
└── 🎧 PLAYLISTS
    ├── Playlist (PlaylistId, Name)
    └── PlaylistTrack (PlaylistId, TrackId)
```

### **📋 Detailed Table Structure & Attributes**

#### **🎤 Artist Table**
| Attribute | Type | Description |
|-----------|------|-------------|
| `ArtistId` | INTEGER | Primary key, unique identifier for each artist |
| `Name` | VARCHAR(120) | Artist or band name |

#### **💿 Album Table**
| Attribute | Type | Description |
|-----------|------|-------------|
| `AlbumId` | INTEGER | Primary key, unique identifier for each album |
| `Title` | VARCHAR(160) | Album title or name |
| `ArtistId` | INTEGER | Foreign key referencing Artist table |

#### **🎵 Track Table**
| Attribute | Type | Description |
|-----------|------|-------------|
| `TrackId` | INTEGER | Primary key, unique identifier for each track |
| `Name` | VARCHAR(200) | Song/track title |
| `AlbumId` | INTEGER | Foreign key referencing Album table |
| `MediaTypeId` | INTEGER | Foreign key referencing MediaType table |
| `GenreId` | INTEGER | Foreign key referencing Genre table |
| `Composer` | VARCHAR(220) | Song composer(s) name |
| `Milliseconds` | INTEGER | Track duration in milliseconds |
| `Bytes` | INTEGER | File size in bytes |
| `UnitPrice` | NUMERIC(10,2) | Price per track in currency |

#### **🎭 Genre Table**
| Attribute | Type | Description |
|-----------|------|-------------|
| `GenreId` | INTEGER | Primary key, unique identifier for each genre |
| `Name` | VARCHAR(120) | Genre name (Rock, Jazz, Pop, etc.) |

#### **📀 MediaType Table**
| Attribute | Type | Description |
|-----------|------|-------------|
| `MediaTypeId` | INTEGER | Primary key, unique identifier for media format |
| `Name` | VARCHAR(120) | Media format (MPEG, AAC, Protected AAC, etc.) |

#### **👥 Customer Table**
| Attribute | Type | Description |
|-----------|------|-------------|
| `CustomerId` | INTEGER | Primary key, unique identifier for each customer |
| `FirstName` | VARCHAR(40) | Customer's first name |
| `LastName` | VARCHAR(20) | Customer's last name |
| `Company` | VARCHAR(80) | Customer's company (if applicable) |
| `Address` | VARCHAR(70) | Street address |
| `City` | VARCHAR(40) | City name |
| `State` | VARCHAR(40) | State or province |
| `Country` | VARCHAR(40) | Country name |
| `PostalCode` | VARCHAR(10) | ZIP or postal code |
| `Phone` | VARCHAR(24) | Phone number |
| `Fax` | VARCHAR(24) | Fax number |
| `Email` | VARCHAR(60) | Email address |
| `SupportRepId` | INTEGER | Foreign key referencing Employee table |

#### **🧾 Invoice Table**
| Attribute | Type | Description |
|-----------|------|-------------|
| `InvoiceId` | INTEGER | Primary key, unique identifier for each invoice |
| `CustomerId` | INTEGER | Foreign key referencing Customer table |
| `InvoiceDate` | DATETIME | Date and time of purchase |
| `BillingAddress` | VARCHAR(70) | Billing street address |
| `BillingCity` | VARCHAR(40) | Billing city |
| `BillingState` | VARCHAR(40) | Billing state or province |
| `BillingCountry` | VARCHAR(40) | Billing country |
| `BillingPostalCode` | VARCHAR(10) | Billing ZIP or postal code |
| `Total` | NUMERIC(10,2) | Total invoice amount |

#### **📋 InvoiceLine Table**
| Attribute | Type | Description |
|-----------|------|-------------|
| `InvoiceLineId` | INTEGER | Primary key, unique identifier for each line item |
| `InvoiceId` | INTEGER | Foreign key referencing Invoice table |
| `TrackId` | INTEGER | Foreign key referencing Track table |
| `UnitPrice` | NUMERIC(10,2) | Price per unit at time of purchase |
| `Quantity` | INTEGER | Number of units purchased |

#### **🏢 Employee Table**
| Attribute | Type | Description |
|-----------|------|-------------|
| `EmployeeId` | INTEGER | Primary key, unique identifier for each employee |
| `LastName` | VARCHAR(20) | Employee's last name |
| `FirstName` | VARCHAR(20) | Employee's first name |
| `Title` | VARCHAR(30) | Job title or position |
| `ReportsTo` | INTEGER | Foreign key referencing Employee table (manager) |
| `BirthDate` | DATETIME | Employee's birth date |
| `HireDate` | DATETIME | Date employee was hired |
| `Address` | VARCHAR(70) | Employee's street address |
| `City` | VARCHAR(40) | Employee's city |
| `State` | VARCHAR(40) | Employee's state or province |
| `Country` | VARCHAR(40) | Employee's country |
| `PostalCode` | VARCHAR(10) | Employee's ZIP or postal code |
| `Phone` | VARCHAR(24) | Employee's phone number |
| `Fax` | VARCHAR(24) | Employee's fax number |
| `Email` | VARCHAR(60) | Employee's email address |

#### **🎧 Playlist Table**
| Attribute | Type | Description |
|-----------|------|-------------|
| `PlaylistId` | INTEGER | Primary key, unique identifier for each playlist |
| `Name` | VARCHAR(120) | Playlist name |

#### **🎶 PlaylistTrack Table**
| Attribute | Type | Description |
|-----------|------|-------------|
| `PlaylistId` | INTEGER | Foreign key referencing Playlist table |
| `TrackId` | INTEGER | Foreign key referencing Track table |

**Note:** This is a junction table with composite primary key (PlaylistId, TrackId)

### **🔗 Key Relationships:**
- `Customer` → `Invoice` (1:N) - Customer purchase history
- `Invoice` → `InvoiceLine` (1:N) - Detailed line items
- `Track` → `InvoiceLine` (1:N) - Products sold
- `Artist` → `Album` → `Track` (1:N:N) - Music hierarchy
- `Employee` → `Customer` (1:N) - Support representative assignment
- `Playlist` ↔ `Track` (M:N) - Many-to-many relationship via PlaylistTrack

## 📝 Complete SQL Analysis Code

### **🏆 QUESTION SET 1: Basic Business Intelligence**

```sql
-- Question 1: Which countries have the most Invoices?
SELECT billing_country, COUNT(billing_country) AS Invoice_Number
FROM invoice
GROUP BY billing_country
ORDER BY Invoice_Number DESC;

-- Question 2: Which city has the best customers? 
-- Find the city with highest sum of invoice totals for promotional festival
SELECT billing_city, SUM(total) AS InvoiceTotal
FROM invoice
GROUP BY billing_city
ORDER BY InvoiceTotal DESC
LIMIT 1;

-- Question 3: Who is the best customer?
-- Customer who has spent the most money
SELECT customer.customer_id, first_name, last_name, SUM(total) AS total_spending
FROM customer
JOIN invoice ON customer.customer_id = invoice.customer_id
GROUP BY (customer.customer_id)
ORDER BY total_spending DESC
LIMIT 1;
```

### **🎸 QUESTION SET 2: Genre & Artist Deep Dive**

```sql
-- Question 1: Rock Music Customer Analysis
-- Method 1: Using Subquery
SELECT DISTINCT email, first_name, last_name
FROM customer
JOIN invoice ON customer.customer_id = invoice.customer_id
JOIN invoiceline ON invoice.invoice_id = invoiceline.invoice_id
WHERE track_id IN(
    SELECT track_id FROM track
    JOIN genre ON track.genre_id = genre.genre_id
    WHERE genre.name LIKE 'Rock'
)
ORDER BY email;

-- Method 2: Using Multiple Joins
SELECT DISTINCT email AS Email, first_name AS FirstName, last_name AS LastName, genre.name AS Name
FROM customer
JOIN invoice ON invoice.customer_id = customer.customer_id
JOIN invoiceline ON invoiceline.invoice_id = invoice.invoice_id
JOIN track ON track.track_id = invoiceline.track_id
JOIN genre ON genre.genre_id = track.genre_id
WHERE genre.name LIKE 'Rock'
ORDER BY email;

-- Question 2: Top 10 Rock Artists by Track Count
SELECT artist.artist_id, artist.name, COUNT(artist.artist_id) AS number_of_songs
FROM track
JOIN album ON album.album_id = track.album_id
JOIN artist ON artist.artist_id = album.artist_id
JOIN genre ON genre.genre_id = track.genre_id
WHERE genre.name LIKE 'Rock'
GROUP BY artist.artist_id
ORDER BY number_of_songs DESC
LIMIT 10;

-- Question 3: Best Selling Artist & Top Customer Analysis
WITH tbl_best_selling_artist AS(
    SELECT artist.artist_id AS artist_id, artist.name AS artist_name, 
           SUM(invoiceline.unit_price * invoiceline.quantity) AS total_sales
    FROM invoiceline
    JOIN track ON track.track_id = invoiceline.track_id
    JOIN album ON album.album_id = track.album_id
    JOIN artist ON artist.artist_id = album.artist_id
    GROUP BY 1
    ORDER BY 3 DESC
    LIMIT 1
)
SELECT bsa.artist_name, SUM(il.unit_price * il.quantity) AS amount_spent, 
       c.customer_id, c.first_name, c.last_name
FROM invoice i
JOIN customer c ON c.customer_id = i.customer_id
JOIN invoiceline il ON il.invoice_id = i.invoice_id
JOIN track t ON t.track_id = il.track_id
JOIN album alb ON alb.album_id = t.album_id
JOIN tbl_best_selling_artist bsa ON bsa.artist_id = alb.artist_id
GROUP BY 1,3,4,5
ORDER BY 2 DESC;
```

### **🌍 QUESTION SET 3: Advanced Analytics with CTEs**

```sql
-- Question 1: Most Popular Genre by Country
WITH RECURSIVE
    tbl_sales_per_country AS(
        SELECT COUNT(*) AS purchases_per_genre, customer.country, genre.name, genre.genre_id
        FROM invoiceline
        JOIN invoice ON invoice.invoice_id = invoiceline.invoice_id
        JOIN customer ON customer.customer_id = invoice.customer_id
        JOIN track ON track.track_id = invoiceline.track_id
        JOIN genre ON genre.genre_id = track.genre_id
        GROUP BY 2,3,4
        ORDER BY 2
    ),
    tbl_max_genre_per_country AS(
        SELECT MAX(purchases_per_genre) AS max_genre_number, country
        FROM tbl_sales_per_country
        GROUP BY 2
        ORDER BY 2
    )
SELECT tbl_sales_per_country.* 
FROM tbl_sales_per_country
JOIN tbl_max_genre_per_country ON tbl_sales_per_country.country = tbl_max_genre_per_country.country
WHERE tbl_sales_per_country.purchases_per_genre = tbl_max_genre_per_country.max_genre_number;

-- Question 2: Tracks Longer Than Average Length
SELECT name, miliseconds
FROM track
WHERE miliseconds > (
    SELECT AVG(miliseconds) AS avg_track_length
    FROM track
)
ORDER BY miliseconds DESC;

-- Question 3: Top Customer by Country
WITH RECURSIVE 
    tbl_customter_with_country AS (
        SELECT customer.customer_id, first_name, last_name, billing_country, 
               SUM(total) AS total_spending
        FROM invoice
        JOIN customer ON customer.customer_id = invoice.customer_id
        GROUP BY 1,2,3,4
        ORDER BY 2,3 DESC
    ),
    tbl_country_max_spending AS(
        SELECT billing_country, MAX(total_spending) AS max_spending
        FROM tbl_customter_with_country
        GROUP BY billing_country
    )
SELECT tbl_cc.billing_country, tbl_cc.total_spending, tbl_cc.first_name, tbl_cc.last_name, tbl_cc.customer_id
FROM tbl_customter_with_country tbl_cc
JOIN tbl_country_max_spending tbl_ms ON tbl_cc.billing_country = tbl_ms.billing_country
WHERE tbl_cc.total_spending = tbl_ms.max_spending
ORDER BY 1;
```

## 🔥 BONUS QUERIES: Advanced Business Intelligence

### **📊 Monthly Revenue Trends Analysis**
```sql
SELECT 
    DATE_TRUNC('month', invoice_date) AS month,
    SUM(total) AS monthly_revenue,
    COUNT(*) AS total_invoices,
    ROUND(AVG(total), 2) AS avg_invoice_value,
    LAG(SUM(total)) OVER (ORDER BY DATE_TRUNC('month', invoice_date)) AS prev_month_revenue,
    ROUND(
        ((SUM(total) - LAG(SUM(total)) OVER (ORDER BY DATE_TRUNC('month', invoice_date))) / 
         LAG(SUM(total)) OVER (ORDER BY DATE_TRUNC('month', invoice_date))) * 100, 2
    ) AS revenue_growth_percent
FROM invoice
GROUP BY DATE_TRUNC('month', invoice_date)
ORDER BY month;
```

### **🎭 Genre Revenue & Customer Distribution**
```sql
SELECT 
    g.name AS genre,
    SUM(il.unit_price * il.quantity) AS total_revenue,
    COUNT(DISTINCT i.customer_id) AS unique_customers,
    COUNT(il.invoice_line_id) AS total_purchases,
    ROUND(SUM(il.unit_price * il.quantity) / COUNT(DISTINCT i.customer_id), 2) AS revenue_per_customer,
    ROUND(AVG(il.unit_price * il.quantity), 2) AS avg_purchase_value,
    RANK() OVER (ORDER BY SUM(il.unit_price * il.quantity) DESC) AS revenue_rank
FROM genre g
JOIN track t ON g.genre_id = t.genre_id
JOIN invoiceline il ON t.track_id = il.track_id
JOIN invoice i ON il.invoice_id = i.invoice_id
GROUP BY g.name
ORDER BY total_revenue DESC;
```

### **👥 Customer Lifetime Value & Segmentation**
```sql
WITH customer_metrics AS (
    SELECT 
        c.customer_id,
        c.first_name || ' ' || c.last_name AS full_name,
        c.country,
        c.email,
        SUM(i.total) AS lifetime_value,
        COUNT(i.invoice_id) AS total_orders,
        ROUND(AVG(i.total), 2) AS avg_order_value,
        MAX(i.invoice_date) AS last_purchase_date,
        MIN(i.invoice_date) AS first_purchase_date,
        EXTRACT(DAYS FROM (MAX(i.invoice_date) - MIN(i.invoice_date))) AS customer_lifespan_days
    FROM customer c
    JOIN invoice i ON c.customer_id = i.customer_id
    GROUP BY c.customer_id, c.first_name, c.last_name, c.country, c.email
),
percentile_ranks AS (
    SELECT *,
        NTILE(4) OVER (ORDER BY lifetime_value) AS value_quartile,
        NTILE(3) OVER (ORDER BY total_orders) AS frequency_tertile
    FROM customer_metrics
)
SELECT *,
    CASE 
        WHEN lifetime_value >= 45 THEN 'VIP Customer'
        WHEN lifetime_value >= 25 THEN 'High Value'
        WHEN lifetime_value >= 15 THEN 'Medium Value'
        ELSE 'Low Value'
    END AS customer_segment,
    CASE
        WHEN value_quartile = 4 AND frequency_tertile = 3 THEN 'Champions'
        WHEN value_quartile = 4 THEN 'Loyal Customers'
        WHEN frequency_tertile = 3 THEN 'Potential Loyalists'
        ELSE 'Regular Customers'
    END AS rfm_segment
FROM percentile_ranks
ORDER BY lifetime_value DESC;
```

### **🎵 Track Performance & Popularity Analysis**
```sql
WITH track_performance AS (
    SELECT 
        t.track_id,
        t.name AS track_name,
        ar.name AS artist_name,
        al.title AS album_name,
        g.name AS genre,
        COUNT(il.track_id) AS times_purchased,
        SUM(il.unit_price * il.quantity) AS track_revenue,
        ROUND(AVG(il.unit_price), 2) AS avg_selling_price,
        t.unit_price AS catalog_price,
        ROUND((t.milliseconds / 1000.0 / 60.0), 2) AS duration_minutes
    FROM track t
    JOIN album al ON t.album_id = al.album_id
    JOIN artist ar ON al.artist_id = ar.artist_id
    JOIN genre g ON t.genre_id = g.genre_id
    JOIN invoiceline il ON t.track_id = il.track_id
    GROUP BY t.track_id, t.name, ar.name, al.title, g.name, t.unit_price, t.milliseconds
    HAVING COUNT(il.track_id) >= 2
)
SELECT *,
    RANK() OVER (ORDER BY track_revenue DESC) AS revenue_rank,
    RANK() OVER (ORDER BY times_purchased DESC) AS popularity_rank,
    ROUND(track_revenue / times_purchased, 2) AS revenue_per_purchase
FROM track_performance
ORDER BY track_revenue DESC
LIMIT 25;
```

### **🏢 Employee Sales Performance Dashboard**
```sql
WITH employee_performance AS (
    SELECT 
        e.employee_id,
        e.first_name || ' ' || e.last_name AS employee_name,
        e.title,
        e.city AS employee_city,
        COUNT(DISTINCT c.customer_id) AS customers_managed,
        COUNT(DISTINCT i.invoice_id) AS total_transactions,
        SUM(i.total) AS total_sales_generated,
        ROUND(AVG(i.total), 2) AS avg_transaction_value,
        MAX(i.invoice_date) AS last_sale_date,
        COUNT(DISTINCT DATE_TRUNC('month', i.invoice_date)) AS active_months
    FROM employee e
    LEFT JOIN customer c ON e.employee_id = c.support_rep_id
    LEFT JOIN invoice i ON c.customer_id = i.customer_id
    WHERE c.customer_id IS NOT NULL
    GROUP BY e.employee_id, e.first_name, e.last_name, e.title, e.city
)
SELECT *,
    ROUND(total_sales_generated / customers_managed, 2) AS sales_per_customer,
    ROUND(total_sales_generated / active_months, 2) AS avg_monthly_sales,
    RANK() OVER (ORDER BY total_sales_generated DESC) AS sales_rank
FROM employee_performance
ORDER BY total_sales_generated DESC;
```

### **🎯 Market Opportunity Analysis**
```sql
-- Identify potential expansion opportunities
WITH country_analysis AS (
    SELECT 
        c.country,
        COUNT(DISTINCT c.customer_id) AS total_customers,
        SUM(i.total) AS total_revenue,
        ROUND(AVG(i.total), 2) AS avg_invoice_value,
        COUNT(i.invoice_id) AS total_invoices,
        ROUND(SUM(i.total) / COUNT(DISTINCT c.customer_id), 2) AS revenue_per_customer,
        COUNT(DISTINCT DATE_TRUNC('month', i.invoice_date)) AS active_months
    FROM customer c
    JOIN invoice i ON c.customer_id = i.customer_id
    GROUP BY c.country
),
genre_by_country AS (
    SELECT 
        c.country,
        g.name AS top_genre,
        COUNT(*) AS genre_purchases,
        ROW_NUMBER() OVER (PARTITION BY c.country ORDER BY COUNT(*) DESC) AS genre_rank
    FROM customer c
    JOIN invoice i ON c.customer_id = i.customer_id
    JOIN invoiceline il ON i.invoice_id = il.invoice_id
    JOIN track t ON il.track_id = t.track_id
    JOIN genre g ON t.genre_id = g.genre_id
    GROUP BY c.country, g.name
)
SELECT 
    ca.country,
    ca.total_customers,
    ca.total_revenue,
    ca.revenue_per_customer,
    ca.avg_invoice_value,
    gbc.top_genre,
    CASE 
        WHEN ca.total_customers >= 10 AND ca.revenue_per_customer >= 35 THEN 'High Priority Market'
        WHEN ca.total_customers >= 5 AND ca.revenue_per_customer >= 25 THEN 'Growth Market'
        WHEN ca.total_customers >= 2 THEN 'Emerging Market'
        ELSE 'Niche Market'
    END AS market_segment
FROM country_analysis ca
JOIN genre_by_country gbc ON ca.country = gbc.country
WHERE gbc.genre_rank = 1
ORDER BY ca.total_revenue DESC;
```

## 🛠️ Setup & Installation

### **Prerequisites**
- PostgreSQL 12+ or any SQL database system



## 📈 Key Business Insights

This analysis reveals:

🎯 **Customer Insights**
- Identification of high-value customers for VIP programs
- Geographic distribution for targeted marketing campaigns
- Customer segmentation for personalized recommendations

📊 **Revenue Optimization**
- Top-performing genres and artists for inventory decisions
- Seasonal trends for promotional planning
- Price optimization opportunities

🌍 Market Expansion

Untapped markets with high growth potential
Genre preferences by geographic region
Employee performance metrics for team optimization

🔧 Technologies Used

SQL: PostgreSQL with advanced features
Techniques: Complex JOINs, CTEs, Window Functions, Subqueries
Analysis: Statistical functions, ranking, segmentation
Business Intelligence: KPI calculation, trend analysis

## 👨‍💻 Author

Built by **k.Deepak Varma**  
Feel free to use, modify, or extend this program.
