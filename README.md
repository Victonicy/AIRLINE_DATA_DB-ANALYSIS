# AIRLINE_DATA_DB-ANALYSIS

### Project Overview

This report presents an analysis of a global airline dataset using PostgreSQL and Microsoft Excel. The dataset was prepared, cleaned, and analyzed to uncover insights about passenger demographics, travel patterns, and flight operations. Key objectives included setting up a database, cleaning data, performing queries to extract meaningful information, and understanding trends. This analysis highlights the operational aspects of the airline industry and identifies areas for improvement, such as punctuality and customer targeting.

### Data Source

Airline Date: The primary data set used for this analysis is the "Airline_Dataset_v2" file offering insights into the functioning and efficiency of the aviation industry.

### Tools

- Postgresql (Data Cleaning, filtering and Analysis)
- Microsoft Excel (Data analysis and report creation) [Download here](https://docs.google.com/spreadsheets/d/1Df1o9T5V7MXWneaqlRkih0QA22q6xTu1/edit?usp=drive_link&ouid=106771351717866251422&rtpof=true&sd=true)

### Data Cleaning and Preparation

Data inconsistencies were identified and addressed to ensure accuracy in analysis. Specific actions included:
Removing Invalid Arrival_airport Entries:
- Records with '0' or '-' in Arrival_airport were deleted.
Transaction Management:
- Changes were made within transactions to allow rollback in case of errors.

### Data Analysis
- How many flights were cancelled, delayed, and on time in Europe?
- What are the differences in flight statuses between male and female passengers?
- Which month recorded the highest number of flight cancellations?
- During which month were the fewest flights cancelled?
- In which month did the highest number of flights experience delays?
- When were delayed flights at their lowest?
- Which month recorded the highest number of on-time flights?
- When were on-time flights at their lowest?
- Which airport recorded the highest number of flight cancellations?
- Which airports had the highest number of delayed flights?
- Where were the most on-time flights recorded?
- What is the earliest and latest departure date in the dataset?
  ```Sql
  SELECT MIN(Departure_date), MAX(Departure_date)
  FROM airline_data_tb;

- What are the distinct flight statuses, arrival airports, pilot names, and continents in the dataset?
  ```sql
  SELECT DISTINCT((Flight_status),(Arrival_airport),(pilot_name),(Continents))
  FROM airline_data_tb;

- How can we filter the data to show passengers from a specific nationality, such as Japan?
  ```sql
  SELECT Passenger_id, First_name, Last_name,Gender, Age, Airport_country_code, Departure_date, Arrival_airport
  FROM airline_data_tb
  WHERE Nationality = 'Japan';

- How can we identify passengers whose nationality contains a specific pattern, such as 'ria'?
  ```sql
  SELECT Passenger_id, First_name, Last_name,Gender, Age, Nationality, Airport_country_code, Departure_date, Arrival_airport
  FROM airline_data_tb
  WHERE Nationality LIKE '%ria%'; 

- How can we retrieve data for female passengers over 45 years old arriving at a specific airport, such as 'CXF'?
  ```sql
  SELECT Passenger_id, First_name, Last_name,Gender, Age, Airport_country_code, Departure_date, Arrival_airport
  FROM airline_data_tb
  WHERE gender = 'Female'AND Age > 45 AND Arrival_airport = 'CXF';

- What is the total number of passengers, minimum age, maximum age, and average age for each gender?
```sql
  SELECT Gender, 
  COUNT(*) AS Total_passangers,
  MIN(Age) AS Min_age,
  MAX(Age) AS Max_age,
  ROUND(AVG(Age),2) AS Avg_age
  FROM airline_data_tb
  GROUP BY Gender;
```

- Extraction od data from the airline_data_tb table for records specific to the United Kingdom.
```sql
SELECT *
FROM airline_data_tb
WHERE Country_name = 'United Kingdom';
```
  
### Results/Findings

Overall Flight Status
 - A total of 466 flights were cancelled, 460 delayed, and 445 on time, showing a slightly higher frequency of cancellations.
 - Male passengers experienced slightly fewer delays and cancellations compared to females, but both genders had similar distributions of flight statuses.

Flight Status by Time
 - February recorded the most cancellations (47), potentially due to weather-related challenges typical of winter months.
 - September had the fewest cancellations, suggesting improved operational efficiency during this period.
 - Delays peaked in January (45), possibly linked to post-holiday congestion. Delays were minimal in June and July (32 each), indicating smooth operations during these months.
 - On-time flights were highest in April (43), potentially due to favorable conditions, while February saw the lowest on-time performance (30), reflecting the impact of disruptions.

Flight Status by Airports
 - Belfast International Airport faced the most cancellations (10), possibly due to its high traffic volume or specific challenges.
 - Raf Fairford and St. Mary’s Airport recorded the most delays (9 each), pointing to potential logistical or operational issues.
 - Raf Mildenhall Airport excelled in punctuality with the highest number of on-time flights (9), showcasing its efficient processes.

### Recommendations

Based on the analysis, we recommend the following actions:
- Focus on mitigating challenges during February and January, such as enhanced scheduling, weather resilience strategies, and additional resources for high-demand periods.
- Investigate and address specific issues at Belfast International Airport, Raf Fairford, and St. Mary’s Airport to reduce cancellations and delays. Collaborate with airport authorities to identify bottlenecks.
- Analyze practices at Raf Mildenhall Airport and replicate its successful strategies at other airports to improve overall on-time performance.
- Use insights from monthly patterns to adjust schedules and resources proactively, particularly during high-risk months like February and January.
- Further examine the slight disparities in flight statuses by gender to identify any underlying causes and ensure equitable service delivery.
