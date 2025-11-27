  # Approach


1. Diagnose

Before integration, I analyzed existing USSD logs to identify:

- high-failure nodes

- frequent timeout paths

- endpoints exceeding 3-second latency

- mismatches between user expectation and system output

I produced a simple decision-tree visualization showing where users were most likely to drop off.



2. Integrate

I collaborated with the aggregator and Engineering to align:

- API payload structure

- Authentication mechanism

- Transaction lifecycle behavior

- Error-handling logic

- Callback/update flows



3. Validate (UAT + Performance Testing)

I created and executed UAT test cases covering:

- happy paths

- negative paths

- invalid inputs

- aggregator downtime

- delayed responses

- edge-case flows (e.g., input errors, session expiry)

- Latency testing was conducted with Engineering, targeting:

P95 < 1.5s

P99 < 2.0s

USSD is unforgiving, so achieving these targets was crucial.


