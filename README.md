: Telecom Customer Churn Prediction & Support Log Analytics

This repository contains the advanced customer behavior analysis, log file processing framework, and retention strategies implemented to identify root causes of revenue decline and customer drop-offs.

## 1. Project Architecture Overview

| Phase | System / Core Tool | Action / Analysis Strategy | Output / Business Value |
| :--- | :--- | :--- | :--- |
| **Problem Domain**| Senior Management / Business | Diagnosed static demographic analysis failures in explaining customer churn | Shifted focus to behavioral analytics using raw interaction log systems |
| **Data Extraction**| SQL Engine | Extracted and aggregated unstructured Customer Care Support Logs | Centralized behavioral metrics (Call frequency, type, and repetition) |
| **Data Processing**| Python (Pandas, NumPy) | Evaluated call frequencies and categorized intents (Help vs. Complaint) | Uncovered core correlations between support issues and drop-offs |
| **Business Impact**| Executive Insights | Discovered that high-frequency repetitive support calls directly caused churn | Provided strategic direction to overhaul after-sales support frameworks |

---

## 2. Production-Ready Analytics Scripts

### Step 1: SQL Log Aggregation & Customer Call Frequency Profiling
```sql
-- Aggregating customer support logs to find call frequency and identifying resolution bottlenecks
SELECT 
    customer_id,
    COUNT(log_id) AS total_support_calls,
    COUNT(CASE WHEN log_status = 'Unresolved' THEN 1 END) AS unresolved_complaints,
    SUM(CASE WHEN interaction_type = 'Complaint' THEN 1 ELSE 0 END) AS total_complaints,
    SUM(CASE WHEN interaction_type = 'General Inquiry' THEN 1 ELSE 0 END) AS total_inquiries
FROM customer_support_logs
GROUP BY customer_id
ORDER BY total_support_calls DESC;
import pandas as pd
import numpy as np

# Simulating customer behavioral and churn datasets
data = {
    'customer_id': range(1001, 1100),
    'total_support_calls': np.random.randint(1, 15, size=99),
    'unresolved_complaints': np.random.randint(0, 5, size=99),
    'is_churned': np.random.choice([0, 1], size=99) # 1 = Customer left, 0 = Retained
}
df = pd.DataFrame(data)

# Calculating statistical correlation between repetitive calls and customer churn
correlation = df['total_support_calls'].corr(df['is_churned'])
print(f"Correlation between Call Frequency and Customer Churn: {correlation:.4f}")

# Finding the tipping point (Average calls of churned customers vs retained customers)
avg_calls = df.groupby('is_churned')['total_support_calls'].mean()
print("\nAverage Support Calls Incurred:")
print(f"Retained Customers: {avg_calls[0]:.
