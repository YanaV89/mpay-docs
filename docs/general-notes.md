# General Notes

The m-pay Merchant API is designed for secure processing of online payments, wallet payments, recurring transactions, refunds, and payouts using server-to-server communication.

## Technical Requirements

- **Protocol:** HTTPS only
- **HTTP Method:** POST
- **Encoding:** UTF-8
- **Request format:** `application/x-www-form-urlencoded`

All requests must be sent from a **secure backend environment**.

Client-side requests are not allowed.

---

## Authentication

Each request must contain a valid **digital signature** generated using merchant secret keys.

Requests without a valid signature will be rejected.

---

## Important Rules

- Redirects and browser responses are **not proof of payment**
- Always confirm payment result via **Payment Status**
- Store `transID` for every transaction
- Do not retry payment execution blindly

---

## Environments

| Environment | Base URL |
|------------|----------|
| Test | `https://test.ecom.m-pay.me` |
| Production | `https://ecom.m-pay.me` |
