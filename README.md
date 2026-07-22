# 📊 Olist Brazilian E-Commerce Power BI Dashboard

An interactive, end-to-end **Power BI Business Intelligence Solution** analyzing over **100k+ Brazilian E-Commerce orders** from **Olist** (2016 - 2018). This project covers Sales, Logistics, Customer Satisfaction, Seller Performance, and Sales Forecasting.

---

## 📌 Executive Summary / ملخص المشروع

يقدم هذا المشروع تحليلاً شاملاً وتفاعلياً لبيانات منصة التجارة الإلكترونية البرازيلية **Olist**. تم بناء التقرير باستخدام **Power BI** مع استخدام لغة **DAX** لبناء المقاييس الذكية ونموذج بيانات (Data Model) محسن لحل المسارات الغامضة (Ambiguous Paths).

### 🎯 Key Metrics Highlights (أبرز الأرقام الرئيسية)

- 💰 **Total Revenue / Price:** $13.59M
- 🚚 **Total Freight:** $2.25M (~16.5% of sales)
- 📦 **Total Distinct Orders:** 97.26K Orders (111K Total Items)
- 📍 **Geographic Reach:** 4,119 Cities across 27 States
- ⭐ **Average Review Score:** 4.07 / 5.00
- ⏱️ **On-Time Delivery Rate:** 91.37%

---

## 📂 Dashboard Architecture & Pages / صفحات اللوحة التفاعلية

### 1️⃣ Sales Analytics Page (صفحة المبيعات)

- **Sales vs Freight Trends:** Area charts analyzing yearly and monthly revenue trends (2016–2018).
- **Product Categories Performance:** Top 10 and Bottom 10 categories by order volume.
- **Custom Tooltip Pages:** Hovering over any category reveals dynamic state/city order percentage breakdowns (`% Total Orders por State/City`).

### 2️⃣ Logistics & Delivery Page (صفحة الخدمات اللوجستية)

- **Interactive Geo Map:** ArcGIS map visualizing spatial distribution of orders using latitude/longitude.
- **Delivery Performance:** Pie chart measuring **On Time** vs **Late** orders based on estimated delivery date.
- **Status Tracking:** Order status breakdown (Delivered, Shipped, Canceled, Invoiced).

### 3️⃣ Quality & Customer Satisfaction Page (صفحة الجودة والتقييمات)

- **Rating Distribution:** Stacked area visual tracking order volumes grouped by review score (1–5 Stars) over time.
- **Best vs Worst Products:** Category filtering for high ratings (4-5★) vs low ratings (1-2★).
- **Word Cloud Sentiment Analysis:** Visualizing common customer review feedback.

### 4️⃣ Sellers & Customer Behavior Page (أداء البائعين وسلوك المستهلك)

- **Seller Performance:** Scatter chart comparing sales volume vs seller ratings.
- **Payment Preferences:** Order distribution by Payment Methods (Credit Card, Boleto, Voucher, Debit) and Installments.
- **Basket Analysis:** Average Basket Size and Items per Order.

### 5️⃣ Forecasting & Executive KPI Page (التوقعات والذكاء الاصطناعي)

- **Time Series Forecasting:** Built-in AI forecasting for sales over a 6-month horizon with a 95% confidence interval.

---

## 🛠️ Tech Stack & DAX Calculations / التقنيات والمقاييس

- **BI Tool:** Power BI Desktop
- **ETL & Data Transformation:** Power Query (Denormalization with Left Outer Joins, Role-Playing Dimensions)
- **Data Model:** Star Schema / Snowflake Hybrid

### Key DAX Measures Used

```dax
-- Total Revenue
Total Price = SUM('olist_order_items_dataset'[price])

-- Distinct Order Count
Total Distinct Orders = DISTINCTCOUNT('olist_orders_dataset'[order_id])

-- Year-over-Year Sales Growth
Orders YoY Growth % = 
VAR CurrentOrders = [Total Distinct Orders]
VAR PastOrders = CALCULATE([Total Distinct Orders], SAMEPERIODLASTYEAR('Calendar'[Date]))
RETURN
DIVIDE(CurrentOrders - PastOrders, PastOrders)

-- Inactive Relationship Handling (Delivery Date)
Delivered Sales = 
CALCULATE(
    SUM('olist_order_items_dataset'[price]),
    USERELATIONSHIP('Calendar'[Date], 'olist_orders_dataset'[order_delivered_customer_date])
)

-- Delivery Performance Calculation (Calculated Column)
Delivery Performance = 
IF(
    ISBLANK('olist_orders_dataset'[order_delivered_customer_date]), 
    BLANK(),
    IF('olist_orders_dataset'[order_delivered_customer_date] <= 'olist_orders_dataset'[order_estimated_delivery_date], "On time", "Late")
)
```

### 💡 Key Business Insights / أهم التوصيات والمخرجات

- **Regional Concentration:** 43% of total orders originate from São Paulo (SP).Expansion strategies should target secondary states like RJ and MG.
- **Logistics Impact on Ratings:** Sentiment analysis shows that negative reviews (1-2★) are primarily driven by delivery delays (Atraso, Não chegou) rather than product defect.
- **Credit & Installments Preference:** Credit Card is the dominant payment method (>80%), with a high preference for installment payments (1-3 installments).

### 🚀 How to Run the Project / كيفية تشغيل الملف

Clone this repository:Bashgit clone [https://github.com/AhmedAmmar187/Olist-Brazilian-E-Commerce.git](https://github.com/AhmedAmmar187/Olist-Brazilian-E-Commerce.git)
=======
# 📊 Olist Brazilian E-Commerce Power BI Dashboard

An interactive, end-to-end **Power BI Business Intelligence Solution** analyzing over **100k+ Brazilian E-Commerce orders** from **Olist** (2016 - 2018). This project covers Sales, Logistics, Customer Satisfaction, Seller Performance, and Sales Forecasting.

---

## 📌 Executive Summary / ملخص المشروع

يقدم هذا المشروع تحليلاً شاملاً وتفاعلياً لبيانات منصة التجارة الإلكترونية البرازيلية **Olist**. تم بناء التقرير باستخدام **Power BI** مع استخدام لغة **DAX** لبناء المقاييس الذكية ونموذج بيانات (Data Model) محسن لحل المسارات الغامضة (Ambiguous Paths).

### 🎯 Key Metrics Highlights (أبرز الأرقام الرئيسية)

- 💰 **Total Revenue / Price:** $13.59M
- 🚚 **Total Freight:** $2.25M (~16.5% of sales)
- 📦 **Total Distinct Orders:** 97.26K Orders (111K Total Items)
- 📍 **Geographic Reach:** 4,119 Cities across 27 States
- ⭐ **Average Review Score:** 4.07 / 5.00
- ⏱️ **On-Time Delivery Rate:** 91.37%

---

## 📂 Dashboard Architecture & Pages / صفحات اللوحة التفاعلية

### 1️⃣ Sales Analytics Page (صفحة المبيعات)

- **Sales vs Freight Trends:** Area charts analyzing yearly and monthly revenue trends (2016–2018).
- **Product Categories Performance:** Top 10 and Bottom 10 categories by order volume.
- **Custom Tooltip Pages:** Hovering over any category reveals dynamic state/city order percentage breakdowns (`% Total Orders por State/City`).

### 2️⃣ Logistics & Delivery Page (صفحة الخدمات اللوجستية)

- **Interactive Geo Map:** ArcGIS map visualizing spatial distribution of orders using latitude/longitude.
- **Delivery Performance:** Pie chart measuring **On Time** vs **Late** orders based on estimated delivery date.
- **Status Tracking:** Order status breakdown (Delivered, Shipped, Canceled, Invoiced).

### 3️⃣ Quality & Customer Satisfaction Page (صفحة الجودة والتقييمات)

- **Rating Distribution:** Stacked area visual tracking order volumes grouped by review score (1–5 Stars) over time.
- **Best vs Worst Products:** Category filtering for high ratings (4-5★) vs low ratings (1-2★).
- **Word Cloud Sentiment Analysis:** Visualizing common customer review feedback.

### 4️⃣ Sellers & Customer Behavior Page (أداء البائعين وسلوك المستهلك)

- **Seller Performance:** Scatter chart comparing sales volume vs seller ratings.
- **Payment Preferences:** Order distribution by Payment Methods (Credit Card, Boleto, Voucher, Debit) and Installments.
- **Basket Analysis:** Average Basket Size and Items per Order.

### 5️⃣ Forecasting & Executive KPI Page (التوقعات والذكاء الاصطناعي)

- **Time Series Forecasting:** Built-in AI forecasting for sales over a 6-month horizon with a 95% confidence interval.

---

## 🛠️ Tech Stack & DAX Calculations / التقنيات والمقاييس

- **BI Tool:** Power BI Desktop
- **ETL & Data Transformation:** Power Query (Denormalization with Left Outer Joins, Role-Playing Dimensions)
- **Data Model:** Star Schema / Snowflake Hybrid

### Key DAX Measures Used

```dax
-- Total Revenue
Total Price = SUM('olist_order_items_dataset'[price])

-- Distinct Order Count
Total Distinct Orders = DISTINCTCOUNT('olist_orders_dataset'[order_id])

-- Year-over-Year Sales Growth
Orders YoY Growth % = 
VAR CurrentOrders = [Total Distinct Orders]
VAR PastOrders = CALCULATE([Total Distinct Orders], SAMEPERIODLASTYEAR('Calendar'[Date]))
RETURN
DIVIDE(CurrentOrders - PastOrders, PastOrders)

-- Inactive Relationship Handling (Delivery Date)
Delivered Sales = 
CALCULATE(
    SUM('olist_order_items_dataset'[price]),
    USERELATIONSHIP('Calendar'[Date], 'olist_orders_dataset'[order_delivered_customer_date])
)

-- Delivery Performance Calculation (Calculated Column)
Delivery Performance = 
IF(
    ISBLANK('olist_orders_dataset'[order_delivered_customer_date]), 
    BLANK(),
    IF('olist_orders_dataset'[order_delivered_customer_date] <= 'olist_orders_dataset'[order_estimated_delivery_date], "On time", "Late")
)
```

### 💡 Key Business Insights / أهم التوصيات والمخرجات

- **Regional Concentration:** 43% of total orders originate from São Paulo (SP).Expansion strategies should target secondary states like RJ and MG.
- **Logistics Impact on Ratings:** Sentiment analysis shows that negative reviews (1-2★) are primarily driven by delivery delays (Atraso, Não chegou) rather than product defect.
- **Credit & Installments Preference:** Credit Card is the dominant payment method (>80%), with a high preference for installment payments (1-3 installments).

### 🚀 How to Run the Project / كيفية تشغيل الملف

Clone this repository:Bashgit clone [https://github.com/AhmedAmmar187/Olist-Brazilian-E-Commerce.git](https://github.com/AhmedAmmar187/Olist-Brazilian-E-Commerce.git)

Download the official Olist Dataset from Kaggle.Open Olist_Analytics_Dashboard.pbix in Power BI Desktop.Update the dataset file paths in Power Query if prompted.
