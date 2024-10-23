# Second hand Data analysis- SQL

## Project Overview
This project demonstrates the use of SQL for analyzing a dataset containing information about used cars. The dataset includes various features such as year, fuel type, transmission type, selling price, mileage, and more. I have performed multiple SQL queries to extract meaningful insights about the cars and their attributes.


### This project involves a dataset that includes car listings, with attributes like:

- Year: Year of manufacture.
- Fuel: Type of fuel (Petrol, Diesel, CNG).
- Transmission: Whether the car is automatic or manual.
- Selling Price: The selling price of the car.
- Mileage: Distance covered by the car.
- Seller Type: Whether the seller is an individual, a dealer, or a trusted dealer.
- Owner: The number of previous owners.

**1. Query to find Total petrol cars In year 2020?**
```sql
SELECT count(*),year from car_dekho where fuel ="Petrol" and year=2020;
```

**2. Write query to find Total fuel cars in each year ?**
```sql
SELECT count(*),year,fuel from car_dekho where fuel in ("petrol","diesel","cng") group by year,fuel;
```

**3. Query to find Find out year having more than 100 cars ?**
```sql
select count(*),year from car_dekho group by year having count(*)>100;
```

**4. Query to find  Details of car between 2015 and 2020?**
```sql
select * from car_dekho where year between 2015 and 2020;
```

**5. Query to find the average selling price of cars based on the combination of fuel type and transmission type. Display the fuel type, transmission type, 
-- and the average selling price, sorted by the average selling price in descending order?**
```sql
SELECT fuel, transmission , avg(selling_price) from car_dekho group by fuel,transmission order by avg(selling_price) desc;
```

**6. Write a query to identify the car model with the highest number of listings for each seller type. Display the seller type, car model, and the count of listings?**
```sql
SELECT seller_type, name, COUNT(*) AS listing_count FROM car_dekho
GROUP BY seller_type, name
HAVING COUNT(*) = (SELECT MAX(listing_count)FROM 
(SELECT seller_type, name, COUNT(*) AS listing_count FROM car_dekho
GROUP BY seller_type, name) AS subquery WHERE subquery.seller_type = car_dekho.seller_type);
```

**7.Write a query to analyze the impact of the number of previous owners on the selling price. Calculate the average selling price for cars with different numbers of previous owners, and sort the results by the number of previous owners?**
```sql
Select owner, avg(selling_price) from car_dekho group by owner order by owner asc;
```

**8.Write a query to find the total number of cars sold by each seller type in a specific year?**
```sql
select count(*) , seller_type from car_dekho where year=2020 group by seller_type;
```

---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------




### Conclusion
This project demonstrates how SQL can be used to extract key insights from a dataset, such as the distribution of cars by fuel type and year, the effect of ownership history on car prices, and identifying the top-listed car models. These analyses provide valuable information for understanding the used car market dynamics.

