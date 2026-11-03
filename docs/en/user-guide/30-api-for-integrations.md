---
title: "API for integrations"
description: "Programs — a 1C exchange, BI reports, your own scripts — work with xtab through its REST API."
version: "v0.5.0"
lang: "en"
order: 30
---

Programs — a 1C exchange, BI reports, your own scripts — work with xtab through its REST API.

- Get a token: **account menu → API tokens** (for an integration, prefer a service account, see “API tokens” above).
- The address of the API is the address of xtab plus `/api/v1`, e.g. `https://xtab.example.ru/api/v1/tables/{table}/records`. Every method is described in the OpenAPI specification of the documentation set.
- The token goes in a header: `Authorization: Bearer xtab_…`. A token in the address or in a cookie is not accepted.
- A token acts with the rights of its owner, but only within the permissions and bases chosen. Without a permission, xtab answers `403` and names it; a revoked, expired token or one from a foreign address gets `401`.
- The rate of requests is limited: by default 20 a second per token, with room for 50 in a row. Beyond the limit the answer is `429`; the header `Retry-After` says in how many seconds to retry, and `RateLimit` how many requests are left.
