## Approach (How I Executed the Integration Work)

The project followed a three-phase workflow designed for clarity, speed, and reduced friction across teams.

### 1. Diagnose (Understand the Problem Before Touching Anything)

I began by analyzing historical USSD logs and monitoring dashboards to identify:

- nodes with high failure rates

- timeout-prone transaction paths

- endpoints exceeding the 3-second USSD threshold

- UX mismatches between system responses and user expectations

This produced a decision-tree map showing where users most frequently dropped off — the foundation for the integration logic.

### 2. Integrate (Design the Interaction Between Aggregator ↔ Bank Systems)

I collaborated with both the Aggregator team and Engineering to align:

- API payload standards

- session handling formats

-  and security flow

- transaction lifecycle behavior (initiate → authorize → confirm)

- error mapping (raw aggregator errors → user-friendly messages)

- callback/update sequences

This phase established the “contract” that ensures consistency across all USSD menus and services.

### 3. Validate (UAT + Performance Stress Testing)

I designed and executed a comprehensive test suite covering:

- happy paths

- negative and invalid-input scenarios

- latency spikes

- aggregator downtime

- reconnection behavior

- transaction reversals and edge-case journeys

  Performance testing targeted:

- P95 < 1.5 seconds

- P99 < 2.0 seconds

Achieving this was essential because USSD terminates sessions aggressively if responses delay.
