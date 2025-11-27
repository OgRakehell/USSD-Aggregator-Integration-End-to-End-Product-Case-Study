# API Mapping – USSD Aggregator Integration

This document outlines the fictional API structure used during the aggregator integration project.  

---

## 1. Base URL (Sandbox)
`https://sandbox.aggregator.com/api/v1/ussd`

---

## 2. Endpoints

### 2.1 Initialize Session
**POST** `/session/init`

#### Sample Request
```json
{
  "msisdn": "2348012345678",
  "sessionId": "abc123",
  "channel": "USSD",
  "entryCode": "*123#"
}

```
#### Sample Response

```json
{
  "status": "success",
  "message": "Session started",
  "context": "STEP1"
}
```
### 2.2 Airtime Purchase

**POST** `/transactions/airtime`

### Request
```json
{
  "msisdn": "2348012345678",
  "amount": "500",
  "beneficiary": "2348098765432",
  "ref": "TXN-1002922"
}
```






