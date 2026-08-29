---
name: g2-research-board-curation
description: >-
  Create and curate a G2 research board — the only writable, reversible resource in the G2 API
  and the surface G2 exposes to agents over MCP.
api: G2 API
version: v2
base_url: https://data.g2.com
operations:
  - listResearchBoards
  - createResearchBoard
  - getResearchBoard
  - updateResearchBoard
  - deleteResearchBoard
  - listResearchBoardProducts
  - addProductToResearchBoard
  - batchAddProductsToResearchBoard
  - batchRemoveProductsFromResearchBoard
  - removeProductFromResearchBoard
  - getProducts
scopes:
  - openid
  - profile
  - products.read
  - research_boards.read
  - research_boards.write
---

# Curate a G2 research board

Research boards are the only resource in the G2 API an agent can create, change and delete.
They are also the only writes exposed through the G2 MCP server
(`create_research_board`, `update_research_board`, `delete_research_board`,
`add_products_to_research_board`, `remove_products_from_research_board`).

## Steps

1. **List existing boards.** `listResearchBoards` (`GET /api/v2/users/me/research_boards`)
   before creating anything — **create is not idempotent**, and calling it twice produces two
   boards.

2. **Create.** `createResearchBoard` (`POST /api/v2/users/me/research_boards`). Keep the
   returned `uuid`.

3. **Resolve products.** `getProducts` with `filter[slug][]` or `filter[product_name_eq]` to
   turn names into UUIDs. Do not guess UUIDs.

4. **Add products.**
   - One product: `addProductToResearchBoard`
     (`POST /api/v2/users/me/research_boards/{research_board_uuid}/products`).
   - Several: `batchAddProductsToResearchBoard` (`.../products/batch_create`) — one round trip,
     and the operation the MCP tool `add_products_to_research_board` maps onto.

5. **Read back.** `listResearchBoardProducts` to confirm membership.

## Reversibility

| Action | Reversal | Window |
|---|---|---|
| `createResearchBoard` | `deleteResearchBoard` | none stated |
| `addProductToResearchBoard` / batch | `removeProductFromResearchBoard` / `batch_destroy` | none stated |
| `updateResearchBoard` (PATCH) | **none** | — |

`updateResearchBoard` is a lossy overwrite: there is no version history, no ETag and no restore
operation. **Read the board with `getResearchBoard` and keep the prior state before you PATCH**,
or the previous contents are gone.

G2 states no retention or restore window for deletes. Do not assume one exists.

## Rules

- Requires `research_boards.write`; without it you get `403 "Missing ... scope"`.
- Errors are JSON:API error objects, not RFC 9457.
- 100 req/s per source IP; no rate-limit headers.
