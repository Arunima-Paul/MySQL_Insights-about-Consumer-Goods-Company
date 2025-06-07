# MySQL_Insights-about-Consumer-Goods-Company
This is a summary report with key insights and recommendations given for the Executive Management at a Consumer Goods Company.

First, we’ll look into the problem statement, then we’ll understand the database give for analysis, then we’ll move through the ad-hoc requests and analyse the insights gathered from them and lastly we’ll finish with strategic recommendations.


**Problem Statement :** AtliQ Hardwares (which is an imaginary company) is one of the leading computer hardware producers in India and they are well expanded in other countries too.
However, the management noticed that they do not get enough insights to make quick and smart data-informed decisions. They want to expand their data analytics team and want to hire someone who is good at both tech and soft skills.

Hence, they decided to conduct a SQL challenge which will help them to understand both the skills.

My Task is to analyse their ‘ad-hoc-requests.pdf’ where there are 10 ad hoc requests given for which the business needs insights. Then I have to run SQL queries to answer these requests and present the insights to the top management.

Let's understand the dataset give for analysis.

The dataset includes information for **six main tables** detailed as below :

**1. dim_customer** - this table contains customer-related data. 

**(i) The 'customer_code'** column features unique identification codes for every customer in the dataset. These codes can be used to track a customer's sales history, demographic information, and other relevant details. For example, the codes could look like '70002017', '90005160', and '80007195' respectively.

**(ii) customer:** The 'customer' column lists the names of customers, for example 'Atliq Exclusive', 'Flipkart' and 'Surface Stores' etc.

**(iii) platform:** The 'platform' column identifies how a company's products or services are sold. "Brick & Mortar" represents the physical store/location and 	"E-Commerce" represents online platforms.

**(iv) channel:** The 'channel' column reflects the distribution methods used to sell a product. These methods include "Retailers", "Direct" and "Distributors". 
Retailers refer to physical or online stores that sell products to consumers.

Direct sales refer to sales made directly to consumers through a company's website or other direct means.

Distributors refer to intermediaries or middlemen between the manufacturer and retailer or end consumers.

**(v) market:** The 'market' column lists the countries in which the customer is located.

**(vi) region:** The 'region' column categorizes countries according to their geographic location, including "APAC" (Asia Pacific), "EU" (Europe), "NA" (North America), and  "LATAM" (Latin America).

**(vii)	The 'sub_zone'** column further breaks down the regions into sub-regions, such as "India", "ROA" (Rest of Asia), "ANZ" (Australia and New Zealand), "SE" Southeast Asia), "NE" (Northeast Asia), "NA" (North America), and "LATAM" (Latin America).

**2. dim_product:** This table contains product-related data.

**(i) product_code:** The 'product_code' column features unique identification codes for each product, serving as a way to track and distinguish individual products within a database or system.

**(ii) division:** The 'division' column categorizes products into groups such as "P & A" (Peripherals and Accessories), "N & S" (Network and Storage) and "PC" (Personal Computer).

**(iii) segment:** The 'segment' column categorizes products further within the division, such as "Peripherals" (keyboard, mouse, monitor, etc.), 

"Accessories" (cases, cooling solutions, power supplies), 

"Notebook" (laptops), "Desktop" (desktops, all-in-one PCs, etc), 

"Storage" (hard disks, SSDs, external storage), and "Networking" (routers, switches, modems, etc.).

**(iv) category:** The 'category' column classifies products into specific subcategories within the segment.

**(v) product:** The 'product' column lists the names of individual products, corresponding to the unique identification codes found in the 'product_code' column.

**(vi) variant:** The "variant" column classifies products according to their features, prices, and other characteristics. 

The column includes variants such as "Standard", "Plus", "Premium" that represent different versions of the same product.

**3. fact_gross_price:** This table contains gross price information for each product.

**(i) product_code:** The 'product_code' column features unique identification codes for each product.

**(ii) fiscal_year:** The 'fiscal_year' column contains the fiscal period in which the product sale was recorded. A fiscal year is a 12-month period that is used for accounting purposes and often differs from the calendar year. 

For AtliQ Hardware the fiscal year starts in September. The data available in this column covers the fiscal years 2020 and 2021.

**(iii) gross_price:** The 'gross_price' column holds the initial price of a product, prior to any reductions or taxes. It is the original selling price of the product.

**4. fact_manufacturing_cost:** this table contains the cost incurred in the production of each product.

**(i) product_code:** The 'product_code' column features unique identification codes for each product.

**(ii) cost_year:** The "cost_year" column contains the fiscal year in which the product was manufactured.

**(iii) manufacturing_cost:** The "manufacturing_cost" column contains the total cost incurred for the production of a product. This cost includes direct costs like raw materials, labor, and overhead expenses that are directly associated with the production process.

**5.fact_pre_invoice_deductions:** this table contains pre-invoice deductions information for each product.

**(i) customer_code:** The 'customer_code' column features unique identification codes for every customer in the dataset. These codes can be used to track a customer's sales history, demographic information, and other relevant details. For example, the codes could look like '70002017', '90005160', and '80007195' respectively.

**(ii) fiscal_year:** The "fiscal_year" column holds the fiscal period when the sale of a product occurred.

**(iii) pre_invoice_discount_pct:** The "pre_invoice_discount_pct" column contains the percentage of pre-invoice deductions for each product. Pre-invoice deductions are discounts that are applied to the gross price of a product before the invoice is generated and typically applied to large orders or long-term contracts.

**6.fact_sales_monthly:** this table contains monthly sales data for each product.

**(i) date:** The "date" column contains the date when the sale of a product was made, in a monthly format for 2020 and 2021 fiscal years. This information can be used to understand the sales performance of products over time.

**(ii) product_code**: The "product_code" column contains a unique identification code for each product. This code is used to track and differentiate individual products within a database or system.

**(iii)	customer_code:** The 'customer_code' column features unique identification codes for every customer in the dataset. These codes can be used to track a customer's sales history, demographic information, and other relevant details. For example, the codes could look like '70002017', '90005160', and '80007195' respectively.

**(iv) sold_quantity:** The "sold_quantity" column contains the number of units of a product that were sold. This information can be used to understand the sales volume ofproducts and to compare the sales volume of different products or variants.

**(v) fiscal_year:** The "fiscal_year" column holds the fiscal period when the sale of a product occurred.

**Let's see the Ad-hoc requests and gather insights about the product, sales and customer data to help AtliQ Hardwares make data-informed decisions.**

**1.Provide the list of markets in which customer "Atliq Exclusive" operatesits business in the APAC region.**

![q1(3)_Ans](https://github.com/user-attachments/assets/79f80b05-12b0-411e-aaab-b21e1b92819a)

**Insight-**  **Market presence** 

•	Atliq Exclusive operates in eight markets within the APAC region- India, Indonesia, Japan, Philippines, South Korea, Australia, New Zealand and Bangladesh.

•	This shows wide geographical coverage in South and Southeast Asia.

**2. What is the percentage of unique product increase in 2021 vs. 2020?**
   
**The final output contains these fields,**

**unique_products_2020**, **unique_products_2021** , **percentage_chg**

![q2 (3)_Ans](https://github.com/user-attachments/assets/46de4384-1b87-4efd-9e64-2968dd39e52d)

**Insight-** **Product expansion**

• The number of unique products increased from 245 in 2020 to 334 in 2021 showing a 36.33% growth in product variety YoY.

**3. Provide a report with all the unique product counts for each segment and sort them in descending order of product counts.**

**The final output contains 2 fields,**

**segment , product_count**

![q3 (3)](https://github.com/user-attachments/assets/001c0ba7-0fbd-4d68-950c-e636a8c4f408)

**Insight-** **Segment growth**

• The 'Notebook' segment has the highest number of unique products at 129, followed by 'Accessories' with 116 and 'Peripherals' with 84. 

• Segments like 'Desktop', 'Storage' and 'Networking' have significantly fewer products, with no. of 32, 27 and 9 respectively.

**4. Follow-up: Which segment had the most increase in unique products in 2021 vs 2020?**

**The final output contains these fields,**

**segment**, **product_count_2020**, **product_count_2021**, **difference**

![q4 (2)_ans](https://github.com/user-attachments/assets/ac1957d4-3e66-4348-a40f-b5940fd3b8c9)

**Insight:** **Segment growth**

•	In 2021 Accessories segment added the most new products with an increase of 34 compared to 2020. 

•	Notebook and Peripherals segments both added 16 new products.

•	Desktop products tripled from 7 to 22 indicating increase in demand.

**5. Get the products that have the highest and lowest manufacturing costs.**

**The final output should contain these fields,**

****product_code**, **product**, **manufacturing_cost****

![q5_ans](https://github.com/user-attachments/assets/21bfca1e-dae6-427d-9fae-db07a80e6c5a)

**Insight:**  **Manufacturing cost variation**

•	The product with the highest manufacturing cost is 'AQ HOME Allin1 Gen 2' at 240.54. 

•	The product with the lowest manufacturing cost is 'AQ Master wired x1 Ms' at just 0.89. 

•	This shows a large difference in production cost between the two products.

**6. Generate a report which contains the top 5 customers who received an average high pre_invoice_discount_pct for the fiscal year 2021 and in the Indian market.**

**The final output contains these fields,**

**customer_code, customer, average_discount_percentage**

![q6 (2)_Ans](https://github.com/user-attachments/assets/92ab6f61-13c9-40ec-bdc7-ceb701053c81)

**Insight: Customer discount strategy**

These are the top 5 customers by average discount received.

• In the Indian market for fiscal year 2021, Flipkart received the highest average pre-invoice discount of 0.31. 

• Viveks, Croma and Ezone followed closely with an average discount of 0.30. 

• Amazon had a slightly lower average discount of 0.29. 

**7. Get the complete report of the Gross sales amount for the customer “Atliq Exclusive” for each month.**
   
**The final report contains these columns:**

**Month, Year, Gross sales Amount**

![q7_ans](https://github.com/user-attachments/assets/7a5cffc8-991c-4721-a9e1-e212c7532fb6)

**Insight:**  **Monthly sales trend for Atliq Exclusive**

•	In 2021, Atliq Exclusive had higher gross sales compared to 2020 in most months. 

•	In January sales increased from 9.58M in 2020 to 19.57M in 2021. 

•	Similar improvements were seen in February, March, May and August. 

•	The highest sales in the dataset occurred in November 2020 at 32.25M. 

•	These patterns suggest stronger performance in the second half of the year during November and December. 

•	Sales are generally strongest in Q4 and Q1.

**8. In which quarter of 2020, got the maximum total_sold_quantity?**

**The final output contains these fields sorted by the total_sold_quantity,**

**Quarter, total_sold_quantity**

![q8](https://github.com/user-attachments/assets/1b3921a6-4b80-4c59-80e2-f0ebd90c9dbe)

![q8_chart](https://github.com/user-attachments/assets/b0908251-6dc3-41cc-b6cd-51f7ef81e7a4)

**Insight:** **Quarterly sales performance**

•	In the fiscal year 2020, Q1 had the highest total sold quantity with over 7 M units. 

•	Q2 sales was around 6.65 M units. 

•	Q4 saw a drop in sales to 5.04 M and Q3 had the lowest sales with just over 2M units. 

•	This shows that the beginning of the fiscal year had the strongest sales performance.

**9. Which channel helped to bring more gross sales in the fiscal year 2021 and the percentage of contribution?**

**The final output contains these fields,**

**channel, gross_sales_mln, percentage**

![q9_ans](https://github.com/user-attachments/assets/e53eaae1-7550-4bc6-b73b-848f2424dda8)

![q9_chart](https://github.com/user-attachments/assets/8ab2ea0e-ee5b-468d-8103-ac0cdaeca901)

**Insight:** **Sales by Channel**

•	In FY2021 the Retailer channel generated the highest gross sales at 1924.17M which is 73.22% of total sales. 

•	The Direct channel made 406.69 M (15.48%) and the Distributor channel had the lowest sales at 297.18 M (11.31%). 

•	This shows that most of the sales came through the Retail Channel.


**10. Get the Top 3 products in each division that have a high total_sold_quantity in the fiscal_year 2021?**

**The final output contains these fields,**

**division, product_code, product, total_sold_quantity, rank_order**

![q10_ans](https://github.com/user-attachments/assets/df40fefa-a183-422b-bc17-9a9469af07b8)

![q10_chart](https://github.com/user-attachments/assets/ab6b6cfb-5fc9-431f-bfe3-51090699f0a0)

**Insight:** **Top Performing Products**

•	The top-selling product is 'AQ Pen Drive 2 IN 1' from the N & S division with 7,01,373 units sold.

•	Other high-performing products are 'AQ Pen Drive DRC' and 'AQ Gamers Ms' with over 400,000 units sold. 

•	In the PC division, 'AQ Digit' and 'AQ Velocity' had much lower sales, with under 18,000 units each. 

•	This shows that products from the N & S and P & A divisions are selling in much higher volumes compared to the PC division.

•	If the Barchart is looked, the top product sold is 'AQ Pen Drive DRC' with a total quantity sold at 13,64,248 units, 
followed by 'AQ Maxima MS' (total 8,39,336 units sold) and 'AQ Pen Drive 2 IN 1' (total 7,01,373 units sold).







