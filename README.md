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

**(V) market:** The 'market' column lists the countries in which the customer is located.

**(vi) region:** The 'region' column categorizes countries according to their geographic location, including "APAC" (Asia Pacific), "EU" (Europe), "NA" (North America), and  "LATAM" (Latin America).

**(vii)	The 'sub_zone'** column further breaks down the regions into sub-regions, such as "India", "ROA" (Rest of Asia), "ANZ" (Australia and New Zealand), "SE" Southeast Asia), "NE" (Northeast Asia), "NA" (North America), and "LATAM" (Latin America).




