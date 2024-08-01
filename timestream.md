# Timestream

Fast scalable and serverless TSDB. Built in time series analytics that support time series functions and can help identify consumer behavious trends.

- 10^3 times faster than RDBMS and 1/10th of the cost.
- Can store 100s of TB of data.
- Automatically scales up/down to adjust capacity
- Stores and Analyses up to 10^12 events per day.
- Multimeasure records.
- Memory store for recent data and magnetic store for historical.
- Periodically and automatically schedule queries to perform real-time analytics on incoming data.


## INPUTS

- AWS IoT
- KDS -> Lambda -> Timestream
- KDS -> Timestream
- Telegraf
- Prometheus
- KDS/MSK -> KDA for Apache Fink -> Timestream

## OUTPUTS

- Quicksight
- Sagemaker
- Grafana
- JDBC

