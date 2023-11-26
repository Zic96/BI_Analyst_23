/*1. Data Understanding*/

/* 1.1 Understanding ids (order and user) */
SELECT 
    COUNT(*) AS total_rows,
    COUNT(DISTINCT order_id) AS unique_orders,
    COUNT(DISTINCT user_id) AS unique_users,
FROM 
  `as-efood-bi-2023.assesment.orders`
/*Total_rows: 656209. unique_orders: 656209 with 101379 distinct_users, some users order more than once time*/

/*This query calculate the number of orders per user_id and sort them from highest count to lowest. The most orders is 218*/
SELECT
  user_id, COUNT(order_id) AS total_orders
FROM 
  `as-efood-bi-2023.assesment.orders`
  GROUP BY user_id
  ORDER BY total_orders DESC 


/*This query calculate the average orders by user(6.47)*/
SELECT AVG(orders_per_user) AS avg_orders_per_user
FROM (
    SELECT user_id, COUNT(DISTINCT order_id) AS orders_per_user
    FROM `as-efood-bi-2023.assesment.orders`
    GROUP BY user_id
) AS user_orders;


/* 1.2 Understanding user_class */

/*This query calculate the number of null values for the column user_class_name(0 null values found)*/
SELECT 
    COUNT(CASE WHEN user_class_name IS NULL THEN 1 END) AS user_class_null
FROM 
    `as-efood-bi-2023.assesment.orders`

/*This query calculate the number of orders group by user_class_name and sort them from highest to lowest(6 unique classes found)*/
SELECT
  user_class_name, COUNT(*) AS count_by_class
FROM
  `as-efood-bi-2023.assesment.orders`
  GROUP BY user_class_name
  ORDER BY count_by_class DESC

/* 1.3 Understanding order_timestamp 


More detailed analysis in the section 2.Time-Based Analysis
*/
SELECT 
    DATE(order_timestamp) AS order_date,
    COUNT(*) AS daily_orders
FROM `as-efood-bi-2023.assesment.orders`
GROUP BY order_date
ORDER BY order_date;

/* 1.4 Understanding city */

/*This query calculate the number of null values for the column city(0 null values found)*/
SELECT 
    COUNT(CASE WHEN city IS NULL THEN 1 END) AS city_null
FROM 
    `as-efood-bi-2023.assesment.orders`

/*This query calculate the number of orders group by city and sort them from highest to lowest*/
SELECT
  city, COUNT(*) AS count_by_city
FROM 
  `as-efood-bi-2023.assesment.orders`
  GROUP BY city
  ORDER BY count_by_city DESC

/* 1.5 Understanding vertical */

/*This query calculate the number of null values for the column vertical(0 null values found)*/
SELECT 
    COUNT(CASE WHEN vertical IS NULL THEN 1 END) AS vertical_null
FROM 
    `as-efood-bi-2023.assesment.orders`

/*This query calculate the number of orders group by vertical and sort them from highest to lowest(99% of the values are restaurant and 1% local stores)*/
SELECT
  vertical, COUNT(*) AS count_by_vertical
FROM 
  `as-efood-bi-2023.assesment.orders`
  GROUP BY vertical
  ORDER BY count_by_vertical DESC


  /* 1.6 Understanding cuisine */

/*This query calculate the number of null values for the column cuisine(0 null values found)*/
SELECT 
    COUNT(CASE WHEN cuisine IS NULL THEN 1 END) AS cuisine_null
FROM 
    `as-efood-bi-2023.assesment.orders`


/*This query calculate the number of orders group by cuisine and sort them from highest to lowest. Also calculate the percentage of each cuisine.(5 categories found ,breakfast 43% and meat 30% category sums to 73%)*/
SELECT 
  cuisine,
  COUNT(*) AS count_by_cuisine,
  ROUND((COUNT(*) * 100.0) / SUM(COUNT(*)) OVER (), 2) AS pct_by_cuisine
FROM 
  `as-efood-bi-2023.assesment.orders`
GROUP BY 
  cuisine
ORDER BY 
  count_by_cuisine DESC;


 /* 1.7 Understanding device */

/*This query calculate the number of null values for the column device(0 null values found)*/
SELECT 
    COUNT(CASE WHEN device IS NULL THEN 1 END) AS device_null
FROM 
    `as-efood-bi-2023.assesment.orders`


/*This query calculate the number of orders group by device and sort them from highest to lowest. Also calculate the percentage of each device.(4 categorys found.android 48% and ios 38% category sums to 86%)*/
SELECT 
  device,
  COUNT(*) AS count_by_device,
  ROUND((COUNT(*) * 100.0) / SUM(COUNT(*)) OVER (), 2) AS pct_by_device
FROM 
  `as-efood-bi-2023.assesment.orders`
GROUP BY 
  device
ORDER BY 
  count_by_device DESC;



 /* 1.8 Understanding paid_cash */

/*This query calculate the number of null values for the column paid_cash(0 null values found)*/
SELECT 
    COUNT(CASE WHEN paid_cash IS NULL THEN 1 END) AS paid_cash_null
FROM 
    `as-efood-bi-2023.assesment.orders`

/*This query calculate the number of orders group by paid_cash and sort them from highest to lowest(52% paid in cash 47% without)*/
SELECT 
  paid_cash,
  COUNT(*) AS count_by_paid_cash,
  ROUND((COUNT(*) * 100.0) / SUM(COUNT(*)) OVER (), 2) AS pct_by_paid_cash
FROM 
  `as-efood-bi-2023.assesment.orders`
GROUP BY 
  paid_cash
ORDER BY 
  count_by_paid_cash DESC;


 /* 1.9 Understanding order_contains_offer */

/*This query calculate the number of null values for the column paid_cash(0 null values found)*/
SELECT 
    COUNT(CASE WHEN order_contains_offer IS NULL THEN 1 END) AS order_contains_offer_null
FROM 
    `as-efood-bi-2023.assesment.orders`

/*This query calculate the number of orders group by order_contains_offer and sort them from highest to lowest(only 11% of orders was with offer)*/
SELECT 
  order_contains_offer,
  COUNT(*) AS count_by_order_contains_offer,
  ROUND((COUNT(*) * 100.0) / SUM(COUNT(*)) OVER (), 2) AS pct_by_order_contains_offer
FROM 
  `as-efood-bi-2023.assesment.orders`
GROUP BY 
  order_contains_offer
ORDER BY 
  count_by_order_contains_offer DESC;


 /* 1.10 Understanding coupon_discount_amount */

/*This query calculate the number of null values for the column coupon_discount_amount(0 null values found)*/
SELECT 
    COUNT(CASE WHEN coupon_discount_amount IS NULL THEN 1 END) AS coupon_discount_amount_null
FROM 
    `as-efood-bi-2023.assesment.orders`

/*This query calculate the basic statistics for the column coupon_discount_amount

Output: avg 0.07, min 0, max 22.42, std 0.56
*/

SELECT 
    MIN(coupon_discount_amount) AS min_coupon_discount_amount,
    AVG(coupon_discount_amount) AS avg_coupon_discount_amount,
    MAX(coupon_discount_amount) AS max_coupon_discount_amount,
    STDDEV(coupon_discount_amount) AS std_coupon_discount_amount
FROM `as-efood-bi-2023.assesment.orders`;

/*
This query creates a distribution histogram for the 'coupon_discount_amount' column in the '`as-efood-bi-2023.assesment.orders`' table.

Explanation:
- The query uses the FLOOR() function to group 'coupon_discount_amount' values into bins based on their integer part.
- It employs the GROUP BY clause to group the values into bins and COUNT(*) to calculate the frequency of values within each bin.
- 'bin_start' represents the starting value of each bin (the integer part of 'coupon_discount_amount').
- The result displays the frequency of 'coupon_discount_amount' values within each bin, ordered by the starting value of the bins.

Output: positive (right) skewed distribution detected, we need to check for outliers
*/
SELECT 
    FLOOR(coupon_discount_amount) AS bin_start,
    COUNT(*) AS frequency
FROM 
    `as-efood-bi-2023.assesment.orders`
GROUP BY 
    bin_start
ORDER BY 
    bin_start

/*
This query identifies potential outliers in the 'coupon_discount_amount' column of the '`as-efood-bi-2023.assesment.orders`' table using the Z-score method. 

Explanation:
1. The 'stats' Common Table Expression (CTE) calculates the mean ('mean_coupon_discount_amount') and standard deviation ('stddev_coupon_discount_amount') of the 'coupon_discount_amount' column from the 'orders' table.

2. The main query computes the Z-score for each 'coupon' value by subtracting the mean and dividing by the standard deviation. 

3. It filters rows where the absolute Z-score is greater than 3, indicating potential extreme outliers beyond three standard deviations from the mean.

Output: 15788 outliers detected
*/
WITH stats AS (
    SELECT 
        AVG(coupon_discount_amount) AS mean_coupon_discount_amount,
        STDDEV(coupon_discount_amount) AS stddev_coupon_discount_amount
    FROM 
        `as-efood-bi-2023.assesment.orders`
)
SELECT 
    o.order_id, o.coupon_discount_amount
FROM 
    `as-efood-bi-2023.assesment.orders` o
CROSS JOIN 
    stats s
WHERE 
    ABS((o.coupon_discount_amount - s.mean_coupon_discount_amount) / s.stddev_coupon_discount_amount) > 3;


 /* 1.11 Understanding amount */

/*This query calculate the number of null values for the column amount(0 null values found)*/
SELECT 
    COUNT(CASE WHEN amount IS NULL THEN 1 END) AS amount_null
FROM 
    `as-efood-bi-2023.assesment.orders`

/*This query calculate the basic statistics for the column amount

Output: 9.7 avg, min 0 max 493.5 std 7.41
*/
SELECT 
    AVG(amount) AS avg_amount,
    MIN(amount) AS min_amount,
    MAX(amount) AS max_amount,
    STDDEV(amount) AS std_amount
FROM `as-efood-bi-2023.assesment.orders`


/*
This query creates a distribution histogram for the 'amount' column in the '`as-efood-bi-2023.assesment.orders`' table.

Explanation:
- The query uses the FLOOR() function to group 'amount' values into bins based on their integer part.
- It employs the GROUP BY clause to group the values into bins and COUNT(*) to calculate the frequency of values within each bin.
- 'bin_start' represents the starting value of each bin (the integer part of 'amount').
- The result displays the frequency of 'amount' values within each bin, ordered by the starting value of the bins.

Output: positive (right) skewed distribution detected, we need to check for outliers
*/
SELECT 
    FLOOR(amount) AS bin_start,
    COUNT(*) AS frequency
FROM 
    `as-efood-bi-2023.assesment.orders`
GROUP BY 
    bin_start
ORDER BY 
    bin_start



/*
This query identifies potential outliers in the 'amount' column of the '`as-efood-bi-2023.assesment.orders`' table using the Z-score method. 

Explanation:
1. The 'stats' Common Table Expression (CTE) calculates the mean ('mean_amount') and standard deviation ('stddev_amount') of the 'amount' column from the '`as-efood-bi-2023.assesment.orders`' table.

2. The main query computes the Z-score for each 'amount' value by subtracting the mean and dividing by the standard deviation. 

3. It filters rows where the absolute Z-score is greater than 3, indicating potential extreme outliers beyond three standard deviations from the mean.

Output: 10433 outliers detected
*/
WITH stats AS (
    SELECT 
        AVG(amount) AS mean_amount,
        STDDEV(amount) AS stddev_amount
    FROM 
        `as-efood-bi-2023.assesment.orders`
)
SELECT 
    o.order_id, o.amount
FROM 
    `as-efood-bi-2023.assesment.orders` o
CROSS JOIN 
    stats s
WHERE 
    ABS((o.amount - s.mean_amount) / s.stddev_amount) > 3;


/* 1.12 Understanding delivery_cost */

/*This query calculate the number of null values for the column delivery_cost(0 null values found)*/
SELECT 
    COUNT(CASE WHEN delivery_cost IS NULL THEN 1 END) AS amount_null
FROM 
    `as-efood-bi-2023.assesment.orders`

/*This query calculate the basic statistics for the column delivery_cost

Output: avg 0.12 min 0, max 5, std 0.32
*/
SELECT 
    AVG(delivery_cost) AS avg_delivery_cost,
    MIN(delivery_cost) AS min_delivery_cost,
    MAX(delivery_cost) AS max_delivery_cost,
    STDDEV(delivery_cost) AS std_delivery_cost
FROM `as-efood-bi-2023.assesment.orders`


/*
This query creates a distribution histogram for the 'delivery_cost' column in the '`as-efood-bi-2023.assesment.orders`' table.

Explanation:
- The query uses the FLOOR() function to group 'delivery_cost' values into bins based on their integer part.
- It employs the GROUP BY clause to group the values into bins and COUNT(*) to calculate the frequency of values within each bin.
- 'bin_start' represents the starting value of each bin (the integer part of 'delivery_cost').
- The result displays the frequency of 'delivery_cost' values within each bin, ordered by the starting value of the bins.

Output: high positive (right) skewed distribution detected,majority of objervasion at zeor which make sense, next step check for outliers
*/
SELECT 
    FLOOR(delivery_cost) AS bin_start,
    COUNT(*) AS frequency
FROM 
    `as-efood-bi-2023.assesment.orders`
GROUP BY 
    bin_start
ORDER BY 
    bin_start



/*
This query identifies potential outliers in the 'delivery_cost' column of the '`as-efood-bi-2023.assesment.orders`' table using the Z-score method. 

Explanation:
1. The 'stats' Common Table Expression (CTE) calculates the mean ('mean_delivery_cost') and standard deviation ('stddev_delivery_cost') of the 'delivery_cost' column from the '`as-efood-bi-2023.assesment.orders`' table.

2. The main query computes the Z-score for each 'delivery_cost' value by subtracting the mean and dividing by the standard deviation. 

3. It filters rows where the absolute Z-score is greater than 3, indicating potential extreme outliers beyond three standard deviations from the mean.

Output: 16673 outliers detected
*/
WITH stats AS (
    SELECT 
        AVG(delivery_cost) AS mean_delivery_cost,
        STDDEV(delivery_cost) AS stddev_delivery_cost
    FROM 
        `as-efood-bi-2023.assesment.orders`
)
SELECT 
    o.order_id, o.delivery_cost
FROM 
    `as-efood-bi-2023.assesment.orders` o
CROSS JOIN 
    stats s
WHERE 
    ABS((o.delivery_cost - s.mean_delivery_cost) / s.stddev_delivery_cost) > 3;


/* 2.Time-Based Analysis*/

/* This query retrieves the date and the count of orders placed on each day

Comments: 
1.There is trend were the orders per day moves with in tha range of 10-12k orders, also cyclicality detacted further investigation in below qeuries for peak days and peak hours. 
2. Significant drop in orders at 15th august which make sense as is a very significant holiday for greek and the majority of the shops are close / customers prefer to eat home made with family and frierds or go dine out.
.*/
SELECT 
    DATE(order_timestamp) AS order_date,
    COUNT(*) AS daily_orders
FROM `as-efood-bi-2023.assesment.orders`
GROUP BY order_date
ORDER BY order_date;

/* This query will perform a similar analysis as the previous one, helping you identify the day of the week with the highest order volume

Comments: 
1. The orders per day of the week are evenly destributed
2. Friday has the most orders 99769 and second is Suterday 97885 the worse day is Monday with 83003
.*/

SELECT 
    EXTRACT(DAYOFWEEK FROM order_timestamp) AS day_of_week,
    COUNT(*) AS daily_orders
FROM `as-efood-bi-2023.assesment.orders`
GROUP BY day_of_week
ORDER BY daily_orders DESC;

/* This query will perform a similar analysis as the previous one, helping you identify the hour of the day with the highest order volume

Comments: 
1. We observe 3 cycles during the day: The first start 6 the morning peak at 11 and bottom at 12. The second peak at 2 where is the common luncy time bottom at around 6-7 and the last one peak at 9 which is the common dinner time and its by far the biggest peak for the day.
2. After midnight we observe a step slow down which make sense as the majority of stores are closed and the majority of the clients sleeping
.*/

SELECT 
    EXTRACT(HOUR FROM order_timestamp) AS hour_of_day,
    COUNT(*) AS hourly_orders
FROM `as-efood-bi-2023.assesment.orders`
GROUP BY hour_of_day
ORDER BY hourly_orders DESC


/* 3.Customer Segmentation Analysis*/

/* This query will provide a result with columns for user_class_name,order_count_per_user_class, average_amount_per_user_class,pct_coupon_used, average_coupon_discount_amount_per_user_class,average_delivery_cost_per_user_class, displaying the average order amount,the average_coupon_discount_amount_per_user_class and the for average_delivery_cost_per_user_class each distinct user class present


Insights:  
1.The biggest average amount is 16 by high spenders and the second is 13.65 for one timers
2. However one timers has average coupon 0.24 which 3x times from the average (0.07) and the pct_coupon_used is aligh with the other classes which mean for these class the coupons are higher.
3. Average Delivery cost is almost evenly destributed accross all segments except loyal customers where the average delivery cost is 0.07 which is the half of the general avearge.
*/

SELECT 
user_class_name, 
COUNT(order_id) AS order_count_per_user_class,
ROUND(AVG(amount),2) AS average_amount_per_user_class,
COUNT(CASE WHEN order_contains_offer = TRUE THEN 1 ELSE NULL END) AS coupon_used_count,
ROUND(COUNT(CASE WHEN order_contains_offer = TRUE THEN 1 ELSE NULL END) / COUNT(order_id),2) as pct_coupon_used,
ROUND(AVG(coupon_discount_amount),2) AS average_coupon_discount_amount_per_user_class,
ROUND(AVG(delivery_cost),2) AS average_delivery_cost_per_user_class,
FROM `as-efood-bi-2023.assesment.orders`
GROUP BY user_class_name

/* 4.User Behavior Analysis*/


/* This query will breakdown the number of order placed using differend divices and grouped by user_class

*/
SELECT 
    user_class_name, 
    COUNT(order_id) AS order_count_per_user_class,
    COUNT(CASE WHEN device = 'Android' THEN 1 ELSE NULL END) AS android_count,
    COUNT(CASE WHEN device = 'iOS' THEN 1 ELSE NULL END) AS iOS_count,
    COUNT(CASE WHEN device = 'Desktop' THEN 1 ELSE NULL END) AS Desktop_count,
    COUNT(CASE WHEN device = 'MobWeb' THEN 1 ELSE NULL END) AS Mobweb_count,
FROM `as-efood-bi-2023.assesment.orders`
GROUP BY user_class_name

/* This query will breakdown the number of order paid with and without cash and grouped by user_class

Insights: 
1. Only loyal class has significant more orders paid in cash than without cash
*/
SELECT 
    user_class_name, 
    COUNT(order_id) AS order_count_per_user_class,
    COUNT(CASE WHEN paid_cash = TRUE THEN 1 END) AS cash_count,
    COUNT(CASE WHEN paid_cash = FALSE THEN 1 END) AS non_cash_count
FROM `as-efood-bi-2023.assesment.orders`
GROUP BY user_class_name


/* 5.Cuisine Analysis*/


/*
This quiery calculate the order count, total amount, how much coupon used and the pct of these coupons order by cuisines.

Insights: 
1. The most frequent order cuisine is breakfast but its second in total value behind category meat which is the second more popoular cuisine.
2. In terms of coupon pct used the italian cuisine is in first place with 18% where is the 3rd most populara cuisine in terms of order volums and total amount.
*/
SELECT 
    cuisine, 
    COUNT(order_id) AS order_count_per_cuisine,
    ROUND(SUM(amount),2) AS total_amount_per_cuisine,
    COUNT(CASE WHEN order_contains_offer = TRUE THEN 1 ELSE NULL END) AS coupon_used_count,
    ROUND(COUNT(CASE WHEN order_contains_offer = TRUE THEN 1 ELSE NULL END) / COUNT(order_id),2) as pct_coupon_used
FROM `as-efood-bi-2023.assesment.orders`
GROUP BY cuisine


/* 6.Targeting Users for Breakfast Coupon Campaign*/


/* The first question we have to answer is who we need to target, so we want to investigate how classes distributed in the follow dimensions: 1. order volume 2. high average order value 3. pct of coupon used
From these dimensions we will create 2 pools: 
A) loyal/high spenders (customers who order frequently or spend significant more than other classes per order) as reward coupon
B) Customers who doesnt used coupons and/or doesnt order breakfast casually to motivate them try this cuisine

Output: The class with most orders is the all star, the class with biggest avg_amount is high spenders with 9.32 avg_amount and also one of the two class with the lowest usage of coupons.
Finally the class with the less orders is the one timers also is one of the two classes with the lowest usage of coupons.

These three clasees will be used for the coupon capaign.
*/
SELECT 
    user_class_name, 
    COUNT(*) AS order_count_breakfast,
    ROUND(SUM(amount),2) AS total_amount_breakfast,
    ROUND(AVG(amount),2) AS avg_amount,
    COUNT(CASE WHEN order_contains_offer = TRUE THEN 1 ELSE NULL END) AS coupon_used_count,
    ROUND(COUNT(CASE WHEN order_contains_offer = TRUE THEN 1 ELSE NULL END) / COUNT(order_id),2) as pct_coupon_used
FROM `as-efood-bi-2023.assesment.orders`
WHERE cuisine = 'Breakfast'
GROUP BY user_class_name


/* The second question we have to answer now is which hours of the day should these coupons be active?*/

SELECT 
    EXTRACT(HOUR FROM order_timestamp) AS hour_of_day,
    COUNT(*) AS hourly_orders
FROM `as-efood-bi-2023.assesment.orders`
WHERE cuisine = 'Breakfast'
GROUP BY hour_of_day
ORDER BY hourly_orders DESC

/* 
Insight: the trend from breakfast starts around 6-7 in the morning and peaks at 10-11 and then slow down until 12 and then drop more aggressive.

coupon active period: 8-12
*/
