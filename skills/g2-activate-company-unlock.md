---
name: g2-activate-company-unlock
description: >-
  Spend G2 Activate credits to reveal the identity of companies showing intent. THIS SKILL
  SPENDS MONEY AND CANNOT BE UNDONE — it exists to make the guardrails explicit.
api: G2 API
version: v2
base_url: https://data.g2.com
operations:
  - getOrganizationCreditAccount
  - getOrganizationCreditDeductions
  - getG2ActivateLockedCompanies
  - postG2ActivateUnlockedCompanies
  - getG2ActivateUnlockedCompanies
  - getG2ActivateUnlockedCompany
  - createG2ActivateIndustrySearch
scopes:
  - openid
  - profile
  - g2_activate.read
  - g2_activate.write
consequence: irreversible-billable
---

# Unlock G2 Activate companies (billable, irreversible)

`postG2ActivateUnlockedCompanies` is the only operation in the entire G2 contract that spends
money, and there is **no refund, void, or re-lock operation**. Treat it as a point of no return.

## Guardrails — do all of these before writing

1. **Check the budget.** `getOrganizationCreditAccount`
   (`GET /api/v2/organization/{organization_id}/credit_account`), optionally with
   `include=deductions`. Review historical burn with `getOrganizationCreditDeductions`.

2. **Rehearse.** `getG2ActivateLockedCompanies`
   (`GET /api/v2/products/{product_id}/g2_activate/locked_companies`) returns masked companies
   plus an opaque `sig` per company. This call costs nothing and is the closest thing to a dry
   run G2 provides.

3. **Check what you already own.** `getG2ActivateUnlockedCompanies` lists companies already
   unlocked for the product. Anything already there needs no spend.

4. **Get human confirmation** of the exact company count and the credit cost before step 5.
   An agent should never take this step autonomously.

## The write

`postG2ActivateUnlockedCompanies`
(`POST /api/v2/products/{product_id}/g2_activate/unlocked_companies`)

- Accepts **1–25** opaque `sig` tokens per request. Over the cap, or with blank entries, you
  get `400 "sigs: must include at least one sig"`.
- **Idempotent by natural key.** G2 states in the contract: *"replaying an already-unlocked sig
  costs 0 credits and returns the existing record."* This is the only replay guarantee in the
  API, and it is the reason a retry after a network timeout is safe here.
- **Always returns 200.** Per-`sig` failures land in `meta.skipped[]`, not as HTTP errors.
  **You must read `meta.skipped[]`** — a 200 does not mean every company was unlocked.
- Then read `getG2ActivateUnlockedCompany`
  (`GET /api/v2/products/{product_id}/g2_activate/unlocked_companies/{id}`) for resolved contacts.
  A `404 "Company exists but has no unlock for this product"` is an entitlement outcome, not a
  missing record.

## Related

`createG2ActivateIndustrySearch`
(`POST /api/v2/products/{product_id}/g2_activate/industry_search`) matches free-text business
descriptions to NAICS industry names. It is a POST but it is not billable. It is the only
operation with a documented `503` — *"AI industry matcher is temporarily unavailable. Retry with
backoff."* — because it is backed by an LLM/embedding service. Retry that one with exponential
backoff.

## Scope errors

`403 "Missing g2_activate.read scope"` / `"Missing g2_activate.write scope"` mean the OAuth app
or token permission grid does not grant Activate. Fix it in the Developer Portal at
https://my.g2.com/developers; do not retry.
