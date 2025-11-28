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

#### Request
```json
{
  "msisdn": "2348012345678",
  "amount": "500",
  "beneficiary": "2348098765432",
  "ref": "TXN-1002922"
}
```
#### Response
```json
{
  "status": "success",
  "code": "00",
  "description": "Airtime Top-up Successful",
  "reference": "AGG-98111232"
}
```

### 2.3 Funds Transfer

**POST** `/transactions/transfer`

#### Request
```json
{
  "sourceAccount": "1234567890",
  "destinationAccount": "0987654321",
  "amount": "2000",
  "narration": "USSD Transfer",
  "ref": "TXN-883712"
}
```
#### Possible Responses

```json
{ "code": "00", "message": "Transfer Successful" }
{ "code": "91", "message": "Issuer or Switch Inoperative" }
{ "code": "52", "message": "Insufficient Funds" }
```


## 3. High-Level Architecture

Below is the architecture for the fictional aggregator integration:

![Architecture Diagram](./assets/architecture-diagram.png)

