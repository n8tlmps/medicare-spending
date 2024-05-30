<!DOCTYPE html>
<html>
    <h1>Medicare Spending</h1>
    <section id='Introduction'>
    <h2>Introduction</h2>
        <p>
In this detailed exploration, Medicare spending data from 2011 to 2015 was examined to identify and analyze spending patterns across the United States. The dataset used in this study summarizes the utilization and payments for procedures, services, and prescription drugs provided to Medicare beneficiaries by specific inpatient and outpatient hospitals, physicians, and other suppliers. It includes data on common inpatient and outpatient services, all physician and other supplier procedures and services, and all Part D prescriptions.
    
By investigating the average Medicare payments made to providers in each state over these years, this analysis aims to uncover trends and variations in healthcare expenditures. The findings from this study provide valuable insights into how Medicare resources are allocated and highlight significant differences in spending across different regions of the country. For more information: <a href="https://data.cms.gov/tools">click here</a>
</p>
    </section>
    <section id='setup'>
        <h2>Setup</h2>
        <p> The dataset for this study was obtained using Google BigQuery, a powerful and scalable data warehouse solution provided by Google Cloud. BigQuery enables users to run fast, SQL-like queries on large datasets, making it an ideal tool for handling extensive Medicare spending data. By leveraging BigQuery, the data extraction process was efficient and seamless, allowing for the integration of multiple years of data (2011 to 2015) from various Medicare-related tables. The benefits of using BigQuery include its ability to handle large-scale data analysis with high performance, its support for real-time data processing, and its ease of use for executing complex queries.
        </p>

<!-- Gets data from 2011 to 2015 -->

    WITH combined_data AS 
    (SELECT provider_state, average_medicare_payments, 2011 AS year FROM `bigquery-public-data.cms_medicare.inpatient_charges_2011` UNION ALL 
    SELECT provider_state, average_medicare_payments, 2012 AS year FROM `bigquery-public-data.cms_medicare.inpatient_charges_2012` UNION ALL 
    SELECT provider_state, average_medicare_payments, 2013 AS year FROM `bigquery-public-data.cms_medicare.inpatient_charges_2013` UNION ALL 
    SELECT provider_state, average_medicare_payments, 2014 AS year FROM `bigquery-public-data.cms_medicare.inpatient_charges_2014` UNION ALL 
    SELECT provider_state, average_medicare_payments, 2015 AS year FROM `bigquery-public-data.cms_medicare.inpatient_charges_2015`) SELECT provider_state, year, AVG(average_medicare_payments) AS avg_medicare_payments FROM combined_data GROUP BY provider_state, year ORDER BY provider_state, year;
</section>

<img src='map_2011.jpg' />
</html>




