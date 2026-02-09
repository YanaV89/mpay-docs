# Quick Start (API v1)

Follow these steps to integrate m-pay payments.

## Basic Flow
1. Receive `account` and `secret keys`
2. Register payment
3. Execute payment or redirect payer
4. Confirm result via Payment Status

```bash
POST https://test.ecom.m-pay.me/api/payment/start
POST https://test.ecom.m-pay.me/api/payment/execute
POST https://test.ecom.m-pay.me/api/payment/operate
