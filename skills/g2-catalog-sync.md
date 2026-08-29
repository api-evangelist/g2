---
name: g2-catalog-sync
description: >-
  Incrementally sync the G2 product, vendor, category and review catalog into a local store
  using cursor pagination and updated_at windows. Read-only.
api: G2 API
version: v2
base_url: https://data.g2.com
operations:
  - getCategories
  - getCategory
  - getProducts
  - getProduct
  - getVendors
  - getVendor
  - getProductReviews
  - getProductRatings
  - getProductFeatures
  - getAllProductFeatures
  - getProductMedals
  - getDataSolutionsReviews
scopes:
  - openid
  - profile
  - products.read
  - products.reviews.read
  - vendors.read
---

# Sync the G2 catalog

G2 publishes **no events and no webhooks for catalog change**. Polling with `updated_at`
filters is the supported incremental pattern.

## Steps

1. **Taxonomy first.** `getCategories` (`GET /api/v2/categories`) with
   `include=children,parent,ancestors,descendants` to build the category tree. Categories are
   self-referencing; resolve the hierarchy before products so category ids resolve locally.

2. **Products.** `getProducts` (`GET /api/v2/products`) with:
   - `include=categories,discussions,screenshots,vendor` to pull related records in the same
     round trip via the JSON:API `included` array,
   - `fields[products]=...` to trim the payload,
   - `filter[updated_at_gt]=<last successful run>` for the incremental window,
   - `page[size]=250` and the `page[after]` cursor to walk the set.

3. **Vendors.** `getVendors` (`GET /api/v2/vendors`), same pagination discipline.

4. **Per-product detail.** For each changed product:
   `getProductReviews` (`/reviews`), `getProductRatings` (`/product_ratings/{product_id}`),
   `getProductFeatures` (`/features`), `getProductMedals` (`/badges`).
   `getAllProductFeatures` (`GET /api/v2/products/features`) returns features grouped by
   product and is cheaper than per-product calls on a wide sync.

5. **Enriched reviews (entitlement required).** If the account holds G2 Data Solutions, use
   `getDataSolutionsReviews` (`GET /api/v2/data_solutions/reviews`) — the same review data in a
   flat attribute structure rather than the JSON:API relationship graph.

## Rules

- **Checkpoint on the cursor, not the page number.** `page[after]` cursors are opaque and there
  is no total-count field. Persist the last cursor and the run start time.
- **Budget:** 100 req/s per source IP, 60-second block on exhaustion, and **no rate-limit
  headers**. A parallel sync sharing an egress IP with any other G2 caller — including an MCP
  agent session — shares the same budget.
- Page size default 25, max 250.
- `403 "Your current plan does not provide access to this resource"` is an entitlement wall.
  Record it and skip that resource; do not retry it on the next run.
- Errors are JSON:API error objects. See `errors/g2-problem-types.yml`.
