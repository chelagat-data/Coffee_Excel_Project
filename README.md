**PROJECT SUMMARY**

As a data analyst at Company X, tasked with examining sales data from 2019 to 2022, the objective is to gain insights into the company's performance in the United States, Ireland, and the United Kingdom markets. By analyzing sales data over the specified period, the aim is to identify trends, patterns, and opportunities for optimization and growth.


**QUESTIONS TO ANSWER**
1. How does Company X's sales performance vary across the United States, Ireland, and the United Kingdom?
2. What seasonal patterns can be observed in coffee sales within each market?
3. Who are the top 5 customers?


**DATA SOURCE**

I will use Company X's coffee data to analyze and identify trends from Jan 2019 to July 2022 which can be downloaded from https://github.com/mochen862/excel-project-coffee-sales/blob/main/coffeeOrdersData.xlsx.


**DATA EXPLORATION**

The data set has three sheets, orders, customers, and products. 

The order sheet has five columns; Order ID,	Order Date,	Customer ID,	Product ID, and	Quantity.

![image](https://github.com/tabby1307/Coffee_Excel_Project/assets/112205355/274ef05f-c8f1-4cce-b3e9-34dfeecdced0)

The customer sheet has nine columns; Customer ID,	Customer Name,	Email,	Phone Number,	Address Line 1,	City,	Country,	Postcode, and Loyalty Card.

![image](https://github.com/tabby1307/Coffee_Excel_Project/assets/112205355/f45653e5-1735-4b8a-b1ee-5ac9547efa82)

The Products sheet has seven columns; Product ID,	Coffee Type,	Roast Type,	Size,	Unit Price,	Price per 100g, and	Profit.

![image](https://github.com/tabby1307/Coffee_Excel_Project/assets/112205355/b1d7d190-1569-4bac-9760-a2307e20f13b)

All three sheets have 1001 rows with no duplicates.


**DATA FORMATTING**

All the information was aggregated to the Orders sheet.
With the customer's ID as the primary key, the XLOOKUP function was used to populate the customer's name, email, country, and loyalty card from the customer's sheet.

**Customer's name**: =XLOOKUP(C5,customers!$A$1:$A$1001,customers!$B$1:$B$1001,,0)

**Customer's email**: =IF(XLOOKUP(C5,customers!$A$1:$A$1001,customers!$C$1:$C$1001,,0)=0,"",XLOOKUP(C4,customers!$A$1:$A$1001,customers!$C$1:$C$1001,,0))

**Customer's country**: =XLOOKUP(C5,customers!$A$1:$A$1001,customers!$G$1:$G$1001,,0)

**Loyalty card**: =XLOOKUP(C5,customers!$A$1:$A$1001,customers!$I$1:$I$1001,0)

The XLOOKUP function was also used to populate the coffee type, size, roast type, and unit price from the products sheet with the product ID as the primary key.

**Coffee type**: =XLOOKUP(D3,products!$A$1:$A$49,products!$B$1:$B$49,0)

**Roast type**: =XLOOKUP(D3,products!$A$1:$A$49,products!$C$1:$C$49,0)

**Size**: =XLOOKUP(D3,products!$A$1:$A$49,products!$D$1:$D$49,0)

**Unit price**: =XLOOKUP(D3,products!$A$1:$A$49,products!$E$1:$E$49,0)

The dataset was later augmented by introducing a new column labeled "Sales," computed using the formula "=L2*E2". This formula multiplies the values in column "L" (quantity of units sold) by the corresponding values in column "E" (denoting unit price per unit), resulting in the calculation of total sales for each entry in the dataset.

**DATA TRANSFORMATION**

For easy interpretation, I transformed the abbreviations Rob, Exc, Ara, and Lib, which are coffee types to Robusta, Excelds, Arabia, and Liberica, respectively, using the following formula: 

=IF(I2="Rob","Robusta",IF(I2="Exc","Excelds",IF(I2="Ara","Arabia",IF(I2="Lib","Liberica","")))) 

and M, L, and D, which are roast type, to Medium, Light and Dark using the following formula: 

=IF(J2="L","Light",IF(J2="M","Medium",IF(J2="D","Dark",""))).

**DATA ANALYSIS**

The data is stored appropriately and is now prepared for analysis. I queried multiple relevant tables for the analysis using pivot tables and visualized them.
The analysis question is: What seasonal patterns can be observed in coffee sales within each market?

First of all, sales are compared from 2019 to 2022 for the different types of coffee.
![image](https://github.com/tabby1307/Coffee_Excel_Project/assets/112205355/b0f1a332-5431-4aae-9f5e-8b9b8a893702)

Sales tend to peak during certain months across all four coffee types. There are spikes in sales around February-March and August-September in each year. These peaks coincide with periods of increased coffee consumption due to seasonal factors. For instance, in many regions, there could be a spike in coffee consumption during the colder winter months (February- March) as people seek warm beverages. Similarly, the late summer months (August-September) might see heightened coffee consumption as people return to their routines after vacations or seek refreshments in warmer weather.

Sales appear to dip during certain months as well, in May and November. In May, consumers might be more focused on outdoor activities as the weather improves, leading to less indoor coffee consumption. In November, consumers might be more focused on holiday preparations and spending, diverting funds away from discretionary purchases like coffee.

Next, sales performance across the United States, Ireland, and the United Kingdom was examined.

![image](https://github.com/tabby1307/Coffee_Excel_Project/assets/112205355/994b18ff-4da5-460a-8f2d-77b6e164080c)

While the UK has a strong coffee culture with a significant presence in coffee shops, tea remains a traditional favorite beverage. This cultural preference for tea may somewhat limit the growth of the coffee market.

The proliferation of coffee shop chains like Starbucks, Dunkin', and local independent cafes has significantly contributed to the growth of the coffee market in the US. These outlets serve as social hubs and convenient locations for consumers to purchase coffee on the go.

Finally, the top 5 consumers were examined

![image](https://github.com/tabby1307/Coffee_Excel_Project/assets/112205355/3381bf41-5f57-474c-b2c1-983edf36937f)


**DASHBOARD**

![Screenshot (192)](https://github.com/tabby1307/Coffee_Excel_Project/assets/112205355/5068ada1-695c-452d-8a52-0c4b61719aa0)


On the dashboard, I implemented interactive features to enhance data exploration and analysis:

**Timeline Filter**:

I added a timeline filter component, allowing stakeholders to navigate through different periods of the year dynamically. Users can select specific time ranges or periods of interest, such as months, quarters, or years, to focus on relevant data subsets. This feature enables stakeholders to track sales trends over time and identify seasonal patterns or fluctuations in coffee consumption.
Slicers for Roast Type, Size, and Loyalty:

Additionally, I incorporated **slicers** for roast type, size, and loyalty, providing stakeholders with further data filtering options. Users can refine their analysis by selecting specific roast types (light, medium, dark), coffee sizes, or customer loyalty status (yes, no). These slicers enable stakeholders to segment the data based on different product attributes or customer characteristics, facilitating deeper insights into sales performance and consumer preferences. By adjusting these slicers, users can explore how sales vary across different product categories or customer segments, helping inform strategic decision-making and marketing efforts.

**ACT**

**Expand Marketing Efforts in the United Kingdom**:

Given the relatively lower sales figures in the United Kingdom compared to Ireland and the United States, the company could focus on expanding its marketing efforts in the UK market. This could include targeted advertising campaigns, promotions, and partnerships with local cafes and retailers to increase brand visibility and customer engagement. By raising awareness and generating excitement around its coffee products, the company can attract new customers and drive sales growth in the UK.

**Introduce Specialty Coffee Offerings in Ireland**:

With Ireland experiencing a cultural shift towards embracing coffee culture and a growing demand for specialty coffee beverages, the company could capitalize on this trend by introducing new specialty coffee offerings tailored to the Irish market. This could include unique blends, single-origin coffees, and innovative brewing methods to appeal to discerning coffee enthusiasts. By catering to the evolving preferences of Irish consumers and offering premium coffee experiences, the company can capture a larger share of the market and drive sales expansion in Ireland.

**Enhance Customer Loyalty Programs in the United States**:

Given the significant sales volume in the United States and the competitive landscape of the coffee market, the company could focus on enhancing its customer loyalty programs to incentivize repeat purchases and foster customer retention. This could involve offering exclusive discounts, rewards, and personalized perks to loyal customers, encouraging them to choose Company X for their coffee needs consistently. By building strong relationships with its customer base and rewarding loyalty, the company can increase customer lifetime value, drive repeat business, and ultimately boost sales in the US market.






