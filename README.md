Warehouse and Retail Sales Analysis Report
==========================================

1\. Introduction
----------------

The beverage industry is a dynamic and competitive sector where understanding sales performance across various channels and identifying key drivers of revenue are critical for strategic decision-making. This report analyzes a comprehensive dataset of warehouse and retail sales from 2017 to 2020, focusing on alcoholic and non-alcoholic beverages, including beer, wine, liquor, and related supplies. By examining sales trends, supplier performance, and seasonal patterns, this analysis aims to provide actionable insights for stakeholders in the beverage distribution ecosystem.

The objectives of this report are fivefold: (1) to analyze total sales performance across retail and warehouse channels to uncover distribution trends; (2) to identify top-performing suppliers and item types driving revenue; (3) to visualize monthly sales patterns for strategic planning; (4) to compare retail versus warehouse sales contributions to assess business model efficiency; and (5) to evaluate average sales per transaction for key suppliers. These objectives will guide the exploration of the dataset and the formulation of data-driven recommendations.

2\. Source of Dataset
---------------------

The dataset used in this analysis is sourced from the public repository at [https://catalog.data.gov/dataset/warehouse-and-retail-sales](https://catalog.data.gov/dataset/warehouse-and-retail-sales), provided by the U.S. government’s open data initiative. It contains detailed records of beverage sales transactions spanning multiple years (2017–2020), including fields such as year, month, supplier, item code, item description, item type, retail sales, retail transfers, warehouse sales, and total sales. This dataset is a valuable resource for understanding sales dynamics in the beverage industry, offering granular insights into both retail and warehouse distribution channels.

3\. Dataset Preprocessing
-------------------------

The raw dataset required preprocessing to ensure accuracy and usability for analysis. The following steps were undertaken, with corresponding formulas where applicable:

*   **Data Cleaning**: Missing or incomplete entries (e.g., truncated supplier names like "BROWN-...") were identified but retained as they did not significantly impact aggregated metrics. Duplicate rows were checked using a formula to identify unique combinations of key fields:
    
    *   Formula: =IF(COUNTIFS(A$2:A2, A2, B$2:B2, B2, C$2:C2, C2)>1, "Duplicate", "Unique") (where A, B, C represent columns like YEAR, MONTH, ITEM CODE). Duplicates were removed if detected.
        
*   **Column Standardization**: Columns such as "RETAIL SALES," "WAREHOUSE SALES," and "Total Sales" were verified for numerical consistency, converting text-based numbers to float values where necessary using:
    
    *   Formula: =VALUE(TRIM(D2)) (where D2 is a cell with potential text data). This ensured all sales figures were numeric for calculations.
        
*   **Aggregation**: The dataset was summarized to calculate key performance indicators (KPIs) like total sales, retail sales, warehouse sales, and counts of transactions. Aggregations were performed as follows:
    
    *   Total Sales: =SUM(H2:H305701) (where H is the "Total Sales" column).
        
    *   Retail Sales: =SUM(F2:F305701) (where F is "RETAIL SALES").
        
    *   Warehouse Sales: =SUM(G2:G305701) (where G is "WAREHOUSE SALES").
        
    *   Transaction Count: =COUNT(A2:A305701) (where A is any non-empty column, e.g., YEAR).
        
*   **Categorization**: Items were grouped by type (e.g., BEER, WINE, LIQUOR) using pivot tables or a formula to assign categories:
    
    *   Formula: =SUMIFS(H:H, E:E, "BEER") (where E is "ITEM TYPE" and H is "Total Sales") to sum sales by category.
        
*   **Temporal Structuring**: Data was organized by year and month using sorting or filtering, with sales totals calculated per period:
    
    *   Formula: =SUMIFS(H:H, A:A, 2020, B:B, 1) (where A is YEAR, B is MONTH, and H is Total Sales) to aggregate January 2020 sales.
        

The preprocessed dataset, as reflected in the dashboard, contains 305,701 records with a total sales value of $10,071,177.16, split between retail ($2,150,814.03) and warehouse ($7,920,363.13) channels.

4\. Analysis on Dataset
-----------------------

### Objective 1: Analyze Total Sales Performance Across Retail and Warehouse Channels to Uncover Distribution Trends

#### i. General Description

This objective seeks to understand how sales are distributed between retail and warehouse channels over time and across item types, revealing the broader operational dynamics of the beverage distribution model.

#### ii. Specific Requirements

*   Calculate total sales by year and channel (retail vs. warehouse).
    
*   Assess the proportion of sales attributed to each channel.
    
*   Identify trends in sales distribution over the period (2017–2020).
    

#### iii. Analysis Results

The total sales from 2017 to 2020 amount to $10,071,177.16, with warehouse sales dominating at 78.6% ($7,920,363.13) and retail sales contributing 21.4% ($2,150,814.03). Year-wise analysis reveals:

*   **2017**: Total sales of $3,066,587.93, with warehouse sales ($2,381,434.29) far exceeding retail ($685,153.64).
    
*   **2018**: Total sales dropped to $683,014.36, with warehouse ($529,905.59) still leading retail ($153,108.77).
    
*   **2019**: A peak year with $4,568,138.86 in total sales, driven by warehouse ($3,610,456.13) over retail ($957,682.73).
    
*   **2020**: Total sales of $1,753,436.01, with warehouse ($1,398,567.12) maintaining dominance over retail ($354,868.89).
    

The consistent predominance of warehouse sales suggests a business model heavily reliant on bulk distribution, possibly to wholesalers or large retailers, rather than direct-to-consumer retail transactions.

#### iv. Visualization

A line chart plotting total sales by year, with separate lines for retail and warehouse channels, would illustrate the dominance of warehouse sales and the peak in 2019. A stacked bar chart could further break down sales by item type (e.g., BEER, WINE) per year to highlight distribution trends.

### Objective 2: Identify Top-Performing Suppliers and Item Types Driving Revenue in the Beverage Industry

#### i. General Description

This objective focuses on pinpointing the suppliers and item categories that generate the most revenue, providing insights into market leaders and product preferences.

#### ii. Specific Requirements

*   Rank suppliers by total sales.
    
*   Analyze sales distribution across item types (e.g., BEER, WINE, LIQUOR).
    
*   Identify the top 5 suppliers and their contribution to overall revenue.
    

#### iii. Analysis Results

*   **Top 5 Suppliers**:
    
    1.  **CROWN IMPORTS**: $1,736,309.17 (17.2% of total sales)
        
    2.  **MILLER BREWING COMPANY**: $1,512,304.65 (15.0%)
        
    3.  **ANHEUSER BUSCH INC**: $1,507,731.07 (15.0%)
        
    4.  **HEINEKEN USA**: $884,936.74 (8.8%)
        
    5.  **E & J GALLO WINERY**: $363,360.68 (3.6%)These top 5 suppliers collectively account for $6,004,642.31, or approximately 59.6% of total sales, indicating significant concentration among a few key players.
        
*   **Sales by Item Type**:
    
    *   **BEER**: $7,098,227.18 (70.5% of total sales)
        
    *   **WINE**: $1,901,501.47 (18.9%)
        
    *   **LIQUOR**: $896,652.43 (8.9%)
        
    *   **KEGS**: $118,621 (1.2%)
        
    *   Other categories (NON-ALCOHOL, STR\_SUPPLIES, REF) contribute minimally (<1% combined).BEER emerges as the dominant revenue driver, reflecting strong consumer demand or effective distribution in this category.
        

#### iv. Visualization

A bar chart ranking the top 5 suppliers by total sales would clearly showcase their dominance. A pie chart illustrating the sales distribution by item type would emphasize BEER’s overwhelming contribution, with WINE and LIQUOR as secondary drivers.

### Objective 3: Visualize Monthly Sales Patterns to Pinpoint Seasonal Peaks and Troughs for Strategic Planning

#### i. General Description

Understanding monthly sales fluctuations helps identify seasonal trends, enabling better inventory management and marketing strategies.

#### ii. Specific Requirements

*   Aggregate total sales by month across all years.
    
*   Identify peak and trough months.
    
*   Analyze seasonal patterns for strategic insights.
    

#### iii. Analysis Results

Monthly total sales (2017–2020) reveal distinct patterns:

*   **Peak Months**:
    
    *   **July**: $1,397,591.71 (13.9% of annual sales)
        
    *   **September**: $1,255,801.73 (12.5%)
        
    *   **January**: $1,061,796.23 (10.5%)
        
*   **Trough Months**:
    
    *   **April**: $385,156.50 (3.8%)
        
    *   **December**: $444,901.14 (4.4%)
        
    *   **May**: $484,293.05 (4.8%)The summer peak (July) and early fall surge (September) suggest heightened demand during warm weather and possibly back-to-school or harvest seasons. The January peak may reflect post-holiday restocking, while the April trough could indicate a seasonal lull.
        

#### iv. Visualization

A line chart of monthly total sales, averaged across years, would highlight the July and September peaks and the April trough. Overlaying retail and warehouse sales as separate lines could further reveal channel-specific seasonality.

### Objective 4: Compare Retail Versus Warehouse Sales Contributions to Assess Business Model Efficiency

#### i. General Description

This objective evaluates the relative contributions of retail and warehouse channels to total sales, assessing the efficiency and focus of the distribution model.

#### ii. Specific Requirements

*   Compare retail and warehouse sales totals and proportions.
    
*   Analyze channel contributions by month and item type.
    
*   Assess implications for business efficiency.
    

#### iii. Analysis Results

*   **Overall Contribution**: Warehouse sales ($7,920,363.13) account for 78.6% of total sales, dwarfing retail sales ($2,150,814.03) at 21.4%.
    
*   **Monthly Breakdown**: Warehouse sales consistently outpace retail across all months (e.g., July: $1,122,803.34 warehouse vs. $274,788.37 retail), with the gap widest in high-volume months.
    
*   **Item Type Breakdown**:
    
    *   **BEER**: Warehouse ($6,524,306.99) vs. Retail ($566,803.37)
        
    *   **WINE**: Warehouse ($1,156,309.69) vs. Retail ($734,638.07)
        
    *   **LIQUOR**: Warehouse ($94,968.19) vs. Retail ($794,783.57)Liquor is the only category where retail sales exceed warehouse, indicating a direct-to-consumer preference for spirits.
        

The heavy reliance on warehouse sales suggests an efficient bulk-distribution model, though the retail channel’s strength in liquor sales highlights a niche for consumer-facing sales.

#### iv. Visualization

A stacked bar chart comparing retail and warehouse sales by month would illustrate the consistent warehouse dominance. A separate bar chart by item type would highlight liquor’s retail skew.

### Objective 5: Evaluate Average Sales Per Transaction for Key Suppliers

#### i. General Description

This objective assesses the average sales value per transaction for top suppliers, offering insights into their transaction efficiency and customer spending behavior.

#### ii. Specific Requirements

*   Calculate average retail and warehouse sales per transaction for the top 10 suppliers.
    
*   Compare these averages to identify high-value transaction suppliers.
    

#### iii. Analysis Results

*   **Average Retail Sales per Transaction**:
    
    1.  **FIFTH GENERATION INC**: $302.33
        
    2.  **CROWN IMPORTS**: $66.85
        
    3.  **YUENGLING BREWERY**: $50.48
        
    4.  **CHARLES JACQUIN ET CIE INC**: $50.14
        
    5.  **HEINEKEN USA**: $44.09
        
*   **Average Warehouse Sales per Transaction**:
    
    1.  **CROWN IMPORTS**: $1,307.90
        
    2.  **HEINEKEN USA**: $651.07
        
    3.  **MILLER BREWING COMPANY**: $442.47
        
    4.  **YUENGLING BREWERY**: $294.19
        
    5.  **ANHEUSER BUSCH INC**: $243.74FIFTH GENERATION INC leads in retail transaction value, likely due to premium products (e.g., Tito’s Vodka), while CROWN IMPORTS excels in warehouse transactions, reflecting high-volume beer sales (e.g., Corona).
        

#### iv. Visualization

Dual bar charts comparing average retail and warehouse sales per transaction for the top 10 suppliers would highlight FIFTH GENERATION INC’s retail strength and CROWN IMPORTS’ warehouse dominance.

5\. Conclusion
--------------

This analysis reveals a beverage distribution model heavily skewed toward warehouse sales (78.6% of total), with BEER as the primary revenue driver (70.5%). Top suppliers like CROWN IMPORTS and MILLER BREWING COMPANY dominate, contributing nearly 60% of sales, while seasonal peaks in July and September offer opportunities for targeted strategies. The retail channel, though smaller, shows efficiency in liquor sales, suggesting a balanced approach could optimize overall performance. Average transaction values highlight premium retail opportunities (e.g., FIFTH GENERATION INC) and bulk warehouse efficiency (e.g., CROWN IMPORTS).

6\. Future Scope
----------------

The insights derived from this project lay a foundation for several future enhancements and practical applications:

*   **Expanded Data Integration**: Incorporating cost data to assess profitability by channel and supplier, using formulas like Profit = Total Sales - Cost to calculate margins. Extending the dataset beyond 2020 would enable long-term trend analysis.
    
*   **Predictive Analytics**: Applying time-series forecasting models (e.g., ARIMA) to predict seasonal sales peaks, enhancing inventory planning and marketing efforts.
    
*   **Consumer Insights**: Integrating consumer demographics or purchase behavior data to understand demand drivers, potentially using clustering techniques (e.g., K-means) to segment customers.
    
*   **Uses and Benefits**:
    
    *   **Inventory Optimization**: Seasonal insights (e.g., July peaks) can guide stock replenishment, reducing overstocking or shortages and improving cash flow.
        
    *   **Supplier Negotiations**: Identifying top performers like CROWN IMPORTS empowers businesses to negotiate better terms or expand partnerships, boosting profitability.
        
    *   **Marketing Strategies**: Targeting high-transaction-value suppliers (e.g., FIFTH GENERATION INC) for retail promotions can increase per-customer revenue, while warehouse trends inform bulk sales campaigns.
        
    *   **Operational Efficiency**: Understanding retail vs. warehouse dynamics aids in resource allocation, such as staffing retail outlets for liquor sales or scaling warehouse capacity for beer distribution.
        
    *   **Industry Benchmarking**: This analysis can serve as a benchmark for competitors or regulators, offering a standardized view of sales performance in the beverage sector.
        
*   **Broader Impact**: The project’s methodology and findings could be adapted to other industries (e.g., food, retail goods), providing a scalable framework for sales analysis and strategic planning.
    

These advancements would transform this project into a robust tool for decision-making, benefiting distributors, suppliers, and retailers by enhancing efficiency, profitability, and market responsiveness.

7\. References
--------------

*   U.S. Government Open Data. (n.d.). Warehouse人力Retail Sales Dataset. Retrieved from [https://catalog.data.gov/dataset/warehouse-and-retail-sales](https://catalog.data.gov/dataset/warehouse-and-retail-sales)
