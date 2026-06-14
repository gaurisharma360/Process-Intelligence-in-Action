# Process-Intelligence-in-Action

This folder contains the analysis and validation notebooks used for the supermarket checkout process mining project (2AMI30). The files cover exploratory data analysis, bottleneck identification, hypothesis validation, simulation evaluation, and intervention assessment.

## Files 

### `intro_xes_combined-Copy.ipynb`

The analysis begins with XES log processing and event-log validation before conducting extensive temporal analyses at the hourly, daily, and weekday levels to identify workload patterns, seasonal effects, and demand fluctuations. It then investigates counter utilisation by examining customer arrivals per counter, counter opening and closing behaviour, queue lengths, queue pressure, customer distribution across counters, and resource allocation decisions. The notebook further performs detailed cart abandonment analysis, exploring abandonment trends over time, abandonment rates, customer types, basket sizes, payment methods, and the relationship between congestion, customer arrivals, and abandonment behaviour. Additional analyses focus on clerk activities such as price checks and abandoned-item cleanups to assess whether supporting processes contribute to operational bottlenecks. The notebook also tries to gather evidence, simulation results, and the impact evaluation.
   
### `intro_xes_combined_analysis.ipynb`

This notebook is chronological from the bottom up, the file begins with loading the raw event logs, converting them into structured DataFrames, and conducting foundational exploratory data analysis (EDA) and baseline hypothesis testing on the old system data. The bottom sections visualize baseline performance through global wait time distributions, initial queue length profiles, and baseline conditional abandonment rates to establish historical bottlenecks. Moving upward into the analysis of the new simulation data, the notebook constructs integrated DataFrames to perform direct comparative testing against the old baseline. This upper section generates event-driven visualization plots to evaluate the interventions, including unfiltered and capacity-controlled shift handover wait time distributions to isolate the impact of the protocol, alongside global queue length histograms and boxplots. Finally Ordinary Least Squares (OLS) linear regression models are compared across both data states to map changes in wait time drivers and mathematically validate the structural stabilization of the checkout process.

### `customer_xes_analysis.ipynb`

This notebook covers basic EDA on the customer log: hourly and daily arrival patterns, overall abandonment counts and rates, abandonment broken down by hour, and customer waiting times computed from Enter Queue to Start Payment events, including distributions and hourly averages. It also looks at cashier shift durations and active counter counts per hour for a selected day. 


### `simulation_results_queue_depth.ipynb`

This notebook evaluates how the interventions influenced customer patience and abandonment behaviour. The core metric is P(abandon | min queue < 4), the conditional probability that a customer abandons their cart despite arriving when the shortest available counter line was below the standard patience threshold of four people. Queue depth is tracked at the exact moment a customer enters the checkout area, mirroring what they actually observe when deciding whether to stay. Fisher's Exact Test is performed for the key bottleneck hours (14:00, 15:00, and 19:00). The notebook produces comparison plots and summary tables covering both the binary arrival metric and the conditional abandonment rate, showing where the intervention made a measurable difference and where it didn't.


### `supermarket_hypothesis_validation.ipynb`

This notebook works through five hypotheses about supermarket checkout operations: whether customers with fewer items abandon more readily based on queue length, whether payment method affects checkout duration and contributes to queue buildup, whether manager absence leads to slower staffing response and higher abandonment, whether high customer arrivals necessarily cause congestion when capacity is sufficient, and whether cashier shift handovers create temporary bottlenecks. Each hypothesis gets its own section with dedicated tests and visualisations to either support or rule it out.

