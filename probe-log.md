
## With a Developer Portal token (same day)

| call | result |
|---|---|
| `data.g2.com/api/v2/*` with default Python UA | 403, Cloudflare 1010 `browser_signature_banned` (not the token) |
| same with an identifying User-Agent, `Authorization: Bearer` | categories 200; products 200 but empty; product by slug 404; badges/competitors 403; grid 400 (needs UUID + `reports.read`) |
| `Authorization: Token token=` | 401 Bad Credentials everywhere |
| `www.g2.com/chat_gpt_plugin/reports` | 200 with the token; Summer 2023 Grids, 5 per quadrant, season params ignored |
