# AIRLINE_DATA_DB-ANALYSIS

### Project Overview

This report presents an analysis of a global airline dataset using SQL in PostgreSQL. The dataset was prepared, cleaned, and analyzed to uncover insights about passenger demographics, travel patterns, and flight operations. Key objectives included setting up a database, cleaning data, performing queries to extract meaningful information, and understanding trends. This analysis highlights the operational aspects of the airline industry and identifies areas for improvement, such as punctuality and customer targeting.

### Data Source

Airline Date: The primary data set used for this analysis is the "Airline_Dataset_v2" file offering insights into the functioning and efficiency of the aviation industry.

### Tools

- Postgresql

### Data Cleaning and Preparation

Data inconsistencies were identified and addressed to ensure accuracy in analysis. Specific actions included:
Removing Invalid Arrival_airport Entries:
- Records with '0' or '-' in Arrival_airport were deleted.
Transaction Management:
- Changes were made within transactions to allow rollback in case of errors.

### Data Analysis

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

### Results/Findings
-

### Recommendations
- 

