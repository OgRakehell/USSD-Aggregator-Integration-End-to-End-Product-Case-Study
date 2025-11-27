# Findings & Insights – Latency + User Journey Review

This section contains fictional but realistic analysis derived from a reconstructed USSD aggregator project.

## 1. Latency Analysis
Baseline (Before Integration)

- P50 (median): 1.9s

- P95: 4.0s

- P99: 7.2s

Root causes:

- Round-trip routing through legacy middleware

- No local caching for balance enquiry

- High aggregation delay during peak hours

  ## 2. After Optimization
Post-Integration

- P50: 0.7s

- P95: 1.5s

- P99: 2.4s

Improvements driven by:

- Direct aggregator → switch connection

- Connection pooling

- Reduced XML payload size

- Standardized timeout handling

## 3. Product Insights
#### Insight 1 – User Drop-offs

- 40% of airtime failures came from:

- confusing menu steps

- poor error messages

- unnecessary PIN re-entry

#### Insight 2 – Menu Optimization

- Reducing the journey from 5 steps → 3 steps improved:

- Completion rate by 22%

- Average handling time (AHT)

#### Insight 3 – Mobility Network Variance

- MTN traffic required priority routing due to volume.
