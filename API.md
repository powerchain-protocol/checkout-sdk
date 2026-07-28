# PowerChain Checkout™ UI SDK

# API Reference

**Enterprise Foundation Edition**  
**Version:** `1.0.0-beta.0`  
**API Version:** `v1`  
**Base Path:** `/api/v1`  
**Platform:** PowerChain Platform™  
**Release Status:** Beta Foundation

---

# Table of Contents

- Overview
- Design Principles
- API Versioning
- Base URL
- Authentication
- Request Lifecycle
- Response Format
- Error Model
- Pagination
- Filtering & Sorting
- Idempotency
- Rate Limits
- API Resources
- Checkout API
- Payments API
- Billing API
- Wallet API
- Digital Assets API
- Orders API
- Customer API
- Treasury API
- Settlement API
- Analytics API
- Webhooks
- Event Model
- SDK Support
- API Governance
- Deprecation Policy
- Changelog

---

# Overview

PowerChain Checkout™ UI SDK exposes a modern REST API for building enterprise financial applications.

The API is designed for:

- Commerce platforms
- Checkout experiences
- Payment orchestration
- Wallet infrastructure
- Digital assets
- Treasury operations
- Settlement processing
- Enterprise analytics
- AI-powered financial workflows

---

# API Design Principles

The API follows several core principles.

## RESTful

Resources are represented using predictable REST endpoints.

```
/payments

/orders

/customers

/assets

/wallets
```

---

## Resource Oriented

Each endpoint represents a business entity.

Example

```
Checkout Session

↓

Payment Intent

↓

Settlement

↓

Receipt
```

---

## Stateless

Every request contains all required authentication and context.

---

## JSON

Requests and responses use UTF-8 JSON.

```
Content-Type:
application/json
```

---

## Secure by Default

Supported authentication methods include:

- OAuth 2.0
- OpenID Connect
- JWT Bearer Tokens
- API Keys
- Enterprise SSO

---

# API Versioning

Current version

```
v1
```

Base path

```
/api/v1
```

Example

```
POST /api/v1/payments
```

Future versions

```
/api/v2
```

Breaking changes are introduced only through new API versions.

---

# Base URL

Production

```
https://api.powerchain.example/api/v1
```

Sandbox

```
https://sandbox-api.powerchain.example/api/v1
```

Demo

```
https://demo-api.powerchain.example/api/v1
```

Mock

```
http://localhost:4000/api/v1
```

Runtime selection should be controlled through configuration rather than application code.

---

# Runtime Profiles

```
Mock

↓

Demo

↓

Sandbox

↓

Production
```

| Profile | Purpose |
|----------|----------|
| Mock | Local development with deterministic data |
| Demo | Interactive product demonstrations |
| Sandbox | Integration testing against non-production services |
| Production | Live customer workloads |

---

# Authentication

Supported methods

- OAuth 2.0
- OpenID Connect
- JWT
- API Keys
- Enterprise SSO

Example

```
Authorization: Bearer eyJhbGciOi...
```

API Key

```
X-API-Key:
pc_live_xxxxxxxxx
```

---

# Request Lifecycle

```
Client

↓

Authentication

↓

Validation

↓

Authorisation

↓

Business Logic

↓

Persistence

↓

Events

↓

Response
```

---

# Standard Response

Success

```json
{
  "success": true,
  "data": {},
  "meta": {
    "requestId": "req_123456789"
  }
}
```

---

Error

```json
{
  "success": false,
  "error": {
    "code": "PAYMENT_DECLINED",
    "message": "Payment could not be authorised."
  }
}
```

---

# Error Model

Every error follows the same contract.

```json
{
  "error": {
    "code": "INVALID_REQUEST",
    "message": "Validation failed.",
    "details": [],
    "requestId": "req_xxxxxx"
  }
}
```

---

## Common Error Codes

| Code | Description |
|------|-------------|
| INVALID_REQUEST | Request validation failed |
| UNAUTHENTICATED | Missing credentials |
| UNAUTHORISED | Permission denied |
| RESOURCE_NOT_FOUND | Resource not found |
| RATE_LIMIT_EXCEEDED | Too many requests |
| PAYMENT_DECLINED | Provider declined payment |
| WALLET_ERROR | Wallet operation failed |
| INTERNAL_ERROR | Unexpected server error |

---

# Pagination

Cursor pagination is recommended.

Example

```
GET /payments?limit=25&cursor=abc123
```

Response

```json
{
  "data": [],
  "page": {
    "nextCursor": "def456",
    "hasNext": true
  }
}
```

---

# Filtering

```
GET /payments?status=succeeded
```

```
GET /orders?customerId=cus_001
```

---

# Sorting

```
GET /payments?sort=-createdAt
```

Ascending

```
sort=amount
```

Descending

```
sort=-amount
```

---

# Idempotency

POST operations should include an idempotency key.

```
Idempotency-Key:
checkout-001
```

This prevents duplicate financial transactions.

---

# Rate Limits

Default tiers

| Tier | Requests / Minute |
|-------|------------------:|
| Developer | 300 |
| Business | 2,000 |
| Enterprise | 10,000 |
| Institutional | 50,000 |
| Partner | Custom |

Headers

```
X-RateLimit-Limit

X-RateLimit-Remaining

Retry-After
```

---

# API Resources

```
/auth

/users

/organisations

/customers

/cart

/orders

/checkout

/payments

/refunds

/wallets

/assets

/billing

/subscriptions

/treasury

/settlement

/webhooks

/events

/analytics

/admin
```

---

# Authentication API

```
POST /auth/login

POST /auth/logout

POST /auth/register

POST /auth/token/refresh

GET /auth/session
```

---

# Checkout API

```
POST /checkout/sessions

GET /checkout/sessions/{id}

PATCH /checkout/sessions/{id}

DELETE /checkout/sessions/{id}
```

Create session

```json
{
  "currency": "EUR",
  "amount": 125,
  "customerId": "cus_001"
}
```

---

# Payments API

```
POST /payments

GET /payments

GET /payments/{id}

POST /payments/{id}/capture

POST /payments/{id}/cancel

POST /payments/{id}/refund
```

Example

```json
{
  "amount": 100,
  "currency": "EUR",
  "paymentMethod": "card"
}
```

---

# Orders API

```
GET /orders

POST /orders

GET /orders/{id}

PATCH /orders/{id}
```

---

# Cart API

```
GET /cart

POST /cart/items

PATCH /cart/items/{id}

DELETE /cart/items/{id}
```

---

# Billing API

```
GET /billing/customers

POST /billing/invoices

GET /billing/subscriptions

POST /billing/subscriptions
```

---

# Wallet API

```
GET /wallets

POST /wallets/connect

POST /wallets/disconnect

POST /wallets/sign

POST /wallets/send
```

---

# Digital Assets API

```
GET /assets

POST /assets

GET /assets/{id}

POST /assets/{id}/transfer
```

---

# Treasury API

```
GET /treasury/accounts

POST /treasury/transfers

GET /treasury/balances
```

---

# Settlement API

```
POST /settlement/run

GET /settlement/{id}

GET /settlement/reports
```

---

# Analytics API

```
GET /analytics/payments

GET /analytics/customers

GET /analytics/revenue

GET /analytics/settlements
```

---

# Webhooks

Webhook endpoint

```
POST /webhooks
```

Example events

```
payment.created

payment.authorised

payment.failed

payment.refunded

checkout.completed

wallet.connected

wallet.disconnected

settlement.completed
```

---

# Event Format

```json
{
  "id": "evt_123",
  "type": "payment.succeeded",
  "createdAt": "2026-01-01T12:00:00Z",
  "data": {}
}
```

---

# API Governance

Every endpoint requires:

- API review
- Security review
- Documentation
- OpenAPI specification
- SDK generation
- Integration tests
- Backwards compatibility review

---

# OpenAPI Pipeline

```
TypeScript

↓

OpenAPI 3.1

↓

SDK Generator

↓

Developer Portal

↓

TypeDoc

↓

MDX Documentation
```

---

# SDK Support

Official SDKs

- TypeScript
- React
- React Native
- Next.js
- CLI
- Partner SDK

Future SDKs

- Vue
- Angular
- Flutter
- Swift
- Kotlin

---

# Deprecation Policy

Deprecated endpoints remain available throughout the current major API version.

Deprecations include:

- Documentation notice
- Changelog entry
- Migration guide
- Sunset timeline

Breaking changes are introduced only in a new API version.

---

# Best Practices

- Use HTTPS for all requests.
- Always send an `Idempotency-Key` for payment creation.
- Prefer cursor-based pagination.
- Validate webhook signatures before processing events.
- Store only the minimum data necessary to fulfil your business requirements.
- Monitor rate-limit headers and implement retries with exponential backoff for transient failures.

---

# Related Documentation

- `README.md`
- `ARCHITECTURE.md`
- `SECURITY.md`
- `VERSIONING.md`
- `COMPATIBILITY.md`
- `docs/api/`
- `docs/sdk/`
- `docs/security/`
- `docs/architecture/`

---

# Changelog

## v1.0.0-beta.0

- Initial Enterprise Foundation API
- REST `/api/v1` baseline
- Checkout API
- Payment orchestration API
- Wallet API
- Billing API
- Settlement API
- Analytics API
- OpenAPI 3.1 foundation
- Enterprise authentication model
- Webhook event framework
- Runtime profile support (Mock, Demo, Sandbox, Production)

---

<p align="center">

**PowerChain Checkout™ UI SDK**  
**Enterprise Foundation Edition**  
**API Version:** `v1`  
**Platform:** PowerChain Platform™  
**Documentation Standard:** OpenAPI 3.1 + TypeDoc + MDX + Storybook

</p>
