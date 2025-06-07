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

**Let's see the Ad-hoc requests and gather insights about the product, sales and customer data to help AtliQ Hardwares make data-informed decisions.****

**1.Provide the list ofmarkets in which customer "Atliq Exclusive" operatesits business in the APAC region.**

![q1(3)_Ans](https://github.com/user-attachments/assets/79f80b05-12b0-411e-aaab-b21e1b92819a)

**Insight-**  **Market Presence** 

•	Atliq Exclusive operates in eight markets within the APAC region- India, Indonesia, Japan, Philippines, South Korea, Australia, New Zealand and Bangladesh.

•	This shows wide geographical coverage in South and Southeast Asia.

**2. What is the percentage of unique product increase in2021 vs. 2020?**
   
**The final output contains these fields,**

**unique_products_2020**

**unique_products_2021**

**percentage_chg**

![q2 (3)_Ans](https://github.com/user-attachments/assets/46de4384-1b87-4efd-9e64-2968dd39e52d)

**Insight-** **Product Expansion**
• The number of unique products increased from 245 in 2020 to 334 in 2021 showing a 36.33% growth in product variety YoY.

•The Notebook and Accessories segments lead the product count with 129 and 116 unique items respectively.

****3. Provide a report with all the unique product counts for each segment and sort them in descending order of product counts.**

**The final output contains 2 fields,**

**segment , product_count**

![q3 (3)](https://github.com/user-attachments/assets/001c0ba7-0fbd-4d68-950c-e636a8c4f408)

**Insight-** **Segment Growth**
• The 'Notebook' segment has the highest number of unique products at 129, followed by 'Accessories' with 116 and 'Peripherals' with 84. 

• Segments like 'Desktop', 'Storage' and 'Networking' have significantly fewer products, with no. of 32, 27 and 9 respectively.

**4. Follow-up: Which segment had the most increase in unique products in 2021 vs 2020?**

**The final output contains these fields,**

**segment**

**product_count_2020**

**product_count_2021**

**difference**

![q4 (2)_ans](https://github.com/user-attachments/assets/ac1957d4-3e66-4348-a40f-b5940fd3b8c9)

**Insight** 

•	In 2021 Accessories segment added the most new products with an increase of 34 compared to 2020. 

Notebook and Peripherals segments both added 16 new products. This shows that Accessories and Desktop had the strongest growth in product variety.

•	Desktop products tripled from 7 to 22 indicating increase in demand.





