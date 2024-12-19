# Part 3 - System Integration Challenge: Building the Fleet Management Platform

Following the successful implementation of edge processing solutions across Boskalis' vessel fleet, a new challenge has emerged: creating a centralized yet flexible system to manage and analyze data from all vessels while maintaining operational efficiency and data integrity.

---
From: James Thompson, Operations Director, Boskalis Technical Department  
To: Jan Bagger, Data Engineer, Data Science & Engineering Team DTED  
Subject: Fleet Management Platform Requirements - Phase 3

Dear Jan,

Thanks for your excellent work on the edge processing solution. Now that we have reliable data collection from our vessels, we need to build a robust central platform that can handle our entire fleet's data management needs.

Last week's management meeting highlighted several critical requirements:

1. The UAE project team complained they couldn't access their vessel data through our current system when working from their local office. They ended up creating their own Excel sheets, which caused confusion during project handover.

2. Our maintenance team in Singapore needs real-time access to vessel data for predictive maintenance, but they're experiencing significant delays in data availability.

3. The QHSE department reminded us that we need to retain certain engine data for 7 years for compliance purposes, but storing everything is becoming cost-prohibitive.

4. Our ML team has developed some promising predictive maintenance models, but we're struggling to deploy and update them across the fleet efficiently.

Current Pain Points:
- Each regional office has developed its own way of accessing and analyzing vessel data
- Critical alerts sometimes get lost in the flood of incoming data
- No standardized way to handle data conflicts when vessels sync after being offline
- Storage costs are growing exponentially as we collect more detailed vessel data
- Manual deployment of software updates to vessels is becoming unmanageable

Infrastructure Context:
- Main data center in Netherlands
- Regional offices in Singapore, UAE, and Mexico
- Vessels frequently move between regions
- Mix of connectivity options (Starlink, 4G, Satellite) depending on vessel and location
- Growing need for near real-time analytics across the fleet

We need a solution that centralizes our fleet data management while providing flexible access for different stakeholders. The system should be robust enough to handle our current fleet of 1000 vessels but scalable for future growth.

Can you design a comprehensive system that addresses these challenges? Please consider our global operations and the need for both real-time monitoring and historical analysis.

Best regards,
James

---

Your task is to help Jan design and implement a fleet management platform that meets Boskalis' requirements. Consider the specific challenges outlined in the email and propose a scalable, efficient system that can handle data management for the entire fleet. How would you approach this problem? What technologies and architectural decisions would you recommend?

Note: You can assume the edge processing solutions have been successfully implemented on the vessels, and the data is being collected and stored in the existing database schema.

