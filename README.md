# Datathon 2025: Beyond the Bus
<div align='center'>

[![Video Submission](https://logos-world.net/wp-content/uploads/2024/01/MTA-Metropolitan-Transportation-Authority-Emblem.png)](https://www.youtube.com/watch?v=UBy34hkhmKg)

 ### A Spatial and Socio-Economic Analysis of MTA Bus Violations

</div>

<br>

<div align='center'>

***

# 🎙️ *Public Interest Technology (PIT) PopUp* 🎙️

#### November 11, 2025

### A huge thanks to the CUNY PIT Lab for the opportunity to present our findings to the general public at the Oculus WTC! We met tons of amazing, like-minded people and discussed how our technical skills can solve real, civic issues.

  <img src="https://github.com/user-attachments/assets/d6e85961-3e7a-4784-a8fb-1953bda192a4" width="49%" alt="team-pic" />
  <img src="https://github.com/user-attachments/assets/8032cd5a-7bc7-4478-84ee-b672d989f48f" width="49%" alt="entrance" />

### *You can check out our dashboard and presentation with the links below. In our dashboard, we expanded way beyond our original scope using a full data pipeline. Our ETL process fed into Tableau to create a geospatial map, annotated charts, and multiple interactive pages using navigation objects, allowing us to guide our audience through our story-driven analysis.*

| Dashboard | YouTube |
| :---: | :---: |
| <a href="https://public.tableau.com/app/profile/rolando.mancilla.rojas/viz/BeyondTheBusMTABusACEAnalysis/1_HomePage#1" target="_blank"><img src="https://img.shields.io/badge/Tableau-E97627?style=for-the-badge&logo=tableau&logoColor=white" alt="Tableau Dashboard"/></a> | <a href="https://www.youtube.com/watch?v=AIM11-ueYqI" target="_blank"><img src="https://img.shields.io/badge/YouTube-FF0000?style=for-the-badge&logo=youtube&logoColor=white" alt="YouTube Video"/></a> |

</div>

<div align='center'>

***

# 🎊 *Nova Alpha: Top 3 Datathon Team* 🎊

#### September 26, 2025

<img width="553" height="336" alt="datathon-win" src="https://github.com/user-attachments/assets/d58b4d0c-b1dd-47db-902c-23ed80083dc0" />

<img width="553" height="414" alt="image" src="https://github.com/user-attachments/assets/2085fb35-3ff5-4c47-95d6-8b0614b91021" />

### *Thankful that our team took home 2nd place at Datathon 2025! Catch us on November 5th, 2025, as we showcase our project at the Oculus World Trade Center for the [first NYC PIT Pop Up!](https://nycpitpopup.org/event/beyond-the-bus-a-spatial-and-socio-economic-analysis-of-mta-bus-violations/)*

#### *Also shoutout to our sibling team, [Nova Beta](https://github.com/ayemaqu/Nova-Beta-Datathon), for taking home 4th place!*

</div>

***

<br>

## README Navigation

- [Project Overview](#Project-Overview)
  - [The Team](#The-Team)
  - [Business Problem](#Business-Problem)
- [Datasets & Schema](#Data-and-Schema)
- [Exploratory Data Analysis](#EDA)
- [Data Cleaning & Feature Engineering](#Data-Cleaning-and-Feature-Engineering)
- [Visualization](#Visuals)
- [Insights & Recommendations](#Insights-and-Recommendations)
- [Ethics & Bias](#Ethics-and-Bias)
- [Repository Navigation](#Repo-Navigation)
- [Project Video Submission](#Video-Submission)
<br>

## Project Overview

<div align='center'>
At the start of 2019, the MTA introduced a new technology with efforts to speed of bus routes in the NYC boroughs. The Bus Automated Camera Enforcement (ACE) system was implemented onto specific buses, eventually spreading onto buses across the five boroughs. This project aimed to explore the intricacies regarding the data collected from this ACE system by looking through a socio-economic spatial lens.
</div>

<br>

<div align='center'>

## The Team



![ibra-pic](https://github.com/user-attachments/assets/209ab7a6-e21c-4707-afda-289ddfedd069)

### Ibrahima Diallo

Hi, my name is Ibrahima Diallo, and I’m a data analyst passionate about transforming raw data into insights that drive smarter decisions and real impact.

[LinkedIn](https://www.linkedin.com/in/ibranova/) | [GitHub](https://github.com/ibranova)

</div>

<br>

<div align='center'>
    
![casual-septum](https://github.com/user-attachments/assets/86b1b472-797d-4c8e-ae70-3cf6ae68bc88)

### Rolando Mancilla-Rojas

Hi! I'm Rolando, but I mainly like to go by Ro. I have a particular interest in business/finance, and I enjoy getting my hands dirty in the data.

[LinkedIn](https://www.linkedin.com/in/rolandoma33/) | [GitHub](https://github.com/ro-the-creator)

</div>

<br>

<div align='center'>

![kabbo-pic](https://github.com/user-attachments/assets/01d88fc1-33c5-44ea-83fe-45f9495d8bb5)

### Kabbo Sultan

My name is Kabbo Sultan, I am an AI-driven cybersecurity and data analytics professional securing businesses with data intelligence.

[LinkedIn](https://www.linkedin.com/in/kabbosultan/) | [GitHub](https://github.com/kabbosultan)

</div>

<br>

***

## Business Problem
Bus lines are consistently slowed by bus lane obstructions, which affect bus efficiency and cause delays. For this reason, the ACE system has been a driving force in waning these issues.
<br>
<br>
Since its inception, there have been over 3 million violations issued, with their implications embedded inside the data. Our team aimed to bring forth these implications, especially in regards to their impact on people and communities.
<br>
<br>
With this goal in mind, this lead our team to 3 overarching questions:
</div>

1. What are the key characteristics of violation hotspots?

2. What are the impacts of repeat offenders on violation rates?

3. Is there a connection between violation frequency and the socio-economic factors of their corresponding bus stops?

-----

## Data and Schema

### The Main Dataset: [ACE System](https://data.ny.gov/Transportation/MTA-Bus-Automated-Camera-Enforcement-Violations-Be/kh8p-hcbm/about_data)

This project's main dataset from the MTA is renamed to `enforcement_violations` in SQL. This "flat file" structure contains detailed records for each enforcement event, whether it resulted in an issuance or not. This design allows for flexible aggregation and analysis across multiple dimensions like time, location, and vehicle behavior.
  * The data is captured at the level of a single enforcement event, uniquely identified by `violation_ID`.
  * Analysis is conducted by grouping and filtering on key descriptive columns like `bus_route_ID`, `stop_name`, `violation_status`, and `violation_type`.
  * `bus_stop_latitude` and `bus_stop_longitude` are in point coordinate format. This is later used to assign bus stops to ZIP codes.
### Key Columns Overview
  * `vehicle_ID`: A unique identifier for each vehicle.
  * `bus_route_ID`: The bus route on which the event occurred.
  * `stop_name`: The name of the nearest bus stop.
  * `first_occurrence`: The timestamp of the enforcement event.
  * `violation_status`: The outcome of the event (e.g., 'VIOLATION ISSUED', 'EXEMPT', 'TECHNICAL ISSUE/OTHER').
  * `violation_type`: The specific category of the violation (e.g., 'Bus Lane Violation').
  * `bus_stop_latitude`, `bus_stop_longitude`: Geographic coordinates of the bus stop.

<br>

### Subset: [Populations per ZIP](https://datacommons.org/tools/download#pt=CensusZipCodeTabulationArea&place=geoId%2F3651000&sv=Count_Person_BelowPovertyLevelInThePast12Months__Count_Person&dtType=RANGE&dtMin=2019-01&dtMax=2024-12&facets=%7B%7D)
This dataset was used to find poverty rates per ZIP code in the five boroughs of NYC. The data was originally queried for the years 2019 - 2024 in order to maintain consistency and relevancy with the dates.
- This dataset was also used to feature engineer `poverty_rate`, which was done by dividing `Value:Count_Person_BelowPovertyLevelInThePast12Months` by `Value:Count_Person` for each ZIP code.

### Key Columns Overview
- `placeDcid` – Unique identifier for the geographic unit (ZIP code, in this case).  
- `placeName` – Human-readable name of the place (ZIP code as a number).  
- `Date:Count_Person_BelowPovertyLevelInThePast12Months` – Year of the poverty data.  
- `Value:Count_Person_BelowPovertyLevelInThePast12Months` – Number of people in poverty in that year.  
- `Source:Count_Person_BelowPovertyLevelInThePast12Months` – Data source link for poverty counts.  
- `Date:Count_Person` – Year of the total population data.  
- `Value:Count_Person` – Total number of people in that year.  
- `Source:Count_Person` – Data source link for total population counts.  

<br>

### Subset: [MODZCTA NYC](https://data.cityofnewyork.us/Health/Modified-Zip-Code-Tabulation-Areas-MODZCTA-/pri4-ifjk/about_data)
This is the Modified ZIP Code Tabulation Areas (MODZCTA) by the Department of Health and Mental Hygiene (DOHMH). This was mainly used to assign the ZIP codes for the bus stops, to later run statistical tests on spatially harmonized datasets.
- `the_geom` includes coordinates in multipolygon format, which encompass an entire shaped area. The point coordinates from the main dataset were pinpointed within these geometry coordinates.
- Also was used to assign ZIP codes to boroughs, which was a significant part of the cleaning.

### Key Columns Overview
- `MODZCTA` – Modified ZIP Code Tabulation Area (ZCTA).  
- `modzcta` – Text field with a comma-delimited list of all known populated ZIP codes corresponding to the MODZCTA geometry.  
- `label` – Text field containing the Census ZCTAs that were combined to form the MODZCTA area (comma-delimited).  
- `pop_est` – Population estimate for each MODZCTA, aggregated from the 2018 ACS 5-year population estimates for each ZCTA.  
- `the_geom` – Polygon geometry for the Modified ZIP Code Tabulation Area (ZCTA).  


-----
## EDA
Exploratory Data Analysis was performed to establish a baseline understanding of the enforcement landscape. Three key areas were investigated:
1.  **Violation Status Distribution:** We analyzed the different outcomes of enforcement events. While 'VIOLATION ISSUED' was the most common, a significant number were logged as 'EXEMPT' or 'TECHNICAL ISSUE/OTHER', highlighting the need to filter for issued violations to analyze true offender behavior.
2.  **Geographic Hotspots:** We ran an initial aggregation of violations by bus stop. The analysis immediately revealed a highly skewed distribution: a small number of bus stops are responsible for a disproportionately large number of total violations, confirming the "hotspot" theory.
3.  **Repeat Offender Prevalence:** We performed an initial calculation on repeat vehicles and found that a substantial percentage of vehicles receive more than one ticket. This confirmed that targeting repeat offenders is a viable and potentially high-impact strategy.
-----
## Data Cleaning and Feature Engineering
To prepare the data for deep analysis, critical cleaning and feature engineering steps were performed.
### Data Cleaning
The primary data quality issue was the non-standard date format.
  * **Parsing Timestamps:** The `first_occurrence` column was stored as text in the format `MM/DD/YYYY HH:MM:SS PM`. We used `SUBSTR()` functions to parse and reformat this text into a standard `YYYY-MM-DD` format that SQLite's date functions could process.

### Feature Engineering

New features were created to unlock temporal and behavioral insights:
  * `day_type`: Categorized timestamps into 'Weekday' or 'Weekend'. Rationale: To analyze if violation patterns differ between workdays and weekends.
  * `hour_of_day`: Extracted the hour from the timestamp. Rationale: To identify peak violation times for targeted deployment.
  * `days_since_last_violation`: Calculated the time gap between a vehicle's consecutive violations. Rationale: To quantify the "recidivism rate" and understand offender habits.
-----

## Visuals

<div align='center'>

<img width="841" height="684" alt="viz-3" src="https://github.com/user-attachments/assets/537373d7-0aa7-4f80-af18-ba0dd2327e0d" />

### Figure 1 
Proportion of Repeat vs. One-Time Offenders (12-Month Period): This chart establishes the scale of the recidivism problem, showing that over one-third (37.6%) of all vehicles receiving a ticket will receive at least one more within a year. This confirms that a substantial portion of violations are caused by a core group of chronic offenders, making them a high-value target for focused enforcement strategies.

</div>

<div align='center'>

<img width="1089" height="525" alt="viz-4" src="https://github.com/user-attachments/assets/8c151552-c689-458c-b3d1-c2c48c21fd81" />

### Figure 2
Dominant Violation Type for Each Bus Route: This chart provides the core strategic insight for route-level enforcement by color-coding the top bus routes by their primary enforcement challenge. It clearly demonstrates that different routes face different problems—for example, the M15+ is overwhelmingly dominated by bus lane violations, while the BX19's main issue is vehicles stopped at bus stops. This proves the need for route-specific, rather than city-wide, intervention strategies.

</div>

<div align='center'>

<img width="886" height="703" alt="viz-5" src="https://github.com/user-attachments/assets/20fac49d-3028-42a5-ad0d-25ce12e682ba" />

### Figure 3:
Peak Violation Hours (Weekday vs. Weekend): This time-series analysis reveals the city's "violation rhythm." The weekday trend (top) shows two sharp peaks corresponding to the morning (8-9 AM) and evening (3-5 PM) commutes, identifying clear windows for targeted enforcement. The weekend trend (bottom) displays a single, broader peak in the afternoon, requiring a different staffing and deployment strategy.

</div>

<div align='center'>

<img width="886" height="591" alt="viz-6" src="https://github.com/user-attachments/assets/de6a2c8c-2ea9-41c5-8547-d18387cc6e37" />

### Figure 4
Average Time to Next Violation (Recidivism Rate): This chart quantifies how quickly repeat offenders receive another ticket, broken down by the type of their subsequent violation. It reveals that vehicles ticketed for a 'MOBILE BUS STOP' violation re-offend the fastest, on average. This insight into offender behavior can be used to tailor deterrent strategies and penalty structures for different types of infractions.

</div>

<div align='center'>

<img width="832" height="692" alt="viz-7" src="https://github.com/user-attachments/assets/726c2ffd-c760-400e-8b41-1e7b7842b999" />

### Figure 5
Top 10 Bus Routes by Reported Technical Issues: This chart moves beyond driver behavior to identify routes with potential equipment or system reliability problems. The M15+ route reports a disproportionately high number of technical issues compared to all others, suggesting an urgent need for a maintenance audit on its specific enforcement cameras or bus-mounted equipment to ensure data integrity and program effectiveness.

</div>

<div align='center'>

<img width="1926" height="1288" alt="image" src="https://github.com/user-attachments/assets/75fda382-7eb8-43d8-a4ea-76a3f370424e" />


### Figure 6
Shows the poverty rate severity by ZIP codes across the 5 boroughs. Overlayed are the violations per bus stop across the 5 boroughs. Visually, we can see that there is a high violation density in the Bronx, where there are also higher levels of poverty. While this gives us a general direction of where to look, it was important to conduct a statistical test across all poverty levels per ZIP code in our ANOVA.

</div>

-----
## Insights and Recommendations

<div align='center'>

With the culmination of our cleaning, analyzing, visualization, and statistical testing all coming together, we found several key insights that helped us come up with recommendations for the MTA. To do this, we looked back at our original questions:

</div>

1. What are the key characteristics of violation hotspots?

2. What are the impacts of repeat offenders on violation rates?

3. Is there a connection between violation frequency and the socio-economic factors of their corresponding bus stops?

***

#### Insight: 
Bus lane enforcement is not a uniform problem; it is a series of distinct, predictable challenges concentrated in specific locations, times, and routes. A small group of repeat offenders causes a disproportionate impact.

#### Recommendation:
**Champion a shift from a volume-based to a targeted, data-driven enforcement model.** Frame this as a strategic initiative to directly improve bus speeds and service reliability, using the "Top 10 Hotspots" as a pilot program to prove effectiveness.

<br>

#### Insight:
Violations are highly predictable. The top 10 bus stops account for a massive portion of all tickets, and peak violation times are consistent. Furthermore, certain routes and vehicles show a high rate of 'Technical Issue' logs, suggesting potential equipment failure.

#### Recommendations:
1. **Deploy Resources Surgically:** Reallocate enforcement teams to the **Top 10 Hotspots** identified on the map, specifically during the **peak weekday hours** (8-10 AM, 4-6 PM).
2.  **Target "Super Offenders":** Use the list of top 5% repeat offenders to create a high-priority monitoring list for intervention.
3.  **Conduct an Equipment Audit:** Launch an investigation into the vehicles and routes with the highest number of 'Technical Issue' logs to ensure camera and system reliability.

<br>

#### Insight:
The *type* of violation is not random but strongly correlated with the bus route. This suggests that enforcement issues are often symptoms of underlying environmental or infrastructural problems.

#### Recommendations:
1. **Inform Infrastructure Redesigns:** For routes where 'Bus Lane Violation' is the dominant issue (e.g., M15), use this data to advocate for physical redesigns like protected, red-painted lanes or curb extensions that make incursions more difficult.
2.  **Review Curbside Policy:** For routes dominated by 'Parking at Bus Stop' or 'Double Parking' violations, partner with the Department of Transportation to review parking regulations, signage clarity, and loading zone policies near the identified hotspot stops.

<br>

#### Insight:
Bus stops within areas of high poverty rates are getting *significantly* higher violations than medium or low poverty rates. This finding was supported by an ANOVA, Tukey Post-Hoc test, and checking their normalized means. These tests showed the high poverty grouped ZIPS having a statistically significantly higher difference than its counterparts.

#### Recommendation:
While this test may show there is statistical significance between the poverty rate groups, this in no way does it show the possible factors that may lead to this statistical significance. Therefore, it is recommended that the MTA tracks other metrics that could support this finding. This could include metrics like:
1. **Transit Infrastructure Work** - To be tracked alongside time stamps. Flagged if construction/other factors contribute to violations.
2. **Violation Overturn Rate** - Could potentially show if these violations were upheld even after issuance.
3. **Qualitative Data** - Could give a voice to the neighborhoods being affected by higher violation issuances.
-----
## Ethics and Bias

<div align='center'>

Overall, this project being analyzed in an ethical lens was very important to us, as these are values strongly instilled into us at The Marcy Lab School. We all value giving underrepresented groups a larger voice, as they are often never given a chance to speak. Furthermore, we wanted to ensure our data analytical work was up to industry standard. Given this, several steps were taken:

</div>

<br>

  * **Data Quality:** The primary data cleaning challenge was parsing non-standard text-based timestamps. All conversion logic is documented.
  * **Missing Values:** A small percentage of records with `NULL` for `vehicle_id` and `bus_stop_id` were excluded which could slightly underrepresent violations in those areas.
  * **Time Window:** This analysis is based on a specific dataset time frame (2019 - 2024). The findings are highly relevant but should be re-validated with data from different years to check for patterns.
  * **No Severity Modeled:** The analysis treats all issued violations equally. It does not account for the duration or severity of the obstruction, which is a limitation when assessing the true impact on bus service.
-----
## Repo Navigation

- [/cleaning](./cleaning) – Contains all files related to cleaning datasets.
- [/statistics](./statistics) – Notebook detailing ANOVA and Tukey Post-Hoc Test.
- [/visualizations](./visualizations) – Contains folders for the visualization aspect of the project.
  - [/charts](./visualizations/charts) – Final PNG image files for the visuals.
  - [/code](./visualizations/code) – Notebook containing code for producing visuals.


***

## Video Submission

<div align='center'>

[Datathon 2025: Nova Alpha Project Submission Video on YouTube](https://www.youtube.com/watch?v=UBy34hkhmKg)

<br>

***

<br>

[Back to README Navigation](#README-Navigation)

</div>


