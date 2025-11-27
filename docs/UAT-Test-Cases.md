# USSD Aggregator Integration – UAT Test Cases
This document captures the full User Acceptance Test (UAT) scenarios executed for the fictional USSD Aggregator Integration Project.  
Due to sensitivity and intellectual property concerns, this is a reconstructed portfolio version based on my real experience with digital channels.

---

## 1. Test Scope
- Complete USSD flow routed through a new aggregator.
- Supported actions: Airtime Purchase, Funds Transfer, Balance Enquiry, Bill Payments.
- Channels: USSD → Aggregator → Bank Core → Downstream Services.

---

## 2. Test Environment
- Aggregator: Sandbox and Staging 
- Bank Systems: USSD Engine, Payment Switch, Notification Service
- Mobile Network Emulator: Enabled
- Connectivity: Secure VPN/Whitelisted IP

---

## 3. Key Test Scenarios

### 3.1 Airtime Purchase
| Test Case ID | Scenario | Steps | Expected Result |
|--------------|----------|--------|------------------|
| AT-01 | Airtime Self | Dial code → Select Airtime → Enter Amount | Successful debit + instant recharge |
| AT-02 | Airtime for Others | Phone number input → Amount | Success + correct beneficiary |
| AT-03 | Insufficient Funds | Balance < amount | User-facing “Insufficient Funds” |
| AT-04 | Telco Timeout | Aggregator delay | Graceful failure + no debit |

---

### 3.2 Funds Transfer
| ID | Scenario | Steps | Expected Result |
|----|----------|--------|----------------|
| FT-01 | Same bank transfer | Enter account → amount → PIN | Success + reference returned |
| FT-02 | Interbank | Same as above | Routing handled by aggregator switch |
| FT-03 | Wrong PIN | Incorrect PIN | User-facing “Invalid PIN” |
| FT-04 | NIP Timeout | 5s delay introduced | Reversal triggered or no debit |

---

### 3.3 Balance Enquiry
| ID | Scenario | Expected Result |
|----|----------|----------------|
| BE-01 | Successful check | Balance retrieved < 1.5s (P95 target) |
| BE-02 | Core Banking Slow | Retry or graceful fail message |

---

### 3.4 Bill Payments
| ID | Scenario | Expected Result |
|----|----------|----------------|
| BL-01 | DSTV | Success + token |
| BL-02 | Electricity | Success + token |
| BL-03 | Biller Down | Error mapped to user-friendly message |

---

## 4. Acceptance Criteria
- 98% transaction success rate for Airtime & Balance Enquiry.
- P95 latency ≤ 1.5s across all journeys.
- Zero silent fails.
- All system fails mapped to clean user messages.

