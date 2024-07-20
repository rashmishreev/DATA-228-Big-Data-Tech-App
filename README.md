![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54) ![AmazonS3](https://img.shields.io/badge/Amazon_S3-FF9333?style=for-the-badge&logo=amazons3&logoColor=black) ![Redshift](https://img.shields.io/badge/Amazon_Redshift-%238C4FFF?style=for-the-badge&logo=amazonredshift&logoColor=black) ![AWSGlue](https://img.shields.io/badge/AWS_Glue-B2FF33?style=for-the-badge&logoColor=black) ![Spark](https://img.shields.io/badge/Apache_Spark-%23E25A1C?style=for-the-badge&logo=apachespark&logoColor=black) ![Tableau](https://img.shields.io/badge/Tableau-%23E97627?style=for-the-badge&logo=tableau&logoColor=black)

## ATM Transactions Data Analysis for Spar Nord Bank Using AWS

### Project Overview
This project analyzes Spar Nord Bank's ATM transaction data to optimize their ATM network, enhance security, and improve customer service. Utilizing AWS services and big data tools, a robust ETL pipeline was created to process and analyze over 2.5 million ATM transactions.

### Problem Statement
The primary goal is to improve ATM management and usage patterns, which is crucial for providing an efficient, secure, and customer-oriented banking experience. The project aims to gain insights into customer withdrawals and ATM usage to minimize costs and mitigate risks associated with fraudulent activities.

### Key Objectives
- Analyze ATM usage patterns and customer behavior.
- Optimize ATM placement and cash management.
- Enhance security measures and fraud detection.
- Improve overall customer experience.

### Data Overview
The [dataset](https://www.kaggle.com/datasets/sparnord/danish-atm-transactions) consists of over 2.5 million records of ATM transactions, including transaction date and time, amount, location, transaction type, and success status. The data is stored in RDS, extracted using Sqoop, and initially cleaned before being stored in Amazon S3 for further processing.

## Architecture and Project Flow
1. **Data Extraction**: Data is extracted from RDS and stored directly in AWS S3 as CSV files.
2. **Data Preprocessing**: PySpark is used for initial cleaning and transformation of the data.
3. **Data Storage**: Processed data is stored in AWS S3.
4. **ETL Process**: AWS Glue is utilized for Extract, Transform, Load operations from S3 to Redshift.
5. **Data Warehousing**: Transformed data is loaded into AWS Redshift for analysis.
6. **Analysis**: In-depth analysis is performed using Redshift Query Editor.
7. **Visualization**: Interactive dashboards are created using Tableau and Redshift Query Editor V2.
   
![](/images/architecture.png)

### Data Modeling
- Implemented Star Schema design.
- **Fact Table**: `fact_atm_trans`
- **Dimension Tables**: `atm`, `date`, `location`, `card_type`

![](/images/data_model.png)

### Data Engineering Process
1. **Data Import**: Schema definition and merging of CSV files into a single DataFrame.
2. **Data Cleaning**: 
   - Data validation
   - Removing duplicates and irrelevant columns
   - Handling outliers
   - Resolving inconsistencies
3. **Feature Engineering**: Created 'full_date_time' attribute.
4. **Dimension and Fact Table Creation**: Separate tables for location, card_type, date, ATM, and transactions.

### ETL Process
1. **Data Lake**: Raw and processed data is stored in Amazon S3.
2. **Metadata Extraction**: AWS Glue Crawler extracts metadata into Glue Data Catalog.
3. **Data Transformation**: PySpark scripts in AWS Glue jobs for data transformation.
4. **Security**: VPC and VPC Endpoint are used for secure data processing.
5. **Data Loading**: Transformed data is loaded into Amazon Redshift.
6. **Verification**: Data integrity is checked using Redshift Query Editor V2.

## ATM Transaction Analysis Results

#### Top 10 ATMs with Highest Inactive Transactions
![Top 10 Inactive ATMs](/images/Top%2010%20ATMs%20with%20the%20highest%20percentage%20of%20'inactive'%20transactions.png)
This visualization shows the ATMs with the highest percentage of failed transactions helping the bank identify problematic ATMs that need immediate attention or maintenance, improving overall customer experience.

#### ATM Failures by Weather Conditions

<img src="/images/ATM%20failures_various%20weather%20conditions.png" width="400" align="left" style="margin-right: 20px;">

This graph illustrates how weather conditions impact ATM functionality. It allows the bank to anticipate potential issues during extreme weather and take preventive measures.

<br clear="left">

#### Top 10 ATMs with Most Transactions
![Top 10 Busy ATMs](/images/Top%2010%20ATMs%20with%20the%20most%20transactions.png)
Highlighting the busiest ATMs helps the bank identify locations that may need additional machines or more frequent maintenance and cash replenishment.

#### Monthly Inactive Transactions
![Monthly Inactive Transactions](/images/overall%20ATM%20transactions%20going%20inactive%20per%20month.png)
This chart shows the number of unsuccessful transactions per month, helping the bank identify seasonal trends in ATM failures and plan maintenance accordingly.

#### Top 10 ATMs by Withdrawal Amount
![Top 10 ATMs by Withdrawal](/images/Top%2010%20ATMs%20with%20the%20highest%20amount%20of%20money%20withdrawn%20overall%20.png)
This visualization identifies ATMs handling the highest cash volumes, assisting in cash management and security planning.

#### Unsuccessful Transactions by Card Type
![Unsuccessful Transactions by Card Type](/images/Number%20of%20unsuccessful%20ATM%20transactions%20using%20different%20card%20types.png)
This chart helps the bank understand which card types are associated with more failed transactions, potentially leading to improvements in card technology or customer education.

#### Transaction Volume by Time of Day

<img src="/images/Transaction%20Volume%20by%20Time%20of%20Day.png" width="400" align="left" style="margin-right: 20px;">

The resultset shows peak transaction hours, helping the bank schedule maintenance and cash replenishment during off-peak times to minimize customer inconvenience.

<br clear="left">

#### Card Type Usage
![Card Type Usage](/images/Card%20Type%20Usage.png)
This visualization shows the popularity of different card types, helping the bank tailor its services and potentially negotiate better terms with card providers.

#### Daily Transaction Trends
![Daily Transaction Trends](/images/Daily%20Transaction%20Trends.png)
This line chart shows daily transaction patterns, helping the bank understand long-term trends and seasonality in ATM usage.

> These reports provide valuable insights that can help the bank optimize ATM placement, improve maintenance schedules, enhance cash management, and ultimately provide better service to customers. By understanding usage patterns, identifying problematic ATMs, and recognizing external factors that affect ATM usage, the bank can make data-driven decisions to improve efficiency and customer satisfaction.

### Conclusion

Spar Nord Bank's ATM transaction data is analyzed using AWS services to optimize ATM management and usage. Key findings include:

- Peak transaction hours: 10 AM - 12 PM
- Most used cards: Visa, followed by Mastercard
- Significant impact of temperature on ATM usage

> These insights can guide ATM refill schedules, inform partnership strategies, and improve customer comfort at ATM locations. The analysis provides a data-driven foundation for enhancing the bank's ATM network efficiency.

## Project Files
- `ThePieSparkersDATA228_BDT_project.ipynb`: Jupyter notebook containing the project code
- `ThePieSparkersProject_plan_v3.0.pdf`: Detailed project plan
- `ThePieSparkers_DATA228_ATM_Transactions_Analysis.pptx`: Project presentation slides
- `ThePieSparkers_DATA228_projectreport.pdf`: Comprehensive project report
- `atm_data_part1.csv.zip`: First part of the ATM transaction dataset (compressed)
- `atm_data_part2.csv.zip`: Second part of the ATM transaction dataset (compressed)
- `images/`: Directory containing visualization images
- `README.md`: This file, providing an overview of the project
> These files encompass the complete project, including code, documentation, data, and presentation materials.


