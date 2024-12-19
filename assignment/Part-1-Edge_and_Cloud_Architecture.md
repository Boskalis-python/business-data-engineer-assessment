# Part 1 - Maritime Innovation Challenge: The Digital Fleet Transformation
Boskalis, a leading maritime contractor, is facing a critical challenge at one of her departments, the Technical Department (TD). TD operates a fleet of 1000 vessels worldwide, ranging from Trailing Suction Hopper dredgers to small support vessels like Multicats. 
They're struggling with rising fuel costs, maintenance issues, and a lack of real-time insights into their fleets operations.
Jan Bagger, a data engineer working for the Data Science & Engineering team, receives an urgent email from the TD Operations Director:

---
From: James Thompson, Operations Director, Boskalis Technical Department  
To: Jan Bagger, Data Engineer, Data Science & Engineering Team DTED  
Subject: Urgent: Fleet Digitalization Project Requirements  

Dear Jan,  
Our situation has become critical. Last month, we had three vessels experience engine problems on remote project in South East Asia, and our fuel costs have risen by 25% year-over-year. Our current manual logging and monthly reporting system isn't working.
Key issues we're facing:

- Engineers are manually recording engine data every 4 hours
- We only get updates when vessels are in port (sometimes going 2-3 weeks without data)
- No way to detect engine problems before they become serious
- Can't optimize our fuel consumption
- Losing valuable data during ocean crossings

We've already installed sensors on all vessels that can capture:

- Engine performance metrics (RPM, temperature, fuel consumption)
- Navigation data (speed, heading, location)
- Connectivity status (satellite, 4G, port WiFi, Starlink)

Our IT team has set up a basic database structure (attached schema), but we need your expertise to build a complete solution.
Requirements:

- Need real-time(ish) monitoring - understand we have connectivity limitations
- Must work even when vessels are offline
- Can't overwhelm our satellite bandwidth - costs are already too high
- Need historical analysis capabilities for optimization
- Solution must work across our diverse fleet - vessels range from 5 to 15 years old

Budget isn't a primary concern, but satellite transmission costs need to be considered.
Can you design a solution that addresses these challenges?  

Best regards,  
James

---

Your task is to help Jan design and implement a solution for the Technical Department. Consider both the technical requirements and the underlying business needs. How would you approach this problem?
Note: The database schema is already implemented as provided in the original tables (vessel_logs, vessel_metadata, and connectivity_logs).

```sql
CREATE TABLE vessel_logs (
    id SERIAL PRIMARY KEY,
    vessel_id INTEGER,
    timestamp TIMESTAMP,
    latitude DECIMAL(9,6),
    longitude DECIMAL(9,6),
    speed_knots DECIMAL(5,2),
    heading DECIMAL(5,2),
    engine_rpm DECIMAL(7,2),
    fuel_consumption_rate DECIMAL(7,2),
    engine_temperature DECIMAL(5,2)
);

CREATE TABLE vessel_metadata (
    vessel_id INTEGER PRIMARY KEY,
    vessel_name VARCHAR(100),
    vessel_type VARCHAR(50),
    gross_tonnage DECIMAL(10,2),
    build_year INTEGER
);

CREATE TABLE connectivity_logs (
    id SERIAL PRIMARY KEY,
    vessel_id INTEGER,
    connectivity_start TIMESTAMP,
    connectivity_end TIMESTAMP,
    connection_type VARCHAR(20)  -- 'satellite', '4G', 'port_wifi'
);
```

Further, the Technical Department has requested the following queries to be implemented in the solution:

a) Write a query to analyze fuel efficiency patterns during different speed ranges  
b) Create a query to identify vessels with abnormal engine temperature patterns  
c) Calculate total offline time per vessel per month  

Also provide a high-level overview of the architecture you would propose for this solution. What technologies would you use? How would you ensure the solution is scalable and cost-effective?