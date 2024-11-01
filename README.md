# X-Mas-Sales

### **About the Company & Business Objectives**

With Christmas around the corner, Alex's Retail, a regional retailer, enlisted me as their Business Analyst to uncover insights on sales trends and customer behavior during the festive season. The business has been facing challenges in fulfilling stock demands during peak periods, especially around Black Friday and Christmas sales. The primary objectives are:

1. **Optimize holiday sales** by targeting high-demand products and peak times.
2. **Reduce return rates** by identifying and addressing product categories with the highest returns.
3. **Improve stock and logistics planning** by better understanding demand patterns and customer preferences.


### **About the Dataset**

The dataset used for this analysis consists of six years of sales data, covering November and December. This period includes two major marketing campaigns: Black Friday (the last Friday in October) and Christmas (December 25). Each campaign drives significant sales, and the company is keen to understand which campaign generates more revenue and repeat customers.

Key data points include:

- **Transaction details**: dates, times, amounts, and return status.
- **Customer demographics**: age, gender, and location.
- **Product information**: category, type, and unit price.
- **Shopping channels**: online and in-store.

This data enables a comprehensive look at customer behavior, sales trends, and seasonality patterns across customer demographics and product categories.

**Data Processing**

To prepare the dataset for analysis, the following steps were taken:

- **Data Cleaning**: Ensured data accuracy by removing duplicate transactions and verifying that there were no null values, which could skew insights on transaction volumes and return rates.
- **Calendar Table**: A Calendar Table was added to enable time-based comparisons, like year-over-year (YoY) growth and monthly sales trends, essential for identifying seasonal and campaign-specific trends.

**Return Rate Calculation**: To understand return rates better, values in the `ReturnFlag` column were converted to binary (1 for Yes, 0 for No) using the following DAX formula:

```jsx
Returns = 
SWITCH(
    TRUE(),
    'Sales Record'[ReturnFlag]=TRUE,1,0
)
```

**Transaction Time Analysis**: Rounding transaction times to the nearest hour helps identify peak shopping times.

```jsx
RoundedTime = 
TIME(HOUR('Sales Record'[Time]) + ROUND(MINUTE('Sales Record'[Time]) / 60, 0), 0, 0)
```

**Customer Age Categories**: Customer ages were grouped by decade to enable age-based trend analysis.

```jsx
Age Group = 
SWITCH(
    TRUE(),
    'Sales Record'[Age]>60,"60 above",
    AND('Sales Record'[Age]<60,'Sales Record'[Age]>=50),"50-59",
    AND('Sales Record'[Age]<50,'Sales Record'[Age]>=40),"40-49",
    AND('Sales Record'[Age]<40,'Sales Record'[Age]>=30),"30-39",
    AND('Sales Record'[Age]<30,'Sales Record'[Age]>=20),"20-29",
    "Below 20"
)

```

### Key Insights

**Business Performance**
The analysis revealed that Alex's Retail experienced steady YoY growth, with a 5% increase in sales from 2022 to 2023. However, the return rate also increased by 2%, which warrants attention. **Drones** emerged as the top-selling product again this year, driven by high demand among tech-savvy shoppers.

**Seasonality**

**COVID-19 Impact**: 

The sales decline from 2020 to 2022 aligns with the pandemic, with YoY decreases of 3-5%. However, there was a strong recovery of +16% in 2022-2023, surpassing pre-COVID levels, showing market resilience and an increase in consumer spending post-lockdown.

**Shopping Channel Insights**:

- **74% of sales occurred on weekdays** rather than weekends, indicating a significant deviation from the typical retail trend. This weekday preference suggests that customers shop more during work breaks or after work hours, particularly online.
- **In-store shopping** peaked on Thursdays and Fridays, with Thursday at 12 PM and Friday at 3 PM being the busiest times.
- **Online shopping** showed a peak on weekday evenings from 7 PM to 9 PM, with late-night hours (12 AM) dominating weekends.

This insight highlights potential to align promotions and operational hours with customer shopping habits.

**Product Performance**

**Electronics & Toys** are the top-selling categories, making up 82% of total sales across five categories. Within electronics, **TVs, Drones, and Laptops** are the best sellers, contributing 32% of the total electronic sales. Notably, these products have shown steady growth since 2022 and are the most popular across all states where Alex's Retail operates.

However, Electronics and Decorations exhibit the highest return rates (50%). **Gaming Consoles** and **Headphones** in Electronics, and **Christmas Trees** and **Centerpieces** in Decorations, account for over 56% of returns, suggesting a need to refine return policies and ensure product quality in these categories.

**Customer Segment**

The **Gen-Z** (ages 20-29) and **Millennial** (ages 30-39) segments collectively make up over 50% of sales, dominating all categories except for Food. Interestingly, **Baby Boomers** (60+) are highly responsive to promotions, as they tend to be more budget-conscious.

There’s a notable preference for digital payment methods among Gen-Z, who favor debit cards and online payments, while Millennials show a tendency toward cash. **Credit card usage emerged as the preferred payment method overall**, highlighting an opportunity for credit-based incentives or loyalty programs.

### **Recommendations**

Based on the findings, here are several recommendations for Alex’s Retail to optimize their sales strategy and improve customer satisfaction during the holiday season:

1. **Enhance Online Shopping Experience**:
    - Invest in website UX/UI improvements to streamline the checkout process and reduce cart abandonment.
    - Consider creating a dedicated mobile app to cater to younger customers who prefer mobile shopping.
2. **Midnight Sales for Gen-Z and Millennials**: Since younger customers shop predominantly at night (8 PM - 3 AM), **introducing midnight sales or flash sales** can help capture this demographic more effectively.
3. **Promote Weekday and Time-Specific Discounts**: Since weekday sales dominate:
    - Run promotions during weekday evenings and late nights, particularly targeting online shoppers who shop after work hours.
4. **Revise Return Policy for High-Return Categories**:
    - For seasonal items like Christmas Trees, ensure clear return policies to minimize losses from post-holiday returns.
    - Offer product guides or demos for high-return electronics like gaming consoles to help set customer expectations.
5. **Holiday Return Policy Extension**: Offer an extended holiday return window, allowing customers to make larger purchases with confidence, knowing they can return items if needed.
6. **Customer Loyalty Programs for Boomers**: To cater to Baby Boomers’ sensitivity to promotions, implement loyalty rewards or discounts on bulk purchases. This can encourage larger purchases and build customer loyalty among this budget-conscious segment.
7. **Leverage Payment Preferences for Marketing**:
    - Create credit-based promotions (like cashback offers) and introduce buy-now-pay-later options to appeal to Gen-Z and Millennials.
    - Highlight these payment options in marketing materials, emphasizing flexibility for holiday shopping.
8. **Refine Product Quality and Marketing for Electronics & Decorations**:
    - For electronics, ensure high-quality standards and consider adding extended warranties or service plans to mitigate returns.
    - For holiday decorations, improve product descriptions and ensure the quality of materials, particularly for items with high return rates, to set customer expectations.

### **Conclusion**

Through targeted recommendations, Alex’s Retail can capitalize on these insights to meet customer demands, reduce operational bottlenecks, and boost profitability. By refining their marketing, return policies, and shopping experience, they can provide a better shopping experience tailored to each customer segment, ultimately fostering loyalty and increasing sales during the high-stakes holiday season.

Thank you for staying until the end. This PowerBi file is available on my [Github Repository](https://github.com/WanQi-K/X-Mas-Sales/tree/main), feel free to star this repository so you can always come back refer to it.

While I am sure you learned a thing or two here, do leave a comment, claps or share with someone who you think would like to check this post out.

Until my next post, you can reach me on [LinkedIn](https://www.linkedin.com/in/wan-qi-khaw-2ba442185/) or email me at [kwanqi.yt@gmail.com](mailto:kwanqi.yt@gmail.com).
