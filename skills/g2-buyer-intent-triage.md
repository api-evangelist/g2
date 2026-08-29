---
name: g2-buyer-intent-triage
description: >-
  Pull G2 buyer intent signals for a product, rank the accounts showing intent, and enrich the
  top accounts with the competitors they are also evaluating. Read-only and non-billable.
api: G2 API
version: v2
base_url: https://data.g2.com
operations:
  - getProducts
  - getCurrentUserProducts
  - getBuyerIntentInteractions
  - getGlobalBuyerIntentInteractions
  - getSandboxBuyerIntentInteractions
  - getProductCompetitors
scopes:
  - openid
  - profile
  - products.read
  - buyer_intent.read
---

# Triage G2 buyer intent for a product

Read-only. Nothing in this skill spends credits or writes data.

## Preconditions

- A bearer token: either a Developer Portal account token (`Authorization: Bearer <token>`) or an
  OAuth access token. Account tokens expire one year after creation.
- The account must be entitled to Buyer Intent. Without it every intent call returns
  `403 "Your current plan does not provide access to this resource"`. **Do not retry that
  error** — it is a commercial gate, not a transient failure.

## Steps

1. **Resolve the product.** Call `getCurrentUserProducts` (`GET /api/v2/users/me/products`) to
   list products the account owns. To resolve a product you do not own, call `getProducts`
   (`GET /api/v2/products`) with `filter[slug][]` or `filter[product_name_eq]`. Keep the UUID.

2. **Rehearse first if you are unsure of the shape.** `getSandboxBuyerIntentInteractions`
   (`GET /api/sandbox/products/{subject_product_id}/buyer_intent`) mirrors the live call and
   costs nothing. It is the only sandbox path in the contract.

3. **Pull the signals.** `getBuyerIntentInteractions`
   (`GET /api/v2/products/{subject_product_id}/buyer_intent`). Page with `page[size]` (default
   25, max 250) and follow the opaque `page[after]` cursor from the response's
   `cursor_pagination.next`. For a product-agnostic sweep use
   `getGlobalBuyerIntentInteractions` (`GET /api/v2/buyer_intent`).

4. **Window the pull.** Use `filter[created_at_gt]` / `filter[created_at_lt]` (or the
   `updated_at` pair) to fetch only what changed since the last run. There are no events —
   polling with these filters is the supported incremental pattern.

5. **Sort deliberately.** `sort` accepts only the values the operation enumerates
   (`intent_score` / `-intent_score` on this surface). Anything else is a `400` whose title
   lists the allowed set.

6. **Enrich the top accounts.** For each product of interest call `getProductCompetitors`
   (`GET /api/v2/products/{product_id}/competitors`) with `include=categories` to name the
   alternatives buyers are weighing.

## Rules

- **Rate limit:** 100 requests/second per source IP, enforced by Cloudflare. Exceeding it
  blocks the IP for 60 seconds. G2 returns **no** `RateLimit-*` or `Retry-After` headers, so
  shape your own request rate — you will get no runtime warning.
- **Compound documents:** an unknown value in `include` or `fields[...]` is a hard `400` that
  echoes the bad value. Only use relationship names the operation's `include` description lists.
- **Errors** are JSON:API objects (`{"errors":[{"status","title","links","source"}]}`), not
  RFC 9457 problem+json, and carry no stable machine code. Branch on HTTP status first. See
  `errors/g2-problem-types.yml`.
- Do **not** call anything under `/g2_activate/` from this skill. That surface spends credits.
