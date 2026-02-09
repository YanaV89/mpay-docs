# Authentication & Signatures

All requests to the m-pay API must be authenticated using a **digital signature**.

The signature guarantees:
- Merchant identification
- Request integrity
- Protection against data tampering

Requests without a valid signature are rejected.

---

## Merchant Credentials

Each merchant is provided with:

- **Account** (merchant account number)
- **Secret keys** (one or two, depending on configuration)
- **Signature algorithm**

Secret keys must be stored securely and **never exposed client-side**.

---

## Supported Signature Algorithms

The following algorithms are supported:

- **MD5**
- **HMAC-SHA256**

The algorithm used must match the one configured for the merchant account.

---

## Signature Generation Rules

Signature generation follows strict rules:

1. Collect all request parameters except `signature`
2. Sort parameters **alphabetically by parameter name**
3. Concatenate **only parameter values**
4. Append merchant secret keys
5. Apply the hashing algorithm
6. Convert the result to **uppercase**

Empty parameters must not be included.

---

## Signature Example (MD5)

### Parameters

# Authentication & Signatures

All requests to the m-pay API must be authenticated using a **digital signature**.

The signature guarantees:
- Merchant identification
- Request integrity
- Protection against data tampering

Requests without a valid signature are rejected.

---

## Merchant Credentials

Each merchant is provided with:

- **Account** (merchant account number)
- **Secret keys** (one or two, depending on configuration)
- **Signature algorithm**

Secret keys must be stored securely and **never exposed client-side**.

---

## Supported Signature Algorithms

The following algorithms are supported:

- **MD5**
- **HMAC-SHA256**

The algorithm used must match the one configured for the merchant account.

---

## Signature Generation Rules

Signature generation follows strict rules:

1. Collect all request parameters except `signature`
2. Sort parameters **alphabetically by parameter name**
3. Concatenate **only parameter values**
4. Append merchant secret keys
5. Apply the hashing algorithm
6. Convert the result to **uppercase**

Empty parameters must not be included.

---

## Signature Example (MD5)

### Parameters

amount=100.25
amountcurr=EUR
account=ACC123
number=ORD001


### Concatenated string



100.25EURACC123ORD001SECRETKEY


### Result



A94A8FE5CCB19BA61C4C0873D391E987


---

## Signature Validation

All responses from m-pay are also signed.

Merchants must:
1. Recalculate the response signature
2. Compare it with the received `signature`
3. Accept the response only if signatures match

---

## Security Recommendations

- Generate signatures server-side only
- Never log secret keys
- Always use HTTPS
- Validate response signatures
