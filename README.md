# York Street Footfall Analysis for Optimal Vendor Positioning
*Maximising Customer Exposure: Footfall Analytics for York Street Locations*

![Status](https://img.shields.io/badge/Status-Project_Completed-success)
![SQL](https://img.shields.io/badge/SQL-Data_Extraction-4479A1?style=flat&logo=postgresql&logoColor=white)
![Tableau](https://img.shields.io/badge/Tableau-Dashboarding-E97627?style=flat&logo=tableau&logoColor=white)

---
## Table of Contents

- [Project Overview](#project-overview)
- [Data Description](#data-description)
- [Report Summary](#report-summary)
- [Conclusion](#conclusion)

---

## Project Overview

This project examines **daily footfall data from multiple locations in York** to determine the optimal site for a market vendor aiming to maximise visibility and customer exposure. Using **R** for statistical analysis, data cleaning, and visualisation, the study evaluates how foot traffic varies across locations, days of the week, and weekends.

The analysis includes:

- A summary of footfall patterns at each monitored location
- Distributional comparisons across sites
- Two hypothesis tests (t-tests) comparing Coney Street and Stonegate
- A separation of weekday vs weekend footfall performance
- Data-driven recommendations for where a promoter should place their stall

By applying statistical reasoning and clear visual evidence, the project provides a practical, business-oriented assessment of location attractiveness, supporting decision-making for vendors or local planners who rely on accurate foot traffic insights.

---

## Data Description

|Variable	    | Description |
|-------------|---------------------------------------------------------|
|Date	        | The date the record was created                         |
|SiteName	    | The site where the record was collected                 |
|LocationName |	The location where the record was collected             |
|WeekDay	    | The day the record was collected                        |
|TotalCount	  | The number of people who walk past a particular location|
|Recording_ID	| Unique ID of each record was created                    |

---

## Report Summary

This report includes a summary table, distribution plots, and several two-sided t-tests. It intends to report the results of specific analyses requested from the promoter to **maximise the number of passers across a particular location in York**.  
Before the reported analysis below was conducted, 17 records were removed from the original data because of missing values and abnormal data with too-high values.  
Table 1 presents a summary of statistics on daily footfall across locations. It contains the first and last day of data recording, the mean and standard deviation of daily footfall, and the highest and lowest daily footfall for each location.  

*Table 1. Summary of daily footfall across locations*

|LocationName	            | FirstDay	 | LastDay	  | MeanFootfall | StddevFootfall |	HighestFoofall | LowestFootfall|
|-------------------------|------------|------------|--------------|----------------|----------------|---------------|
|Church Street	          | 2015-01-01 | 2017-06-18	| 4352	       | 1389           |	26848	         | 402           |
|Coney Street	            | 2015-01-01 | 2019-12-31	| 23507	       | 6608	          | 51050	         | 2960          |
|Micklegate	              | 2015-01-01 | 2019-12-31	| 7487	       | 4800	          | 98180	         | 1309          |
|Parliament Street	      | 2015-06-08 | 2019-12-31	| 22631	       | 6610	          | 53749	         | 1227          |
|Parliament Street at M&S	| 2015-01-01 | 2015-06-07	| 22432	       | 7750	          | 53057	         | 7802          |
|Stonegate	              | 2015-01-01 | 2019-12-31 |	18883	       | 6753	          | 56371	         | 1297          |

The distribution of daily footfall in each location is shown in Figure 1.

<p align="center">
  <img src="/Figure1.png" width="900">
  <br>
  <em>Figure 1: Distribution of Daily Footfall Across Locations in 2019</em>
</p>

These four plots, divided by different locations, underscore two findings. Firstly, Micklegate has a lower volume of passers than the other three locations, indicating lower popularity and the possibility of achieving the promoter’s goal.

Secondly, plots in the other three locations show a trend of a higher number of passers, which illustrates a chance to conduct an additional analysis, particularly at weekends. Analysing the pattern can help us discover whether there are correlations between the number of passers and weekends.

**Goal: To maximise the number of passers if a stall is placed on Coney Street or Stonegate**  

*If placing the stall across all days (Figure 2)*

Across all days in 2019, a two-sided t-test shows that **Coney Street records significantly higher daily footfall than Stonegate**, *t(699.18) = 3.36, p = 0.0008*.  
This result aligns with Figure 2, where Coney Street’s distribution is consistently right-shifted and exhibits a higher mean.  
Therefore, placing the stall on **Coney Street** across the full week would maximise exposure.  

<p align="center">
  <img src="/Figure2.png" width="900">
  <br>
  <em>Figure 2: Comparative Distribution of Daily Footfall on Coney Street and Stonegate in 2019</em>
</p>

*If placing it only at weekends (Figure 3)*

A two-sided t-test on weekend data suggests no statistically significant difference between the two streets, *t(203.88) = -0.29, p = 0.772*.  
The histogram in Figure 3 also shows broadly similar weekend distributions.

To ensure the result is not driven by a small number of unusually high observations—primarily in Stonegate, where occasional peaks create a long right tail—a sensitivity analysis was conducted by removing values beyond the upper whisker of a boxplot rule (i.e., values > 40000). 

This alternative threshold is different from the global outlier rule used earlier (>100,000) and is applied **only to weekends**, as the distribution is more variable in this subset. Importantly, this procedure does not replace the main test but checks whether results depend on these extreme points. 

After applying this sensitivity check, the t-test result remains non-significant, *t(198) = 0.53, p = 0.599*, with Coney Street showing a marginally higher mean. This indicates that weekend differences between the two locations are **not statistically meaningful**, and conclusions are stable regardless of treatment of these extreme values.

<p align="center">
  <img src="/Figure3.png" width="900">
  <br>
  <em>Figure 3: Distribution of Daily Footfall on Coney Street and Stonegate at weekends in 2019</em>
</p>

---

## Conclusion

Overall, **Coney Street** provides consistently higher or steadier footfall across the week and remains a safe choice for stall placement. At weekends, although Stonegate displays occasional high spikes, these are infrequent and do not reflect the general pattern.
Therefore, for both daily and weekend operation, **Coney Street is the more reliable location for maximising passer numbers**.

