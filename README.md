<!DOCTYPE html>
<html>
    <h1>Medicare Spending</h1>

    <!-- Gets data from 2011 to 2015 -->
    WITH combined_data AS (
    SELECT 
        provider_state,
        average_medicare_payments,
        2011 AS year
    FROM `bigquery-public-data.cms_medicare.inpatient_charges_2011`
    
    UNION ALL
    
    SELECT 
        provider_state,
        average_medicare_payments,
        2012 AS year
    FROM `bigquery-public-data.cms_medicare.inpatient_charges_2012`
  
    UNION ALL
    
    SELECT
        provider_state,
        average_medicare_payments,
        2013 AS year
    FROM `bigquery-public-data.cms_medicare.inpatient_charges_2013`
    
    UNION ALL
    
    SELECT 
        provider_state,
        average_medicare_payments,
        2014 AS year
    FROM `bigquery-public-data.cms_medicare.inpatient_charges_2014`
    
    UNION ALL
    
    SELECT
        provider_state,
        average_medicare_payments,
        2015 AS year
    FROM `bigquery-public-data.cms_medicare.inpatient_charges_2015`
    )
    
    SELECT
        provider_state,
        year,
        AVG(average_medicare_payments) AS avg_medicare_payments
    FROM combined_data
    GROUP BY provider_state, year
    ORDER BY provider_state, year;

<img srs='medicare_spending_2011' />
</html>


