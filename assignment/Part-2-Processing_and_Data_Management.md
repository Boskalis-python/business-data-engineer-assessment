Following the initial architecture proposal for Boskalis' vessel monitoring system, the Technical Department has identified critical issues with the current data processing implementation on their vessels. This second part focuses on optimizing the edge processing capabilities to ensure reliable data collection, efficient storage usage, and intelligent data transmission across their diverse fleet of dredging vessels.
The challenge involves handling data from various vessel types operating in remote locations, often with limited connectivity, while ensuring critical engine and performance data is never lost. Key considerations include the constraints of older vessels' hardware, varying connectivity options (4G, satellite, Starlink), and the need for intelligent data prioritization and compression to manage transmission costs.
Below is the follow-up communication from the Technical Department detailing their specific requirements and current implementation challenges...

---
From: James Thompson, Operations Director, Boskalis Technical Department  
To: Jan Bagger, Data Engineer, Data Science & Engineering Team DTED  
Subject: Re: Edge Processing Requirements - Vessel Data Optimization  

Dear Jan,  

Thank you for your initial response. After discussing with our engineering team and specifically with the Boskalis Fleet Automation Center in Papendrecht, we have some additional requirements regarding data processing on our vessels.
Our current implementation for processing log data on the vessels is quite basic. I've attached a sample of the code we're currently using. Our engineers have noticed it's consuming too much memory during long dredging projects and sometimes crashes on our older vessels with limited computing power.

```python
def process_vessel_logs(log_directory):
    engine_metrics = []
    for file in os.listdir(log_directory):
        if file.endswith('.log'):
            with open(os.path.join(log_directory, file)) as f:
                for line in f:
                    data = json.loads(line)
                    if data['engine_rpm'] > 0:
                        engine_metrics.append({
                            'timestamp': data['timestamp'],
                            'vessel_id': data['vessel_id'],
                            'engine_rpm': data['engine_rpm'],
                            'fuel_rate': data['fuel_consumption_rate'],
                            'temperature': data['engine_temperature']
                        })
    
    return pd.DataFrame(engine_metrics)
```

Additionally, we've had several incidents where critical engine warnings weren't transmitted due to storage overflow during extended offline periods. Just last week, the TSHD Prins der Nederlanden had to delay its departure from Singapore because we couldn't access historical engine data needed for maintenance verification.

Some specific challenges we need addressed:
1. During dredging projects in remote areas, we're losing critical engine warning data because our local storage fills up with lower-priority logs
2. Our satellite costs are astronomical because we're sending raw data - we need some way to compress this. Currently, we've installed Starlink on some vessels, but not all vessels have this capability yet.
3. Engineers are complaining that they can't quickly spot engine problems because our metrics are all over the place with timezone issues (especially challenging when vessels move between projects in different regions)
4. We need better real-time analysis on the vessels themselves - currently, we only spot issues during routine inspections

Our vessels are equipped with industrial PCs (2-4 GB RAM), running Linux, and have local SSDs (256GB-1TB depending on vessel age). Our newer vessels have better specs but we need a solution that works across the fleet.
Could you help us design a more robust edge processing system that addresses these issues? We're open to using modern data processing libraries - our team is familiar with both pandas and polars.

Best regards,  
James  
P.S. The Prins der Nederlanden incident cost us €45,000 in delays - management is very motivated to get this right.
---

Your task is to help Jan design and implement an optimized edge processing solution for the Technical Department. Consider the specific challenges outlined in the email and propose a scalable, efficient system that can handle data processing on Boskalis' diverse fleet of dredging vessels. How would you approach this problem?
Note: The sample code provided is a simplified version of the current implementation. You can assume the vessels are running Linux and have the specified hardware configurations.
