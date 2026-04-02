# enterprise-fraud-intelligence
An end-to-end Big Data pipeline and executive dashboard for detecting and intercepting financial fraud using PySpark and Azure Synapse.

# 🛡️ Enterprise Fraud Intelligence Command
An End-to-End Big Data Pipeline & Machine Learning Threat Detection Platform

## 📌 Executive Summary
Financial institutions face asymmetric threats where a single compromised corporate account can cause catastrophic liquidity loss. This project is a complete, end-to-end Enterprise Data Pipeline that simulates, ingests, processes, and visualises 5.00 Million banking transactions to detect and intercept fraud rings in real-time.

By engineering a dynamic, sliding-window algorithm in PySpark and deploying a DirectQuery intelligence terminal in Power BI via Azure Synapse, this system successfully isolated 29,000 fraudulent anomalies, effectively "intercepting" 962.98 Million AZN in stolen funds.

## 🏗️ Architecture & Tech Stack
1) Data Simulation (Python): Generated 5 million rows of mathematically sound financial data utilising Lognormal Distributions to accurately simulate realistic spending behaviours across Retail, Corporate, and ATM channels.
2)Big Data Processing (PySpark): Engineered custom behavioural aggregation pipelines to establish moving historical baselines for tens of thousands of unique accounts.
3)Cloud Data Warehouse (Azure Synapse Analytics): Deployed a Serverless SQL endpoint to host the processed "Gold" data layer, enabling live querying of massive datasets.
4)Command Center UI (Power BI & DAX): Designed a high-contrast, dark-mode executive dashboard utilising advanced DAX measures, dual-axis temporal tracking, and cross-filtered UI mechanics.

## 🧠 The Detection Engine (PySpark Logic)
Rather than relying on static rules that trigger false positives as customer wealth grows, this engine utilises Adaptive Windowing to handle Concept Drift.

PYTHON CODE:
Establishing a bounded historical window to adapt to current customer lifestyles
history_window = Window.partitionBy('customer_id') \
                       .orderBy('timestamp') \
                       .rowsBetween(-60, -1)

Calculating dynamic spending baselines
df_features = df_features.withColumn(
    'historical_avg_amount',
    F.avg('amount').over(history_window)
)

The algorithm flags a transaction as a critical threat (risk_label = "Fraud") if the spend_multiplier exceeds 10x the customer's dynamically adjusting baseline, instantly detecting account takeovers regardless of whether the baseline is 5 AZN or 500,000 AZN.

## 📊 The Command Center (Dashboard Interface)
### 1. Segmented Threat Radars
(Insert PNG of Page 1 of your dashboard here)
![Segmented Threat Radars](link_to_your_page_1_image.png)

To prevent massive Corporate Wires from visually crushing standard Retail Swipes on the same axis, the dataset is strictly segmented into three auto-scaling portfolios:

* Retail Portfolio (CUST-): High-frequency, low-volume anomaly detection.
* Corporate Portfolio (CORP-): Low-frequency, massive-volume wire intercept.
* ATM Network (ATM-): Machine-level cash withdrawal anomalies.
* Insight: Plots Customer Lifetime Value (CLV) against Peak Risk Multiplier to instantly identify high-value hijacked accounts.

### 2. Temporal Threat Tracking & Asymmetric Vulnerability
(Insert PNG of Page 2 of your dashboard here)
![Temporal Tracking](link_to_your_page_2_image.png)

* Dual-Axis Timeline: Tracks total processed Volume (AZN) against the Fraud Risk % to detect coordinated, seasonal attacks by fraud rings, separating them from natural bank growth.
* The Asymmetry Matrix: While Retail Swipes account for the highest count of fraud attempts, the Donut Chart reveals that Corporate Wires account for 98.35% (947.05M AZN) of the monetary damage, dictating where human security personnel should be deployed.
* The Actionable Hit-List: A live, cross-filtered Matrix sorted by the highest Risk Multiplier, allowing human analysts to instantly freeze compromised targets (e.g., stopping CORP-341 from wiring 3.9M AZN).

### 🚀 Business Impact & Results
* Optimised False-Positive Ratio: Scanned 4.14 Billion AZN in transaction volume and accurately isolated the threat to just 0.58% of total transactions (29K anomalies).
* Massive ROI: Prevented the loss of 962.98 Million AZN.
* Resource Reallocation: Proved mathematically that manual security reviews should be entirely focused on the CORP- network, while CUST- and ATM- networks can be handled by automated freezing protocols.
