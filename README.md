# Insights into New York Airbnb Listings

## Table of Contents
1. [Project Overview](#project-overview)  
2. [Project Objective](#project-objective)  
3. [Data Used](#data-used)  
4. [Key Questions](#key-questions)  
5. [Dashboard](#dashboard)  
6. [Data Cleaning](#data-cleaning)  
   - [Removing Duplicates](#removing-duplicates)  
   - [Handling Missing Values](#handling-missing-values)  
   - [Date Extraction](#date-extraction)  
   - [Handling Outliers](#handling-outliers)  

I developed a comprehensive project in Excel, with detailed tables with Pivot Table, and visualizations in Tabeau. This process includes series of stage, including data processing, data cleaning, descriptive statistics and visualizations.

## Project Objective:
New York City Airbnb data want to provide insights and recommendations to improve the company's business model and increase revenue. By analyzing this data, New York City Airbnb will be able to make data-driven decisions about pricing, marketing, and customer experience.

## Data Used 
- <a href="https://github.com/Nkemjika123/-NEW_YORK_AIRBNB_ANALYSIS/blob/main/newyork_bnb_analysis.xlsx">Dataset</a>

## Key Questions:
1.	What is the average price of Airbnb listings in each neighbourhood and how does it vary by room type?
2.	Which neighborhood have the highest and lowest average prices for Airbnb listings?
3.	How many listings are there per room type, and how does the price and availability vary by room type?
4.	Are there any trends in the popularity of Airbnb listings in different neighbourhoods over time?
5.	What is the impact of reviews on the price and popularity of Airbnb listings?
6.	What are the top hosts and neighbourhoods in terms of customer satisfaction, based on ratings and reviews?
7.	Dashboard interaction - <a href="https://github.com/Nkemjika123/-NEW_YORK_AIRBNB_ANALYSIS/blob/main/Screenshot%202025-01-16%20160016.png">View Dashboard </a>

## DATA CLEANING
•	Remove duplicate – there was no dublicates

•	 I noticed there is missing value in “last report date”, to fill in missing value in a date format - I used: =IF(ISBLANK(M2), "30/07/2019", M2). M2= the date column and “30/07/2019” is the default date.

•	 I used the IF and ISBLANK function in Excel.

•	To extract the DAY, MONTH AND YEAR, I used date function in Excel to  Extract the Day:

•	 I used the DAY function. For example, if your date is in cell A2, you can use =DAY(A2) to get the day.

•	 Extract the Month:
•	Use the MONTH function. For example, =MONTH(A2) will give you the month from the date in cell A2.

•	 Extract the Year:

•	Use the YEAR function. For example, =YEAR(A2) will extract the year from the date in cell A2.

•	I noticed some blank cells in “host_name” , as I could not contact the provider of the data for more information/correction, I decided to fill in the missing host names by cross-referencing other data points, such as “Host_ID”. (This was done to answer the question 6 of my analysis.

•	I noticed blank cells in “Reviews” column, I Calculate the mean of the "Reviews" column and use it to fill missing values.

•	Use =AVERAGE(N2:N48896)  to find these values, then replace missing entries with the result

•	To look for outliers in “Price” column- I first applied the Quartiles Method 

•	 Calculate Quartiles and IQR:

•	Q1: =QUARTILE(J:J, 1)

•	Q3: =QUARTILE(J:J, 3)

•	IQR: =Q3 - Q1

•	To Determine Outlier Boundaries:

•	Lower Bound: =Q1 - 1.5 * IQR

•	Upper Bound: =Q3 + 1.5 * IQR

•	To replace the outliers I use the IF and OR function - =IF(OR(J2 < $Lower_Bound, J2 > $Upper_Bound), "Outlier", "Normal")

•	 Unfortunately, this approach did not work because my lower bound is -90(negative) and my upper bound is 16, which indicate that the data has a very small range or includes negative values. Double-check your dataset I found out that there is a ZERO value in the “Price” column.

•	The zero value in the price column is not valid, because there is, no free services provided in this dataset, non that I am aware of. So, I decided to replace it with the =Avarage method?

•	To Calculate the Average Price:

•	 I used the AVERAGE function to calculate the mean of the non-zero prices. For example, =AVERAGEIF(J:J, ">0") will give you the average of all prices greater than zero.

•	Replace Zero Values:
•	In a new column, I use a formula to replace zero values with the average. =IF(J2 = 0, $Average_Price, J2)

•	 I used this method to maintain the integrity of my dataset by ensuring all prices are realistic. Then I used “Find” and "Replace All" to replace all zero values with the average price.

## DESCRIPTIVE STATISTICS

•	**TO FIND AND REPLACE OUTLIERS IN “PRICE” COLUMN**

•	I used the Z-Score Method:

•	Calculate the mean and standard deviation of the price data.

•	Compute the Z-score for each price: Z = (Price - Mean) / Standard Deviation.

•	 I Set a threshold (of 2 ). Prices with a Z-score beyond this threshold are considered outliers.

•	Then I Replace outliers with the mean of the dataset.

•	TO IDENTIFY THE OUTLIERS

•	I used the if function. =IF(ABS(C2) > 2, "Outlier", "Normal")

•	TO REPLACE THE OUTLIERS

•	I use the “IF” function =IF(ABS(C2) > 2, $D$1, B2)


## Dashboard 
![Screenshot 2025-01-16 160016](https://github.com/user-attachments/assets/33076e05-3099-44f0-bdd5-2f443abe2260)

## Project Insight

**Difference in Price by Room Type:**
I noticed there are no much price difference by room type, it could indicate a few things about the market and provide opportunities for strategic adjustments. Here's how it might affect the business and some strategies the company can follow:
**Impact on Business:**
1.	**Competitive Pricing:**
o	If prices are similar across room types, it might suggest a highly competitive market where differentiation is challenging.
2.	 **Perceived Value:**
o	Guests might not perceive significant value differences between room types, potentially affecting their booking decisions.

3  **Trends in Popularity of Airbnb in different neighborhood overtime:**
I also observed a trend in Airbnb listings, such as a spike in June,this can provide valuable insights for strategic planning. Here are some insights and recommendations based on this trend:
Insights:
1. **Seasonal Demand:**
o	June might be a peak travel month, possibly due to summer vacations, local events, or favorable weather conditions.
o	This trend suggests a higher demand for accommodations during this period.
2.	 **Market Opportunities:**
o	The increase in listings could indicate that hosts are capitalizing on the higher demand by making more properties available.

**Impact of reviews on the price and popularity of Airbnb listing:**
I found that listings with high review counts are very low, it might suggest a few things about the relationship between reviews and listings:
Possible Interpretations:
1.	 **New Listings:**
o	Many listings might be relatively new, which could explain the low number of reviews. Newer listings haven't had enough time to accumulate reviews.
2.	 **Guest Behavior:**
o	Guests might not be leaving reviews consistently, which can result in fewer reviews even for popular listings.
3.	 **Market Dynamics:**
o	The market might be highly competitive, with many listings available, leading to a spread of reviews across numerous properties.


## Recommendation 
**Difference in Price by Room Type:**
1.	**Encourage customer feedback to understand preferences and improve offerings accordingly Enhance Differentiation:**
o	Encourage hosts to highlight unique features or amenities of different room types to justify price differences.
o	Consider offering additional services or experiences that can add value to certain room types.
2.	**Market Segmentation:**
o	Analyze customer segments to tailor marketing strategies. For example, target budget travelers with competitive pricing and luxury seekers with premium offerings.
3.	**Dynamic Pricing:**
o	Implement dynamic pricing strategies to adjust prices based on demand, seasonality, and local events, ensuring competitiveness and maximizing revenue.
4.	**Customer Feedback:**
o	Gather and analyze.
**By focusing on these strategies, the company can better position itself in the market and potentially increase revenue**

**Trends in Popularity of Airbnb in different neighborhood overtime:**
1.	**Dynamic Pricing:**
o	Implement dynamic pricing strategies to maximize revenue during peak months. Adjust prices based on demand to optimize occupancy and profitability.
2.	**Marketing Campaigns:**
o	Launch targeted marketing campaigns leading up to June to attract more guests. Highlight unique experiences or events happening during this time.
3.	 **Host Engagement:**
o	Encourage hosts to prepare their properties for the influx of guests. This could include enhancing amenities or offering special promotions.
4.	**Event Partnerships:**
o	Collaborate with local events or attractions to create package deals, enhancing the appeal of staying in an Airbnb during June.
##By leveraging these insights, Airbnb can better align its strategies with market trends and enhance its competitive edge.

**Impact of reviews on the price and popularity of Airbnb listing:**
1.	**Encourage Reviews:**
o	**Hosts can encourage guests to leave reviews by providing excellent service and sending polite reminders after their stay.**

## Conclusion:
Our analysis of Airbnb listings has yielded significant insights into the factors influencing customer satisfaction and their subsequent impact on pricing and popularity. Through a detailed examination of reviews, several key conclusions have emerged:
1.	**Impact of Reviews:**
The analysis highlighted that while the sheer number of reviews did not directly correlate with higher prices, listings with consistently high ratings tended to attract more bookings. This indicates that quality, as perceived by guests, is a more critical driver of popularity than quantity alone.
2.	** Neighborhood:**
Certain neighborhoods emerged as leaders in customer satisfaction, characterized by higher average ratings and a substantial number of positive reviews. These areas can serve as models for other neighborhoods aiming to enhance their attractiveness to potential guests.
3.	**Host Best Practices:**
Top-performing hosts were found to excel in areas such as hospitality, cleanliness, and accurate listing descriptions. These factors were frequently cited in positive reviews, underscoring their importance in achieving high customer satisfaction.
4.	**Strategic Recommendations:**
Hosts should focus on maintaining high standards of service and actively engage with guest feedback to refine their offerings. Highlighting positive reviews in marketing strategies can further enhance a listing's appeal and competitive edge.

   ## In conclusion, this analysis underscores the pivotal role of customer satisfaction in the Airbnb marketplace and provides actionable insights for hosts seeking to optimize their listings' success.




